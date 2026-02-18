---
title: "Generating DDL for a Db2 object"
---

# {{ page.title }}

---

Db2 Developer Extension provides the capability to generate DDL for a Db2 object. Data Definition Language (DDL) is a subset of SQL commands that are used to create and modify database objects. You can generate DDL to completely re-create a database or only certain parts of it. By generating DDL for database objects, you can:
- Keep a snapshot of the database structure.
- Set up a test system where the database acts like the production system but contains no data.
- Produce templates for new objects based on the existing ones.

You can generate DDL for the following Db2 objects:
- Tables
- Views
- Procedures
- Functions
- Triggers
- Indexes
- Aliases
- Check constraints
- Comments
- Sequences
- Security label components
- Service classes
- User-defined types
- Variables



## Generating DDL for a table 
---

1. Click the database connection and click the schema that you want. 
2. Click the **Tables** section to expand all the tables.
2. Select the required table and right-click it.
3. From the menu, click the option **Generate DDL**. 

   The extension opens the DDL for the selected table structure in a read-only editor tab. You can copy the DDL for an object but cannot run it directly.
   
   
   ![Generate DDL]({{site.baseurl}}/assets/images/create-ddl.png)

<!--Check if this is true..The generated DDL must be saved as a SQL file with the **.sql** file extension.-->
   
   
You can follow the same steps to generate DDL for other object types, such as Views.