---
title: "Supported types of stored procedures"
---

# {{ page.title }}

The IBM Db2 Developer Extension provides comprehensive support for working with stored procedures in your Db2 databases. This topic describes the types of stored procedures that the extension supports.

## Native SQL stored procedures

The Db2 Developer Extension currently supports **native SQL stored procedures**. These are procedures written entirely in SQL and created using the [`CREATE PROCEDURE`](https://www.ibm.com/docs/en/db2/12.1.x?topic=statements-create-procedure-sql) or [`CREATE OR REPLACE PROCEDURE`](https://www.ibm.com/docs/en/db2/12.1.x?topic=statements-create-procedure-sql) statement.

### Key characteristics

Native SQL stored procedures:
- Run directly inside the Db2 database engine.
- Require no external programs or languages.
- Provide optimal performance for database operations.
- Support SQL control statements (IF, WHILE, FOR, etc.).
- Include multiple SQL statements in a single procedure.
- Support input (IN), output (OUT), and input/output (INOUT) parameters.


