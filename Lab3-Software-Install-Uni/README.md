Lab 3 – Software Installation & Removal (GUI + PowerShell)
===========================================================

Lab Summary:
------------
This lab simulates the installation and uninstallation of software using both GUI and PowerShell (Winget). These tasks represent common Help Desk responsibilities when setting up new software or troubleshooting existing applications.

Tasks Performed:
----------------
1. Install VLC Media Player via Microsoft Store (GUI)
2. Uninstall VLC Media Player via Windows Settings
3. Install VLC Media Player using Winget (PowerShell)

Tools Used:
-----------
- Microsoft Store
- Windows Settings (Apps)
- PowerShell with Winget

--------------------------------------------------
TASK 1: Install Software via GUI (Microsoft Store)
--------------------------------------------------
App: VLC Media Player

Steps:
- Opened Microsoft Store
- Searched and installed VLC Media Player

[Screenshot](vlc_installed_gui.png)

--------------------------------------------------
TASK 2: Uninstall Software via GUI (Settings)
--------------------------------------------------
Steps:
- Opened Settings > Apps > Installed apps
- Found and uninstalled Notepad++

[Screenshot:](VLC_uninstalled_gui.png)

--------------------------------------------------
TASK 3: Install Software via PowerShell
--------------------------------------------------
Command:
    winget search vlc --source=msstore
    
    Name    Id             Version
------------------------------
VLC     XPDM1ZW6815MQM Unknown
VLC UWP 9NBLGGH4VVNH   Unknown

winget install XPDM1ZW6815MQM --source=msstore

Result:
- Successfully installed via command line

[Screenshot:](VLC_installed_winget.png)
