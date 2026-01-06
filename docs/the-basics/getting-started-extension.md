

# Getting started 
---
This topic guides you through the initial setup of Db2 Developer Extension, settings, and usage steps. 


## Prerequisites
---
Before you begin, ensure the following software is installed:

- Visual Studio Code** version `1.103.0` or later
- Java Runtime Environment (JRE)** version `17` or later


## Installing the Extension
---
1. Open **Visual Studio Code**.
2. Click **Extensions**.
3. Search for **IBM Db2 Developer Extension**.
4. Select the extension and click **Install**.


The Db2 Developer Extension icon (![Db2 developer icon]({{site.baseurl}}/assets/images/Db2-developer-extension-icon.png){:width="25" :height="25"}) will be displayed in the Activity Bar.


## Configuring Db2 Developer Extension
---
1. Open Visual Studio Code and click the gear icon in the bottom-left corner and click **Settings** . 
2. Navigate to **Extensions** in the left sidebar and select **IBM Db2 Developer Extension Settings**.
3. You can configure the following settings as required:


   ![Db2 developer seetings]({{site.baseurl}}/assets/images/extension-settings.png)
   - **Db2service: Max Rows**
     Set the maximum number of rows to fetch in query results (Default is 1000).
   - **Db2service: Service Port**
     Enter the port number for the Db2 service (Default is 9000).


4. Click **Backup and Sync Settings** at the top-right corner to save your settings.

## Getting started with Db2 Developer Extension
---
When you open the Db2 Developer Extension, you will see the **DB2 CONNECTIONS** pane. Use this pane to create a Db2 instance or add a database connection.


**If you already have a Db2 instance**: 

Click **Add connection** and follow the steps [here](creating-a-database-connection.md#create-db-connection) to create a database connection.


**If you do not have a Db2 instance**: 

Click **Create Db2 instance** and follow the steps [here](creating-a-database-connection.md#create-db2-instance-id) to create one.

   
   
   ![Creating Db2 instance]({{site.baseurl}}/assets/images/db2-developer-initial-screen.png){:width="300" :height="350"}

## DB2 CONNECTIONS toolbar  
---

You can see the following icons on the **DB2 CONNECTIONS** toolbar. 



| **Icon** | **Action** | **Description** |
|----------|------------|------------------|
|  ![Adding a database connection]({{site.baseurl}}/assets/images/add-database-connection.png){:width="25" :height="25"}| **Add Connection** | Add database connections. |
| ![Opening a new SQL editor]({{site.baseurl}}/assets/images/open-sql-editor.png){:width="25" :height="25"} | **Open SQL Editor** | Open a new SQL editor to write and execute queries. |
| ![Refresh schema]({{site.baseurl}}/assets/images/refresh.png){:width="25" :height="25"} | **Refresh Explorer** | Reload schemas and objects to reflect the latest changes in the database. |
| ![Creating new SQL file]({{site.baseurl}}/assets/images/create-new-sql-file.png){:width="25" :height="25"} | **Create New SQL File** | Opens a new SQL editor window where you can write and execute SQL statements against your connected Db2 database. |
| ![Creating new Db2 instance]({{site.baseurl}}/assets/images/create-db2-instance.png){:width="25" :height="25"} | **Create Db2 Instance** | Create new Db2 instance using the Community Edition license. |
| ![Adding a database connection]({{site.baseurl}}/assets/images/collapse-all.png){:width="25" :height="25"} | **Collapse All** | Collapse all objects to return to a compact view. |

You can see the following icons on the database connection:


![database connection toolbar]({{site.baseurl}}/assets/images/dbconnection-toolbar.png){:width="300" :height="200"}

| **Icon** | **Action** | **Description** |
|----------|------------|------------------|
|  ![Connecting to database]({{site.baseurl}}/assets/images/connect-database.png){:width="25" :height="25"}| **Connect** | Connect to the database. |
| ![Editing connection]({{site.baseurl}}/assets/images/edit-connection.png){:width="25" :height="25"} | **Edit Connection** | Edit the database connection. |
| ![Delete connection]({{site.baseurl}}/assets/images/delete-connection.png){:width="25" :height="25"} | **Delete Connection** | Delete the connection. |
| ![Disconnect connection]({{site.baseurl}}/assets/images/disconnect.png){:width="25" :height="25"} | **Disconnect** | Disconnect the connection. This icon will be visible only after connecting to the database. |





