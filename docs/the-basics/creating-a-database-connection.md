

# Creating and managing Db2 instances and database connections
---

**IBM Db2 Developer Extension** provides a streamlined way to set up and manage Db2 environments all within your VS Code Editor. Before you can start writing queries or exploring schemas, you need a Db2 instance.

 If you have a Db2 instance, [create a database connection](#create-db-connection) to work with your databases. For users who do not have a Db2 instance, get started by using [IBM Db2 Community Edition to create the instance](#create-db2-instance-id), which offers a free and fully functional environment for development and testing.

When you create a new Db2 instance, the extension automatically handles the following actions:


- Creates two databases testdb (or your chosen name) and SAMPLE.

- Creates corresponding database connections and connects to these databases.

You can immediately start working with the databases—running queries, browsing schemas, and managing objects—without any additional configuration.


## Creating a Db2 instance by using Community Edition {#create-db2-instance-id}
---

> **Note**:
> Skip this step if you already have a Db2 instance.
{: .note-right}

### Prerequisites

Before you create a Db2 instance, ensure that your system meets the following requirements:

##### MacOS

- **Homebrew**: Homebrew is required for installing dependencies such as Colima and Docker CLI. If Homebrew is not installed on your system, the extension shows a prompt to install it during the Db2 instance setup. This opens a terminal window where you can enter your system password and interact as needed. The installation script runs automatically. Monitor the terminal for any errors. After Homebrew is installed, the Db2 instance creation resumes automatically.
  

- **System resources**: Ensure that your system has a minimum of 4 GB of available RAM and sufficient disk space for the Db2 container.

##### Windows Subsystem for Linux (WSL)

If you use the extension within WSL on Windows, ensure that the following prerequisites are met:

- WSL 2 is installed and set as the default version. Run `wsl --set-default-version 2` in PowerShell to set it.
- Docker Desktop for Windows is installed with WSL integration enabled. In Docker Settings, go to **Resources** > **WSL Integration** and enable it.
- Ubuntu or another supported Linux distribution is configured as your WSL environment.
- A minimum of 4 GB of RAM is allocated to WSL.

<!--Without these prerequisites, the Db2 container setup might fail. For more information about WSL setup, see the [Microsoft WSL documentation](https://docs.microsoft.com/en-us/windows/wsl/).-->

#### Dependencies installed 

During the Db2 instance creation, the extension automatically installs the necessary libraries and tools.

##### MacOS


- **Colima**: Lightweight Docker‑compatible runtime used to run the Db2 Community Edition container without Docker Desktop.
- **Docker CLI**: Installed through Homebrew alongside Colima.

##### Linux


- **Docker Engine / Docker CLI**: Installed through the system package manager (for example, apt-get) if they are not already available.


These dependencies are installed on your system to support the Db2 Community Edition container.

### Procedure

To create a Db2 instance by using IBM Db2 Community Edition:
1. On the **DB2 CONNECTIONS** pane, click the **Create Db2 instance** button or the **Create Db2 Instance** icon ![Creating new Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance.png){:width="25" :height="25"}.
   
   The extension checks for an existing Db2 instance on your system. If an instance exists, the **Db2 Instance Already Exists** window opens. For more information, see [Managing an existing Db2 instance](#managing-db2-instance).

2. If no Db2 instance exists, the **Add Db2 instance** dialog opens. Enter the following details:

   ![Creating Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance-window.png)

   - **Host**: Enter the hostname or IP address that hosts the instance.
   - **Port**: Enter the internal Docker port number (between 1 and 65535) for the instance.
   - **Username**: Enter a username for the instance. The username is automatically converted to lowercase.
   - **Password**: Enter a password for the instance.
   - **Database Name**: Enter the name of the database that you want to create. By default, the database name is set to `testdb`.
   
   When you create a Db2 instance, the extension automatically creates two databases:
   - **testdb**: The default database that you specify during instance setup.
   - **SAMPLE**: A sample database for testing and learning purposes.

3. Click **Create Db2 instance**.

4. Review the Db2 instance creation checklist that appears on the right side of the window. The checklist verifies that your environment meets the prerequisites.


   The checklist runs automatically. When all checks are complete, the Db2 instance is created successfully.

   During the Db2 instance creation process, the extension:
   - Creates the `testdb` (or your chosen name) and `SAMPLE` databases.
   - Creates corresponding database connections for both databases.
   - Automatically connects to the `testdb` (or your chosen name) and `SAMPLE` databases.

   The database connections are listed on the **DB2 CONNECTIONS** pane.

   ![testdb-sample-connections]({{site.baseurl}}/assets/images/test-sample-connections.png){:width="200" :height="300"}

   > **Note**: If you prefer to install Db2 Community Edition manually (outside the extension), follow the installation steps in the [IBM Db2 Community Edition documentation](https://www.ibm.com/docs/en/db2/11.5?topic=edition-community).
   {: .note-right}

### Managing an existing Db2 instance {#managing-db2-instance}

If a Db2 instance is already installed on your system, you can see the *Db2 Instance Already Exists* message when you click the **Create Db2 instance** button. You can have only one instance at a time.
  
  
  ![existing db2 instance]({{site.baseurl}}/assets/images/db2-instance-exists.png){:width="550" :height="750"}




The window shows the following information about the instance:


- Status: Indicates the current state of the Db2 Community Edition instance. If the status is *Running*, it means that the instance is active and ready for use.
- Container Name: The container name that runs the Db2 instance.
- Host: The hostname or IP address where the Db2 instance is accessible.
- Port: The port number used for database connection.
- Username: The username for connecting to the Db2 instance.
- Password: The password for connecting to the Db2 instance.
- Available Databases: Lists the databases within the instance. The **connect** button is to establish a connection to the database and the **Drop** button is to delete the database
 
   > **Note**: You can also connect to the database by manually [adding the database connection](#create-db-connection) from the DB2 CONNECTIONS pane.
   {: .note-right}

- Action Buttons
   - **+ Create Database**:  When you click **+ Create Database**, a **Create New Database** dialog appears. Enter the database name in the **Database Name** field, then click **Create & Connect**. 
   
   
      This action will:
      - Create a new database.
      - Create a connection profile for it.
      - Automatically connects the database to the instance by using the newly created database connection.
   - **Restart Instance**: Restarts the Db2 instance by using a tiered restart process:
     - **Soft restart (default)**: Attempts a soft restart by running `db2stop` followed by `db2start` to refresh the Db2 engine without disrupting the underlying container.
     - **Full restart (fallback)**: If issues occur with `db2stop` or `db2start` (for example, due to locked resources or connection problems), the process escalates to a full restart by restarting Colima (on macOS), Docker services, and the Db2 container, then runs `db2start` again.
     
     Click **Restart Instance** button when you experience connection timeouts, slow query performance, database lock issues, or unexpected errors after configuration changes.
   - **Delete Instance**: Removes the Db2 instance completely.
   - **Close**: Closes the window without making the changes.




## Creating a database connection {#create-db-connection}
---
To work with IBM Db2 databases, you need to create a database connection to connect to the required database within the Db2 instance.

1. From the **DB2 CONNECTIONS** pane, click **Add Connection** button or **Add Connection** ![Adding a database connection]({{site.baseurl}}/assets/images/add-database-connection.png){:width="25" :height="25"} to open the **Db2 Connection** dialog.
![Adding a database connection]({{site.baseurl}}/assets/images/add-db2-connection.png)

2. Enter the following details:
      - Host: The IP address or hostname of the Db2 server you want to connect to.
      - Port: The port number used by the Db2 server for database connection.
      - Database: The name of the Db2 database you want to connect to.
      - Connection name: Enter the name for the database connection.
      - Connection URL: Auto-generated JDBC (Java Database Connectivity) URL for the database connection.
      - Username: Enter the username to access the Db2 instance.
      - Password: Enter the password to access the Db2 instance.
3. Under the **Security** section, the checkbox **Use SSL** is selected by default. This option is used to enable SSL encryption for the database connection.
      - **Certificate**: Select the appropriate SSL certificate from the list, or select **None** if SSL is not required.
      - **Truststore Path**: Provide the path to your truststore file.
      - **Truststore Password**: Enter the truststore password.
4. (Optional) Select the **Save credentials** checkbox to save your credentials.  
5. Click **Test connection** to verify the credentials are correct.  
   You get a **Test connection successful** notification if the credentials are correct.
6. Click **Create connection**.  
   If your connection was created successfully, you can see it on the **DB2 CONNECTIONS** pane.


> **Note**: If your database connection gets disconnected, click the **Connect** icon (![Connecting to database]({{site.baseurl}}/assets/images/connect-database.png){:width="25" :height="25"}) on the specific database connection. When prompted, enter the password in the input field of the extension and press **Enter** to connect to the database again.
{: .note-right}



## Editing a database connection
---
To edit a database connection:
1. Click **Edit Connection** icon (![Editing connection]({{site.baseurl}}/assets/images/edit-connection.png){:width="25" :height="25"}) on the connection. The **Db2 Connection** dialog opens.
2. Update the details as required. 
3. Click **Update connection** to update the database connection details. 

## Deleting an unused database connection
---

To delete a database connection, click **Delete Connection** icon (![Delete connection]({{site.baseurl}}/assets/images/delete-connection.png){:width="25" :height="25"}) on the specific database connection.
