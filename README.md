# postgreesql
## Comparison: PostgreSQL vs MySQL, PostgreSQL vs SQL Server
### PostgreSQL vs MySQL
Both PostgreSQL and MySQL are open-source relational database management systems (RDBMS), but they have different use cases and strengths.

| Feature | PostgreSQL | MySQL |
|---------|--------------|--------------|
| **ACID Compliance** | Fully ACID-compliant in all configurations | Fully ACID-compliant when using InnoDB (default engine) |
| **Performance** | Better for complex queries, analytics, and write-heavy applications | Faster for read-heavy workloads and simple queries |
| **Indexing** | Supports advanced indexing: GIN, GiST, BRIN, and full-text search | Basic indexing with B-Tree and some full-text search |
| **Replication & Clustering** | Supports streaming replication and logical replication natively | Supports replication but requires third-party tools for clustering |
| **JSON Support** | Advanced JSONB support for semi-structured data | JSON functions available but not as optimized as PostgreSQL |
| **Stored Procedures & Functions** | Supports procedural languages (PL/pgSQL, PL/Python, etc.) | Supports stored procedures but with fewer built-in language options |
| **Concurrency Control** | Uses MVCC (Multi-Version Concurrency Control) to handle concurrent transactions efficiently | Also uses MVCC but may have issues under high concurrency |
| **Extensibility** | Highly extensible with custom data types, operators, and procedural languages | Limited extensibility compared to PostgreSQL |
| **Community & Support** | Large and active community, with strong enterprise support | Larger adoption, strong community support |

### PostgreSQL vs SQL Server
PostgreSQL and Microsoft SQL Server (SQL Server) are both powerful RDBMS, but SQL Server is a proprietary system mainly used in enterprise environments.

| Feature | PostgreSQL | SQL Server |
|---------|--------------|--------------|
| **License** | Open-source (PostgreSQL License) | Proprietary (Microsoft) |
| **Platform Compatibility** | Runs on Linux, Windows, macOS | Primarily Windows, with some support for Linux |
| **ACID Compliance** | Fully ACID-compliant | Fully ACID-compliant |
| **Performance** | Optimized for complex queries and analytics | Strong performance, optimized for Windows environments |
| **JSON Support** | Full JSONB support | JSON support but not as advanced as PostgreSQL |
| **Stored Procedures & Functions** | Supports PL/pgSQL, PL/Python, and other procedural languages | Uses T-SQL for stored procedures and functions |
| **Scalability** | High scalability with horizontal scaling | Supports vertical scaling with enterprise features |
| **Security** | Advanced role-based access control, SSL encryption | Enterprise-level security, integration with Active Directory |
| **Cost** | Free and open-source | Requires licensing fees, can be expensive for large deployments |

## CRUD
## Foreign key
A **foreign key** is a column (or a group of columns) in one table that references the **primary key** of another table, establishing a link between the two tables. The table containing the foreign key is known as the “child table” and the table to which it refers is known as the “parent table.”

A foreign key creates a link between two tables by ensuring that any data entered into the foreign key column must already exist in the parent table. This helps maintain data integrity by preventing orphan records and ensuring that relationships between data remain consistent.

In PostgreSQL, foreign keys come with several constraints when creating or altering a table:
- **ON DELETE CASCADE**: Automatically deletes any rows in the child table when the corresponding row in the parent table is deleted.
- **ON DELETE SET NULL**: Sets the foreign key value in the child table to NULL when the corresponding row in the parent table is deleted.
- **ON UPDATE CASCADE**: Updates the foreign key in the child table when the corresponding primary key in the parent table is updated

## Join
**JOIN** is used to combine columns from one (self-join) or more tables based on the values of the common columns between related tables. The common columns are typically the primary key columns of the first table and the foreign key columns of the second table.
PostgreSQL supports *inner join*, *left join*, *right join*, *full outer join*, *cross join*, *natural join*, and a special kind of join called *self-join*.
### Inner join
`INNER JOIN` returns only matching rows from both tables. If there is no match, the row is excluded.

### Left join
`LEFT JOIN` returns all rows from the left table and only matching rows from the right table. If no match is found, NULL is returned for columns from the right table.

### Right join
`RIGHT JOIN` returns all rows from the right table and only matching rows from the left table. If no match is found, NULL is returned for columns from the left table.

### Full outer join
`FULL OUTER JOIN` combine data from two tables and returns all rows from both tables, including matching and non-matching rows from both sides. If no match is found, NULL is returned for missing values.

### Cross join
`CROSS JOIN` returns the cartesian product of two tables. Its clause does not have a join predicate.

### Natural join
`NATURAL JOIN` is a join that creates an implicit join based on the same column names in the joined tables.

### Self-join
A **self-join** is a regular join that joins a table to itself.

## Sub query
## Index
## Partition
## Transaction
A database transaction is a single unit of work that consists of one or more operations.
A classical example of a transaction is a bank transfer from one account to another. A complete transaction must ensure a balance between the sender and receiver accounts.
A PostgreSQL transaction is atomic, consistent, isolated, and durable. These properties are often referred to collectively as ACID:
- **Atomicity** guarantees that the transaction is completed in an all-or-nothing manner.
- **Consistency** ensures that changes to data written to the database are valid and adhere to predefined rules.
- **Isolation** determines how the integrity of a transaction is visible to other transactions.
- **Durability** ensures that transactions that have been committed are permanently stored in the database.
