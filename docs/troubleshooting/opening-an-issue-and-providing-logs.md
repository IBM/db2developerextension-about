---
title: "Opening an issue and providing logs"
---

# {{ page.title }}

When the extension is not working as expected, you can check the extension's logs to see if you can resolve the issue yourself. If you can't resolve the issue yourself, you can open an issue on the [extension's GitHub Issues](https://github.com/IBM/db2developerextension-about/issues) and attach the logs. The following sections describe how to enable, view, and find the extension's logs.

## Enabling logging

When logging is enabled, IBM Db2 Developer Extension collects information when you're using the extension.

- To enable the extension's logging, open the **Command Palette** and select **Preferences: Open Workspace Settings**. Search for the `vscode-db2.toggleCompletionDebugLogging` setting and enable it.


## Viewing the logs

To view the logs collected by IBM Db2 Developer Extension directly in Visual Studio Code, go to **View > Output**. Select the `Db2 Extension` channel from the dropdown. Only the general extension logs are printed here. 

## Locating the log files

To locate the log files, open the **Command Palette** and select **Developer: Open Extension Logs Folder**. The logs for Db2 Developer Extension are located in the `IBM.db2-for-luw` folder.

