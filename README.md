# IBM Db2 Developer Extension
IBM® Db2® Developer Extension integrates Db2 database development directly into Visual Studio Code (VS Code), enabling developers to do a wide range of tasks without switching tools.
Designed for developers, this extension delivers a unified, intuitive environment where you can manage database connections, explore schemas, and write and run SQL.
Complete documentation is available in our [documentation repository](https://ibm.github.io/db2developerextension-about/).
## Licenses
Before downloading this extension, review the [Db2 Developer Extension License Agreement](https://github.com/IBM/db2developerextension-about/raw/main/Licenses/LA_en) and Third Party Notices.
## Overview
This extension provides language support for the Structured Query Language (SQL) syntax used to define, manipulate, and control data in IBM Db2 for Linux, Unix, and Windows databases. It includes productivity features that make it easier to write SQL, such as:
- Syntax checking and highlighting
- Code completion and signature help
- SQL formatting
- Customizable code snippets
- DDL generation
And it includes features that enable you to easily:
- Manage Db2 database connections
- Install and manage Db2 Community Edition instances locally
- Execute SQL queries and view results
- Explore database schemas, tables, views, procedures, and functions
- View detailed information about database objects
- Generate SQL queries and application code for database objects
- Navigate the Db2 catalog
- Work with secure password handling
For more information about the latest features, see our [documentation](https://ibm.github.io/db2developerextension-about/).
## Table of Contents
- [Privacy Notice for Feedback](#privacy-notice-for-feedback)
- [Prerequisites](#prerequisites-for-installing-db2-developer-extension)
- [Configuring Java](#java-runtime-environment)
- [Specifying Port Numbers](#specifying-port-numbers)
- [Extension Settings](#extension-settings)
- [Features](#features)
  - [Db2 Community Edition](#db2-community-edition-installation)
  - [Connection Management](#connection-management)
  - [Schema Browser](#schema-browser)
  - [Object Explorer](#object-explorer)
  - [SQL File and Editor](#sql-file-and-editor)
  - [Code Generation](#code-generation)
  - [Transaction Support](#transaction-support)
  - [LOB Data Viewer](#lob-data-viewer)
  - [SQL Formatting](#sql-formatting)
- [Known Issues](#known-issues)
## Privacy Notice for Feedback
Db2 Developer Extension is provided free of charge, but we ask you to provide us feedback via the various means available, such as submitting an issue in our [GitHub repository](https://github.com/IBM/db2developerextension-about/issues), submitting review comments in the VS Code Marketplace, and keeping the built-in telemetry and crash reports enabled.
This extension uses Microsoft VS Code's Telemetry solution, which collects telemetry data that is used to help understand how to improve the product. While we appreciate the insights this data provides, we also know that not everyone wants to send usage data. You can disable telemetry as described in [Disable Telemetry Reporting](https://code.visualstudio.com/docs/getstarted/telemetry). You can also read [IBM's General Privacy Statement](https://www.ibm.com/privacy) to learn more about our policies.
This current release of Db2 Developer Extension will collect anonymous data for the following events:
- Activation of this VS Code extension
- Connecting to Db2 and errors
- Community edition local instance activation
- SQL execution errors
- Navigating the Db2 catalog
- Deactivation of this VS Code extension
Each of these events is logged with the following information:
- Event time
- Operating system and version
- Country or region
- Anonymous user and session ID
- Version numbers of Microsoft VS Code and Db2 Developer Extension
## Prerequisites for Installing Db2 Developer Extension
Installing Db2 Developer Extension requires the following software:
### Visual Studio Code
- **Db2 Developer Extension 1.2.0 and later**: VS Code 1.103.0 or later is required
Db2 Developer Extension is delivered as an extension to VS Code instead of a stand-alone editor, so you must install and configure VS Code first. We recommend always using the latest version of VS Code available. For information about installing and configuring VS Code, see its [documentation](https://code.visualstudio.com/docs).
### Java Runtime Environment
One of the following Java SDKs or JREs:
- Oracle Java SDK 17, or 21
- OpenJDK version 17, or 21
- Any compatible Java Runtime Environment (JRE) version 17 or higher
**Java Home Configuration Support**: Users can now configure a custom Java Home path for JDBC connectivity.
## Specifying Port Numbers
### Db2 SQL Service
The Db2 SQL Service provides support for parsing Db2 SQL syntax and for communicating with Db2. Complete the following steps to specify the port number that the service will run on:
1. Open VS Code settings and search for the `db2-for-luw.servicePort` setting.
2. Specify the port number or numbers that you want to assign to the Db2 SQL Service.
3. Restart VS Code for the changes to take effect.
**Default port**: 9000
## Extension Settings
This extension provides the following settings:
- `db2-for-luw.servicePort`: Port number for the Db2 service (default: 9000)
- `db2-for-luw.maxRows` : Number of rows to fetch in table details data tab (default: 1000)
## Features
### Db2 Community Edition Installation
The extension automatically provisions a fully functional Db2 Community Edition instance on your local machine — no manual container commands or environment configuration required. The extension installs any required container runtime (if needed), deploys Db2 inside a container, creates the requested databases, and automatically registers the database connections.
#### Prerequisites
| Platform | Requirements |
|---|---|
| All | VS Code, active internet connection, 4 GB available RAM, sufficient free disk space |
| Windows | WSL2 with a supported Linux distribution (e.g. Ubuntu) configured as the default |
| macOS | Nothing extra — Homebrew is installed automatically if needed |
> **Windows note:** WSL2 must be installed and configured before using this feature. The extension detects missing WSL2 and provides a link to the Microsoft installation guide, but does not install WSL2 itself.
#### Supported Container Runtimes
The extension automatically detects and selects the most suitable container runtime in the following order:
1. **Podman** (preferred)
2. **Docker**
3. **Colima** (macOS only)
If none of the supported runtimes are available, the extension installs one automatically:
| Platform | Auto-installed |
|---|---|
| macOS | Homebrew (if needed), then Podman, Docker, or Colima |
| Linux | Podman or Docker |
| WSL2 | Podman or Docker inside WSL2 |
#### Creating a Db2 Instance
1. In the **DB2 CONNECTIONS** view, click the **Create Db2 Instance** button.
2. Enter the required details:
   - **Host**: Hostname or IP address for the instance
   - **Port**: Internal container port (1–65535)
   - **Username**: Access username (auto-converted to lowercase)
   - **Password**: Access password
   - **Database Name**: Name of the database to create (default: `TESTDB`)
3. Click **Create Db2 Instance**.
The extension automatically performs all setup steps and displays real-time progress. When complete, connection profiles are registered in the **DB2 CONNECTIONS** view.
#### Databases Created
After provisioning, the following databases are created and registered automatically:
| Database | Description |
|---|---|
| Your specified database (default: `TESTDB`) | Created with your chosen name |
| `SAMPLE` | IBM's official sample database |
#### Managing Your Db2 Instance
The extension provides commands to manage your local Db2 instance, accessible from the instance status page:
- Start instance
- Stop instance
- Delete instance
- View instance status
### Connection Management
Create, edit, and manage Db2 database connections with the following capabilities:
- **Secure Password Handling**: Option to save passwords securely or enter them only when needed
- **Connection Profiles**: Save and manage multiple database connection profiles
- **Connection Status Monitoring**: Real-time connection status indicators
- **Connection URL**: A bidirectional JDBC URL field that auto-generates the URL as you fill in the Host, Port, and Database fields. You can also paste a complete JDBC URL to automatically populate those fields and any custom JDBC properties
- **Custom JDBC Properties**: In the Optional JDBC Properties section, click **+ Add Property** to add custom connection properties, each requiring a Name and a Value. Click **Remove** to delete a property
### Schema Browser
Explore database schemas, tables, views, procedures, and functions with an intuitive tree view:
- Browse database objects hierarchically
- Quick search and filtering capabilities
- Refresh views to see latest database changes
### Object Explorer
View detailed information about database objects:
- Table structures with column details
- View definitions
- Stored procedure and function signatures
- Foreign key relationships
### SQL File and Editor
Execute SQL queries and view results with advanced features:
- **Syntax Highlighting**: Applies different colors to keywords, variables, and object names to improve readability. Color coding is consistent across all SQL file types — keywords, data types, strings, comments, and other SQL elements are always rendered in the same colors
- **Syntax Checking**: Underlines errors with squiggly lines; hover over an underlined element to view the error and possible fixes. Click **View problems** in the pop-up or open **View > Problems** to see all issues
- IntelliSense code completion
- Query execution with result visualization
- **Query History**: Lists all previously run SQL statements with status details and results. Run at least one SQL statement from the Db2 SQL Editor for history entries to appear
- **Persistent Query History**: Query history is retained even after closing and reopening VS Code — previously run queries are always available for reference
- Multiple result set support
### Streaming Large Result Sets with Pagination
Large query results are streamed and paginated for better performance:
- Results are loaded incrementally rather than all at once, reducing memory usage
- Navigate through pages of results without waiting for the full result set to load
- Ensures a smooth and responsive experience even for queries returning large volumes of data
### Query Cancellation
A **Cancel** button is now available to stop a query that is currently running:
- Cancels an in-progress query execution without closing the editor or losing your work
- Available in both the **SQL file** and the **SQL editor**
- Useful for stopping long-running or unintended queries immediately
### Code Generation
Generate SQL queries and application code for database objects:
- DDL generation for tables, views, and other objects
- INSERT, UPDATE, DELETE statement generation
- SELECT statement generation with customizable options
- Direct copy to SQL editor for immediate execution
### Transaction Support
> **Note:** Transaction support is available in the **SQL file** only.
Each SQL file  maintains a dedicated database connection, preserving transaction state and session state across multiple query executions:
- Execute transaction statements — `BEGIN TRANSACTION`, `ROLLBACK`, `COMMIT`, and `END TRANSACTION` — directly from the SQL file 
- All statements within a tab run on the same connection, allowing Db2 to maintain full transaction context
- Session-specific objects such as temporary tables and session variables remain available across query executions while the connection is active
- Each SQL file is isolated — transactions, temporary tables, and session variables in one tab do not affect other open tabs
- Result sets are limited to 100 rows; run the query directly in the SQL file to retrieve the complete result set
### LOB Data Viewer
View large-object (LOB) data directly in the results panel:
- Supported LOB types: **CLOB, BLOB, DBCLOB, XML, BINARY, Spatial, Vector Embeddings, and Metadata**
- Click any LOB result cell to open the LOB Viewer, which displays the column name, data type, character count, and full content
- Click **Copy** to copy the content to the clipboard
- Open multiple LOB columns simultaneously — each opens in its own tab
- Clicking the same cell again focuses the existing tab instead of opening a duplicate
- Zero-byte or null LOB values are displayed as `NULL` in the viewer
### SQL Formatting
Format SQL code with customizable options:
- Automatic indentation
- Keyword capitalization
- Line breaking and alignment
- Configurable formatting rules
## Limitations
### Db2 Community Edition
- The Db2 Community Edition instance runs in a Docker container and is intended for development and testing purposes only
- Initial setup may take 15-20 minutes depending on your system and network speed
- Requires sufficient disk space for Docker images and database storage (minimum 10GB recommended)
- On macOS, the first-time setup requires Homebrew installation which may prompt for your system password
### General Limitations
- Some advanced Db2 features available in enterprise editions may not be available in the Community Edition
- Performance may vary based on Docker resource allocation
- User privileges may impact installation process
## Known Issues
1. Backward compatibility for Local installation of Db2 might break in windows environment. Cleanup and re-creation of the instance will solve the issue, but data loss is possible.
   
Please report any issues you encounter in our [GitHub repository](https://github.com/IBM/db2developerextension-about/issues).
## Release Notes
For detailed release notes and version history, please visit our [documentation](https://ibm.github.io/db2developerextension-about).
## Support
For support and questions:
- Visit our [documentation](https://ibm.github.io/db2developerextension-about)
- Submit issues on [GitHub](https://github.com/IBM/db2developerextension-about/issues)
---
**Enjoy using IBM Db2 Developer Extension!**
