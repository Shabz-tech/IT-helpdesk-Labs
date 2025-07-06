Lab 1 – Windows OS: Basic User & System Support
==============================================

Lab Summary:
------------
This lab simulates foundational Level 1 IT Help Desk tasks performed on Windows 11, including user account creation, system checks, disk cleanup, environment variable configuration, and Windows updates. Tasks are completed using both GUI and PowerShell to reflect real-world help desk flexibility. Screenshots, logs, and commands are documented to demonstrate technical capability for portfolio and resume use.

Learning Objectives:
--------------------
- Add and manage local users (GUI and PowerShell)
- Check system information
- Perform disk cleanup
- Configure user environment variables
- Check for and manage Windows updates
- Document support actions like a real IT ticket

System Requirements:
--------------------
- OS: Windows 11 (or Windows 10)
- Admin rights: Required
- Tools used: PowerShell, Disk Cleanup, Settings, Control Panel
--------------------------------------------------
TASK 1: Create a Local User via GUI
--------------------------------------------------
Steps:
1. Open Settings > Accounts > Other Users
2. Click "Add account"
3. Select "I don’t have this person’s sign-in information"
4. Choose "Add a user without a Microsoft account"
5. Enter:
   - Username: testuser01
   - Password: Test@1234
6. After account creation, click the user > Change account type > Administrator

Command Log:
- Created user 'testuser01' via GUI and granted admin rights.

[Screenshot:](testuser01admin.png)

--------------------------------------------------
TASK 2: Create a Local User via PowerShell
--------------------------------------------------
Steps:
1. Open PowerShell as Administrator
2. Run the following commands:

    net user testuser02 Test@1234 /add
    net localgroup administrators testuser02 /add

Command Log:
    net user testuser02 Test@1234 /add
    net localgroup administrators testuser02 /add

[Screenshots:](testuser02admin.png)

--------------------------------------------------
TASK 3: Check System Information
--------------------------------------------------
GUI Steps:
- Go to Settings > System > About
- Note Device name, Edition, Processor, RAM, Windows version

PowerShell Command:
    Get-ComputerInfo | Select-Object CsName, WindowsProductName, WindowsVersion, OsArchitecture, OsBuildNumber

Command Log:
    Get-ComputerInfo | Select-Object CsName, WindowsProductName, WindowsVersion, OsArchitecture, OsBuildNumber

--------------------------------------------------
TASK 4: Perform Disk Cleanup
--------------------------------------------------
Steps:
1. Search "Disk Cleanup" from the Start Menu
2. Select drive C:\
3. Tick: Temporary files, Recycle Bin, Windows Update Cleanup
4. Click OK > Delete Files

Command Log:
- Ran Disk Cleanup on drive C:\ – removed temporary files and system cache.

[Screenshot:](disc-cleanup.png)

--------------------------------------------------
TASK 5: Add Environment Variable
--------------------------------------------------
Steps:
1. Right-click "This PC" > Properties
2. Click "Advanced system settings"
3. Click "Environment Variables"
4. Under "User variables" click "New"
   - Name: testlabvariable
   - Value: helpdesklab
5. Click OK

Command Log:
- Created user environment variable MY_TEST_VAR = HelpDeskLab

[Screenshot:](environment variables.png)

--------------------------------------------------
TASK 6: Check for Windows Updates
--------------------------------------------------
GUI Steps:
- Open Settings > Windows Update > Click "Check for updates"

PowerShell (optional):
    Get-WindowsUpdateLog

Command Log:
    Get-WindowsUpdateLog

[Screenshot:](powershellcmdwindowupdate.png)
