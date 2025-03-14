---
title: Remote laptop disconnects from wireless network
description: Troubleshoot an issue in which remote laptop disconnects from wireless network.
ms.date: 01/15/2025
manager: dcscontentpm
audience: itpro
ms.topic: troubleshooting
ms.reviewer: kaushika, rklemen, v-lianna
ms.custom:
- sap:remote desktop services and terminal services\session connectivity
- pcy:WinComm User Experience
---
# Remote laptop disconnects from wireless network

This article helps troubleshoot an issue in which remote laptop disconnects from wireless network.

This issue may occur when a Remote Desktop client connects to a laptop computer by using an 802.1x wireless network. The laptop intermittently disconnects from the wireless network and doesn't automatically reconnect.

This is a known issue that occurs when the network authentication setting for the wireless network connection is **User authentication**.

To work around this issue, set the network authentication setting to **User or computer authentication** or **Computer authentication**.

> [!NOTE]
> To change the network authentication settings on a single computer, you may need to use the Network and Sharing Center control panel to create a new wireless connection with the new settings.

For a full description of how to configure wireless network settings using GPOs, see [Configure Wireless Network (IEEE 802.11) Policies](/windows-server/networking/core-network-guide/cncg/wireless/e-wireless-access-deployment#bkmk_policies).
