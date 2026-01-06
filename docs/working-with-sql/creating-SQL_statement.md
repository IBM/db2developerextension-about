
# Creating a Simple SQL Statement
You can create SQL statements by different ways. 
- 
- From the Open SQL Editor option in the Db2 Connections toolbar
- Create New SQL File option in the Db2 Connections toolbar
- Create a file and save it as SQL
- Right click the objecy and insert queries
>**Note:** You can save your SQL file as **.SQL**. 

## Creating SQL statement from Open SQL Editor toolbar menu icon
1. Click **Open SQL Editor** in the Db2 Connections pane. It opens the Db2 SQL Editor. 
2. Select the target database connection and database from the dropdrown menus in the editor pane. 
3. In the editor pane, write your SQL statement or you can expand the schema in the left pane to view available objects. Right click the object to generate SQL queries in the SQL Editor
4. Click **Run** to run the SQL statement. Your result appear in the **Results** pane.
5. Click **Export** to download results in CSV or JSON format.
6. Click **Save** to store the query for reuse.

## Create and Save a New SQL File
1. Click **File > New File** or click the **Create New SQL File** icon in the Db2 Connections pane.
2. Save it as `anyname.sql` to enable SQL editing features.

> **Note:** Although our examples use a `.sql` file, you can embed SQL in any type of file and run that SQL directly from Db2 Developer Extension.  

2. **Write SQL**  
   - Begin typing `SELECT`.  
   - The extension will suggest the full statement.  
   - Choose **SELECT statement** from the suggestions to insert a code snippet.

   > **Important:** The snippet includes only basic parameters. Many SQL statements have a lot of parameters, so a link to the complete syntax is provided at the top of the snippet.  
   Syntax elements are color-coded for clarity. Hover over squiggly-underlined elements to see error messages and suggestions.

3. **Click Run**  
   - View the results in the **Results** pane.

## Creating SQL statement from Create New SQL File toolbar menu icon
1. In the **Db2 Connections** toolbar, click **Create New SQL File**.
2. A new SQL editor tab opens in a new window with the name Untitled. Save the file with a .sql extension
3. In the SQL editor tab, type your SQL statement. For example, type the first letters of the SELECT statement. You'll only need to type a few letters before `SELECT statement` shows up in the list of available SQL elements. Click `SELECT statement` to insert a code snippet that provides the basic structure of this statement, including required and commonly used parameters.
4. Click **Check SQL Syntax** to validate the syntax of the SQL statement without executing it.
5. Click **Format SQL** if you want to reformat your SQL code to make it more readable and consistent.
6. Click **Show SQL Snippet** if you want to see predefined SQL templates or code snippets you can insert into the editor. Following are the list of used SQL statements and patterns, such as:

   - SELECT TOP N – Select top N rows from a table
   - GROUP BY with HAVING
   - CREATE TABLE
   - INSERT statement
   - JOIN examples
   - MERGE statement
   When you select a snippet, the editor inserts the corresponding SQL template into your current SQL editor tab.
7. Click **Run SQL** to run your queries. 

## Generating DDL and SQL Queries for a Table
1. In the left pane, expand the schema and right-click the table you want to create queries. 
2. From the context menu, select the object-specific actions such as:
   - Generate DDL Queries: Creates the DDL (Data Definition Language) script for the selected table structure.
   - Generate DELETE Query: Generates a template for deleting the rows from the table.
   - Generate INSERT Query: Generates a template for inserting the rows into the table.
   - Generate SELECT Query: Generates a template for retrieving the data from the table.
   - Generate UPDATE Query: Generates a template for updating the rows in the table.
   - Generate Application Code: Creates code snippets for integrating with applications.
   
   The DELETE, SELECT, INSERT, and UPDATE queries opens in a new Db2 SQL Editor window with the **Results** pane on the right. 
3. Run your respective query by clicking the **Run** button. 
4. View the results in the **Results** pane.

**Note:** The generated DDL query opens in a read‑only window. You can only copy the DDL for an object (tables, indexes, etc.), not run it directly.

You can follow the same process for viewing and generating queries for other Db2 objects, but instead of a Table object, select another Db2 object.