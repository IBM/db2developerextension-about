---
title: "Generating and running SQL statements"
---

# {{ page.title }}
---

You can create SQL statements by multiple methods:
- Using the **Open SQL Editor** icon (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) on the DB2 CONNECTIONS pane.
- Using the **Create New SQL File** icon (![Creating new SQL file]({{site.baseurl}}/assets/images/create-new-sql-file.png){:width="25" :height="25"}) on the DB2 CONNECTIONS pane.
- Right-clicking the object in a schema and generating SQL statements.

## Generating and running SQL statement using the open SQL editor icon
---

1. Click **Open SQL Editor** icon (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) ion the DB2 CONNECTIONS pane. **Db2 SQL Editor** opens.


    ![Adding a database connection]({{site.baseurl}}/assets/images/create-sql-open-sql-editor.png)
2. Select the connection from the dropdrown menu.
3. In the editor, write your SQL statements.
4. Click **Run** to run the SQL statement. Your results appear in the **Results** pane.
5. Click **Export** to download the results in CSV or JSON format.

  > **Note**: You can save your SQL query in .sql or .db2.sql format by clicking the **Save** button.
  {: .note-right}


## Creating SQL statement using the Create New SQL File icon
---

1. Click **Create New SQL File** icon (![Creating new SQL file]({{site.baseurl}}/assets/images/create-new-sql-file.png){:width="25" :height="25"}) on the DB2 CONNECTIONS pane. 
2. A new editor tab opens with the name Untitled. Save the file with a .sql extension.

    > **Note**:
    You can also create new sql file by clicking File > New File and then save it as anyname.sql to enable SQL editing features.
    {: .note-right}

3. In the editor, type your SQL statement. For example, type the first letters of SELECT. The SELECT statement appears in the list of available SQL elements. Click SELECT statement to insert a code snippet with the basic structure.
    ![Creating new SQL file]({{site.baseurl}}/assets/images/file-new-sql-ceate.png)

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

7. Click Run SQL and the system prompts you to select the connection to run your query. Select the required connection and click **Enter** to run the queries. 
    ![Creating new SQL file]({{site.baseurl}}/assets/images/select-connection-prompt.png)
    The Query Status tab opens, showing execution details such as timestamp, SQL statement, return code, elapsed time, etc.
        ![Creating new SQL file]({{site.baseurl}}/assets/images/new-file-sql-status.png)

    Switch to the **Result** tab to view the query output in a table format.
        ![Creating new SQL file]({{site.baseurl}}/assets/images/new-file-sql-result.png)


## Generating and running SQL statements for a table 
To generate SQL statements for a table, do the following steps: 
1. On the DB2 CONNECTIONS pane, click the connection and then the schema you want. Expand the Tables section. Right-click the table you want to create queries.
2. From the context menu, select the object-specific actions such as:
   - Generate DDL Query: Generates the Data Definition Language (DDL) to recreate that table's structure, including columns and constraints.
   - Generate DELETE Query: Generates a template for deleting the rows from the table.
   - Generate INSERT Query: Generates a template for inserting the rows into the table.
   - Generate SELECT Query: Generates a template for retrieving the data from the table.
   - Generate UPDATE Query: Generates a template for updating the rows in the table.
   
        ![Adding a database connection]({{site.baseurl}}/assets/images/generate-sql-table.png)


   The DELETE, SELECT, INSERT, and UPDATE queries opens in a new Db2 SQL Editor window with the Results pane on the right. The DDL script opens in a read‑only window. You can only copy the script, not run it directly in the Editor. For more information, see [Generating DDL for a Db2 object](../the-basics/generating-ddl.md).
3. Run your query by clicking the **Run** button. 
4. View the results in the **Results** pane.


You can follow the same steps given above to generate SQL statements for other object types, such as Views.

> **Note**: If you get errors while writing SQL statements or need the correct syntax for Db2-specific commands, see the [IBM Db2 documentation](https://www.ibm.com/docs/en/db2/12.1.x?topic=started-sql).
{: .note-right}
