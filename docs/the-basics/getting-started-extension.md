

# Getting started 
---
The topic guides you through the initial setup of the IBM Db2 Developer Extension, settings, and usage steps. 


## Prerequisites
---
Before you begin, ensure that the following software is installed:

- Visual Studio Code version `1.103.0` or later
- Java Runtime Environment (JRE) version `17` or later


## Installing the Extension
---
1. Open **Visual Studio Code**.
2. Click **Extensions**.
3. Search for **IBM Db2 Developer Extension**.
4. Select the extension and click **Install**.


The Db2 Developer Extension icon (![Db2 developer icon]({{site.baseurl}}/assets/images/Db2-developer-extension-icon.png){:width="25" :height="25"}) appears in the Activity Bar.


## Configuring IBM Db2 Developer Extension
---
1. Open Visual Studio Code and click the gear icon (![gear icon]({{site.baseurl}}/assets/images/gear-icon.png){:width="25" :height="25"}) and then **Settings**. 
2. Go to **Extensions** in the left sidebar and select **IBM Db2 Developer Extension Settings**.
3. Configure the following settings as required:


   ![Db2 developer settings]({{site.baseurl}}/assets/images/extension-settings.png)
   - **Db2service: Max Rows**
     Set the maximum number of rows to fetch in query results (Default is 1000).
   - **Db2service: Service Port**
     Enter the port number for the Db2 service (Default is 9000).


4. Click **Backup and Sync Settings** to save your settings.

## Using the IBM Db2 Developer Extension
---
When you open the Db2 Developer Extension, you can see the **DB2 CONNECTIONS** pane. 


**If you already have a Db2 instance**: 

Click **Add Connection** button or **Add Connection** icon (![Adding a database connection]({{site.baseurl}}/assets/images/add-database-connection.png){:width="25" :height="25"}) in the DB2 CONNECTIONS pane and follow the steps [here](creating-a-database-connection.md#create-db-connection) to create a database connection.


**If you do not have a Db2 instance**: 

Click **Create Db2 instance** button or **Create Db2 Instance** icon (![Creating new Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance.png){:width="25" :height="25"}) in the DB2 CONNECTIONS pane and follow the steps [here](creating-a-database-connection.md#create-db2-instance-id) to create one.

   
   
   ![Creating Db2 instance]({{site.baseurl}}/assets/images/db2-developer-initial-screen.png){:width="300" :height="350"}

## DB2 CONNECTIONS pane  
---

You can see the following icons on the **DB2 CONNECTIONS** pane. 



| **Icon** | **Action** | **Description** |
|----------|------------|------------------|
|  ![Adding a database connection]({{site.baseurl}}/assets/images/add-database-connection.png){:width="25" :height="25"}| **Add Connection** | Add a database connection. |
| ![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"} | **Open SQL Editor** | Open a new SQL Editor to write and run queries. |
| ![Refresh schema]({{site.baseurl}}/assets/images/refresh.png){:width="25" :height="25"} | **Refresh Explorer** | Reload schemas and objects to reflect the latest changes. |
| ![Creating new SQL file]({{site.baseurl}}/assets/images/create-new-sql-file.png){:width="25" :height="25"} | **Create New SQL File** | Open a new editor window where you can write and run SQL queries. |
| ![Creating new Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance.png){:width="25" :height="25"} | **Create Db2 Instance** | Create a new Db2 instance by using the Community Edition license. |
| ![Collapse]({{site.baseurl}}/assets/images/collapse-all.png){:width="25" :height="25"} | **Collapse All** | Collapse all objects to return to a compact view. |

You can see the following icons on each database connection:


![connection toolbar]({{site.baseurl}}/assets/images/dbconnection-toolbar.png){:width="300" :height="200"}

| **Icon** | **Action** | **Description** |
|----------|------------|------------------|
|  ![Connecting to database]({{site.baseurl}}/assets/images/connect-database.png){:width="25" :height="25"}| **Connect** | Connect to a database. |
| ![Editing connection]({{site.baseurl}}/assets/images/edit-connection.png){:width="25" :height="25"} | **Edit Connection** | Edit a database connection. |
| ![Delete connection]({{site.baseurl}}/assets/images/delete-connection.png){:width="25" :height="25"} | **Delete Connection** | Delete a database connection. |
| ![Disconnect connection]({{site.baseurl}}/assets/images/disconnect.png){:width="25" :height="25"} | **Disconnect** | Disconnect a database connection. This icon will be visible only after connecting to the database. |





