---
title: Resolve File Upload Errors Related to Duplicate Data
description: Fix duplicate data errors that occur when you upload employee attribute data to Microsoft Viva Glint.
manager: dcscontentpm
ms.reviewer: aweixelman
ms.date: 04/17/2025
audience: ITPro
ms.topic: troubleshooting
search.appverid: MET150
ms.custom: 
  - CSSTroubleshoot
  - CI190691
---

# Resolve file upload errors related to duplicate data

When you upload employee attribute data to Microsoft Viva Glint, you might receive one of the following error messages that are caused by duplicate data. To fix the issue, select the relevant error, and follow the appropriate resolution.

## INVALID_EMPLOYEE_DATA: Email or ID is assigned to multiple users

**Message:**

> INVALID_EMPLOYEE_DATA: Email \<Email address, such as user@contoso.com\> is assigned to multiple users in the file.
>
> OR
>
> INVALID_EMPLOYEE_DATA: External user id \<x>\ is assigned to more than one record in the user file. Resolve this duplication and reupload.

**Issue type:** Line-level error

This issue occurs because multiple users in the uploaded file share the same email address or employee ID. Email addresses and employee IDs must be unique in the employee attribute data.

### Resolution

To fix the issue, follow these steps:

1. In the admin dashboard, select the **Configuration** icon, then select **Activity Audit Log** in the **Service Configuration** section.
1. In the log, locate the file that didn't upload, and then select **Download errors file** in the **Details** column.
1. Open the errors file, and then identify the users that are assigned the email address or employee ID that's mentioned in the warning message.
1. Open the employee attribute data file, and use the appropriate method, depending on the file type:

    - If the data file has an *.xlsx* extension, open it in Microsoft Excel.
    - If the data file has a *.csv* extension, use the [Text Import Wizard](https://support.microsoft.com/office/text-import-wizard-c5b02af6-fda1-4440-899f-f78bafe41857) to import the data into Excel by preserving the data in its original format.
1. For each user that's identified in step 3, enter a unique email address or employee ID.

    > [!NOTE]
    > For employees who aren't assigned an email address yet, use the following value as their email address:

    \<Employee ID\>@\<your organization's domain\>
1. Save the employee attribute data file, and then upload it again to Viva Glint.

## DUPLICATED_EMAIL

**Message:**

> DUPLICATED_EMAIL: The Email Address \<Email address, such as user@contoso.com\> in the user file is already assigned to a different user in your Viva Glint People Database.

**Issue type:** Line-level error

This issue occurs because one or more users in the uploaded file are assigned an email address that's already associated with a different user in Viva Glint. Email addresses must be unique in the employee attribute data.

### Resolution

To fix the issue, follow these steps:

1. In the admin dashboard, select the **Configuration** icon, and then select **People** in the **Employees** section.
1. Locate the user that's associated with the email address that's mentioned in the warning message, and then select the user to view their profile.

    > [!NOTE]
    > If the user status is **INACTIVE**, and your organization recycles email addresses for employees who left the organization, we recommend that you change their email address to their Employee ID so that the email address can be assigned to a new employee. This action is also recommended when you deactivate a user in Viva Glint.

    If you can't find the email address that's mentioned in the warning message, see the [DUPLICATED_EMAIL: Deleted user](#duplicated_email-deleted-user) section.
1. Open the employee attribute data file, and use the appropriate method, depending on the file type:

    - If the data file has an *.xlsx* extension, open it in Microsoft Excel.
    - If the data file has a *.csv* extension, use the [Text Import Wizard](https://support.microsoft.com/office/text-import-wizard-c5b02af6-fda1-4440-899f-f78bafe41857) to import the data into Excel by preserving the data in its original format.
1. Identify all users who are assigned the email address that's mentioned in the warning message in the data file.
1. For each user that's identified in step 4, compare their Employee ID to the Employee ID of the user that's found in step 2. If the Employee ID is different, enter a unique email address for the user in the data file.
1. Save the employee attribute data file, and then upload it again to Viva Glint.

## DUPLICATED_EMAIL: Deleted user

**Message:**

> DUPLICATED_EMAIL: The Email Address \<Email address, such as user@contoso.com\> in the user file is already assigned to a different user in your Viva Glint People Database.

**Issue type:** Line-level error

This issue occurs because one or more users in the uploaded file are assigned an email address that's already associated with a user whose record is in a [soft deleted state](/viva/glint/setup/manage-general-settings#disregard-employee-ids-of-previously-deleted-employees) in Viva Glint, but the uploaded Employee ID doesn't match the employee ID of the soft deleted user. 

### Resolution

1. In the admin dashboard, select the **Configuration** icon, and then select **Activity Audit Log** in the **Service Configuration** section.
1. Set the filter to **User Deleted** activity.
1. Verify that the email address that's mentioned in the warning message corresponds to a user who was deleted in Viva Glint within the last 30 days. Then, perform one of the following actions:

     - If the user should remain deleted from Viva Glint, remove their records from the file. Then, upload the file again.
     - If the user should be restored in Viva Glint, and 30 days have passed since the deletion date, upload their record to Viva Glint as a new user.
     - If the user should be restored from their soft-deleted state before 30 days pass, upload their record to Viva Glint by using the same email address and Employee ID values that are tied to their soft-deleted record. Employee ID information isn't available in Viva Glint for soft-deleted users. However, admins can verify the user's Employee ID in Entra.

## DUPLICATED_EXTERNAL_USER_ID

**Message:**

> DUPLICATED_EXTERNAL_USER_ID: The Employee ID \<ID\> in the user file is already assigned to another employee with Email Address \<Email address, such as user@contoso.com\> in the Viva Glint database.

**Issue type:** Line-level error

### Resolution

To fix the issue, identify the correct Employee ID for the associated employee records. Compare the employees in your user file to the **People** section in Viva Glint. Correct the user file as appropriate, and then upload it again.
