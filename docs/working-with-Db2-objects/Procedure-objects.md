

# Exploring procedure object details


A stored procedure in Db2 is a precompiled and named set of SQL statements that is stored in the database and is invoked using the CALL statement. When you open a procedure, you can see the following three tabs:

- Properties
- Parameters
- Text

## Viewing the procedure details

1. Under the database connection, click the specific schema that contains the procedure.
2. Click the procedure name you want to view. It displays the following details:


      ![procedure details]({{site.baseurl}}/assets/images/procedure-properties.png)

      
   **Properties**: Provides the metadata about the stored procedure.
   - Name: Logical name of the stored procedure. 
   - Schema: The schema under the procedure resides.
   - Specific name: System-generated unique identifier for this procedure version.
   - Language: The language in which the procedure is written.
   - Origin: Indicates how the procedure was created. The screenshot shows SQL, means the procedure was created directly with SQL statements, not in an external language.
   - Created time: The timestamp when the procedure was created.
   - Owner: The database user who created the procedure.

   **Parameters**: The Parameters section lists all the input and output parameters defined for the stored procedure. 


      ![Adding a database connection]({{site.baseurl}}/assets/images/procedure-parameters.png)


   Each column provides specific details:
   - Parameter number: The sequential position of the parameter in the procedure definition.
   - Usage: Indicates how the parameter is used:

      - IN: Passed into the procedure as input.
      - OUT: Returned as output.
      - INOUT: Used for both input and output.

   - Name: The identifier of the parameter as defined in the procedure.
   - Data type: Specifies the type of data the parameter holds (e.g., INTEGER, VARCHAR, BLOB, CLOB, XML).
   - Length: Maximum size of the parameter value:

      - For numeric types, it’s typically the byte size (e.g., 4 for INTEGER).
      - For character or LOB types, it’s the maximum number of characters or bytes.
   - Scale: Indicates the number of digits to the right of the decimal points.
   

   **Text**: It displays the full source code of the stored procedure, including its definition, parameters, language, and SQL logic.


      ![Adding a database connection]({{site.baseurl}}/assets/images/procedure-text.png)


   








