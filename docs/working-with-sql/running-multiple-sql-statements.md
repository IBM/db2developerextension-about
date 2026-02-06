---
title: "Running SQL statements"
---



# {{ page.title }}


Db2 Developer Extension allows you to run multiple SQL queries in a single editor session, either by running all queries at once or selecting specific statements to run. Each Each ran SQL statements produces its own result tab in the Results pane, making it easy to view and compare outputs individually.


## Running multiple SQL statements in SQL Editor
---


To run multiple SQL statements, do the following steps. 
1. Click Open SQL Editor icon (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) on the DB2 CONNECTIONS pane. Db2 SQL Editor opens. 
2. Select the database connection from the dropdown menu.
3. Write SQL statements in the editor.
4. Right‑click in the editor and select **Run All Queries**. Alternatively, you can click **Run** to run all the statements. 


When you run multiple SQL statements, the extension executes them sequentially and presents the consolidated results in the **Results** pane. Each statement’s result set appears in its own tab (e.g., Query 1, Query 2).

![Run multiple queries]({{site.baseurl}}/assets/images/run-sql-mulitple.png)



You can search in the result set. Click **Export** to download your query results in CSV or JSON.

## Running Selected SQL statements in SQL Editor
---

To run a single SQL statement, do the following steps: 
1. Write your SQL statements in the editor. 
2. Select the appropriate database connection from the dropdown menu.
3. Right‑click in the editor and select **Run Selected Query**. 


    ![Run single query]({{site.baseurl}}/assets/images/run-selected-query.png)

The statement result appears in the **Results** pane.


Click **Save** to save your SQL statements. You can also download the query results in CSV or JSON format for later use. The SQL statements results are also stored in the **QUERY HISTORY** menu in the sidebar.



