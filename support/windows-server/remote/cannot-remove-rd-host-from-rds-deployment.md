---
title: Can't remove an RD Host from an RDS deployment
description: Resolves an issue where you can't remove an RD Host that no longer exists in Active Directory from an RDS deployment.
ms.date: 01/15/2025
manager: dcscontentpm
audience: itpro
ms.topic: troubleshooting
ms.reviewer: kaushika, robertvi
ms.custom:
- sap:remote desktop services and terminal services\session connectivity
- pcy:WinComm User Experience
---
# Cannot remove an RD Host from an RDS deployment

This article helps to fix the error that occurs when you remove an RD Host that no longer exists in Active Directory from an RDS deployment.

_Original KB number:_ &nbsp; 2925854

## Symptoms

Assume that you try to remove a Remote Desktop Session Host (RD Session Host) or Remote Desktop Virtualization Host (RD Virtualization Host) server from your Remote Desktop Services (RDS) deployment. If the target server was already deleted from Active Directory, you may receive the following error message:

> Could not remove the configuration. Object reference not set to an instance of an object.

## Cause

This issue occurs because the removal operation tries to contact the server in order to remove the Connection Broker from the RDS Management Servers internal group. The operation fails because the computer object cannot be resolved in Active Directory.

## Resolution

To safely remove the server from your RDS deployment, contact Microsoft Customer Support Services. For a complete list of Microsoft Customer Support Services telephone numbers and information about support costs, visit [Customer service phone numbers](https://support.microsoft.com/topic/global-customer-service-phone-numbers-c0389ade-5640-e588-8b0e-28de8afeb3f2).

> [!IMPORTANT]
> We do not recommend that you manually edit the database that is used by the RDS deployment.
