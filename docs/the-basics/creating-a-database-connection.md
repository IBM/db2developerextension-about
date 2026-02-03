

# Creating and managing Db2 instances and database connections
---

** IBM Db2 Developer Extension** provides a streamlined way to set up and manage Db2 environments all within your VS Code Editor. Before you can start writing queries or exploring schemas, you need a Db2 instance.

 If you have a Db2 instance, [create a database connection](#create-db-connection) to work with your databases. For users who do not have a Db2 instance, get started by using [IBM Db2 Community Edition to create the instance](#create-db2-instance-id), which offers a free and fully functional environment for development and testing.

When you create a new Db2 instance, the extension automatically handles the following actions:


- Creates two databases testdb (or your chosen name) and SAMPLE.

- Creates corresponding database connections and connects to these databases.

This means that you can immediately start working with the databases—running queries, browsing schemas, and managing objects—without any additional configuration.


## Creating a Db2 instance by using Community Edition {#create-db2-instance-id}
---

> **Note**:
> Skip this step if you already have a Db2 instance.
{: .note-right}



   
Use IBM Db2 Community Edition to create your Db2 instance:
1. Click **Create Db2 instance** button or **Create Db2 Instance** icon ![Creating new Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance.png){:width="25" :height="25"} on the **DB2 CONNECTIONS** pane. The extension checks for an existing Db2 instance on your system. If an instance exists, *the Db2 Instance Already Exists* window opens. See [Managing an existing Db2 instance](#managing-db2-instance) for more information. 
2. When no Db2 instance exists, the extension prompts you with the **Add Db2 instance** dialog. Enter the following details in the dialog. In the **Add Db2 instance** dialog, enter the following details:

   ![Creating Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance-window.png)

   - **Host**: Enter the hostname or IP address that hosts the instance.
   - **Port**: Specify the internal docker port number (between 1 and 65535) for the instance.
   - **Username**: Enter a username (converted to lowercase automatically).
   - **Password**: Enter a password.
   - **Database Name**: Enter the name of the database that you want to create. By default, the database name is set to testdb. 
      When you create a Db2 instance, the Db2 Developer Extension automatically creates two databases:
      - testdb: The default database that you specify during instance setup.
      - SAMPLE: The sample database for testing and learning purposes.
3. Click **Create Db2 instance** to create the Db2 instance.

   

4. Review the Db2 instance creation checklist on the right side and verify that your environment meets these requirements.

   > **Note**: If Homebrew is not installed on your system, a message prompts you to install it. Click **Install Homebrew** to complete the installation. After the Homebrew is installed, the Db2 instance creation process continues automatically.
   {: .note-right}

   The checklist runs automatically. When it completes, the Db2 instance is created successfully.


   During this Db2 instance creation process, Db2 Developer Extension:
   - Creates the testdb (or your chosen name) and SAMPLE databases.
   - Creates their corresponding database connections.
   - Connects to testdb (or your chosen name) and SAMPLE databases automatically.

   The database connections are listed on the DB2 CONNECTIONS pane.


   ![testdb-sample-connections]({{site.baseurl}}/assets/images/test-sample-connections.png){:width="200" :height="300"}





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
- Available Databases: Lists the databases within the instance. **Connect** button is to establish a connection to the database and the **Drop** button is to delete the database
 
   > **Note**: You can also connect to the database by manually [adding the database connection](#create-db-connection) from the DB2 CONNECTIONS pane.
   {: .note-right}

- Action Buttons
   - **+ Create Database**:  When you click **+ Create Database**, a **Create New Database** dialog appears. Enter the database name in the **Database Name** field, then click **Create & Connect**. 
   
   
      This action will:
      - Create a new database.
      - Create a connection profile for it.
      - Automatically connects the database to the instance by using the newly created database connection.
   - **Restart Instance**: Restarts the Db2 instance.
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
