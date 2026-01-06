
# Generating a simple SQL statement
You can create SQL statements by multiple methods. 
- Use the **Open SQL Editor** icon (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) in the Db2 Connections toolbar.
- Use the **Create New SQL File** icon (![Creating new SQL file]({{site.baseurl}}/assets/images/create-new-sql-file.png){:width="25" :height="25"}) in the Db2 Connections toolbar.
- Create a file and save it with a .sql extension.
- Right-click the object in a schema and insert queries.

## Generating SQL statement from open SQL editor toolbar icon
1. Click **Open SQL Editor** icon (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) in the Db2 Connections toolbar. Db2 SQL Editor opens.


    ![Adding a database connection]({{site.baseurl}}/assets/images/create-sql-open-sql-editor.png)
2. Select the target database connection and database from the dropdrown menus. 
3. In the editor pane, write your SQL statement.
    - Alternatively, expand the schema in the navigation pane to view available objects. 
    - Right-click the object to generate SQL queries in the SQL Editor.
4. Click **Run** to run the SQL statement. Your results appear in the **Results** pane.
5. Click **Export** to download the results in CSV or JSON format.
6. Click **Save** to store your queries for reuse.

## Creating and saving a new SQL file
1. Click **File > New File**.
2. Save it as `anyname.sql` to enable SQL editing features.

    > **Note**:
    > Although our examples use a `.sql` file, you can embed SQL in any type of file and run that SQL directly from Db2 Developer Extension. 
    {: .note-right}

3. Write SQL.
   - For example, begin typing `SELECT`.  
   - The extension will suggest the full statement.  
   - Choose **SELECT statement** from the suggestions to insert a code snippet.

    > **Note**:
    > The snippet includes only basic parameters. Many SQL statements have a lot of parameters, so a link to the complete syntax is provided at the top of the snippet. Syntax elements are color-coded for clarity. Hover over squiggly-underlined elements to see error messages and suggestions.
    {: .note-right}



4. Click **Run**. You can view the results in the **Results** pane.

## Creating SQL statement from create new SQL file toolbar icon 
1. Click **Create New SQL File** icon (![Creating new SQL file]({{site.baseurl}}/assets/images/create-new-sql-file.png){:width="25" :height="25"}) in the **Db2 Connections** toolbar.  

    ![Adding a database connection]({{site.baseurl}}/assets/images/create-sql-create-new-sql.png) <br>
2. A new SQL editor tab opens with the name Untitled. Save the file with a .sql extension.
3. In the SQL editor, type your SQL statement. 
    - For example, type the first letters of SELECT.
    - The SELECT statement appears in the list of available SQL elements.
    - Click SELECT statement to insert a code snippet with the basic structure.
4. Click **Check SQL Syntax** to validate the syntax of the SQL statement without executing it.
5. Click **Format SQL** to reformat your SQL code to make it readable and consistent.
6. Click **Show SQL Snippet** to see predefined SQL templates or code snippets you can insert into the editor. 
    Common snippets include:
    - SELECT TOP N – Select top N rows from a table
    - GROUP BY with HAVING
    - CREATE TABLE
    - INSERT statement
    - JOIN examples
    - MERGE statement
   
   
   When you select a snippet, the editor inserts the corresponding SQL template into your current SQL editor.

7. Click **Run SQL** to execute your queries. 

## Generating SQL statements for a table object 
1. In the left pane, expand the schema and right-click the table you want to create queries. 
2. From the context menu, select the object-specific actions such as:
   - Generate DDL Query: Generates the Data Definition Language (DDL) script to recreate that table’s structure, including columns and constraints.
   - Generate DELETE Query: Generates a template for deleting the rows from the table.
   - Generate INSERT Query: Generates a template for inserting the rows into the table.
   - Generate SELECT Query: Generates a template for retrieving the data from the table.
   - Generate UPDATE Query: Generates a template for updating the rows in the table.
   
        ![Adding a database connection]({{site.baseurl}}/assets/images/sql-query-table-object.png)


   The DELETE, SELECT, INSERT, and UPDATE queries opens in a new Db2 SQL Editor window with the **Results** pane on the right. The DDL script opens in a read‑only window. You can only copy the script, not run it directly in the Editor.
3. Run your respective query by clicking the **Run** button. 
4. View the results in the **Results** pane.


You can follow the same process for generating queries for other Db2 objects, but instead of a Table object, select another Db2 object.