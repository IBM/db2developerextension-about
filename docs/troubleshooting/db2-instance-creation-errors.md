---
title: "Db2 Instance creation errors"
---

# {{ page.title }}

The topic provides solutions for common issues that you might encounter during the Db2 instance creation and management.

## Db2 Instance creation failures

If you encounter issues during the Db2 instance creation (for example, errors that are related to Docker, Colima, or Homebrew), you can restart the extension to recover from the failed installation.

### Solution

1. Reload VS Code by using one of the following methods:
   - Open the Command Palette (press `Cmd+Shift+P` on macOS or `Ctrl+Shift+P` on Windows or Linux) and select **Developer: Reload Window**.
   - Press `Cmd+R` on macOS or `Ctrl+R` on Windows or Linux.

   After VS Code restarts, a pop‑up appears prompting you to complete the cleanup and reinstallation process.

3. Follow the instructions to remove any incomplete or corrupted installation before proceeding with a fresh installation.

   > **Note**: If VS Code was closed unexpectedly during installation, whether due to a crash or manual termination, the cleanup prompt automatically appears the next time you start VS Code.
   {: .note-right}



## Common instance creation issues

### Homebrew installation errors on macOS

**Problem**: The Homebrew installation process hangs or does not complete.

**Solution**:
1. Check the terminal window that opened during installation for any prompts or error messages.
2. Ensure that you entered your system password when prompted.
3. If the installation is stuck, press `Ctrl+C` to cancel it, then reload VS Code and try again.
4. Verify that you have a stable internet connection, as Homebrew downloads packages from the internet.

### Docker or Colima fails to start

**Problem**: The Db2 instance creation fails with Docker or Colima errors.

**Solution**:
1. Ensure that no other Docker-related processes are running on your system.
2. Check that you have sufficient system resources (at least 4 GB of available RAM).
3. On macOS, try manually restarting Colima by running `colima restart` in the terminal.
4. If the issue persists, delete the existing instance and try creating a new one.

### WSL integration errors on Windows

**Problem**: The Db2 instance fails to create in WSL.

**Solution**:
1. Verify that WSL 2 is installed and set as the default version.
2. Ensure that Docker Desktop for Windows has enabled WSL integration.
3. Check that your WSL distribution has allocated sufficient resources.
4. Restart Docker Desktop and try again.

### Port errors

**Problem**: The Db2 instance creation fails due to port conflicts.

**Solution**:
1. Check if another application is using the specified port.
2. Choose a different port number (between 1 and 65535) when creating the instance.
3. On macOS or Linux, use the command `lsof -i :<port_number>` to identify processes using the port.
4. On Windows, use `netstat -ano | findstr :<port_number>` to identify processes using the port.



For problems specific to the Db2 Community Edition, for example, query execution errors, inherent limitations in the Docker image, or performance issues, see [IBM Db2 Community Edition documentation](https://www.ibm.com/docs/en/db2/12.1.x?topic=deployments-db2-community-edition-docker)


