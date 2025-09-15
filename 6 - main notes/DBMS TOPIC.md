# Database Study Guide

## 1. Introduction to Databases
### 1.1 Difference between DBMS and File-Processing System
- **DBMS**: Centralized data management, reduces redundancy, enforces integrity, supports concurrent access, and provides security.
- **File System**: Decentralized data, redundancy issues, limited security, and no direct support for complex queries.

### 1.2 Advantages of DBMS
- **Data Independence**: Logical and physical layers.
- **Integrity & Security**: Constraints and access control.
- **Concurrent Access**: Transaction management.
- **Reduced Redundancy**: Normalization.

### 1.3 Data Abstraction & Levels
1. **Physical Level**: Storage details (e.g., file structures).
2. **Logical Level**: Data relationships (e.g., tables, schemas).
3. **View Level**: User-specific interfaces.

### 1.4 3-Schema Architecture
- **External Schema**: User views.
- **Conceptual Schema**: Global database structure.
- **Internal Schema**: Physical storage details.

### 1.5 Data Independence
- **Physical**: Change storage without affecting logical schema.
- **Logical**: Modify logical schema without changing applications.

---

## 2. Data Models & Database Design
### 2.1 ER Model
- **Entity Sets**: 
  - *Strong*: Independent existence (e.g., `Student`).
  - *Weak*: Depends on a strong entity (e.g., `Dependent` linked to `Employee`).
- **Attributes**:
  - *Derived*: Computed from others (e.g., `Age` from `DOB`).
  - *Composite*: Sub-attributes (e.g., `Address` → Street, City).
  - *Multivalued*: Multiple values (e.g., `Phone Numbers`).
- **Relationships**:
  - *Degree*: Unary (recursive), Binary, Ternary.
  - *Cardinality*: 1:1, 1:N, M:N.
- **ER Diagram**: Entities (rectangles), Relationships (diamonds), Attributes (ovals).
- **Mapping Constraints**: 
  - *Disjoint*: Subclasses are mutually exclusive.
  - *Participation*: Total (mandatory) vs Partial.

### 2.2 Extended ER (EER)
- **Generalization**: Grouping entities (e.g., `Vehicle` ← `Car`, `Truck`).
- **Specialization**: Refining entities (e.g., `Employee` → `Manager`).
- **Inheritance**: Subclasses inherit superclass attributes.
- **Multiple Inheritance**: Conflicts resolved via precedence.

### 2.3 Other Models
- **Relational**: Tables with rows/columns.
- **Network**: Graph with owner-member sets.
- **Object-Oriented**: Classes/objects with methods.
- **Object-Relational**: Combines OO and relational models.

---

## 3. Relational Database Concepts
### 3.1 Keys
- **Super Key**: Any unique identifier set.
- **Candidate Key**: Minimal super key.
- **Primary Key**: Chosen candidate key.
- **Foreign Key**: Links to another table’s primary key.

### 3.2 Integrity Constraints
- **Entity Integrity**: Primary keys cannot be `NULL`.
- **Referential Integrity**: Foreign keys must match existing primary keys.

### 3.3 Relational Algebra
- **Operations**: 
  - σ (Selection), π (Projection), ⋈ (Join), × (Cartesian Product), ∪ (Union).

### 3.4 Functional Dependencies
- **Armstrong’s Axioms**: Reflexivity, Augmentation, Transitivity.
- **Canonical Cover**: Minimal set of FDs.

### 3.5 Normalization
| Form | Description                                                         |
| ---- | ------------------------------------------------------------------- |
| 1NF  | Atomic values, no repeating groups.                                 |
| 2NF  | No partial dependencies (all non-key attributes depend on full PK). |
| 3NF  | No transitive dependencies.                                         |
| BCNF | Every determinant is a candidate key.                               |
| 4NF  | No multivalued dependencies.                                        |
| 5NF  | No join dependencies.                                               |

- **Anomalies**: Insertion, deletion, update issues due to poor design.

---

## 4. SQL & Database Languages
### 4.1 SQL Basics
- **DDL**: `CREATE`, `ALTER`, `DROP`.
- **DML**: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
- **DCL**: `GRANT`, `REVOKE`.

### 4.2 Advanced SQL
- **Views**: Virtual tables (simplify queries, restrict access).
- **Triggers**: Automate actions on events (e.g., `BEFORE INSERT`).
- **Transactions**: `COMMIT` (save changes), `ROLLBACK` (undo changes).

### 4.3 Query Optimization
- **Join Strategies**: Nested-loop, merge, hash joins.
- **Query Trees**: Visual representation of query execution.

---

## 5. Storage & Indexing
### 5.1 File Organization
- **Indexing**: 
  - *Dense*: Entry per record. 
  - *Sparse*: Entry per block.
- **B+ Trees**: Balanced trees with all data in leaves.
- **Hashing**: Bucket overflow handled via chaining.

### 5.2 Indices
- **Primary Index**: Clustered (data sorted by PK).
- **Secondary Index**: Non-clustered.

---

## 6. Transaction Management
### 6.1 ACID Properties
- **Atomicity**: All-or-nothing execution.
- **Consistency**: Valid state transitions.
- **Isolation**: Concurrent transactions appear serial.
- **Durability**: Committed changes persist.

### 6.2 Concurrency Control
- **2PL**: Growing (acquire locks), Shrinking (release locks).
- **Deadlock Handling**: 
  - *Wait-Die*: Older transactions wait.
  - *Wound-Wait*: Older transactions preempt.

### 6.3 Recovery Techniques
- **Log-Based**: Undo (rollback), Redo (replay logs).
- **Checkpoints**: Reduce recovery time.

---

## 7. Advanced Topics
### 7.1 Distributed Databases
- **Fragmentation**: 
  - *Horizontal*: Split rows.
  - *Vertical*: Split columns.

### 7.2 Security
- **Authorization Models**: DAC (user-defined), MAC (system-enforced), RBAC (role-based).

### 7.3 Data Warehousing vs Database
- **Warehouse**: Optimized for analysis (OLAP).
- **Database**: Optimized for transactions (OLTP).

---

## 8. Miscellaneous
- **Metadata**: Data about data (e.g., schema details).
- **Null Handling**: Use `IS NULL` in queries.
- **Open Source DBMS**: MySQL, PostgreSQL.
- **Commercial DBMS**: Oracle, SQL Server.