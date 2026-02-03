---
title: "Running stored procedures in the SQL editor"
---

# {{ page.title }}

This topic shows you how to execute stored procedures that are stored under a schema using the SQL editor and how to understand the execution results.

## Executing a stored procedure using CALL statement

To execute a stored procedure in the SQL editor, use the CALL statement with the schema-qualified procedure name.

### Syntax

```sql
CALL schema_name.procedure_name(parameters);
```

  Where:
  - `schema_name` is the schema where the procedure is stored (for example, `DB2INST1`).
  - `procedure_name` is the name of the procedure.
  - `parameters` are the input and output parameters required by the procedure.

### Using parameter markers

For procedures with OUT parameters, use the `?` parameter marker to automatically capture and display output values.

**Example:**

The below example shows how to execute the [CalculateBonus procedure]({{site.baseurl}}/docs/working-with-stored-procedures/creating-native-sql-stored-procedures.html#example-complete-spsql-file) that is stored under SAMPLE database under DB2INST1 schema:

```sql
CALL DB2INST1.CalculateBonus('000010', 0.10, ?, ?);
```

  Where:
  - `'000010'` is the employee ID (IN parameter)
  - `0.10` is the bonus rate of 10% (IN parameter)
  - `?` placeholders capture the bonus amount and status message (OUT parameters)

  The `?` acts as a placeholder for each OUT parameter. The extension automatically captures and displays the returned values in the Results pane.

## Procedure

Follow the steps below to execute a stored procedure:

### Step 1: Locate your procedure

Verify that your procedure exists in the database by expanding the schema on the DB2 CONNECTIONS pane:

  1. Navigate to your connection (for example, `localhost@SAMPLE`).
  2. Expand the schema (for example, `DB2INST1`).
  3. Expand the **Procedures** folder.
  4. Locate your procedure (for example, `CALCULATEBONUS`).

If you haven't created the procedure yet, see [Creating native SQL stored procedures]({{site.baseurl}}/docs/working-with-stored-procedures/creating-native-sql-stored-procedures.html#example-complete-spsql-file) for the CalculateBonus example.

### Step 2: Open the SQL Editor

Click the SQL editor icon on the DB2 CONNECTIONS pane.

### Step 3: Select the connection

Ensure the correct connection is selected in the dropdown menu at the top of the editor (for example, `localhost@SAMPLE`).

### Step 4: Write and execute the CALL statement

1. Execute the [CalculateBonus procedure]({{site.baseurl}}/docs/working-with-stored-procedures/creating-native-sql-stored-procedures.html#example-complete-spsql-file) using the command below:

   ```sql
   CALL DB2INST1.CalculateBonus('000010', 0.10, ?, ?);
   ```

2. Click the **Run** button to execute the procedure.

## Understanding the execution results

When you execute a stored procedure, the results are displayed in the **Results** pane on the right side of the editor.

![Result pane showing procedure execution]({{site.baseurl}}/assets/images/result-procedure.png)



  When you execute a procedure, the **Results** pane displays:

  - **Query tab**: Query Results: 1 total rows means the number of rows returned. Since the above stored procedure returns output parameters, you get one row with each output parameter shown as a column.
  - **Output parameters**: Each OUT parameter appears as a column in the result grid.
    - Column headers show generic names like `output-param-1`, `output-param-2` when using `?` parameter markers. These correspond to the actual parameter names in order (for example, `output-param-1` = `P_BONUS_AMOUNT`, `output-param-2` = `P_STATUS_MESSAGE`).
    - Values are displayed in the corresponding cells.



## Exporting results

You can export the query results using the **Export** button in the Results pane:

1. Click the **Export** button.
2. Choose your format:
   - **CSV**
   - **JSON**
3. Select the save location. The results are saved to the specified file.



## Related topics

- [Creating native SQL stored procedures]({{site.baseurl}}/docs/working-with-stored-procedures/creating-native-sql-stored-procedures.html)
- [Supported types of stored procedures]({{site.baseurl}}/docs/working-with-stored-procedures/supported-types-of-stored-procedures.html)
