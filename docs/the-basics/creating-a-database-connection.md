

# Creating and managing Db2 instances and connections
---
 **Db2 Developer Extension** provides a streamlined way to set up and manage Db2 environments without leaving your editor. Before you can start writing queries or exploring schemas, you need a Db2 instance and a secure database connection.


If you already have a Db2 instance, you can skip the instance creation step and directly create database connections using the extension. For users who do not have an existing instance, the easiest way to get started is by using IBM Db2 Community Edition, which offers a free and fully functional environment for development and testing. 


Once your instance is ready — whether existing or newly created — the extension allows you to create and manage multiple database connections simultaneously, enabling you to work across different environments without switching tools or losing context.



## Creating a Db2 instance using Community Edition {#create-db2-instance-id}
---

> **Note**:
> Skip this step if you already have a Db2 instance.
{: .note-right}
   
Use IBM Db2 Community Edition to create your Db2 instance:
1. Click **Create Db2 instance** button or **Create Db2 instance** icon ![Creating new Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance.png){:width="25" :height="25"} on the **DB2 CONNECTIONS** pane. 
2. In the **Create Db2 instance** dialog, enter the following details:

   ![Creating Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance-window.png)

   - **Host**: Enter the hostname or IP address where the instance will run.
   - **Port**: Specify the port number for the instance.
   - **Username**: Enter a user name.
   - **Password**: Enter a password.
   - **Database Name**: Enter the name of the database you want to create.
3. Click **Create Db2 instance** to create the Db2 instance.
4. Review Db2 instance creation checklist on the right side and ensure that your environment meets these requirements.

Once all the checklist items are marked complete, the Db2 instance is created. You can now manage your database by adding connections from the Db2 Explorer.

### If a Db2 instance already exists

If a Db2 Community Edition instance is already installed on your system, you will see the *Db2 Instance Already Exists* message when you click the **Create Db2 instance** button. You can only have one instance at a time.
  
  
  ![existing db2 instance]({{site.baseurl}}/assets/images/db2-instance-exists.png)




The window displays the following information about the instance:


- Status: Indicates the current state of the Db2 Community Edition instance. If the status is Running, it means that the instance is active and ready for use.
- Container Name: Displays the name of the container running the Db2 instance.
- Host: The hostname or IP address where the Db2 instance is accessible.
- Port: The port number used for database connections.
- Username: The user name for connecting to the Db2 instance.
- Password: The password for connecting to the Db2 instance.
- Available Databases: Lists databases within the instance. 
   Each database has Connect and Drop options. 
   - Connect: Establish a connection to the database.
   - Drop: Delete the database.

- Action Buttons
   - **+ Create Database**:  When you click **+ Create Database**, a **Create New Database** dialog appears. Enter desired database name in the **Database Name** field, then click **Create & Connect**. 
   
   
      This action will:
      - Create a new database.
      - Create a connection profile for it.
      - Automatically connect the database to the instance using the newly created connection.
   - **Restart Instance**: Restarts the Db2 instance.
   - **Delete Instance**: Removes the Db2 instance completely.
   - **Close**: Closes the window without making the changes.




## Creating a database connection {#create-db-connection}
---
To work with IBM Db2 databases, you first need to create a database connection and then connect to the desired database within the Db2 instance.

1. From the **DB2 CONNECTIONS** pane, click **Add Connection** button or **Add Connection**  ![Adding a database connection]({{site.baseurl}}/assets/images/collapse-all.png){:width="25" :height="25"}   to open the **Db2 Connection** dialog.
![Adding a database connection]({{site.baseurl}}/assets/images/add-db2-connection.png)

2. Enter the Db2 connection details:
      - Host
      - Port
      - Database
      - Connection name
      - Connection URL
      - Username
      - Password
3. (optional) Under the **Security** section, select the checkbox **Use SSL**.
      - **Certificate**: Select the appropriate SSL certificate from the dropdown (or leave as **None** if not required).
      - **Truststore Path**: Provide the path to your truststore file.
      - **Truststore Password**: Enter the truststore password.
4. Select the **Save credentials** checkbox to save your credentials.  
5. Click **Test connection** to verify the credentials are correct.  
   You will get a **Test connection successful** notification if the credentials are correct.
6. Click **Create connection**.  
   If your database connection was created successfully, it will be added to the **Db2 Explorer**.

Db2 Developer Extension supports multiple active database connections. You can create, edit, and manage several connections at once. 

> **Note**:
> To add another database connection, click the plus sign (+) in the **Db2 Explorer** toolbar and follow the above steps from step 2 to step 6. 
{: .note-right}

## Connecting to your Db2 database
---

After creating a database connection, click **Connect** icon (![Connecting to database]({{site.baseurl}}/assets/images/connect-database.png){:width="25" :height="25"}) on the specific database connection to connect to the database within the Db2 instance. 

## Editing and updating a database connection
---
To edit a database connection:
1. Click **Edit Connection** icon (![Editing connection]({{site.baseurl}}/assets/images/edit-connection.png){:width="25" :height="25"}) on the database connection. The **Db2 Connection** dialog opens.
2. Update the details as required. 
3. Click **Update connection** to update the connection details. 

## Deleting an unused database connection
---

To delete a database connection, click **Delete Connection** icon (![Delete connection]({{site.baseurl}}/assets/images/delete-connection.png){:width="25" :height="25"}) on the specific database connection.
