## Conceptual Design(Entity relationship diagrams)
SQL(Structured Query Language) Standard:
	Query Language(**QUEL**)
	
Implementations are:
* mySQL
* Oracle
* SQL Server(Microsoft)
* PosgreSQL

![[Pasted image 20260123141749.png]]

## ER(Entity Relations) Diagrams:
* Chen's Notation
* Arrow notation(Cardinality notation)
* Crow-foot notation -> Relational diagram
### **Entity Set**

- A collection of similar entities (objects) in the database
- **No duplicate entities** allowed (each entity is uniquely identifiable)
---
### **Types of Attributes**
**1. Multivalued Attribute**
- An attribute that can have **multiple values** for a single entity
- Example: `phone_number` (a person can have more than one)
**2. Composite Attribute**
- An attribute that can be **broken into smaller sub-attributes**
- Example: `address → (street, city, state, zip)`
**3. Derived Attribute**
- An attribute whose value is **calculated from other attributes**
- Example: `age` derived from `date_of_birth`

**Problem:** In a large enough DB, 2 people can have same names, conflicting data inputs
**Solution**: Candidate Keys
- id(ex: student id) 
- phone number
- name, dob
- unique number that can only be 1 of 1
	These are considered to be Minimal, because getting rid of it makes data unidentifiable. no backup. You cannot remove any of those fields.

**Primary Key**: is a candidate key enforced by the DBMS
!! Every Entity Set must have a [primary key] !!!

### Integrity constraints
**Primary Key Constraint**
**Domain Constraints:**
	Types:
	- int
	- float
	- char(n) where n=fixed size(ex: SSN)
	- varchar(n) variable length has a max size n
	- text
	- blob(multimedia)
**Assumptions**
**Cardinality constraints**

### Relationships:
establishes connections between 2 sets of data
#### different types of relationships:

Many-to-many
- Example: Students ↔ Courses  
  A student can enroll in many courses, and a course can have many students.

one-to-many
- Example: Department → Employees  
  One department can have many employees, but each employee belongs to one department.

one-to-one
- Example: Person ↔ Passport  
  One person has one passport, and each passport belongs to one person.
