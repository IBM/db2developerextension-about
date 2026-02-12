---
title: "Supported types of procedures"
---

# {{ page.title }}

IBM Db2 Developer Extension provides comprehensive support for working with procedures in your Db2 databases.

## Native SQL procedures

IBM Db2 Developer Extension currently supports **native SQL procedures**. These procedures are written entirely in SQL and created by using the [`CREATE PROCEDURE`](https://www.ibm.com/docs/en/db2/12.1.x?topic=statements-create-procedure-sql) or [`CREATE OR REPLACE PROCEDURE`](https://www.ibm.com/docs/en/db2/12.1.x?topic=statements-create-procedure-sql) statement.

### Key characteristics

The key characteristics of the native SQL procedures are:
- Run directly within the Db2 database engine.
- Require no external programs or languages.
- Provide optimal performance for database operations.
- Support SQL control statements (IF, WHILE, FOR, and so on).
- Include multiple SQL statements in a single procedure.
- Support input (IN), output (OUT), and input/output (INOUT) parameters.


