# Database Normalization: The Ultimate Guide to Data Integrity

Normalization is the systematic process of organizing a database to minimize **data redundancy** (duplication) and eliminate **update anomalies**. Essentially, it involves decomposing large, messy tables into smaller, well-structured ones while ensuring that data dependencies make sense.

---
## 1. Functional Dependencies (FD)
Before we can normalize, we must understand **Functional Dependencies**. These are the rules that describe the relationship between attributes in a relation.

### Definition
A functional dependency $X \rightarrow Y$ (read as "$X$ functionally determines $Y$") means that for every unique value of $X$, there is exactly one value of $Y$. If two rows have the same $X$, they **must** have the same $Y$.

### Types of Functional Dependencies
* **Trivial FD:** $X \rightarrow Y$ is trivial if $Y \subseteq X$ (e.g., $\{ID, Name\} \rightarrow ID$).
* **Full FD:** $Y$ is fully dependent on $X$ if $Y$ depends on the *whole* of $X$, not just a part of it.
* **Partial FD:** Occurs when an attribute depends on only part of a composite primary key. (A major no-no in 2NF).
* **Transitive FD:** Occurs when $A \rightarrow B$ and $B \rightarrow C$. Therefore, $A \rightarrow C$ via $B$. (A major no-no in 3NF).

### How to Create an FD Table
To map these out for your notes, you list your attributes and identify what "points" to what. 

| Determinant ($X$)   | Dependent ($Y$) | Logic                                                                       |
| :------------------ | :-------------- | :-------------------------------------------------------------------------- |
| `Emp_ID`            | `Emp_Name`      | An ID uniquely identifies a name.                                           |
| `Dept_Code`         | `Dept_Name`     | Each department code has one specific name.                                 |
| `{Emp_ID, Proj_ID}` | `Hours_Worked`  | You need both the person AND the project to know how many hours were spent. |
### Example: Creating an FD Table

**Relation Schema:**
`Project_Management (Emp_ID, Emp_Name, Proj_Code, Proj_Title, Hours_Worked)`

**Functional Dependency Table:**

| Determinant (LHS)     | Dependent (RHS) | Type of Dependency | Reason                                                      |
| :-------------------- | :-------------- | :----------------- | :---------------------------------------------------------- |
| `Emp_ID`              | `Emp_Name`      | Partial            | Employee name depends only on their ID.                     |
| `Proj_Code`           | `Proj_Title`    | Partial            | Project title depends only on the project code.             |
| `{Emp_ID, Proj_Code}` | `Hours_Worked`  | Full               | You need both the Person and the Project to know the hours. |

---
### Step-by-Step Logic to Build This Table:
1. **Identify the Primary Key:** In this case, it's a composite key `{Emp_ID, Proj_Code}`.
2. **Test Relationships:** Ask, "If I know X, do I definitely know Y?"
   * *If I know Emp_ID, do I know the Name?* **Yes.** (Emp_ID → Emp_Name)
   * *If I know Emp_ID, do I know the Hours Worked?* **No**, because they work on multiple projects.
3. **List the Findings:** Map every determinant (the "boss" column) to its dependent (the "determined" column).

---

## 2. The Normal Forms (1NF - BCNF)

### First Normal Form (1NF)
**Rule:** Data must be atomic.
* No multi-valued attributes (no lists or arrays in a single cell).
* Each column must have a unique name.
* The order in which data is stored does not matter.

**Example of Non-1NF:**
| Student | Subjects |
| :--- | :--- |
| Alex | Math, Science |

**Solution:** Split the values into separate rows.

---

### Second Normal Form (2NF)
**Rule:** Must be in 1NF **AND** have no **Partial Dependencies**.
* This only applies to tables with **Composite Primary Keys** (keys made of two or more columns).
* Every non-prime attribute (columns that aren't part of the key) must depend on the *entire* primary key.

**The Problem:** If your PK is `{Student_ID, Course_ID}` but you have a column `Course_Name`, that is a partial dependency because `Course_Name` only needs `Course_ID` to be identified.

**Solution:** Move the partially dependent attributes into a new table.



---

### Third Normal Form (3NF)
**Rule:** Must be in 2NF **AND** have no **Transitive Dependencies**.
* A non-prime attribute should not depend on another non-prime attribute.
* In simpler terms: "The key, the whole key, and nothing but the key, so help me Codd."

**The Problem:**
In a table with `Emp_ID (PK)`, `Dept_ID`, and `Dept_Name`:
1. `Emp_ID \rightarrow Dept_ID`
2. `Dept_ID \rightarrow Dept_Name`
3. Therefore, `Emp_ID \rightarrow Dept_Name` (Transitive!)

**Solution:** Remove `Dept_Name` from the Employee table and create a separate Department table where `Dept_ID` is the PK.

---

### Boyce-Codd Normal Form (BCNF)
**Rule:** A stronger version of 3NF. For every functional dependency $X \rightarrow Y$, **$X$ must be a Super Key.**
* While 3NF allows $Y$ to be a prime attribute (part of a candidate key), BCNF does not.
* BCNF is reached when there are no dependencies from a part of a composite key to another part of a composite key.

**Example Scenario:**
Imagine a table `(Student, Subject, Teacher)` where:
1. A student can take multiple subjects.
2. Each teacher teaches only one subject.
3. For a specific subject, a student is assigned one teacher.

The FDs are:
* `{Student, Subject} \rightarrow Teacher`
* `Teacher \rightarrow Subject`

**Why it fails BCNF:** In the dependency `Teacher \rightarrow Subject`, the determinant (`Teacher`) is **not** a super key (since one teacher can have many students).

**Solution:**
* Table 1: `(Student, Teacher)`
* Table 2: `(Teacher, Subject)`



---

## 3. Summary Table for Quick Reference

| Normal Form | Requirement | Eliminates... |
| :--- | :--- | :--- |
| **1NF** | Atomic values, No repeating groups | Atomicity issues |
| **2NF** | 1NF + No Partial Dependencies | Redundancy from composite keys |
| **3NF** | 2NF + No Transitive Dependencies | Redundancy from non-key relationships |
| **BCNF** | 3NF + Every determinant is a Super Key | Remaining functional dependency anomalies |

---

## 4. Why Bother? (The Anomalies)
If you don't normalize, you face the "Three Evils" of Database Design:
1.  **Insertion Anomaly:** You can't insert a new department because you don't have any employees assigned to it yet (and the PK requires an Employee ID).
2.  **Update Anomaly:** If a department moves, you have to update the address in 500 rows. If you miss one, the data is inconsistent.
3.  **Deletion Anomaly:** If you delete the last employee in a department, you accidentally delete the department's existence and address from the database entirely.