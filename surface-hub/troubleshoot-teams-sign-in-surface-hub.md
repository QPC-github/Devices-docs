---
title: Troubleshoot Teams sign-in issues on Surface Hub
description: This page explains recommended troubleshooting steps if you're unable to sign in to Microsoft Teams on Surface Hub. 
manager: frankbu
ms.prod: surface-hub
author: coveminer
ms.author: hachidan
ms.topic: troubleshooting
ms.date: 08/10/2022
ms.localizationpriority: medium
---

# Troubleshoot Teams sign-in issues on Surface Hub

If you can't sign in to Microsoft Teams on Surface Hub, several recommended troubleshooting steps are described on this page.
 
- First, make sure your Surface Hub is running the latest updates. To learn more, see the following video: [How to verify a Surface Hub is fully updated](https://youtu.be/rxL5cUS_3TA).
- Check Microsoft Teams is updated to the latest version. On Surface Hub, open **Microsoft** **Teams**, select **…** > **Settings** > **Check for updates**.

- Use the [Azure sign-in logs](/azure/active-directory/reports-monitoring/howto-troubleshoot-sign-in-errors#troubleshoot-sign-in-errors-using-the-sign-ins-report) for insights into sign-in errors. You can filter by the Surface Hub device account and look for any failures.
- If you still can't sign in, look for the error code displayed on the Teams sign-in screen and review the following table for troubleshooting steps and links to relevant documentation.


| **Error codes**                   | **Possible root cause**           | **How to resolve**        | **Learn more**       |
| --------------------------------- | --------------------------------- | ----------------------------------------------------- | ----------------------------------- |
| **CAA20003**                      | Incorrect time on device          | Ensure [KB5011543](/surface-hub/surface-hub-update-history) or a newer Windows update is installed (build 19042.1682 or later).<br>  | - Video: [How to verify a Surface Hub is fully updated](https://youtu.be/rxL5cUS_3TA)<br>- [Manage Windows updates on Surface Hub](/surface-hub/manage-windows-updates-for-surface-hub)        |
|                                   | Conditional Access (CA) Policy    | A [device account can't have CA enabled](/surface-hub/create-and-test-a-device-account-surface-hub). To resolve this issue, ensure your Surface Hub device account is excluded from any CA policies.<br> <br><br>1. Begin with the Azure AD conditional access [What If tool](/azure/active-directory/conditional-access/troubleshoot-conditional-access-what-if) to see which policies currently apply to your device account.<br>2. Run the tool in [Report-only mode](/azure/active-directory/conditional-access/concept-conditional-access-report-only), which lets you evaluate the impact of Conditional Access policies before enabling them in their environment. | - [Troubleshooting sign-in problems with Conditional Access](/azure/active-directory/conditional-access/troubleshoot-conditional-access-what-if)<br>- [Troubleshoot Conditional Access using the What If tool](/azure/active-directory/conditional-access/troubleshoot-conditional-access-what-if)<br>- [What is Conditional Access report-only mode?](/azure/active-directory/conditional-access/concept-conditional-access-report-only)<br>- Video: [Use the Report Only feature to test Conditional Access policies](https://youtu.be/NZbPYfhb5Kc) |
| **CAA90014** <br>             | Device account password expired   | 1. Open Microsoft Edge and attempt to sign in to [Microsoft 365](https://www.office.com/) with your device account credentials.<br>2. If prompted to change the device account password, go ahead and change it.<br>3. On Surface Hub, go to **Settings** > **Surface** **Hub** > **Accounts**> **Device account** > **Change**.<br>4. Select **Start over with a new device account**. The current device account will be removed when you set up a new one using your new credentials.            | - [Password management (Surface Hub)](/surface-hub/password-management-for-surface-hub-device-accounts)         |
|                                   | Incorrect time on device          | Ensure [KB5011543](/surface-hub/surface-hub-update-history) or a newer Windows update is installed (build 19042.1682 or later).        | - Video: [How to verify a Surface Hub is fully updated](https://youtu.be/rxL5cUS_3TA)<br>- [Manage Windows updates on Surface Hub](/surface-hub/manage-windows-updates-for-surface-hub)           |
|                                   | Multi-Factor Authentication (MFA) | A [device account can't have MFA enabled](/surface-hub/create-and-test-a-device-account-surface-hub#configuration-overview). To resolve this issue, try excluding the Surface Hub device account from MFA and test again.                                                                                                                         | - [Create and test a device account](/surface-hub/create-and-test-a-device-account-surface-hub)       |
| **CAA10001 or AUTH0006**<br>  | Conditional Access (CA) Policy    | Follow the instructions above to resolve Conditional Access issues.       |                |
|                               | No device account added           | To confirm a device account is added:<br><br>1. On Surface Hub, go to **Settings** > **Surface** **Hub** > **Accounts**.<br>2. Verify that a device account is added successfully: A device account will show as **Not Set** if it isn't added.<br>3. [Create and add a device account](/surface-hub/create-and-test-a-device-account-surface-hub) and try connecting to Teams again.      | - [Create and test a device account](/surface-hub/create-and-test-a-device-account-surface-hub)     |
| **unknownautherror**<br>      |Hub still running earlier OS             | Surface Hub v1 only:<br>   1. Ensure the device is updated to [Windows 10 Team 2020 Update (20H2)](/surface-hub/surface-hub-update-history#windows-10-team-2020-update-20h2).<br>2. If your Hub v1 device is still running an earlier OS, it could be affected by the following [known issue:](/surface-hub/surface-hub-2020-team-update-known-issues) **A small subset of v1 Surface Hub devices is not able to automatically upgrade to the Windows 10 Team 2020**<br>3. To resolve, reimage Hub v1 using the [Surface Hub Recovery Tool](/surface-hub/surface-hub-recovery-tool) and upgrade to 20H2.        | - [Known issues: Surface Hub](/surface-hub/surface-hub-2020-team-update-known-issues)<br>- [Using the Surface Hub Recovery Tool](/surface-hub/surface-hub-recovery-tool)      |
|                               | Conditional Access (CA) Policy    | Follow the instructions above to resolve Conditional Access issues.       |     |

## Support requests

If you still can't successfully sign in to Teams, you can [create a support request](https://support.serviceshub.microsoft.com/supportforbusiness/onboarding?). Include the following items: 

- Any error codes displayed when you attempt to sign in to Teams.
- Log files, as noted below. 
 
### Diagnostic Teams log files

When creating a support request with Microsoft Support, the support engineer will require diagnostic log files. Having the logs before creating the support request will allow Microsoft to quickly start troubleshooting the problem.

**To collect Teams log files:** 

1. Connect an external keyboard to Surface Hub. 
2. Open the Teams app and reproduce the issue by attempting to sign in.  
3. Select the Teams app and ensure the focus is on Teams as the active app on the Hub display. 
4. On your keyboard, press **Tab** three times to highlight the UI element for settings, represented by three dots (**...**). 
5. Press **CTRL + ALT + SHIFT + 1** to download the Teams log files.
6. Open **File Explorer**, go to **Downloads**, and look for the folder containing the Teams log files. 
7. Copy the folder to a USB drive. 

To learn more, see [Configure log files for monitoring and troubleshooting in Teams](/microsoftteams/log-files)
 
### Surface Hub & Azure log files

- [Surface Hub log files](/surface-hub/collect-surface-hub-log-files)
- Any applicable [Azure sign-in logs](/azure/active-directory/reports-monitoring/howto-troubleshoot-sign-in-errors#troubleshoot-sign-in-errors-using-the-sign-ins-report) that indicate sign-in failure
