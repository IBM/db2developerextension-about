---
title: "Running SQL statements from any file"
---

# {{ page.title }}

The IBM Db2 Developer Extension supports running SQL statements from any file in Visual Studio Code. SQL statements can be run from any file type, not only .sql files, which helps integrate Db2 workflows within code files, notebooks, or documentation.

### Procedure

To run SQL statements from any file:

1. Open any file in Visual Studio Code (for example, `.sql`, `.txt`, `.md`, or even code files like `.js`, `.py`).

3. Select the SQL statement that you want to run.

4. Right-click the selected SQL statement and choose **Db2: Run SQL** from the menu.

5. Select the active Db2 database connection from the dropdown menu when prompted.

The query runs by using the selected database connection, and the results appear in the Results pane

