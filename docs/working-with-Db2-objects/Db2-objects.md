

# Exploring Tables {#working-with-objects}
---


In Db2, every table is associated with a set of metadata and structural components that define its behavior, organization, and relationships. These components are collectively referred to as table details. They include:
- Properties
- Columns
- Constraints
- Indexes
- Data

## Viewing table details
---

1. Click the database connection and then the schema you want.
2. Expand the **Tables** section and click the table name. It displays the following table details:

      ![Adding a database connection]({{site.baseurl}}/assets/images/table-properties.png)

      
   **Properties**: General details such as table name, schema name, type, encoding scheme, owner, etc.
   
   
   The Properties tab displays the following details:
   - Schema: Schema under which the table resides.
   - Database: Database name.
   - Table space: Logical storage location.
   - Type: Object type (Table).
   - Encoding scheme: Character encoding used for the text data in the table (e.g., UTF-8).
   - No. of primary key columns: Number of columns defined as primary key in metadata.
   - Partition key: Indicates if the table is partitioned and how many columns are used as partition keys.
   - Restrict on drop: Prevents accidental dropping of the table. You must explicitly remove this restriction before dropping.
   - Append on: If set to Yes, new rows are appended at the end of the table. Here, it is disabled.
   - Control: Indicates whether special control features are enabled.
   - Auditing: Specifies if auditing is enabled for this table. Auditing tracks changes for compliance.
   - Data capture: Indicates whether data capture for replication or change tracking is enabled.
   - Owner: User who owns the table.
   - Cardinality: Estimated number of rows in the table.
   - Statistics time: Timestamp of the last statistics update. This default value means statistics have not been collected yet.
   - Created time: Timestamps for creation of the table.
   - Altered time: Timestamps for last modification of the table.


   **Columns**: Lists all column names along with their data types and constraints.


      ![Adding a database connection]({{site.baseurl}}/assets/images/table-columns.png)


   It displays the following details:
   - Column number: Position of the column in the table.
   - Name: The unique identifier for the column within the table.
   - Data type: Specifies the type of data the column can store (e.g., INTEGER, VARCHAR, DECIMAL, DATE).
   - Length: Maximum size of the column data.
   - Scale: Number of digits to the right of the decimal point (used for DECIMAL types).
   - Nullable: Indicates whether the column can contain NULL values.
   - Default value: Value automatically assigned if no value is provided during insert.
   - Encoding scheme:  Character encoding used for text columns (e.g., UTF-8).
   - Generated attribute: Indicates if the column is auto-generated.  


   **Constraints**: Rules applied to the table’s columns. Displays details such as constraint name and type.


      ![Adding a database connection]({{site.baseurl}}/assets/images/table-constraints.png)


   It displays the following details:
   - Name: The name of the constraint.
   - Type: The type of constraint applied to the table. It indicates the rule enforced on the column(s).
      Common Types include:
      - Primary key: Ensures each row has a unique identifier.
      - Foreign key: Links to another table for referential integrity.
      - Unique: Ensures column values are unique.
      - Check: Validates data against a condition.
   - Column name: Shows which column(s) the constraint applies to.
   - Column sequence:  The order of columns in the constraint when multiple columns are involved.
   - Column number: The position of the column in the table. Helps identify the column’s order in the table structure.
   
   **Indexes**: Shows relationships with other objects (like views or indexes).


      ![Adding a database connection]({{site.baseurl}}/assets/images/table-indexes.png)


      It displays the following details:
   - Name: The name of the index.
   - Schema: The schema under which the index is created.
   - Unique: Specifies whether the index enforces uniqueness. If Yes, the index ensures that no two rows have the same value for the indexed column(s).
   - Clustering: Refers to whether the index is a clustered index or not. If it is set to Yes, it means that the table rows are physically sorted by the index column.
   - Cardinality: The number of distinct values in the indexed column(s).
   
   
   **Data**: Displays the actual rows stored in the table.


      ![Adding a database connection]({{site.baseurl}}/assets/images/table-data.png)


>**Note**: The **Max rows** specifies the maximum number of rows to display in the data preview. You can enter desired value in the **Max rows** and press Enter to refresh the data view and show the number of rows entered in the **Max rows** field.
{: .note-right}








