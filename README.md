# Sessional-II-DBMS

## Question: Explain three schema architecture. Why mappings between schema levels are required ?

### Answer:
Three Schema Architecture

The three-schema architecture is a framework proposed by ANSI-SPARC that separates a database system into three levels of abstraction.
It helps achieve data independence and provides multiple views of data to users.

1. Internal Level (Physical Schema)
- Describes how data is physically stored on storage devices.
- Includes file organization, indexes, access paths, and storage blocks.
- Example: Storing data as B+ tree indexes, heap files.

2. Conceptual Level (Logical Schema)
- Describes the structure of the entire database for the community of users.
- Defines entities, attributes, relationships, constraints.
- Independent of physical storage.
- Example: ER diagrams, relational schema definitions.

3. External Level (View Schema)
- Defines individual user views of the database.
- Hides details irrelevant to users, showing only required data.
- Example: A student sees only his marks, while an admin sees all records.

<img width= 500 src="https://miro.medium.com/1*2pF7iW4rT8T-vZyXlZ8zOg.png">

Why Mappings Between Schema Levels Are Required?
- Data Abstraction: Users can query without worrying about how data is stored physically.
- Logical Data Independence: Changes in conceptual schema (e.g., new attribute) should not affect user views.
- Physical Data Independence: Changes in physical storage (e.g., new indexing method) should not affect conceptual schema.
- Multiple User Views: Different external schemas (student, teacher, admin) can map to the same conceptual schema.
- Consistency & Integrity: Ensures that changes at one level don’t break other levels.

## Question: Demonstrate the concepts of Generalization & Specialization with examples ?

Generalization
- **Definition:** A bottom-up process of combining two or more lower-level entities into a higher-level, more general entity.  
- **Purpose:** Used when different entities share common attributes.  
- **Example:**  
  - Entities: Car, Bike, Truck  
  - Generalized entity: Vehicle (common attributes: vehicle_id, color, engine_capacity)
    
<img src="https://bimstudies.com/wp-content/uploads/2024/10/generalization-1-scaled.png" width=500>

---
Specialization
- **Definition:** A top-down process of dividing a higher-level entity into lower-level, more specific entities.  
- **Purpose:** Used when sub-entities need additional attributes or functions.  
- **Example:**  
  - Entity: Employee  
  - Specialized entities:  
    - Teacher (extra attribute: Subject)  
    - Engineer (extra attribute: Project)
      
<img src="https://media.geeksforgeeks.org/wp-content/uploads/20200422233542/Specialisation_1.jpg" width=500>

---
Key Differences
| **Generalization** | **Specialization** |
|---------------------|---------------------|
| Bottom-up approach | Top-down approach |
| Combines multiple entities into one general entity | Splits one entity into multiple sub-entities |
| Focuses on common attributes | Focuses on unique attributes |
| “Many to One” process | “One to Many” process |
| Example: Car, Bike → Vehicle | Example: Employee → Teacher, Engineer |

---
✅ Summary
- **Generalization:** Combining entities (common features).  
- **Specialization:** Splitting entity (unique features).  

## Question: What is an Integrity Constraint? Explain the importance of Referential Integrity Constraint ?

Integrity Constraint
- **Definition:**  
  Integrity constraints are rules enforced on database tables to ensure the **accuracy, consistency, and validity** of the data.  
- **Purpose:**  
  They prevent invalid or inconsistent data from being inserted into the database.  

Types of Integrity Constraints
1. **Entity Integrity:**  
   - Every table must have a primary key.  
   - Primary key values cannot be NULL or duplicate.  

2. **Referential Integrity:**  
   - A foreign key in one table must either be NULL or match a primary key in another table.  

3. **Domain Integrity:**  
   - Attributes must have valid values (e.g., age must be > 0).  
---

Referential Integrity Constraint
- **Definition:**  
  Referential Integrity ensures that the **relationship between two tables remains consistent**.  
  If a table (child) has a foreign key referencing another table (parent), then the foreign key value must exist in the parent table’s primary key.  

**Example:**  
- Table: `Student(Stud_ID, Name, Dept_ID)`  
- Table: `Department(Dept_ID, Dept_Name)`  
- Rule: Every `Dept_ID` in **Student** must exist in **Department**.  

---

Importance of Referential Integrity
1. **Prevents Orphan Records:**  
   Ensures no record in the child table refers to a non-existent record in the parent table.  

2. **Maintains Consistency:**  
   Guarantees relationships between tables remain valid.  

3. **Supports Cascading Actions:**  
   - **Cascade Update:** If a primary key value changes, all related foreign keys are updated.  
   - **Cascade Delete:** If a parent record is deleted, related child records are deleted (if chosen).  

4. **Improves Data Accuracy:**  
   Ensures that foreign key values always point to valid primary keys.  

---

✅ Summary
- **Integrity Constraints** are rules that maintain correctness of data.  
- **Referential Integrity** ensures foreign key values always match existing primary key values, preventing orphan records and preserving consistency in relationships between tables.

## Question: Explain insertion, deletion and modification anomalies. Why are they considered bad? Illustrate with example ?

Introduction
When data is stored in a single large table (without normalization), it often causes **data redundancy** and **inconsistency**.  
The problems that arise are called **Anomalies**.

---
1. Insertion Anomaly
- **Definition:**  
  Occurs when we cannot insert a new fact into the database without inserting some unrelated data.  

- **Example:**  

| StudentID | StudentName | CourseID | CourseName |
|-----------|-------------|----------|------------|
| 1         | Alice       | C101     | DBMS       |

- **Problem:**  
  If a new course `C102 – Networks` is introduced but no student has enrolled yet, we **cannot insert the course** without entering a fake student.

---

2. Deletion Anomaly
- **Definition:**  
  Occurs when deleting one fact also deletes other important information unintentionally.  

- **Example:**  
  If Alice (StudentID=1) drops the course `C101 – DBMS`, and we delete her row, then information about the course `C101 – DBMS` is **also lost**.

---

3. Modification Anomaly
- **Definition:**  
  Occurs when updating a value requires multiple changes, leading to inconsistency if all occurrences are not updated.  

- **Example:**  
  Suppose course `C101 – DBMS` is renamed to `Advanced DBMS`.  
  We must update all rows where CourseID = C101.  
  If one row is missed, the database becomes **inconsistent**.

---

Why Are Anomalies Bad?
- Cause **data redundancy** (same data repeated).  
- Lead to **inconsistency** (different values for same fact).  
- Increase **storage cost** and complexity.  
- Violate data integrity.  
- Make database unreliable.  

---

✅ Summary
- **Insertion Anomaly:** Cannot insert new data without unrelated data.  
- **Deletion Anomaly:** Deleting data causes unintended loss of other information.  
- **Modification Anomaly:** Updating data requires multiple changes → inconsistency risk.  
- **Reason they are bad:** They reduce reliability, increase redundancy, and cause inconsistency in the database.  

