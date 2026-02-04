---
title: "Running SQL commands from any file"
---

# {{ page.title }}

The IBM Db2 Developer Extension provides flexibility in how you execute SQL commands. In addition to using the dedicated SQL Editor, you can run SQL commands directly from any file in Visual Studio Code.

## Running SQL from any file type

You can execute SQL statements from any file type, not just `.sql` files. This feature allows you to integrate Db2 workflows seamlessly into your existing code files, notebooks, or documentation.

### Procedure

To run SQL commands from any file:

1. Open any file in Visual Studio Code (for example, `.sql`, `.txt`, `.md`, or even code files like `.js`, `.py`).

2. Write or paste your SQL statement in the file.

3. Select the SQL statement that you want to execute.

4. Right-click the selected text and choose **Run SQL Command** from the context menu.

5. If prompted, select the active Db2 connection from the dropdown menu.

The query executes against your active Db2 connection, and the results appear in the **Results** pane.

## Benefits of running SQL from any file

- **Flexibility**: Execute SQL queries without switching to a dedicated SQL editor.
- **Integration**: Embed SQL queries in documentation, scripts, or application code for testing and development.
- **Efficiency**: Quickly test SQL statements while working on other files.

## Example use cases

- **Documentation**: Include SQL examples in Markdown files and run them directly to verify they work.
- **Scripts**: Test SQL queries embedded in Python, JavaScript, or other programming language files.
- **Notebooks**: Execute SQL statements from Jupyter notebooks or other notebook formats.
- **Configuration files**: Run SQL commands from YAML, JSON, or other configuration files during setup or testing.

## Additional SQL resources

For more information about Db2 SQL syntax and commands, see the [IBM Db2 SQL documentation](https://www.ibm.com/docs/en/db2/11.5?topic=sql-reference).

This comprehensive reference covers:
- SQL queries (SELECT, INSERT, UPDATE, DELETE)
- Data Definition Language (DDL) statements
- Data Manipulation Language (DML) statements
- Advanced Db2-specific features and functions
- SQL syntax and best practices

> **Tip**: Bookmark the Db2 SQL reference documentation for quick access to syntax details and examples while writing queries.
{: .note-right}