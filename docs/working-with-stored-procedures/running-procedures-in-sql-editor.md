---
title: "Running procedures in SQL Editor"
---

# {{ page.title }}

The topic explains how to run the procedures by using the SQL Editor and how to interpret the results .

## Running a procedure using CALL statement

To run a procedure in the editor, use the CALL statement with the schema-qualified procedure name.

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

The following example shows how to run the [CalculateBonus procedure]({{site.baseurl}}/docs/working-with-stored-procedures/creating-native-sql-stored-procedures.html#example-complete-spsql-file) that is stored under SAMPLE database under DB2INST1 schema:

```sql
CALL DB2INST1.CalculateBonus('000010', 0.10, ?, ?);
```

  Where:
  - `'000010'` is the employee ID (IN parameter).
  - `0.10` is the bonus rate (IN parameter).
  - `?` placeholders capture the bonus amount and status message (OUT parameters).

  The `?` acts as a placeholder for each OUT parameter. The extension automatically captures and displays the returned values in the Results pane.

## Procedure

To run a procedure, do the following steps.

### Step 1: Locate your procedure

Verify that your procedure exists in the database by expanding the schema in the DB2 CONNECTIONS pane:

  1. Go to your database connection (for example, `localhost@SAMPLE`).
  2. Expand the schema (for example, `DB2INST1`).
  3. Expand the **Procedures** section.
  4. Locate your procedure (for example, `CALCULATEBONUS`).

If you haven't created the procedure yet, see [Creating native SQL procedures]({{site.baseurl}}/docs/working-with-stored-procedures/creating-native-sql-stored-procedures.html#example-complete-spsql-file) for the CalculateBonus example.

### Step 2: Open the SQL Editor

Click the **Open SQL Editor** (({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"}) in the DB2 CONNECTIONS pane.

### Step 3: Select the database connection

Ensure the correct database connection is selected in the dropdown (for example, `localhost@SAMPLE`).

### Step 4: Write and run the CALL statement

1. Enter the following command to run the [CalculateBonus procedure]({{site.baseurl}}/docs/working-with-stored-procedures/creating-native-sql-stored-procedures.html#example-complete-spsql-file):

   ```sql
   CALL DB2INST1.CalculateBonus('000010', 0.10, ?, ?);
   ```

2. Click **Run**.

## Understanding the results

When you run a procedure, the results are displayed in the **Results** pane on the right side of the editor.

![Result pane showing procedure execution]({{site.baseurl}}/assets/images/result-procedure.png)



  When you run a procedure, the **Results** pane shows:

  - Query tab: Query Results: 1 total rows indicates the the number of rows returned. Since the previous procedure returns output parameters, you get one row with each output parameter shown as a column.
  - Output parameters: Each OUT parameter appears as a column in the result grid.
    - Column headers show generic names like `output-param-1`, `output-param-2` when using `?` parameter markers. These correspond to the actual parameter names in order (for example, `output-param-1` = `P_BONUS_AMOUNT`, `output-param-2` = `P_STATUS_MESSAGE`).
    - Values are displayed in the corresponding cells.



## Exporting results

To export your results:

1. Click **Export** in the **Results** pane.
2. Choose your format:
   - **CSV**
   - **JSON**
3. Select the save location. The results are saved to the specified file.



## Related topics

- [Creating native SQL procedures]({{site.baseurl}}/docs/working-with-stored-procedures/creating-native-sql-stored-procedures.html)
- [Supported types of procedures]({{site.baseurl}}/docs/working-with-stored-procedures/supported-types-of-stored-procedures.html)
