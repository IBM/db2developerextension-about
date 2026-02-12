---
title: "Installing Db2 Community Edition manually"
---

# {{ page.title }}

The topic describes how to install Db2 Community Edition manually across Windows, Linux, and macOS systems. You can install Db2 Community Edition automatically by using the IBM Db2 Developer Extension. For more information, see [Creating a Db2 instance by using Community Edition](creating-a-database-connection.md#create-db2-instance-id).

> **Note**: The extension automates the entire installation process, including dependency management, container setup, and database creation. Manual installation is only recommended for users who need custom configurations or prefer to manage their Db2 environment independently.
{: .note-right}

## Installing Db2 Community Edition on Windows 


You can install Db2 Community Edition on Windows either natively or by using Docker containers. Docker-based installation is recommended for development environments as it provides better isolation and easier management.

### Prerequisites


Before installing Db2 Community Edition on Windows, ensure the following requirements are met:
- Administrator privileges on the Windows system
- Docker Desktop for Windows installed (for Docker‑based installations)
- Minimum of 4 GB RAM allocated for running the Db2 container
- Minimum of 20 GB available disk space (recommended)

### Installation options

**Native installation:**
- For detailed instructions on installing Db2 Community Edition natively on Windows, see the [IBM Db2 for Windows installation documentation](https://www.ibm.com/docs/en/db2/12.1.x?topic=system-windows).

**Docker-based installation (Recommended):**
- For Docker-based installation instructions, see the [Db2 Community Edition Docker deployment guide](https://www.ibm.com/docs/en/db2/12.1.x?topic=deployments-db2-community-edition-docker).
- For downloading and installing Docker editions, see [Downloading and installing Docker editions](https://www.ibm.com/docs/en/db2/12.1.x?topic=docker-downloading-installing-editions#c_download_install_dokr__section_npb_z5p_gjb__title__1).



## Installing Db2 Community Edition on Linux

You can install Db2 Community Edition on Linux either natively or by using Docker containers. Docker-based installation is recommended for development and testing environments.

### Prerequisites

Before installing Db2 Community Edition on Linux, ensure the following requirements are met:
- Administrator privileges on the Linux system
- Docker Desktop for Windows installed (for Docker‑based installations)
- User membership in the docker group: `sudo usermod -aG docker $USER`
- Minimum of 4 GB RAM allocated for running the Db2 container
- Minimum of 20 GB available disk space (recommended)


### Installation options

**Native installation:**
- For detailed instructions on installing Db2 Community Edition natively on Linux, see the [IBM Db2 for Linux installation documentation](https://www.ibm.com/docs/en/db2/12.1.x?topic=system-linux).

**Docker-based installation (Recommended):**
- For Docker-based installation instructions, see the [Db2 Community Edition Docker deployment guide](https://www.ibm.com/docs/en/db2/12.1.x?topic=deployments-db2-community-edition-docker).
- For downloading and installing Docker editions, see [Downloading and installing Docker editions](https://www.ibm.com/docs/en/db2/12.1.x?topic=docker-downloading-installing-editions#c_download_install_dokr__section_npb_z5p_gjb__title__1).



## Installing Db2 Community Edition on macOS

You can install Db2 Community Edition on macOS either natively or by using Docker containers. Colima is a lightweight alternative for Docker Desktop that provides excellent compatibility with macOS systems.

### Prerequisites

Before installing Db2 Community Edition on macOS, ensure the following requirements are met:

- **macOS version**: macOS 10.15 (Catalina) or later
- **Homebrew**: Required for installing dependencies. Install Homebrew from [brew.sh](https://brew.sh)
- **System resources**: Minimum 4 GB of available RAM (6 GB recommended for optimal performance)
- **Disk space**: Minimum 20 GB of free disk space
- **Administrator privileges**: Required for installing dependencies and managing containers

### Step 1: Install Homebrew (if not already installed)

If Homebrew is not installed on your system, install it by running the following command:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Follow the on-screen instructions and enter your password when prompted.

### Step 2: Install Colima and Docker CLI

Install Colima and Docker CLI using Homebrew:

```bash
brew install colima docker
```

This command installs:
- **Colima**: A lightweight container runtime for macOS.
- **Docker CLI**: Command-line tools for managing containers.

### Step 3: Start Colima

Start Colima with recommended resource allocations and virtualization framework:

```bash
colima start --cpu 2 --memory 4 --disk 60 --vm-type=vz --vz-rosetta
```

**Parameters explained:**
- `--cpu 2`: Allocates 2 CPU cores to the virtual machine
- `--memory 4`: Allocates 4 GB of RAM (increase to 6 or 8 for better performance)
- `--disk 60`: Allocates 60 GB of disk space
- `--vm-type=vz`: Uses Apple's Virtualization.framework for better performance on macOS
- `--vz-rosetta`: Enables Rosetta 2 for x86_64 emulation on Apple Silicon Macs

> **Note**: The `--vm-type=vz` and `--vz-rosetta` flags provide better performance and compatibility, especially on Apple Silicon Macs. Adjust resource values based on your system capabilities.
{: .note-right}

### Step 4: Verify Colima is running

Check that Colima is running properly:

```bash
colima status
```

You can see output indicating that Colima is running. If not, see the [troubleshooting section](#troubleshooting-macos-installation).

### Step 5: Create Docker volume

Create a persistent volume for Db2 data:

```bash
docker volume create db2data
```

This volume will store all database files and persist data even if the container is removed.

### Step 6: Create environment file

Create a directory for Docker configuration and an environment file:

```bash
mkdir -p ~/Docker
cat > ~/Docker/.env_list << 'EOF'
LICENSE=accept
DB2INSTANCE=db2inst1
DB2INST1_PASSWORD=password
DBNAME=testdb
BLU=false
ENABLE_ORACLE_COMPATIBILITY=false
UPDATEAVAIL=NO
TO_CREATE_SAMPLEDB=false
REPODB=false
IS_OSXFS=true
PERSISTENT_HOME=true
HADR_ENABLED=false
ETCD_ENDPOINT=
ETCD_USERNAME=
ETCD_PASSWORD=
EOF
```

**Important environment variables:**
- `LICENSE=accept`: Accepts the Db2 Community Edition license
- `DB2INSTANCE=db2inst1`: Sets the Db2 instance name
- `DB2INST1_PASSWORD=password`: Sets the password (change this to a secure password)
- `DBNAME=testdb`: Name of the database to create (change as needed)
- `IS_OSXFS=true`: Enables macOS file system compatibility
- `PERSISTENT_HOME=true`: Enables persistent home directory

> **Important**: Edit the `DB2INST1_PASSWORD` value in the file to use a strong password of your choice. You can also change `DBNAME` to your preferred database name.
{: .note-right}

### Step 7: Pull the Db2 Community Edition Docker image

Pull the official Db2 Community Edition image with the correct platform flag:

```bash
docker pull --platform linux/amd64 icr.io/db2_community/db2:latest
```

The `--platform linux/amd64` flag ensures compatibility with both Intel and Apple Silicon Macs. The download may take several minutes depending on your internet connection.

### Step 8: Create and start the Db2 container

Create and start a Db2 container with the following command:

```bash
docker run -d \
  --name db2server \
  --privileged \
  --restart unless-stopped \
  --platform linux/amd64 \
  --shm-size=1g \
  --ipc=host \
  -p 50000:50000 \
  --env-file ~/Docker/.env_list \
  -v db2data:/database \
  icr.io/db2_community/db2:latest
```

**Parameters explained:**
- `--name db2server`: Names the container "db2server"
- `--privileged`: Grants extended privileges required by Db2
- `--restart unless-stopped`: Automatically restarts the container unless manually stopped
- `--platform linux/amd64`: Specifies the platform architecture
- `--shm-size=1g`: Allocates 1 GB of shared memory for Db2
- `--ipc=host`: Uses host IPC namespace for better performance
- `-p 50000:50000`: Maps port 50000 for database connections
- `--env-file ~/Docker/.env_list`: Loads environment variables from the file
- `-v db2data:/database`: Mounts the persistent volume

> **Note**: The container uses port 50000 by default. If you need to use a different port, change the first number in `-p 50000:50000` (e.g., `-p 50001:50000` to use port 50001).
{: .note-right}

### Step 9: Monitor container startup

The Db2 container takes several minutes to initialize (typically 15-20 minutes on macOS). Monitor the startup process:

```bash
docker logs -f db2server
```

Wait until you see the message *Setup has completed*.

Press `Ctrl+C` to stop viewing the logs after initialization completes.

> **Note**: The initial setup can take 15–20 minutes on macOS while the container completes database initialization and configuration.
{: .note-right}

### Step 10: Fix macOS-specific permissions

After the container setup completes, update the permissions for the Db2 authentication binaries and fenced user directories. This prevents authentication failures (SQL1639N) and fenced routine errors (SQL1646N) on macOS:

```bash
docker exec -i db2server sh -c "
  chown -R db2inst1:db2inst1 /database/config/db2inst1 2>/dev/null || true
  chown -R db2inst1:db2iadm1 /database/config/db2inst1/sqllib 2>/dev/null || \
  chown -R db2inst1:db2fadm1 /database/config/db2inst1/sqllib 2>/dev/null || \
  chown -R db2inst1:db2inst1 /database/config/db2inst1/sqllib 2>/dev/null || true
  chown -R db2inst1:db2inst1 /home/db2inst1 2>/dev/null || true
"
```

Fix authentication binary permissions (critical for SQL1639N error prevention):

```bash
docker exec -i db2server sh -c "
  if [ -f /database/config/db2inst1/sqllib/security/db2chpw ]; then
    chown root:db2fadm1 /database/config/db2inst1/sqllib/security/db2chpw 2>/dev/null || \
    chown root:db2iadm1 /database/config/db2inst1/sqllib/security/db2chpw 2>/dev/null || true
    chmod u+s,o+x /database/config/db2inst1/sqllib/security/db2chpw 2>/dev/null || true
  fi
  if [ -f /database/config/db2inst1/sqllib/security/db2ckpw ]; then
    chown root:db2fadm1 /database/config/db2inst1/sqllib/security/db2ckpw 2>/dev/null || \
    chown root:db2iadm1 /database/config/db2inst1/sqllib/security/db2ckpw 2>/dev/null || true
    chmod u+s,o+x /database/config/db2inst1/sqllib/security/db2ckpw 2>/dev/null || true
  fi
"
```

### Step 11: Initialize Db2 instance and create databases

Start the Db2 instance:

```bash
docker exec -i db2server su - db2inst1 -c "
  . ~/sqllib/db2profile
  db2start
"
```

Create the SAMPLE database with official Db2 sample data:

```bash
docker exec -i db2server su - db2inst1 -c "
  . ~/sqllib/db2profile
  db2sampl -force -sql
"
```

Verify the SAMPLE database:

```bash
docker exec -i db2server su - db2inst1 -c "
  . ~/sqllib/db2profile
  db2 connect to SAMPLE
  db2 'SELECT EMPNO, FIRSTNME, LASTNAME, WORKDEPT, SALARY FROM EMPLOYEE FETCH FIRST 5 ROWS ONLY'
  db2 connect reset
"
```

### Step 12: Create your custom database

Create your custom database (replace `testdb` with your database name if you changed it in the environment file):

```bash
docker exec -i db2server su - db2inst1 -c "
  . ~/sqllib/db2profile
  db2 create database testdb USING CODESET UTF-8 TERRITORY US COLLATE USING IDENTITY
  db2 activate database testdb
"
```

Configure the database for remote connections:

```bash
docker exec -i db2server su - db2inst1 -c "
  . ~/sqllib/db2profile
  db2 catalog tcpip node MYNODE remote localhost server 50000
  db2 catalog database testdb at node MYNODE
  db2 update dbm cfg using SVCENAME 50000
  db2 update dbm cfg using AUTHENTICATION SERVER
  db2stop force
  db2start
"
```

### Step 13: Create sample tables and data

Connect to your database and create sample tables:

```bash
docker exec -i db2server su - db2inst1 -c "
  . ~/sqllib/db2profile
  db2 connect to testdb
  
  db2 'CREATE TABLE EMPLOYEE_INFO (
    EMP_ID INT NOT NULL PRIMARY KEY,
    FIRST_NAME VARCHAR(50),
    LAST_NAME VARCHAR(50),
    DEPARTMENT VARCHAR(50),
    HIRE_DATE DATE
  )'
  
  db2 'CREATE TABLE EMPLOYEE_SALARY (
    EMP_ID INT NOT NULL PRIMARY KEY,
    SALARY DECIMAL(12,2),
    BONUS DECIMAL(12,2),
    FOREIGN KEY (EMP_ID) REFERENCES EMPLOYEE_INFO(EMP_ID)
  )'
  
  db2 \"INSERT INTO EMPLOYEE_INFO VALUES
    (101, 'John', 'Doe', 'Engineering', '2023-01-15'),
    (102, 'Jane', 'Smith', 'Sales', '2023-02-20'),
    (103, 'Bob', 'Johnson', 'Marketing', '2023-03-10')\"
  
  db2 \"INSERT INTO EMPLOYEE_SALARY VALUES
    (101, 85000.00, 5000.00),
    (102, 65000.00, 4000.00),
    (103, 72000.00, 4500.00)\"
  
  db2 'SELECT E.FIRST_NAME, E.LAST_NAME, E.DEPARTMENT, S.SALARY, S.BONUS
       FROM EMPLOYEE_INFO E
       JOIN EMPLOYEE_SALARY S ON E.EMP_ID = S.EMP_ID'
  
  db2 connect reset
"
```

### Step 14: Verify installation

Verify that both databases are accessible:

```bash
docker exec -it db2server su - db2inst1 -c "
  . ~/sqllib/db2profile
  db2 list active databases
"
```

You can see both the SAMPLE database and your custom database (testdb) listed in the output.

### Connection details

After successful installation, use the following connection details:

- **Host**: `localhost` or `127.0.0.1`
- **Port**: `50000` (or the custom port you specified)
- **Databases**:
  - `SAMPLE` - Official Db2 sample database with pre-populated tables (EMPLOYEE, DEPARTMENT, etc.)
  - `testdb` - Your custom database with EMPLOYEE_INFO and EMPLOYEE_SALARY tables
- **Username**: `db2inst1`
- **Password**: The password you set in `DB2INST1_PASSWORD` (default: `password`)
- **JDBC URL**: `jdbc:db2://localhost:50000/testdb`

> **Security Note**: Change the default password to a strong password in production environments. Edit `~/Docker/.env_list` and recreate the container.
{: .note-right}

### Managing the Db2 container

**Stop the container:**
```bash
docker stop db2server
```

**Start the container:**
```bash
docker start db2server
```

**Restart the container:**
```bash
docker restart db2server
```

**View the container logs:**
```bash
docker logs db2server
```

**Remove the container (this will delete all data):**
```bash
docker stop db2server
docker rm db2server
```

> **Warning**: Removing the container will delete all databases and data unless you've created persistent volumes. Always back up important data before removing containers.
{: .note-right}


## What's next

After successfully installing Db2 Community Edition:

-  **Create a database connection** in the IBM Db2 Developer Extension. See [Creating a database connection](creating-a-database-connection.md#create-db-connection).

-  **Explore DB2 objects** such as schemas, tables, and procedures. See [Exploring Db2 objects](Exploring-Db2-objects.md).

-  **Start writing SQL queries** using the SQL editor. See [Creating SQL statements](creating-SQL-statement.md).

-  **Learn about procedures** and how to create them. See [Creating native SQL stored procedures](../working-with-stored-procedures/creating-native-sql-stored-procedures.md).

## Related topics

- [IBM Db2 Community Edition documentation](https://www.ibm.com/docs/en/db2/12.1.x?topic=deployments-db2-community-edition-docker)
- [Colima documentation](https://github.com/abiosoft/colima)
- [Docker documentation](https://docs.docker.com/)
- [Db2 instance creation errors](../troubleshooting/db2-instance-creation-errors.md)