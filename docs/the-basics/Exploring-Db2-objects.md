
# Db2 objects
---
The **Db2 Developer Extension** provides a clean, intuitive tree-based interface for exploring and managing database objects. With this organized view, you can quickly navigate through schemas and access objects such as tables, views, indexes, and stored procedures—all without leaving your editor. 

Each object can be expanded to reveal detailed information, making it easy to inspect properties, structure, and relationships. The extension offers a seamless way to drill down into object details and manage your Db2 environment efficiently.

## Exploring Db2 objects
---
After creating a database connection, the following object types associated with that connection are listed under the connection name. 
We support the following object types:


- **Tables**: A table is a structured collection of rows and columns used to store data in a relational format. Each column has a defined data type, and each row represents a record.
- **Views**: A view is a virtual table created by a query that retrieves data from one or more tables.
- **Procedure**: Stored procedures are precompiled sets of SQL statements that perform specific tasks. They can accept input parameters, return output, and help encapsulate business logic within the database.
- **Indexes**: Indexes are structures that improve query performance by allowing faster data retrieval based on column values. 
- **Functions**: User-defined or built-in functions perform operations on data and return a single value. They can be scalar (return one value) or table functions (return a set of rows).
- **Aliases**: An alias is an alternate name for a table, view, or sequence. It simplifies referencing objects, especially across schemas or when renaming is needed without changing the original object.
-  **Audit Pilicies**: Audit policies define rules for tracking and recording database activities for security and compliance purposes. They specify what actions should be logged.
- **Buffer Pools**: A buffer pool is an area in memory used to cache table and index pages for faster data access.
- **Check Constraints**: A check constraint enforces a condition on data in a column, ensuring that only values meeting the condition are allowed.
- **Comments**: Comments are descriptive text attached to database objects (tables, columns, etc.) to provide documentation or clarification.
- **Grants**: Grants are permissions given to users or roles to perform actions on database objects (e.g., SELECT, INSERT, UPDATE).
- **Histograms**: Histograms store statistical information about column data distribution.
- **Roles**: Roles are collections of privileges that can be assigned to users, simplifying security management.
- **Sequences**: A sequence generates numeric values in a defined order, often used for auto-incrementing primary keys.
- **Security Lables**: Security labels classify data for access control based on security policies.
- **Security Label Compoenents**: Components define the structure of security labels, such as levels, categories, or compartments.
- **Security Policies**: Security policies govern how security labels are applied and enforced for data access.
- **Service Classes**: Service classes define workload management rules, controlling resource allocation for different workloads.
- **Tablespaces**: A tablespace is a storage structure that groups tables and indexes, managing how data is physically stored on disk.
- **Triggers**: Triggers are actions automatically executed in response to specific events on a table (e.g., INSERT, UPDATE, DELETE).
- **User-defined Types**: Custom data types created by users to represent complex structures beyond built-in types.
- **Variables**: Variables store temporary values during the execution of SQL statements or procedures.

Each object type expands to list all objects of that type under the connected schema, and clicking an object opens its details in the right pane. For example, if you want to view the table object details, see [Viewing tables in a Schema](#tables-schema-id).

## Viewing tables in a Schema {#tables-schema-id}

1. Under the database connection, click the specific schema that contains the tables you want to view.
   It opens a Schema tables overview pane in the right. The pane contains the catalog of tables that belong to that schema. 
   
   
   ![Connecting to database]({{site.baseurl}}/assets/images/schema-table-overview.png)

   
   Each column provides specific details:
   - Name - The unique name assigned to the table within the schema. 
   - Tablespace - The logical storage location where the table’s data resides.
   - Row count - The number of rows (records) currently stored in the table.
   - Owner - The user or role that created and owns the table. 
   - Create time - The date and time when the table was created in the database.
   - Organization Type - Specifies how the table’s data is physically organized. Common types include row-organized or column-organized.
2. Click the table name you want to view. 
   It displays the following details:
   - Properties: General details such as table name, schema name, type, encoding scheme, owner, etc.
   - Columns: Lists all column names along with their data types and constraints.        
   - Constraints: Rules applied to the table’s columns.
   - Indexes: Shows relationships with other objects (like views or indexes).
   - Data: Displays the actual rows stored in the table.
   
   
   You can also view the above details by expanding the Tables object under the schema in Db2 Explorer and clicking the required table. 


For more information about object properties, see [working with objects](../working-with-Db2-objects/Db2-objects.md). 


You can follow the same process to explore other Db2 objects. 







