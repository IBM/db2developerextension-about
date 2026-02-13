---
title: "Troubleshooting Docker and Colima runtime issues"
---

# {{ page.title }}

This topic provides guidance for diagnosing and resolving Docker and Colima issues when using the IBM Db2 Developer Extension. The extension uses Colima as the default container runtime on macOS and Docker Engine on Linux and Windows Subsystem for Linux (WSL). The troubleshooting steps help you to ensure that the extension can create, start, and manage Db2 containers reliably across supported environments.


## Switching between Docker Desktop and Colima (macOS)

**Problem**: The extension automatically switches to Colima on macOS and prevents you from using Docker Desktop as your preferred container runtime.


**Solution**:

The extension uses Colima by default on macOS to ensure optimal compatibility. If you want to use Docker Desktop instead, switch the Docker context manually using the following commands:

1. Switch to Docker Desktop context:
   ```bash
   docker context use default
   ```

2. Verify the active context:
   ```bash
   docker context ls
   ```

3. Run the following command to switch back to Colima:
   ```bash
   docker context use colima
   ```

> **Note**: Ensure that only one container runtime (Docker Desktop or Colima) is running at a time to avoid conflicts.
{: .note-right}

## Resolving Colima startup or behavior issues (macOS)


**Problem**: Colima fails to start or behaves inconsistently, often after uninstalling Docker Desktop or other container tools.

**Solution**: Restart Colima. If the problems persist, rebuild the Colima VM to restore a clean environment using the following commands:

1. Stop Colima:
   ```bash
   colima stop --force
   ```

2. Start Colima again:
   ```bash
   colima start
   ```

3. If the issue persists, restart Colima:
   ```bash
   colima restart
   ```

4. If the problem remains, delete and recreate the VM (this removes Colima‑managed containers, images, and volumes):

   > **Important**: The `colima delete` command removes all containers, images, and volumes. Back up any important data before running the `colima delete` command.
   {: .note-right}

   ```bash
   colima delete
   colima start --cpu 2 --memory 4
   ```

5. Clean up the deprecated Docker Desktop entries if present (for example, "credsStore": "desktop") in `$HOME/.docker/config.json`.

