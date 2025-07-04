---
title: Activation Error Sorry, We are Having Some Temporary Server Issues
description: Troubleshooting methods if you continue to see the activation error Sorry, we are having some temporary server issues.
ms.reviewer: vikkarti
manager: dcscontentpm
audience: ITPro
ms.topic: troubleshooting
ms.custom: 
  - sap:Office Suite (Access, Excel, OneNote, PowerPoint, Publisher, Word, Visio)\Installation, Update, Deployment,  Activation
  - Activation\Errors\We are having some temporary server issues
  - CSSTroubleshoot
  - CI 157597
  - CI 159115
  - CI 5840
search.appverid: 
  - MET150
appliesto: 
  - Microsoft 365
ms.date: 05/19/2025
---

# Microsoft 365 Apps activation error: "Sorry, we are having some temporary server issues"

When you activate Microsoft 365 Apps, you might receive the following error message:

> Sorry, we are having some temporary server issues

It's possible the issue might be temporary. If you continue seeing the error, try the following troubleshooting steps to solve the problem.

> [!NOTE]
> Some of these troubleshooting methods can be performed only by a Microsoft 365 admin. If you aren't an admin, see [How do I find my Microsoft 365 admin?](https://support.microsoft.com/office/how-do-i-find-my-microsoft-365-admin-59b8e361-dbb6-407f-8ac3-a30889e7b99b)

<details>
<summary><b>Sign out of Microsoft 365 and sign back in</b></summary>

1. Open a Microsoft 365 app, such as Word.
1. Select your name and profile picture or icon at the top.
1. Select **Sign out**.
1. Select **Sign in**.
1. Make sure that you're signed in with your **Work or School** account, not your personal Microsoft account.
1. Try to activate Microsoft 365 again.

</details>

<details>
<summary><b>Disconnect Work or School credentials</b></summary>

1. From Start, select **Settings** (the gear icon) > **Accounts** > **Access work or school**.
1. If the account you use to sign in to office.com is listed there, but it isn’t the account you use to sign in to Windows, select it, and then select **Disconnect**.
1. Restart the device and try to activate Microsoft 365 again.

</details>

<details>
<summary><b>Reset Microsoft 365 activation state</b></summary>

See [Reset activation state for Microsoft 365 Apps for enterprise](/office/troubleshoot/activation/reset-office-365-proplus-activation-state).

</details>

<details>
<summary><b>Temporarily disable or uninstall third-party antivirus</b></summary>

If you have a third-party antivirus app installed, temporarily disable or uninstall it, and then try to activate Microsoft 365 again.

</details>

<details>
<summary><b>Check whether you're behind a proxy server</b></summary>

If you aren't sure whether you're behind a proxy server, ask your administrator. If so, you (or your administrator) might have to change the proxy settings for Windows HTTP clients. To do so, follow these steps:

1. Open a Command Prompt window as an administrator. From Start, type *cmd.exe* in the search box, right-click **Command Prompt** in the list, and then select **Run as administrator**.
1. Type the following command, and then press Enter:

   `netsh winhttp set proxy <Address of your proxy server>`
  
You need to allow the [URLs and IP addresses](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide&preserve-view=true#microsoft-365-common-and-office-online).
  
You can also allow Microsoft 365 to bypass the proxy server by creating a PAC file. For more information about how to create a PAC file, see [Managing Microsoft 365 endpoints](/microsoft-365/enterprise/managing-office-365-endpoints).

</details>

<details>
<summary><b>Check whether you're behind a firewall</b></summary>

If you aren't sure whether you're behind a firewall, ask your administrator. If you're behind a firewall, it must be configured to enable access to the following URLs:

- `officecdn.microsoft.com`
- `ols.officeapps.live.com/olsc`
- `activation.sls.microsoft.com`
- `odc.officeapps.live.com`
- `crl.microsoft.com/pki/crl/products/MicrosoftProductSecureServer.crl`
- `crl.microsoft.com/pki/crl/products/MicrosoftRootAuthority.crl`
- `crl.microsoft.com/pki/crl/products/MicrosoftProductSecureCommunicationsPCA.crl`
- `www.microsoft.com/pki/crl/products/MicrosoftProductSecureCommunicationsPCA.crl`
- `go.microsoft.com`
- `Office15client.microsoft.com`
- `login.windows.net`
- `login.microsoft.com`
- `login.microsoftonline.com`
- `crl.microsoft.com`
- `cdn.odc.officeapps.live.com`
- `ajax.aspnetcdn.com`
- `officeclient.microsoft.com`
- `aadcdn.msauth.net`
- `aadcdn.msauthimages.net`
- `enterpriseregistration.windows.net`
  
Each firewall has a different method to enable access to these URIs. Check your software's documentation for instructions or ask your administrator to do it for you.

For more information about Microsoft 365 Apps for enterprise URLs and IP addresses, see [Microsoft 365 URLs and IP address ranges](/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide&preserve-view=true).

</details>

<details>
<summary><b>Reset Microsoft Edge settings</b></summary>

> [!IMPORTANT]
> Resetting Edge settings might cause certain webpages that rely on custom settings to not work properly.
  
To restore Edge default settings, follow these steps:
  
1. Open Edge and select **Settings and more** (...) at the top.
1. Select **Settings**.
1. Select **Reset settings** > **Restore settings to their default values**.
1. In the **Reset settings** window, select **Reset**.
1. After the process completes, close Edge and try to activate Microsoft 365 again.

</details>

<details>
<summary><b>Uninstall and reinstall Microsoft 365 apps</b></summary>

1. Run the Microsoft 365 Uninstall troubleshooter to uninstall Microsoft 365 or Office.

   > [!NOTE]
   > To run the troubleshooter, make sure that you're using the same Windows device on which Microsoft 365 or the Office product is installed. Additionally, make sure that your device is running Windows 10 or a later version.

   1. To start the troubleshooter, select the following button.

      > [!div class="nextstepaction"]
      > [Microsoft 365 Uninstall troubleshooter](https://aka.ms/SaRA-OfficeUninstall-sarahome)

      If you receive a pop-up window that displays "This site is trying to open Get Help," select **Open**.
   1. To run the troubleshooter, follow the instructions in the Get Help app.
1. Restart the device.
1. [Install the correct version](https://support.microsoft.com/office/download-install-or-reinstall-microsoft-365-or-office-2024-on-a-pc-or-mac-4414eaaf-0478-48be-9c42-23adc4716658).

</details>

If the previous steps don't solve the problem, try the steps in [Microsoft 365 activation network connection issues](./network-connection-issues.md).
