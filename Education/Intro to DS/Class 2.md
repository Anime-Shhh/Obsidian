[[Intro to DS]]
# Data Manipulation with [[pandas]]
* Series is 1D
* Data Frame is 2D
simple pandas df functions:
```python
df.head()
# head. Displays only the top few rows.
df.size()
#size. Gives the total number of data points.
#• example. df.size provides the total number of data cells
df.shape()
#shape. Gives the size of the data in rows and columns.
#• example. df.shape
df.describe()
#describe. Provides a summary of the data.
#• example. df.describe
```
![[Pasted image 20260129161535.png]]
Appending is used for when you ahve 2 or more datasets which are the same format. Essentially 2 different data sets for the same scenario which should be one big dataset. This just adds one dataset on top of another

```python
df.merge()
```
**Merge**: Merge is used to combine a dataset over a common factor over one key
![[Pasted image 20260129161909.png]]
### 2 different types of joins
![[Pasted image 20260129161945.png]]
#### Inner Joins: (A^B)
#### Outer Joins: (AUB)

![[Pasted image 20260129162144.png]]

### Split, Apply, combine
Three major ops
* Split - the data into groups based on certain criteria
* Apply - a function to each group independently.
* Combine - the results into a data structure.