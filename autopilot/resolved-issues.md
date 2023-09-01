---
title: Windows Autopilot resolved issues
description: Inform yourself about issues with Windows Autopilot deployment that can be resolved by applying the latest cumulative update.
ms.prod: windows-client
ms.technology: itpro-deploy
ms.localizationpriority: medium
author: frankroj
ms.author: frankroj
ms.reviewer: jubaptis
manager: aaroncz
ms.date: 11/17/2022
ms.collection:
  - M365-modern-desktop
  - tier2
ms.topic: troubleshooting
---

# Windows Autopilot - resolved issues

*Applies to:*

- Windows 11
- Windows 10

The following issues are resolved by installing Windows updates. For a list of issues that can be resolved through configuration changes, see [Windows Autopilot - known issues](known-issues.md).

| Applies to | Issues         | KB |
| :---         | :---         |  :---  |
|18362.145 |Autopilot pre-provisioning fails for non-English builds. |[KB4497935](https://support.microsoft.com/help/4497935)|
|18362.207 |BitLocker policies not enforced during Autopilot for nondefault encryption options. |[KB4501375](https://support.microsoft.com/help/4501375)|
|18362.267 |- Windows Autopilot pre-provisioning doesn't work for a non-English OS and you see a red screen that says "Success."<br> - Windows Autopilot reports an AUTOPILOTUPDATE error during OOBE after sysprep, reset, or other variations. This issue typically happens if you reset the OS or used a custom sysprepped image. <br> - BitLocker encryption isn't correctly configured. Ex: BitLocker didn't get an expected notification after policies were applied to begin encryption. <br> - You're unable to install UWP apps from the Microsoft Store, causing failures during Windows Autopilot. If you're deploying Company Portal as a blocking app during Windows Autopilot ESP, you have probably seen this error. <br> - A user isn't granted administrator rights in the Windows Autopilot user-driven hybrid Azure AD-join scenario. This issue is another non-English OS issue. |[KB4505903](https://support.microsoft.com/help/4505903)|
|18362.329 |- The Windows Autopilot for existing devices feature doesn't properly suppress the **Activities** page during OOBE. Because of this issue, you see this extra page during OOBE. <br> - Sysprep /generalize doesn't clear TPM attestation state, which causes TPM attestation failure during later OOBE flow. (This issue isn't a common one, but you could run into it while testing. For example, if you run sysprep /generalize and then reboot or reimage the device to go back through an Autopilot pre-provisioning or self-deploying scenario.) <br> - TPM attestation may fail if the device has a valid AIK cert but no EK cert (this issue is related to the previous item). <br> - If TPM attestation fails during the Windows Autopilot pre-provisioning process, the landing page appears to stop responding. (Basically, the pre-provisioning landing page, where you select "Provision" to start the pre-provisioning process, isn't reporting errors properly). <br> - TPM attestation fails on newer Infineon TPMs (firmware version > 7.69). (Before this fix, only a specific list of firmware versions was accepted). <br> - Device naming templates may truncate the computer name at 14 characters instead of 15. <br> - Assigned Access policies cause a reboot, which can interfere with the configuration of single-app kiosk devices. |[KB4512941](https://support.microsoft.com/help/4512941)|
|18362.387 |A missing AKI extension in EK certificate caused TPM attestation to fail on Windows 10 version 1903. This issue was due to an extra validation added in Windows 10 version 1903 to check that the TPM EK certs had the proper attributes according to the TCG specifications. The KB4517211 update removes this validation. |[KB4517211](https://support.microsoft.com/help/4517211)|
|18362.449 |On self-deploying scenarios, the device is no longer Azure AD-joined after OOBE and can't sign-in with Azure AD credentials or access company resources. |[KB4522355](https://support.microsoft.com/help/4522355) |
|18362.693, 18363.693 |For pre-provisioning scenarios, ESP is marked as **required to show** to ensure the technician flow completes successfully. |[KB4535996](https://support.microsoft.com/help/4535996) |
|18362.752, 18363.752 | - For hybrid scenarios where the user should be an administrator, the user is forced to sign out at the end of ESP. This behavior makes sure that the user is part of the local **Administrators** group the next time they sign in. <br> - Improves the timeout algorithm on ESP to use processor ticks instead of the system time, which can drift if the device hasn't been powered on after a long duration. |[KB4541335](https://support.microsoft.com/help/4541335) |
|18362.815, 18363.815 | - Autopilot Reset state not set to success on completion, causing the Intune admin center to not show the correct status of the device after reset.  <br> - Enable extra log collection useful for support cases and investigations. |[KB4550945](https://support.microsoft.com/help/4550945) |
|18362.815, 18363.815, 19041.488 | - ESP takes a long time during the "Identifying" phase, especially in hybrid and pre-provisioning scenarios.  <br> - Autopilot Update disabled policy wasn't enforced during pre-provisioning scenarios. <br> - Device setup category fails in self-deploying and pre-provisioning scenarios when the ESP policy is set to disabled. <br> - Allows self-deploying and pre-provisioning scenarios to succeed even if multiple MDM providers are listed in Azure AD. <br> - For self-deploying scenarios, a reboot causes the device to navigate to the pre-provisioning flow, even if the user didn't select the pre-provisioning flow.  |[KB4550945](https://support.microsoft.com/help/4550945), [KB4571744](https://support.microsoft.com/help/4571744) |
|18362.836, 18363.836 |Devices with incompatible TPM versions (before v2.0), attestation times out instead of notifying the user of an incompatible hardware version. |[KB4556799](https://support.microsoft.com/help/4556799) |
|18362.1110, 18363.1110, 19041.488 |Microphone icon always shows in OOBE even on devices without audio/voiceover support. | [KB4577062](https://support.microsoft.com/help/4577062), [KB4571744](https://support.microsoft.com/help/4571744)|
|18362.1237, 18363.1237, 19041.661, 19042.661 | - The Privacy page isn't skipped during OOBE for some policy configurations. <br> - Fixes issues during ESP when multiple policy providers are registered (IME and co-management).  <br> - For pre-provisioning scenarios, addresses an issue where the ESP seems to stop responding during Device Preparation category if a reboot occurs. |[KB4586819](https://support.microsoft.com/help/4586819), [KB4586853](https://support.microsoft.com/help/4586853)|
|19041.661, 19042.661 |ESP doesn't use the configured timeout value. |[KB4586853](https://support.microsoft.com/help/4586853)|
|20H2.2020.11C |ESP doesn't use the configured timeout value. |[KB4586853](https://support.microsoft.com/help/4586853)|
|20H2.2020.11C | - The Privacy page isn't skipped during OOBE for some policy configurations. <br> - Fixes issues during ESP when multiple policy providers are registered (IME and co-management).  <br> - For pre-provisioning scenarios, addresses an issue where the ESP seems to stop responding during Device Preparation category if a reboot occurs. |[KB4586819](https://support.microsoft.com/help/4586819), [KB4586853](https://support.microsoft.com/help/4586853)|
|20H2.2020.9C |Microphone icon always shows in OOBE even on devices without audio/voiceover support. | [KB4577062](https://support.microsoft.com/help/4577062), [KB4571744](https://support.microsoft.com/help/4571744)|
|20H1.2020.5C |Devices with incompatible TPM versions (before v2.0), attestation times out instead of notifying the user of an incompatible hardware version. |[KB4556799](https://support.microsoft.com/help/4556799) |
|20H2.2020.9C, 20H1.2020.4C | - ESP takes a long time during the "Identifying" phase, especially in hybrid and pre-provisioning scenarios.  <br> - Autopilot Update disabled policy wasn't enforced during pre-provisioning scenarios. <br> - Device setup category fails in self-deploying and pre-provisioning scenarios when the ESP policy is set to disabled. <br> - Allows self-deploying scenarios to succeed even if multiple MDM providers are listed in Azure AD. <br> - For self-deploying scenarios, a reboot causes the device to navigate to the pre-provisioning flow, even if the user didn't select the pre-provisioning flow.  |[KB4550945](https://support.microsoft.com/help/4550945), [KB4571744](https://support.microsoft.com/help/4571744) |
|20H1.2020.4C | - Autopilot Reset state not set to success on completion, causing the Intune admin center to not show the correct status of the device after reset.  <br> - Enable extra log collection useful for support cases and investigations. |[KB4550945](https://support.microsoft.com/help/4550945) |
|20H1.2020.3C | - For hybrid scenarios where the user should be an administrator, the user is forced to sign out at the end of ESP so that user is part of the **Administrators** group the time they sign in. <br> - Improves the timeout algorithm on ESP to use processor ticks instead of the system time, which can drift if the device hasn't been powered on after a long duration. |[KB4541335](https://support.microsoft.com/help/4541335) |
|20H1.2020.2C |For pre-provisioning scenarios, ESP is marked as **required to show** to ensure the technician flow completes successfully. |[KB4535996](https://support.microsoft.com/help/4535996) |
|19H2.2019.10C |On self-deploying scenarios, the device is no longer Azure AD joined after OOBE and can't sign in with Azure AD credentials or access company resources. |[KB4522355](https://support.microsoft.com/help/4522355) |
|19H2.2019.9C |A missing AKI extension in EK certificate caused TPM attestation to fail on Windows 10 version 1903. This issue was due to an extra validation added in Windows 10 version 1903 to check that the TPM EK certs had the proper attributes according to the TCG specifications. The KB4517211 update removes this validation. |[KB4517211](https://support.microsoft.com/help/4517211)|
|19H2.2019.8C | - The Windows Autopilot for existing devices feature doesn't properly suppress the **Activities** page during OOBE. Because of this issue, you see this extra page during OOBE.  <br> - Sysprep /generalize doesn't clear TPM attestation state, which causes TPM attestation failure during later OOBE flow. (This issue isn't a common one, but you could run into it while testing. For example, if you run sysprep /generalize and then reboot or reimage the device to go back through an Autopilot pre-provisioning or self-deploying scenario.)  <br> - TPM attestation may fail if the device has a valid AIK cert but no EK cert (this issue is related to the previous item).  <br> - If TPM attestation fails during the Windows Autopilot pre-provisioning process, the landing page appears to stop responding. (Basically, the pre-provisioning landing page, where you select "Provision" to start the pre-provisioning process, isn't reporting errors properly).  <br> - TPM attestation fails on newer Infineon TPMs (firmware version > 7.69). (Before this fix, only a specific list of firmware versions was accepted).  <br> - Device naming templates may truncate the computer name at 14 characters instead of 15.  <br> - Assigned Access policies cause a reboot, which can interfere with the configuration of single-app kiosk devices. |[KB4512941](https://support.microsoft.com/help/4512941)|
|19H2.2019.7C  | - Windows Autopilot pre-provisioning doesn't work for a non-English OS and you see a red screen that says "Success." <br> - Windows Autopilot reports an AUTOPILOTUPDATE error during OOBE after sysprep, reset, or other variations. This issue typically happens if you reset the OS or used a custom sysprepped image.  <br> - BitLocker encryption isn't correctly configured. Ex: BitLocker didn't get an expected notification after policies were applied to begin encryption.  <br> - You're unable to install UWP apps from the Microsoft Store, causing failures during Windows Autopilot. If you're deploying Company Portal as a blocking app during Windows Autopilot ESP, you have probably seen this error.  <br> - A user isn't granted administrator rights in the Windows Autopilot user-driven hybrid Azure AD-join scenario. This issue is another non-English OS issue. |[KB4505903](https://support.microsoft.com/help/4505903)|
|19H1.2019.6C |BitLocker policies not enforced during Autopilot for nondefault encryption options. |[KB4501375](https://support.microsoft.com/help/4501375)|
|19H1.2019.5C |Autopilot pre-provisioning fails for non-English builds. |[KB4497935](https://support.microsoft.com/help/4497935)|

## Related articles

[Windows Autopilot - known issues](known-issues.md)<br>
[Diagnose MDM failures in Windows 10](/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)<br>
[Troubleshooting Windows Autopilot](troubleshooting.md)