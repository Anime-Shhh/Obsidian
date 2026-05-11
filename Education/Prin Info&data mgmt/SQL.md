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


### 5. name of students not in "198:111"
```MySQL
select s.name
from students s, enrolledin e
where s.cid = e.cid
	and e.sid not in (
		select distinct s.sid
		from students
		where s.sid = '198:111');
```


### 6. name of all students with a greater gpa than "Horatio"
```MySQL
select s.name
from students
where s.gpa > any(
	select s.gpa
	from students 
	where s.name='Horatio')
```

### 7. number of courses offered by each department
lets say you had to get a value y `for each` x in a table, you use groupby
```MySQL
select c.dept, count(*)
from courses
group by c.dept
```

### 8. find avg age of students enrolled in each course
```MySQL
select c.name, avg(s.age)
from courses c, students s, enrolledin e
where s.sid = e.sid 
and e.cid = c.cid
group by c.name
```

### 9. Find names of students with max gpa
```MySQL
select s.name
from students s
where s.gpa = (
	select max(gpa)
	from students);
```

### 10. for each student find out how many classes they got an A
```MySQL
select s.name, count(*)
from students s, enrolledin e
where s.sid = e.sid
and e.grade = 'A'
group by s.sid
```

### Aggregate operators