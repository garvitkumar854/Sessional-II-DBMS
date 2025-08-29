# Sessional-II-DBMS

## Question: Explain three schema architecture. Why mappings between schema levels are required?

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

## Question: Demonstrate the concepts of Generalization & Specialization with examples

Generalization
- **Definition:** A bottom-up process of combining two or more lower-level entities into a higher-level, more general entity.  
- **Purpose:** Used when different entities share common attributes.  
- **Example:**  
  - Entities: Car, Bike, Truck  
  - Generalized entity: Vehicle (common attributes: vehicle_id, color, engine_capacity)

---
Specialization
- **Definition:** A top-down process of dividing a higher-level entity into lower-level, more specific entities.  
- **Purpose:** Used when sub-entities need additional attributes or functions.  
- **Example:**  
  - Entity: Employee  
  - Specialized entities:  
    - Teacher (extra attribute: Subject)  
    - Engineer (extra attribute: Project)  

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
