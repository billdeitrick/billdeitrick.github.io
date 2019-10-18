---
description: Additional resources for Intune
type: talk
title: Intune Notes and Resources
index: 3
---

## General Intune Links

* [What is Intune?](https://docs.microsoft.com/en-us/intune/fundamentals/what-is-intune)
* [Getting Ready for Windows 10 - An MDM Primer](https://blogs.technet.microsoft.com/tip_of_the_day/2015/11/27/tip-of-the-day-getting-ready-for-windows-10-an-mdm-primer/)
* [Diagnose MDM Failures in Windows 10](https://docs.microsoft.com/en-us/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)
* [Printix (deploy printers from the cloud)](https://www.printix.net/)
* [MMAT-MDM Migration Analysis Tool (compare GPO set for a target user/computer with MDM policies)](https://github.com/WindowsDeviceManagement/MMAT)


## Configuration Profiles in Intune

### General

* [Creating device [configuration] profiles](https://docs.microsoft.com/en-us/intune/configuration/device-profile-create)
* [Diagnose MDM Failures in Windows 10](https://docs.microsoft.com/en-us/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10)
* [Getting Ready for Windows 10 - An MDM Primer](https://blogs.technet.microsoft.com/tip_of_the_day/2015/11/27/tip-of-the-day-getting-ready-for-windows-10-an-mdm-primer/)

### Custom Configuration Profiles

#### Custom OMA-URI

* [Custom Settings for Windows 10 Devices in Intune](https://docs.microsoft.com/en-us/intune/configuration/custom-settings-windows-10)
* [Configuration service provider reference (reference for configuring custom OMA-URI)](https://docs.microsoft.com/en-us/windows/client-management/mdm/configuration-service-provider-reference)
* [Set Default App Associations Via Windows 10 MDM](https://www.petervanderwoude.nl/post/set-default-app-associations-via-windows-10-mdm/)

#### Custom ADMX

* [Deploying ADMX-Backed policies using Microsoft Intune](https://blogs.technet.microsoft.com/senthilkumar/2018/05/21/intune-deploying-admx-backed-policies-using-microsoft-intune/)
* [Deep dive ingesting third-party ADMX-files](https://www.petervanderwoude.nl/post/deep-dive-ingesting-third-party-admx-files/)
* [How does a custom set of ADMX-based policies work with Intune](https://osddeployment.dk/2019/01/02/how-does-a-custom-set-of-admx-based-policies-work-with-intune/)

## Patching Devices with Intune

* [Windows update settings for Intune](https://docs.microsoft.com/en-us/intune/protect/windows-update-settings)
* [Manage Software Updates in Intune](https://docs.microsoft.com/en-us/intune/protect/windows-update-for-business-configure)
* [Intune Patching Part 1: Human Translation](https://damgoodadmin.com/2019/05/29/intune-patching-part-1-human-translation/)
* [Intune Patching Part II: The Good, The Bad, The Ugly](https://damgoodadmin.com/2019/06/05/intune-patching-part-ii-the-good-the-bad-the-ugly/)

## PowerShell Scripts with Intune

* [Example: Microsoft Teams Download/Install](https://gist.github.com/billdeitrick/93647629becdb4372f4de389b1a8fd6c)
* [Deep dive Microsoft Intune Management Extension – PowerShell Scripts](https://oliverkieselbach.com/2017/11/29/deep-dive-microsoft-intune-management-extension-powershell-scripts/)
* [Part 2, Deep dive Microsoft Intune Management Extension – PowerShell Scripts](https://oliverkieselbach.com/2018/02/12/part-2-deep-dive-microsoft-intune-management-extension-powershell-scripts/)

## Deploying Apps with Intune

* [Part 3, Deep dive Microsoft Intune Management Extension – Win32 Apps](https://oliverkieselbach.com/2018/10/02/part-3-deep-dive-microsoft-intune-management-extension-win32-apps/)
* [Intune Standalone - Win32 app management](https://docs.microsoft.com/en-us/intune/apps/apps-win32-app-management)
* [Deploy customized Win32 apps via Microsoft Intune](https://www.petervanderwoude.nl/post/deploy-customized-win32-apps-via-microsoft-intune/)
* [Troubleshoot App Installation Issues](https://docs.microsoft.com/en-us/intune/apps/troubleshoot-app-install)
* [Intune Win32 App Troubleshooting Client Side Process Flow](https://www.anoopcnair.com/intune-win32-app-troubleshooting/)
    * For Win32 app troubleshooting, it is also helpful to look at registry entries in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\IntuneManagementExtension\Win32Apps`
    * These are user GUIDs (all zeroes is machine scoped), each key underneath is app GUID representing an installation attempt for a particular app
        * App GUIDs can be obtained from the URL for the app in the Intune UI
    * You can force a retry by deleting the key for the app install (under the appropriate user GUID) and then restarting the Microsoft Intune Management Extension service

### Simple Install Command Example: Install BitDefender

Simple batch entry point for installing a Win32 app with command line switches.

```batch
"%~dp0epskit_x64.exe" /bdparams /silent
```

`%~dp0` above specifies the current directory.

Your installer must support silent installation to be deployed with Intune.

### More Interesting Install Script Example: Install Exam View

This is a more involved installation script example that involves working around issues caused by a poorly-behaved installer (symlinks content directories to user's OneDrive, removes secondary installer not needed).

[>> Example Here <<](https://gist.github.com/billdeitrick/d3fa0b7657927768a27c01aaba435e0a)

Troubleshooting
