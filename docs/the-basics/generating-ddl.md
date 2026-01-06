---
title: "Generating DDL for a Db2 object"
---

# {{ page.title }}


Db2 Developer Extension provides the capability to generate DDL for a Db2 object. Data Definition Language (DDL) is a subset of SQL commands that are used to create and modify database objects. You can generate DDL to completely re-create a database or only certain parts of it. For example, by generating DDL for database objects you can:
- Keep a snapshot of the database structure.
- Set up a test system where the database acts like the production system but contains no data.
- Produce templates for new objects based on existing ones.

You can generate DDL for the following Db2 objects:
- Tables
- Views
- Procedures
- Indexes
- Functions
- Aliases
- Audit Policies
- Buffer Pools
- Check Constraints
- Comments
- Grants
- Histograms
- Roles
- Sequences
- Security Labels
- Security Label Components
- Security Policies
- Service Classes
- Tablespaces
- Triggers
- User-defined Types
- Variables


## Generating DDL for a table 

1. Click the database connection and click the schema you want. 
2. Click the **Tables** object to expand all the tables.
2. Select the desired table and right-click it.
3. From the context menu, click the option **Generate DDL Queries**. 

   The DDL (Data Definition Language) script for the selected table structure opens in a read‑only window . You can only copy the DDL for an object, not run it directly. 
   
   
   ![Generate DDL]({{site.baseurl}}/assets/images/generate-DDL.png)

<!--Check if this is true..The generated DDL must be saved as a SQL file with the **.sql** file extension.-->
   
   
Follow the same process for other Db2 objects, but instead of a **Tables** object, select another Db2 object.
