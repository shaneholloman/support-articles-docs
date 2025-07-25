---
title: Errors when running desktop flows that include Excel actions
description: Provides mitigation steps for errors generated by Excel actions in desktop flows.
ms.author: iomavrid
author: yiannismavridis
ms.reviewer: amitrou, nimoutzo
ms.date: 07/22/2025
ms.custom: sap:Desktop flows\Office automation
---
# Errors when running desktop flows that include Excel actions

This article outlines steps to mitigate errors that might occur when using [Excel actions](/power-automate/desktop-flows/actions-reference/excel) in Power Automate desktop flows. Some of these errors might occur when you try to open a blank or existing Excel file using the **Launch Excel** action. Most errors occur in the context of multiple Excel actions, and there's no one-to-one mapping between specific errors and actions.

## More information

|Exception|Mitigation steps|
|---|---|
|System.ArgumentNullException: Value cannot be null.</br> Parameter name: type|When Excel fails to open with this error, ensure that Excel is installed, licensed, and properly configured on the computer. If Excel is already installed, you can try to repair your Office installation.|
|System.IO.FileNotFoundException: documentPathSafe|Ensure that the Excel file exists and its name and path are spelled correctly. Also ensure that the file path doesn't contain more than 255 characters.|
|System.IO.FileNotFoundException: Could not load file or assembly 'Microsoft.Office.Interop.Excel' or one of its dependencies. The system cannot find the file specified.|Ensure that you have Excel installed on the computer.|
|System.IO.IOException: The process cannot access the file 'C:\YourPath\YourFile.xlsx' because it is being used by another process.|Ensure that the Excel application isn't being used or locked by another process. Try terminating all open Excel processes and restart Power Automate for desktop.|
|System.UnauthorizedAccessException: Access to the path 'C:\YourPath\YourFile.xlsx' is denied.| Ensure that access to the path and file isn't restricted, and Power Automate can access the file.|
|Microsoft.Flow.RPA.Desktop.Modules.SDK.ActionException: Excel document '<Excel_file_name>' not found.|Ensure that the Excel file is open and its name or path is spelled correctly.|
|System.OutOfMemoryException: Out of memory|Close all open Excel applications and unnecessary programs to free up memory, and then try again.|
|System.Runtime.InteropServices.COMException: Open method of Workbooks class failed|Ensure that the Excel file path doesn't contain more than 255 characters.|
|System.Runtime.InteropServices.COMException: The RPC server is unavailable. (Exception from HRESULT: 0x800706BA)|When an Excel file fails to open with this error, try to enable the **Nest under a New Excel process** option under the **Advanced** group of parameters. The existing Excel process might be terminated before opening this Excel file.|
|System.Runtime.InteropServices.COMException: Unknown name. (Exception from HRESULT: 0x80020006 (DISP_E_UNKNOWNNAME))|Ensure that the target Excel file is open in Protected View.|
|System.Runtime.InteropServices.COMException: Call was rejected by callee. (Exception from HRESULT: 0x80010001 (RPC_E_CALL_REJECTED))|Ensure that the target Excel file isn't being edited (for example, a cell is actively being edited at the time of the action run) or blocked by a pop-up dialog when the corresponding Excel action runs.|
|System.Runtime.InteropServices.COMException: Exception from HRESULT: 0x800A03EC|When you use an Excel action where a column, a row, or both need to be specified, the column index should be greater than zero and less than 16,385, or the column letter should belong to the range between A and XFD. Furthermore, the row index should be greater than zero and less than 1,048,577.|
|System.Runtime.InteropServices.COMException: The object invoked has disconnected from its clients. (Exception from HRESULT: 0x80010108 (RPC_E_DISCONNECTED))|Keep the Excel instance open and active until all Excel actions are complete. Don't close the file manually or through the "Close Excel" action.|
|System.Runtime.InteropServices.COMException: Retrieving the COM class factory for component with CLSID {ID} failed due to the following error: 80040154 Class not registered (Exception from HRESULT: 0x80040154 (REGDB_E_CLASSNOTREG)).|Ensure that you have Excel 2013 or a later version installed on your computer.|

### Exceptions with embedded mitigation steps

Some exceptions include mitigation steps in their error messages:

|Exception|
|---|
|System.Runtime.InteropServices.COMException: The cell or chart you're trying to change is on a protected sheet. To make a change, unprotect the sheet. You might be requested to enter a password.|
|System.Runtime.InteropServices.COMException: The file name is too long. Rename the file with fewer than 207 characters.|
|System.Runtime.InteropServices.COMException: The password you supplied isn't correct. Verify that the <kbd>Caps Lock</kbd> key is off and be sure to use the correct capitalization.|
|System.Runtime.InteropServices.COMException: Excel cannot open the file '<Excel_file_name>' because the file format or file extension is not valid. Verify that the file hasn't been corrupted and that the file extension matches the format of the file.|
|System.ArgumentOutOfRangeException: Specified argument was out of the range of valid values.</br> Parameter name: The column number must be greater than one or less than 16384.|

## Troubleshooting generic COMException (HRESULT: 0x800xxxxx) errors

When you try to open a blank or existing Excel file in Power Automate for desktop, you might receive an error similar to:

> System.Runtime.InteropServices.COMException: Exception from HRESULT: 0x800xxxxx

### Cause

This error might occur due to one or more of the following reasons:

- Office apps (or just Excel) aren't properly installed.
- Power Automate for desktop isn't properly installed.
- The Excel file is synchronized with OneDrive.

### Resolution

- Manually [uninstall](/power-automate/desktop-flows/install#uninstall-power-automate) and [reinstall](/power-automate/desktop-flows/install) Power Automate for desktop. If it doesn't work, ensure you have Excel properly installed.
- To work around the error caused by the synchronization with OneDrive, see [Using Excel files synchronized through OneDrive or SharePoint](/power-automate/desktop-flows/actions-reference/excel#using-excel-files-synchronized-through-onedrive-or-sharepoint).
