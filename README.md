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

## Question: Discuss in detail the MS-Access Table creation process, including data types, field properties, and field names ?

### MS-Access Table Creation Process

Creating tables is one of the fundamental steps in designing a database in MS Access. Tables store all the data, organized in rows (records) and columns (fields).

---

#### Step 1: Open MS Access
1. Launch MS Access.  
2. Open an existing database or create a new database.  

---

#### Step 2: Create a New Table
- Go to **Create → Table** or **Table Design**.  
- Two options:
  1. **Datasheet View:** Directly enter data in a spreadsheet-like interface.  
  2. **Design View:** Define fields, data types, and properties before entering data. *(Preferred for structured design)*  

---

#### Step 3: Define Field Names
- Each column in a table represents a **field**.  
- **Rules for field names:**
  - Must be unique within the table.  
  - Can include letters, numbers, and underscores.  
  - Avoid spaces and special characters for easier queries.  
- Example: `EmpID`, `EmpName`, `Age`, `Department`.  

---

#### Step 4: Select Data Types
Each field has a **data type** that determines what kind of data it can store. Common data types:

| **Data Type**       | **Description / Example**                     |
|--------------------|---------------------------------------------|
| Short Text         | Text or alphanumeric, max 255 characters    |
| Long Text          | Large text data (memo fields)               |
| Number             | Numeric values for calculations              |
| Date/Time          | Dates and times                              |
| Currency           | Monetary values                               |
| AutoNumber         | Unique sequential numbers (usually primary key) |
| Yes/No             | Boolean values (True/False)                 |
| Hyperlink          | Links to URLs or files                        |

---

#### Step 5: Set Field Properties
Field properties define constraints and formatting for each field. Common properties include:

- **Field Size:** Maximum number of characters for text or numeric precision.  
- **Format:** Display format for date, numbers, currency.  
- **Input Mask:** Template to control how users enter data (e.g., phone numbers).  
- **Default Value:** Value automatically entered if the field is left blank.  
- **Required:** Determines if the field can be left empty (Yes/No).  
- **Primary Key:** Uniquely identifies each record in the table.  

---

#### Step 6: Save the Table
- After defining all fields and properties, save the table.  
- Provide a meaningful **table name** (e.g., `Employees`, `Books`).  
- MS Access will enforce primary key and data type constraints.  

---

#### Step 7: Optional Features
- **Relationships:** Later, define relationships with other tables to enforce referential integrity.  
- **Indexes:** Improve search and query performance.  
- **Validation Rules:** Ensure data correctness (e.g., `Age >= 18`).  

---

#### ✅ Summary
1. Open or create a database.  
2. Create a table in **Design View** or **Datasheet View**.  
3. Define **field names** carefully.  
4. Choose appropriate **data types**.  
5. Set **field properties** for data accuracy and constraints.  
6. Save the table with a meaningful name.  
7. Optional: Define relationships, indexes, and validation rules for better integrity and performance.

## Question: Explain the process of setting up relationships in MS Access, including defining relationships, adding them, and setting referential integrity rules.

### Setting Up Relationships in MS Access

In MS Access, relationships link tables together using fields (usually primary keys and foreign keys).  
They help maintain data consistency and enforce **Referential Integrity**.

---

#### Step 1: Open Relationships Window
1. Open your database in MS Access.  
2. Go to the **Database Tools** tab.  
3. Click on **Relationships**.  
   - A Relationships window opens where you can add tables to define connections.

---

#### Step 2: Add Tables
1. In the Relationships window, click **Show Table**.  
2. Select the tables you want to relate (e.g., `Employees`, `Books`, `Loans`).  
3. Click **Add**, then close the dialog.  
4. Tables now appear in the Relationships window as boxes.

---

#### Step 3: Define Relationships
1. Click and drag the **Primary Key** field of one table (e.g., `EmployeeID` in `Employees`).  
2. Drop it on the matching **Foreign Key** field of another table (e.g., `EmployeeID` in `Loans`).  
3. The **Edit Relationships** dialog box appears.  

---

#### Step 4: Add Relationship Options
- In the dialog, you can see:
  - **Primary Table:** The table with the primary key.  
  - **Related Table:** The table with the foreign key.  
  - **Fields:** The linking columns.  

- Click **Create** to add the relationship.

---

#### Step 5: Enforce Referential Integrity
To maintain consistent data:
1. Check the **Enforce Referential Integrity** box.  
2. Options under it:
   - **Cascade Update Related Fields:** If the primary key is updated, all related records update automatically.  
   - **Cascade Delete Related Records:** If a primary key record is deleted, all related records in the child table are also deleted.  

---

#### Step 6: Save Relationships
- Click **Save** on the toolbar.  
- The defined relationships are now stored in the database schema.  

---

#### ✅ Example
- **Tables:**  
  - `Employees (EmpID, Name, DeptID)`  
  - `Departments (DeptID, DeptName)`  
- **Relationship:**  
  - `Departments.DeptID` → `Employees.DeptID`  
- **Referential Integrity:**  
  - Ensures that no employee can exist without a valid department.  

---

#### ✅ Summary
1. Open **Relationships** window.  
2. Add tables to relate.  
3. Drag and drop **Primary Key → Foreign Key**.  
4. Enable **Referential Integrity** and cascade options.  
5. Save the relationship setup.  

This ensures data consistency, prevents orphan records, and maintains database integrity.

