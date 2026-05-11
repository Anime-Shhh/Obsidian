### Pivot Tables - (Transpose)
### Why is this done?

Data scientists and analysts do this for three main reasons:

1. **Human Readability:** It is much easier for a person to compare enrollment across semesters when they are side-by-side. You can see trends (like the dip in SP 25) at a single glance.
    
2. **Report Generation:** Most business reports and dashboards prefer the "wide" format because it fits more information into a smaller vertical space.
    
3. **Time-Series Analysis:** Having time periods as columns makes it easier to calculate growth rates or differences between semesters using simple subtraction across columns.

**Enrollment (dept, semester, n students)**

| dept | semester | n students |
| :--- | :------- | :--------- |
| CS   | sp 26    | 2954       |
| CS   | fa 25    | 3250       |
| CS   | sp 25    | 2999       |
| CS   | fa 24    | 3500       |
| math | ⋮        | ⋮          |
after pivot on semester it will look like this:

| dept | fa 24 | sp 25 | fa 25 | sp 26 |
| :--- | :---- | :---- | :---- | :---- |
| CS   | 3500  | 2999  | 3250  | 2954  |
| math | ⋮     | ⋮     | ⋮     | ⋮     |

Query to get temporary table in MySQL
**MySQL doesn't have a built in pivot function so you have to do groupby**

```SQL
Enrollment(dept, semester, num_students)
	CREATE temp_table tl
		SELECT e.dept, e.semester, 
			if(e.semester = 'fa24', e.num_students, 0) fa24,
			if(e.semester = 'sp25', e.num_students, 0) sp25,
			if(e.semester = 'fa25', e.num_students, 0) fa25,
			if(e.semester = 'sp26', e.num_students, 0) sp26,
		FROM Enrollment e;
```

This is how if statements in MySQL are written:

```
if(condition, true output, false output)
```

Output of tl:

| dept | semester | fa24 | sp25 | fa25 | sp26 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| CS | sp26 | 0 | 0 | 0 | 2954 |
| CS | fa25 | 0 | 0 | 3250 | 0 |
| CS | sp25 | 0 | 2999 | 0 | 0 |
| CS | fa24 | 3500 | 0 | 0 | 0 |
| math | ⋮ | ⋮ | ⋮ | ⋮ | ⋮ |

final answer:
```MySQL
SELECT tl.dept, 
	   sum(fa24) fa24,
	   sum(sp25) sp25,
	   sum(fa25) fa25,
	   sum(sp26) sp26,
FROM tl
GROUP BY dept;
```
Output:

| dept | fa24 | sp25 | fa25 | sp26 |
| :--- | :--- | :--- | :--- | :--- |
| CS   | 3500 | 2999 | 3250 | 2954 |
| math | ⋮    | ⋮    | ⋮    | ⋮    |

another way to write the final answer is:
```MySQL
SELECT dept,
       SUM(fa24) fa24,
       SUM(sp25) sp25,
       SUM(fa25) fa25,
       SUM(sp26) sp26
FROM (
    SELECT e.dept, 
           IF(e.semester = 'fa24', e.num_students, 0) fa24,
           IF(e.semester = 'sp25', e.num_students, 0) sp25,
           IF(e.semester = 'fa25', e.num_students, 0) fa25,
           IF(e.semester = 'sp26', e.num_students, 0) sp26
    FROM Enrollment e
) tl
GROUP BY dept;
```

how an update would look like on this
```MySQL
UPDATE students,
SET gpa=3.7
WHERE sid=2257
```
---
#### using one table to update anotehr one

Students(sid, name, age, gpa) 
Gpa(sid, gpa)

---
```MySQL
UPDATE students s, gpa g
SET s.gpa=g.gpa
WHERE s.sid = g.sid;
```


## Views (like a table)
**Definition:** It is essentially a query that is stored in the DB instead of a whole table. it retrieves the data needed for the query live. so lets say it helped you get only the gpas of students. instead of having a new table for student gpas and keeping it stored and updating it all the time, you can just save the query and whenever you need just the gpas, you can run the view

--> completed on the fly
* access limitation
* derived attributes

### Example:  creating a limited version of a table
lets say you have:

Students(sid, name, .....,dob, ...)    (dob --> yyyy-mm-dd)
you also have the functions below:
**currdate()** --> gives you the current date
timestampdiff(\____, date1, date2)   where the ____ can be years, months, days

```MySQL
CREATE VIEW age_only
SELECT s.sid, timestampdiff(YEARS,s.dob, currdate()) age
FROM students s
```
---
```MySQL
SELECT * from age_only
```