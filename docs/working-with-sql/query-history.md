---
title: "Managing queries in Query History"
---

# {{ page.title }}
---

The **QUERY HISTORY** view lists previously executed statements. Run at least one SQL statement from the Db2 SQL Editor so that history entries exist. You can open an entry to see the status details and results.

## Viewing queries in Query History
---

1. On the **DB2 CONNECTIONS** pane, locate **QUERY HISTORY** and expand it.


   This section lists all previously executed queries grouped by the timestamp when the queries were executed and are sorted in reverse chronological order by default.


2. Find the timestamped query record you want to inspect and click it to display the **Execution Summary**.

   Execution summary displays the following details:


   ![Run multiple queries]({{site.baseurl}}/assets/images/history-execution-summary.png)


   - File: Indicates the source of the executed statements. For example, Db2 SQL Editor means the statements were run from the SQL editor in the extension.
   - Executed: Displays the timestamp when the execution occurred. This helps track when the batch of statements was processed.
   - Connection: Shows the connection used for execution.
   - Metric:
      - Number of statements executed: Total count of SQL statements that were run together.
      - Success: Number of statements that executed successfully without errors.
      - Failure: Number of statements that failed during execution.
      - Warning: Number of statements that executed with warnings.
      - Total elapsed time (ms): The cumulative time taken to execute all statements in the group, in milliseconds.

3. Expand the  timestamped query record to show individual statements. Select a statement. The editor displays two tabs:




   - **Status** tab shows the following details:

        ![Run multiple queries]({{site.baseurl}}/assets/images/history-status.png)
        - File: Indicates the source from which the SQL statement was executed
        - Executed: Displays the exact timestamp when the query was executed.
        - Connection: Shows the connection details used for execution.
        - Statement: Displays the actual SQL statement that was executed.
        - Return code: Numeric code indicating the outcome of the execution.
        - SQL code: Db2-specific SQLCODE returned after execution.
        - SQL state: Alphanumeric code that is used for the SQL standard for error reporting.
        - Message: Provides a message about the execution result.
        - Elapsed time (ms): Shows the total time taken to execute the query in milliseconds.
    - **Result** tab displays the output of the executed SQL statement in a tabular format. It provides information about the rows returned, execution time, and options for searching and exporting results.

        ![Run multiple queries]({{site.baseurl}}/assets/images/history-result.png)

        - Rows: Indicates the total number of rows returned by the executed query.
        - Execution Time (ms): Shows the time taken to execute the query in milliseconds.

You can search within the displayed results using the Search box. You can export the query results to CSV or JSON using the **Export** button. 



