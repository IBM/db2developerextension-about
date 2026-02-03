---
title: "Running SQL queries"
---



# {{ page.title }}


Db2 Developer Extension allows you to execute multiple SQL queries in a single editor session, either by running all queries at once or selecting specific statements to run. Each executed query produces its own result tab in the Results pane, making it easy to view and compare outputs individually.


## Running multiple queries in SQL Editor
---


To run multiple queries, do the following steps. 
1. Click Open SQL Editor icon (![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) on the DB2 CONNECTIONS pane. Db2 SQL Editor opens. 
2. Select the database connection from the dropdown menu
3. Write SQL queries in the SQL Editor.
4. Right‑click in the SQL Editor and select **Run All Queries**. Alternatively, you can click the **Run** button to run all the queries. 


When you run multiple SQL statements, the extension executes them sequentially and presents the consolidated results in the **Results** pane. Each statement’s result set appears in its own tab (e.g., Query 1, Query 2).

![Run multiple queries]({{site.baseurl}}/assets/images/run-sql-mulitple.png)



You can search in the result set. You can also download your query results in CSV or JSON by clicking the **Export** button.

## Running Selected queries in SQL Editor
---

To run a single SQL query, do the following steps: 
1. Write your SQL query in the **SQL Editor**. 
2. Select the appropriate connection from the dropdown menu.
3. Right‑click in the Db2 SQL Editor and select **Run Selected Query**. 


    ![Run single query]({{site.baseurl}}/assets/images/run-selected-query.png)

The query result appears in the **Results** pane.


You can save your SQL queries by clicking the **Save** button. You can also download the query results in CSV or JSON format for later use. The SQL Query results are also stored in the **QUERY HISTORY** menu in the sidebar.



