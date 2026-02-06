
# Creating a simple SQL statement
---

1. Ensure that you are connected to a Db2 database in the IBM Db2 Developer Extension.

2. Create a new file by clicking **File > New File**. 

3. Save the file with a .sql extension (for example, anyname.sql).

   The .sql extension enables the extension’s syntax help features, such as syntax highlighting, validation, auto‑suggestions, and predefined SQL snippets.

4. Type the first few letters of the **SELECT** statement.
   

      ![Code completion for LOCATE_IN_STRING]({{site.baseurl}}/assets/images/getting-started-select-snippet 2.png)



5. Select the SELECT snippet from the suggestions list to insert the basic structure of a SELECT statement.

   The syntax help features display SQL snippets and suggestions, including keywords, table names, and other database objects.

6. Review the inserted code:

   - **Syntax highlighting** applies different colors to keywords, variables, and object names to improve readability.
   - **Syntax checking or validation** underlines errors with squiggly lines. Hover over an underlined element to view the error and possible fixes.
   - To view all issues, click **View problems** in the pop‑up or open **View** > **Problems**.

7. Replace the placeholder texts with your values. The following example brings all the rows from the table employee in the schema DB2INST1.

   ```

   SELECT *
   FROM DB2INST1.employee;

   ```

8. Save the file.


Continue writing your SQL statements with the assistance of the extension’s syntax help features, which help you to insert correct SQL elements, reduce errors, and speed up the development.
