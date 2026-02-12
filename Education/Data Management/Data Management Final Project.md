initialize the db
```bash
createuser -s $(whoami)   # -s makes superuser; skip if user exists
createdb nyc_accidents
psql -d nyc_accidents
```

Make the schema for the db:
```sql
-- connect to the database first
\c nyc_accidents

CREATE TABLE accidents_raw (
  collision_id BIGINT PRIMARY KEY,
  crash_date DATE,
  crash_time TIME,
  crash_ts TIMESTAMP,           -- will fill from crash_date+crash_time
  borough TEXT,
  zip_code TEXT,
  latitude DOUBLE PRECISION,
  longitude DOUBLE PRECISION,
  location TEXT,
  on_street_name TEXT,
  cross_street_name TEXT,
  off_street_name TEXT,
  number_of_persons_injured INT,
  number_of_persons_killed INT,
  number_of_pedestrians_injured INT,
  number_of_pedestrians_killed INT,
  number_of_cyclist_injured INT,
  number_of_cyclist_killed INT,
  number_of_motorists_injured INT,
  number_of_motorists_killed INT,
  contributing_factor_vehicle_1 TEXT,
  contributing_factor_vehicle_2 TEXT,
  contributing_factor_vehicle_3 TEXT,
  contributing_factor_vehicle_4 TEXT,
  contributing_factor_vehicle_5 TEXT,
  vehicle_type_code_1 TEXT,
  vehicle_type_code_2 TEXT,
  vehicle_type_code_3 TEXT,
  vehicle_type_code_4 TEXT,
  vehicle_type_code_5 TEXT
);

```

import the actual csv into the db:
```sql
\copy accidents_raw(
    crash_date,
    crash_time,
    borough,
    zip_code,
    latitude,
    longitude,
    location,
    on_street_name,
    cross_street_name,
    off_street_name,
    number_of_persons_injured,
    number_of_persons_killed,
    number_of_pedestrians_injured,
    number_of_pedestrians_killed,
    number_of_cyclist_injured,
    number_of_cyclist_killed,
    number_of_motorists_injured,
    number_of_motorists_killed,
    contributing_factor_vehicle_1,
    contributing_factor_vehicle_2,
    contributing_factor_vehicle_3,
    contributing_factor_vehicle_4,
    contributing_factor_vehicle_5,
    collision_id,
    vehicle_type_code_1,
    vehicle_type_code_2,
    vehicle_type_code_3,
    vehicle_type_code_4,
    vehicle_type_code_5
)
FROM './Motor_Vehicle_Collisions_-_Crashes_20251202.csv'WITH (FORMAT csv, HEADER);
```

populate the crash_ts (time stamp)
```sql
-- create crash_ts from date + time
UPDATE accidents_raw
SET crash_ts = (crash_date::text || ' ' || crash_time::text)::timestamp
WHERE crash_ts IS NULL AND crash_date IS NOT NULL;

-- Check missing coords
SELECT COUNT(*) AS missing_coords FROM accidents_raw WHERE latitude IS NULL OR longitude IS NULL;

```


seperates missing cords and available cords into 2 different files
```sql
-- export rows WITH coords
\copy (SELECT collision_id, borough, zip_code, on_street_name, cross_street_name, latitude, longitude
       FROM accidents_raw
       WHERE latitude IS NOT NULL AND longitude IS NOT NULL)
TO '/Users/youruser/projects/nyc_project/valid_coords.csv' CSV HEADER;

-- export rows MISSING coords
\copy (SELECT collision_id, borough, zip_code, on_street_name, cross_street_name
       FROM accidents_raw
       WHERE latitude IS NULL OR longitude IS NULL)
TO '/Users/youruser/projects/nyc_project/missing_coords.csv' CSV HEADER;
```


run python script below in the same root folder of your project in order to use k means clustering to determine the correct missing value coordinates for the missing entries based on the "on street name" "off street name" and "cross street name" columns 

```python
import pandas as pd
from sklearn.cluster import KMeans
import numpy as np
from tqdm import tqdm

# --- LOAD ---
valid = pd.read_csv("valid_coords.csv")
missing = pd.read_csv("missing_coords.csv")

# Drop rows with missing borough in BOTH datasets
valid = valid[valid["borough"].notna()]
missing = missing[missing["borough"].notna()]

# Also remove empty-string boroughs
valid = valid[valid["borough"].str.strip() != ""]
missing = missing[missing["borough"].str.strip() != ""]

output_rows = []

boroughs = valid["borough"].unique()

for b in boroughs:
    print(
        f"\n==================== Processing borough: {b} ====================")

    valid_b = valid[valid["borough"] == b].copy()
    missing_b = missing[missing["borough"] == b].copy()

    print(f"  Existing coords in {b}: {len(valid_b):,}")
    print(f"  Missing coords in {b}:   {len(missing_b):,}")

    # ----------------------------------------------
    #      STEP 1 — Run KMeans on REAL coordinates
    # ----------------------------------------------
    k = max(5, len(valid_b) // 1500)
    print(f"  Running K-Means (k={k}) on {len(valid_b):,} points...")

    km = KMeans(n_clusters=k, random_state=42, n_init=5)
    km.fit(valid_b[["latitude", "longitude"]])

    centroids = km.cluster_centers_

    # Add cluster labels
    valid_b["cluster"] = km.labels_

    # ----------------------------------------------
    #    STEP 2 — Build lookup by (street, cross-street)
    # ----------------------------------------------
    street_lookup = (
        valid_b.groupby(["on_street_name", "cross_street_name"])
        .agg({"latitude": "mean", "longitude": "mean"})
        .reset_index()
        .rename(columns={"latitude": "mean_lat", "longitude": "mean_lon"})
    )

    # Convert to dict for fast lookup
    street_dict = {
        (row.on_street_name, row.cross_street_name): (row.mean_lat, row.mean_lon)
        for _, row in street_lookup.iterrows()
    }

    # ----------------------------------------------
    #     STEP 3 — Impute each missing row
    # ----------------------------------------------
    assigned = []

    for idx, row in tqdm(missing_b.iterrows(), total=len(missing_b)):
        key = (row["on_street_name"], row["cross_street_name"])

        if key in street_dict:
            # Use the average coord of that street pair
            s_lat, s_lon = street_dict[key]
        else:
            # Fallback → use borough centroid average
            s_lat, s_lon = valid_b["latitude"].mean(
            ), valid_b["longitude"].mean()

        # Compute nearest centroid
        dist = np.sqrt((centroids[:, 0] - s_lat) **
                       2 + (centroids[:, 1] - s_lon) ** 2)
        closest = np.argmin(dist)
        c_lat, c_lon = centroids[closest]

        assigned.append(
            {
                "collision_id": row["collision_id"],
                "borough": b,
                "imputed_latitude": c_lat,
                "imputed_longitude": c_lon,
                "method": "kmeans_street",
            }
        )

    output_rows.extend(assigned)
    print(f"  → Finished imputing {len(assigned):,} rows for {b}")

# Save final file
df_out = pd.DataFrame(output_rows)
df_out.to_csv("imputed_coordinates.csv", index=False)
print("\nFINISHED — Saved to imputed_coordinates.csv")

```