For more information about Colima configuration and troubleshooting, see [Colima documentation](https://github.com/abiosoft/colima).

## Repairing a corrupted Colima VM (macOS)

**Problem**: Colima VM fails to start due to corrupted VM or disk issues.

**Solution**: Recreate the Colima VM using the following commands:

1. Stop Colima:
   ```bash
   colima stop --force
   ```

2. Delete the corrupted VM:
   ```bash
   colima delete
   ```

3. Recreate Colima with recommended settings:
   ```bash
   colima start --cpu 2 --memory 4 --disk 60
   ```

4. Verify Colima is running:
   ```bash
   colima status
   ```

## Inspecting the Docker container

You need to verify the `db2server` container's state, logs, configuration, or resource usage using the following commands:

1. Enter db2server container as db2inst1 user:

   ```bash
   docker exec -it db2server sh -c "su - db2inst1"
   ```

   Use the previous command to access the container as the Db2 instance owner and run Db2 commands directly.

2. View the container logs:

   ```bash
   docker logs -f db2server
   ```

   Use the previous command to monitor the container logs as they are generated. Press `Ctrl+C` to stop viewing the real-time logs.

3. View all the container logs:

   ```bash
   docker logs db2server
   ```

   Use the previous command to view the complete log history of the container.

4. List all the containers:

   ```bash
   docker ps -a
   ```

   Use the previous command to see all the containers, including those that have stopped. This allows you to confirm whether the db2server container exists and check its current status.

5. Get detailed container information:

   ```bash
   docker inspect db2server
   ```

   Use the previous command to view detailed configuration and state information about the container, including network settings, mounts, and environment variables.

6. Monitor real-time resource usage:

   ```bash
   docker stats db2server
   ```

   Use the previous command to monitor CPU, memory, network, and disk I/O usage in real time. Press `Ctrl+C` to stop monitoring.

7. Enter container with bash shell:

   ```bash
   docker exec -it db2server bash
   ```

   Use the previous command to open a bash shell inside the container. This lets you perform general troubleshooting and inspect the file system directly.


## Create Instance button changes to Update Instance after Db2 instance creation

**Problem**: After creating a Db2 instance, the button label changes from **Create Instance** to **Update Instance**.

**Solution**:

This is expected behavior. The button label change indicates that a Db2 instance already exists. The **Update Instance** button allows you to:
- Modify instance configuration.
- Update port numbers.
- Change resource allocations.

If you want to create a new instance, you must first delete the existing instance.

## Resolving non‑root user permission limitations

**Problem**: Non-root users without administrative privileges cannot use the extension.

**Solution**:

The extension requires administrative permissions for the following reasons:

- **Docker daemon access**: Docker requires root or sudo privileges to manage containers.
- **Container management**: Creating, starting, and stopping containers requires elevated permissions.
- **Port binding**: Binding to ports (especially ports below 1024) requires administrative access.
- **System resource allocation**: Allocating memory and CPU resources to containers requires elevated privileges.

1. Request administrative access from your system administrator.
2. Add the user to the `docker` group (Linux/WSL only):
   ```bash
   sudo usermod -aG docker $USER
   ```
   Then log out and log back in for the changes to take effect.

3. Ensure your macOS account has administrator privileges.

> **Note**: Add the user to the docker group to run Docker commands without sudo. This action gives the user root‑level access, so perform this step only on trusted systems.
{: .note-right}

## Resolving port conflicts

**Problem**: The Db2 instance fails to start because the required ports are in use.

**Solution**:

1. Identify the process that is using the port:
   - On macOS/Linux:
     ```bash
     lsof -i :50000
     lsof -i :55000
     ```
   - On Windows:
     ```bash
     netstat -ano | findstr :50000
     netstat -ano | findstr :55000
     ```

2. Stop the conflicting process or choose different ports when creating the instance.

3. Stop any other Db2 instance that is using the required ports:
   ```bash
   docker stop db2server
   ```

4. Verify ports are free before creating a new instance:
   ```bash
   docker ps -a
   ```

## Resolving insufficient memory and resource issues


**Problem**: Db2 container fails to start or crashes due to insufficient memory.

**Solution**:

The Db2 Community Edition requires a minimum of 4 GB of RAM. Ensure your system meets these requirements:

1. Check available system memory:
   - On macOS:
     ```bash
     vm_stat
     ```
   - On Linux:
     ```bash
     free -h
     ```

2. For Colima on macOS, allocate sufficient memory:
   ```bash
   colima stop
   colima start --memory 4
   ```

3. In Docker Desktop, increase the memory allocation in **Preferences** → **Resources** → **Memory**.

4. Close other memory‑heavy applications.

> **Note**: For optimal performance, allocate at least 6 GB of RAM to the container if your system has sufficient resources.
{: .note-right}

## Resolving network connectivity issues

**Problem**: The extension or external tools cannot connect to the Db2 instance running in the container.

**Solution**:

1. Verify the container is running:
   ```bash
   docker ps
   ```

2. Check the Db2 listening ports:
   ```bash
   docker exec db2server netstat -an | grep 50000
   ```

3. Verify port mapping:
   ```bash
   docker port db2server
   ```

4. Test host connectivity:
   ```bash
   telnet localhost 50000
   ```

5. Check firewall settings to ensure that the ports are not blocked.

6. Restart the container:
   ```bash
   docker restart db2server
   ```

## Resolving container startup failures

**Problem**: The `db2server` container starts but exits immediately.

**Solution**:

1. Check the container logs for error messages:
   ```bash
   docker logs db2server
   ```

2. Inspect the container's exit code:
   ```bash
   docker inspect db2server --format='{{.State.ExitCode}}'
   ```

3. Address common causes:
   - **Exit code 137**: Indicates an out‑of‑memory condition. Increase the container’s memory allocation.
   - **Exit code 1**: Indicates a configuration error. Verify environment variables and volume mounts.
   - **Exit code 126**: Indicates a permission issue. Ensure that mounted volumes have the correct file permissions.

4. Restart the container with verbose logging:
   ```bash
   docker start db2server
   docker logs -f db2server
   ```

## Resolving Db2 instance initialization issues

**Problem**: The container starts, but the Db2 instance fails to initialize.

**Solution**:

1. Check the Db2 diagnostic logs inside the container:
   ```bash
   docker exec -it db2server sh -c "su - db2inst1 -c 'db2diag -a'"
   ```

2. Verify the Db2 instance status:
   ```bash
   docker exec -it db2server sh -c "su - db2inst1 -c 'db2pd -'"
   ```

3. Start the Db2 instance manually:
   ```bash
   docker exec -it db2server sh -c "su - db2inst1 -c 'db2start'"
   ```

4. Recreate the container if the initialization issue persists:
   ```bash
   docker stop db2server
   docker rm db2server
   ```
   Create a new instance using the extension.

## Resolving Docker permission denied errors

**Problem**: Commands fail with "permission denied" errors when trying to access Docker.

**Solution**: Only privileged users can access the Docker daemon. Adding the user to the Docker group grants the required permissions to run Docker commands without sudo.

1. On Linux or WSL, verify if your user is in the Docker group:
   ```bash
   groups $USER
   ```

2. Add your user to the Docker group if the user is not in the group:
   ```bash
   sudo usermod -aG docker $USER
   ```

3. Log out and log back in for the changes to take effect.

4. Verify Docker socket permissions:
   ```bash
   ls -l /var/run/docker.sock
   ```

5. On macOS with Colima, ensure Colima is running:
   ```bash
   colima status
   ```


## Resolving WSL-specific issues

**Problem**: Docker commands fail in WSL with "cannot connect to the Docker daemon" errors.

**Solution**:

1. Verify that WSL 2 is installed:
   ```bash
   wsl --list --verbose
   ```

2. Ensure Docker Desktop has WSL integration enabled:
   - Open Docker Desktop and go to **Settings** → **Resources** → **WSL Integration**.
   - Enable integration for your WSL distribution.

3. Restart WSL:
   ```bash
   wsl --shutdown
   ```
   Restart Docker Desktop and open WSL again.

4. Verify Docker connectivity:
   ```bash
   docker version
   ```
Docker Desktop must expose its daemon to WSL. Integration settings ensure WSL distributions can communicate with the Docker engine.


### Resolving performance issues in the Db2 container

**Problem**: Db2 container performance is slow or unstable in WSL.

**Solution**:

1. Create or edit the `.wslconfig` on your Windows user directory (`C:\Users\<YourUsername>\.wslconfig`):
   ```ini
   [wsl2]
   memory=8GB
   processors=4
   ```

2. Restart WSL:
   ```bash
   wsl --shutdown
   ```

3. Verify resource allocation:
   ```bash
   free -h
   nproc
   ```

WSL uses dynamic resource allocation by default, which might not provide stable performance for Db2. Setting explicit limits improves the container performance and reliability.

## Related topics

- For more information about troubleshooting Db2 instance creation, see [Troubleshooting Db2 Instance creation errors](db2-instance-creation-errors.md).

- For problems specific to the Db2 Community Edition, such as query execution errors or performance issues, see [Db2 Community Edition for Docker](https://www.ibm.com/docs/en/db2/12.1.x?topic=deployments-db2-community-edition-docker).

- For reporting issues with the extension, see [Opening an issue and providing logs](opening-an-issue-and-providing-logs.md).