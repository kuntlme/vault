**DBMS Exam Revision Notes**

---

## [[DBMS TOPIC]]

## [[DBMS previous year questions]]



### 1. **Database System Architecture**

#### Data Abstraction

- The process of hiding the complexities of the database from users.
    
- Levels:
    
    - **Physical Level**: How the data is actually stored.
        
    - **Logical Level**: What data is stored and what relationships exist.
        
    - **View Level**: What the user sees (user interface).
        

#### Data Independence

- Ability to modify one level of the database without affecting the others.
    
- Types:
    
    - **Physical Data Independence**: Changes in storage structure don’t affect logical schema.
        
    - **Logical Data Independence**: Changes in logical schema don’t affect view level.
        

#### Data Definition Language (DDL)

- Used to define and modify database structure.
    
- Commands: `CREATE`, `ALTER`, `DROP`, `TRUNCATE`.
    

#### Data Manipulation Language (DML)

- Used for accessing and manipulating data.
    
- Commands: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
    

---

### 2. **Data Models**

#### Entity-Relationship (ER) Model

- Represents data as entities (objects) and relationships.
    
- ER Diagram: Graphical representation of entities, attributes, and relationships.
    

#### Network Model

- Data is represented using records and relationships using links.
    
- Allows complex relationships (many-to-many).
    

#### Relational Model

- Data is represented in tables (relations).
    
- Uses keys (primary, foreign) and constraints.
    

#### Object-Oriented Data Model

- Incorporates object-oriented principles.
    
- Supports classes, objects, inheritance, encapsulation.
    

#### Integrity Constraints

- Rules that ensure correctness of data:
    
    - **Primary Key**: Unique identifier.
        
    - **Foreign Key**: References primary key of another table.
        
    - **Unique**, **Not Null**, **Check**.
        

#### Data Manipulation Operations

- Actions on the data:
    
    - **Retrieval**, **Insertion**, **Deletion**, **Modification**.
        

---

### 3. **Relational Query Languages**

#### Relational Algebra

- Procedural query language.
    
- Operations: `SELECT`, `PROJECT`, `UNION`, `SET DIFFERENCE`, `CARTESIAN PRODUCT`, `JOIN`.
    

#### Tuple Relational Calculus

- Non-procedural.
    
- Uses tuple variables: `{t | P(t)}` where `P(t)` is a predicate.
    

#### Domain Relational Calculus

- Uses domain variables (values instead of tuples): `{<x1, x2, ..., xn> | P(x1, x2, ..., xn)}`.
    

#### SQL3

- Advanced version of SQL.
    
- Supports: triggers, recursive queries, object-relational features.
    

#### DDL and DML Constructs

- DDL: `CREATE`, `ALTER`, `DROP`
    
- DML: `SELECT`, `INSERT`, `UPDATE`, `DELETE`
    

#### Open Source & Commercial DBMS

- **Open Source**: MySQL, PostgreSQL
    
- **Commercial**: Oracle, SQL Server, IBM DB2
    

---

### 4. **Relational Database Design**

#### Domain & Data Dependency

- **Domain**: Set of allowable values for an attribute.
    
- **Functional Dependency**: A -> B means B is functionally dependent on A.
    

#### Armstrong's Axioms

- Rules to infer all functional dependencies:
    
    - Reflexivity, Augmentation, Transitivity, Union, Decomposition, Pseudotransitivity.
        

#### Normal Forms

- **1NF**: Atomic values.
    
- **2NF**: No partial dependency.
    
- **3NF**: No transitive dependency.
    
- **BCNF**: Every determinant is a candidate key.
    

#### Dependency Preservation

- After decomposition, all dependencies should be enforceable.
    

#### Lossless Design

- Decomposition should not lose any data.
    

---

### 5. **Query Processing and Optimization**

#### Evaluation of Relational Algebra Expressions

- Convert SQL into efficient low-level operations.
    

#### Query Equivalence

- Two queries are equivalent if they return the same result for all databases.
    

#### Join Strategies

- **Nested Loop Join**, **Sort-Merge Join**, **Hash Join**.
    

#### Query Optimization Algorithms

- Find most efficient way to execute query.
    
- **Cost-based** or **Rule-based** optimizers.
    

---

### 6. **Storage Strategies**

#### Indices

- Used to speed up retrieval.
    
- Types: Primary, Secondary, Clustered, Unclustered.
    

#### B-Trees

- Balanced tree structure.
    
- Efficient for range and equality queries.
    

#### Hashing

- Uses hash function to determine data location.
    
- Efficient for equality searches.
    

---

### 7. **Transaction Processing**

#### Concurrency Control

- Managing multiple transactions simultaneously without conflict.
    

#### ACID Properties

- **Atomicity**: All or none.
    
- **Consistency**: Database remains valid.
    
- **Isolation**: Intermediate states are not visible.
    
- **Durability**: Changes persist after commit.
    

#### Serializability of Scheduling

- Ensures consistency by producing the same result as serial execution.
    

#### Locking & Timestamp Schedulers

- **Lock-based**: Read/write locks to avoid conflicts.
    
- **Timestamp-based**: Transactions ordered by timestamps.
    

#### Multiversion & Optimistic Concurrency Control

- **Multiversion**: Different versions for each transaction.
    
- **Optimistic**: Assume no conflict, check at commit.
    

#### Database Recovery

- Restore to consistent state after failure.
    
- Use logs and checkpoints.
    

---

### 8. **Database Security**

#### Authentication

- Verifying user identity.
    

#### Authorization & Access Control

- Defining what operations users can perform.
    

#### DAC, MAC, RBAC

- **DAC**: Discretionary Access Control - user-based.
    
- **MAC**: Mandatory Access Control - policy-based.
    
- **RBAC**: Role-Based Access Control - based on roles.
    

#### Intrusion Detection

- Monitoring system for malicious activity.
    

#### SQL Injection

- Attack to execute malicious queries.
    
- Prevent using parameterized queries and input validation.
    

---

### 9. **Advanced Topics**

#### Object-Oriented and Object-Relational Databases

- Support objects, inheritance, encapsulation.
    
- Combine relational and OO features.
    

#### Logical Databases

- Use of views or logical schema abstraction.
    

#### Web Databases

- Accessible through web interfaces.
    

#### Distributed Databases

- Spread across multiple locations.
    
- Data appears as a single database.
    

#### Data Warehousing

- Central repository for historical data.
    
- Supports OLAP, reporting.
    

#### Data Mining

- Extracting patterns and knowledge from large datasets.