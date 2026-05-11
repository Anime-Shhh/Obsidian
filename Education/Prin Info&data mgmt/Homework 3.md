### 1. Create the database schema

We must create the tables in an order that respects foreign key constraints (parent tables before child tables).

```SQL
CREATE TABLE students (
    sid INT PRIMARY KEY,
    name VARCHAR(255),
    age INT,
    gpa FLOAT
);

CREATE TABLE courses (
    cid VARCHAR(50) PRIMARY KEY,
    cname VARCHAR(255),
    deptid VARCHAR(50)
);

CREATE TABLE professors (
    ssn INT PRIMARY KEY,
    pname VARCHAR(255),
    address VARCHAR(255),
    phone VARCHAR(20),
    deptid VARCHAR(50)
);

CREATE TABLE sections (
    cid VARCHAR(50),
    section INT,
    ssn INT,
    PRIMARY KEY (cid, section),
    FOREIGN KEY (cid) REFERENCES courses(cid),
    FOREIGN KEY (ssn) REFERENCES professors(ssn)
);

CREATE TABLE enrollment (
    sid INT,
    cid VARCHAR(50),
    section INT,
    grade VARCHAR(2),
    PRIMARY KEY (sid, cid, section),
    FOREIGN KEY (sid) REFERENCES students(sid),
    FOREIGN KEY (cid, section) REFERENCES sections(cid, section)
);
```

### 2. Name of professors in the CS department
```SQL
SELECT pname 
FROM professors 
WHERE deptid = 'cs';
```

### 3. Students (sid) enrolled in CS department courses
```SQL
SELECT DISTINCT e.sid
FROM enrollment e
JOIN courses c ON e.cid = c.cid
WHERE c.deptid = 'cs';
```

### 4. Professors in CS who are NOT teaching any CS courses
```SQL
SELECT ssn, pname
FROM professors
WHERE deptid = 'cs'
AND ssn NOT IN (
    SELECT s.ssn 
    FROM sections s 
    JOIN courses c ON s.cid = c.cid 
    WHERE c.deptid = 'cs'
);
```

### 5. Number of courses offered by each department
```SQL
SELECT deptid, COUNT(cid) AS course_count
FROM courses
GROUP BY deptid;
```

### 6. Departments offering more than 10 courses
```SQL
SELECT deptid
FROM courses
GROUP BY deptid
HAVING COUNT(cid) > 10;
```

### 7. Names of students whose professor's name starts with 'M'
```SQL
SELECT DISTINCT st.name
FROM students st
JOIN enrollment e ON st.sid = e.sid
JOIN sections se ON e.cid = se.cid AND e.section = se.section
JOIN professors p ON se.ssn = p.ssn
WHERE p.pname LIKE 'M%';
```
### 8. Section size matrix per department
This requires a subquery to count students per section before grouping by department.
```SQL
SELECT c.deptid,
    COUNT(CASE WHEN sect_size.total < 30 THEN 1 END) AS small,
    COUNT(CASE WHEN sect_size.total >= 30 AND sect_size.total < 80 THEN 1 END) AS medium,
    COUNT(CASE WHEN sect_size.total >= 80 THEN 1 END) AS large
FROM (
    SELECT cid, section, COUNT(sid) AS total
    FROM enrollment
    GROUP BY cid, section
) AS sect_size
JOIN courses c ON sect_size.cid = c.cid
GROUP BY c.deptid;
```
### 9. Professors in large depts (>20 faculty) with more large sections than small/medium combined
```SQL
WITH SectionCounts AS (
    SELECT s.ssn,
           COUNT(CASE WHEN (SELECT COUNT(*) FROM enrollment e WHERE e.cid = s.cid AND e.section = s.section) >= 80 THEN 1 END) as large_count,
           COUNT(CASE WHEN (SELECT COUNT(*) FROM enrollment e WHERE e.cid = s.cid AND e.section = s.section) < 80 THEN 1 END) as small_med_count
    FROM sections s
    GROUP BY s.ssn
)
SELECT p.pname
FROM professors p
JOIN SectionCounts sc ON p.ssn = sc.ssn
WHERE p.deptid IN (
    SELECT deptid FROM professors GROUP BY deptid HAVING COUNT(*) > 20
)
AND sc.large_count > sc.small_med_count;
```
### 10. Percentage of students that failed each course (section)
```SQL
SELECT cid, section, 
       (COUNT(CASE WHEN grade IN ('D', 'F') THEN 1 END) * 100.0 / COUNT(*)) AS fail_percentage
FROM enrollment
GROUP BY cid, section;
```

### 11. Professor with the maximum percentage of failing students
```SQL
SELECT p.pname
FROM professors p
JOIN sections s ON p.ssn = s.ssn
JOIN enrollment e ON s.cid = e.cid AND s.section = e.section
GROUP BY p.ssn, p.pname
ORDER BY (COUNT(CASE WHEN e.grade IN ('D', 'F') THEN 1 END) * 100.0 / COUNT(*)) DESC
LIMIT 1;
```

### 12. Average percentage of students failing a course (Global Average)
``` SQL
SELECT (COUNT(CASE WHEN grade IN ('D', 'F') THEN 1 END) * 100.0 / COUNT(*)) AS avg_fail_rate
FROM enrollment;
```

### 13. Sections where the failure percentage is greater than the average
``` SQL
SELECT cid, section
FROM enrollment
GROUP BY cid, section
HAVING (COUNT(CASE WHEN grade IN ('D', 'F') THEN 1 END) * 100.0 / COUNT(*)) > (
    SELECT (COUNT(CASE WHEN grade IN ('D', 'F') THEN 1 END) * 100.0 / COUNT(*))
    FROM enrollment
);
```

### 14. Departmental Statistics Matrix
``` SQL
SELECT c.deptid,
    AVG(sect_totals.student_count) AS SPS,
    (COUNT(CASE WHEN e.grade = 'A' THEN 1 END) * 100.0 / COUNT(e.sid)) AS pct_A,
    (COUNT(CASE WHEN e.grade = 'B' THEN 1 END) * 100.0 / COUNT(e.sid)) AS pct_B,
    (COUNT(CASE WHEN e.grade = 'C' THEN 1 END) * 100.0 / COUNT(e.sid)) AS pct_C,
    (COUNT(CASE WHEN e.grade = 'D' THEN 1 END) * 100.0 / COUNT(e.sid)) AS pct_D,
    (COUNT(CASE WHEN e.grade = 'F' THEN 1 END) * 100.0 / COUNT(e.sid)) AS pct_F
FROM courses c
JOIN enrollment e ON c.cid = e.cid
JOIN (
    SELECT cid, section, COUNT(sid) as student_count 
    FROM enrollment GROUP BY cid, section
) AS sect_totals ON e.cid = sect_totals.cid AND e.section = sect_totals.section
GROUP BY c.deptid;
```