 ![[IMG_5404.jpg|700x410]]
 
 ###  

### 1. Query to get SID, name, age of students enrolled in CS courses where name starts with H

```SQL
SELECT s.sid, s.name, s.age
FROM Students s, EnrolledIn e, Courses c
WHERE s.sid = e.sid
  AND e.cid = c.cid
  AND c.dept = 'CS'
  AND s.name LIKE 'H%';
```


### 2. sid and name of students enrolled in (198:336 or 198:205)
```SQL
SELECT s.sid, s.name
FROM Students s, enrolledin e
WHERE s.sid = e.sid
	AND (e.cid = '198:336' or e.cid='18:205')
```


### 3.  sid, name of students enrolled in 198:336 and 198:205
my guess:
```SQL
SELECT s.sid, s.name
FROM Students s, enrolledin e
WHERE s.sid = e.sid
	AND (e.cid = '198:336' and e.cid='18:205')
```
#### This condition can **never be true**:


```
e.cid = '198:336' AND e.cid = '198:205'
```

A single row in `enrolledin` has **one `cid` value**.

It cannot be:
- `'198:336'`  
    AND
- `'198:205'`
at the same time.

So your query will always return **0 rows**.

#### Working example:
***shown in class below:

```SQL
SELECT
FROM students s, enrolledin e
WHERE s.sid = e.sid
	AND e.cid = '198:336'
	AND s.sid in 
		(SELECT e.sid
		FROM enrolledin e
		WHERE e.cid = '198:205')
```

### 4.  name and age of oldest students

```SQL
SELECT s.name, s.age
FROM Students s
WHERE s.age >= all(SELECT s.age from students s)
```


### Aggregate operators
