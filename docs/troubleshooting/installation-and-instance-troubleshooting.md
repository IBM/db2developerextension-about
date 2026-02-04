---
title: "Installation and instance troubleshooting"
---

# {{ page.title }}

This section provides solutions for common issues that you might encounter during Db2 instance installation and management.

## Recovering from installation failures

If you encounter issues during the Db2 instance installation (for example, errors related to Docker, Colima, or Homebrew), you can restart the extension to recover from the failed installation.

### Procedure

1. Reload VS Code by using one of the following methods:
   - Open the Command Palette (press `Cmd+Shift+P` on macOS or `Ctrl+Shift+P` on Windows/Linux) and select **Developer: Reload Window**.
   - Press `Cmd+R` on macOS or `Ctrl+R` on Windows/Linux.

2. After VS Code reloads, a pop-up window appears with options for cleanup and reinstallation due to the previous faulty installation.

3. Follow the prompts to clean up any incomplete or corrupted setup before attempting a fresh installation.

> **Note**: If the installation fails midway, a **Cleanup and Reinstall** message automatically appears, allowing you to retry the process. If VS Code is forcefully closed during installation (for example, due to a crash or manual quit), the same pop-up appears on restart to handle cleanup and reinstallation.
{: .note-right}

## Understanding the Restart Instance button

The **Restart Instance** button, available after a successful Db2 installation, helps you refresh the Db2 instance when needed. Understanding how it works can help you troubleshoot connection or performance issues.

### How the Restart Instance button works

The **Restart Instance** button performs a tiered restart process:

1. **Soft restart (default)**: The button first attempts a soft restart by running `db2stop` followed by `db2start` to refresh the Db2 engine without disrupting the underlying container. This is the fastest option and resolves most issues.

2. **Full restart (fallback)**: If the extension encounters issues with `db2stop` or `db2start` (for example, due to locked resources or connection problems), it escalates to a full restart process:
   - On macOS: Restarts Colima (the lightweight VM for Docker).
   - Restarts Docker services.
   - Restarts the Db2 Community Edition container.
   - Runs `db2start` again to ensure that the instance is fully operational.

This tiered approach minimizes downtime for simple refreshes but provides a robust fallback for more persistent issues.

### When to use the Restart Instance button

Use the **Restart Instance** button when you experience:
- Connection timeouts or failures
- Slow query performance
- Database lock issues
- Unexpected errors after configuration changes

## IBM Db2 Community Edition resources

For problems specific to the Db2 Community Edition (for example, query execution errors, inherent limitations in the Docker image, or performance issues), refer to the official IBM Db2 Community Edition documentation:

- [IBM Db2 Community Edition documentation](https://www.ibm.com/docs/en/db2/11.5?topic=edition-community)

The VS Code extension uses the Db2 Community Edition Docker image, so any core Db2 engine problems should be addressed by using the official documentation.

### Manual installation alternative

If you prefer to install Db2 Community Edition manually (outside the extension), follow the installation steps in the IBM documentation as an alternative to the extension's automated setup.

## Common installation issues

### Homebrew installation hangs on macOS

**Problem**: The Homebrew installation process appears to hang or does not complete.

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

### WSL integration issues on Windows

**Problem**: The Db2 instance fails to create in WSL.

**Solution**:
1. Verify that WSL 2 is installed and set as the default version.
2. Ensure that Docker Desktop for Windows has WSL integration enabled.
3. Check that your WSL distribution has sufficient resources allocated.
4. Restart Docker Desktop and try again.

### Port conflicts

**Problem**: The Db2 instance creation fails due to port conflicts.

**Solution**:
1. Check if another application is using the specified port.
2. Choose a different port number (between 1 and 65535) when creating the instance.
3. On macOS or Linux, use the command `lsof -i :<port_number>` to identify processes using the port.
4. On Windows, use `netstat -ano | findstr :<port_number>` to identify processes using the port.