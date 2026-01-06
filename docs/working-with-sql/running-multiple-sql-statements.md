---
title: "Running SQL queries"
---



# {{ page.title }}


The Db2 Developer Extension for VS Code allows you to execute multiple SQL statements in a single editor session, either by running all queries at once or selecting specific statements to run. Each executed query produces its own result tab in the Results pane, making it easy to view and compare outputs individually.


## Running multiple queries in SQL Editor
---


To execute multiple queries, do the following steps. 
1. Open **SQL Editor**. 
2. In the Status Bar, select the appropraite connection and database.
3. Write SQL queries or you can right-click objects in the desired schema and generate queries in the SQL Editor.
3. Right‑click in the SQL editor and select **Run All Queries**. Alternatively, you can click the **Run** button to run all the queries. 


When you run multiple SQL statements, the extension executes them sequentially and presents a consolidated results in the **Results** pane. Each statement’s result set appears in its own tab (e.g., Query 1, Query 2). 


![Run multiple queries]({{site.baseurl}}/assets/images/multiple-queries.png)



You can search in the Result set and  export your queries to CSV or JSON by clicking the **Export** button.


## Running Selected queries in SQL Editor
---

To run a single SQL query, do the following steps: 
1. Write your SQL query in the **SQL Editor**. 
2. In the Status Bar, select the appropraite connection and database.
3. Right‑click in the SQL editor and select **Run Selected Query**. 


    ![Run single query]({{site.baseurl}}/assets/images/single-query-run.png)

The query result appear in the Results page.


You can save your SQL queries and export the query results in CSV or JSON format for later use. The SQL Query results are also stored in the **QUERY HISTORY** menu in the sidebar. 


