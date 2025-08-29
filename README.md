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
