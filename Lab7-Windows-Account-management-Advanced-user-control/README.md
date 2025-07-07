Lab 4 – Windows Account Management (Advanced User Control)
===========================================================

Lab Summary:
------------
This lab simulates advanced user account management tasks typical for Help Desk and Junior System Administrators. You perform lifecycle actions such as creating users, forcing password resets, modifying group membership, disabling/deleting accounts, and setting NTFS folder permissions.

Tasks Performed:
----------------
1. Created local user with password change options
2. Forced password reset at next login
3. Disabled and re-enabled account access
4. Deleted a local user
5. Added user to Administrators group
6. Created folder and granted NTFS permissions

Tools Used:
-----------
- PowerShell
- Local Users and Groups

--------------------------------------------------
TASK 1: Create User + Password Options
--------------------------------------------------
Command:
    net user testuser03 testuser03 /add
    net user testuser03 /passwordchg:yes

[Screenshot](user-created-pass-chg-allwd.png)

--------------------------------------------------
TASK 2: Force Password Change at Next Login
--------------------------------------------------
Command:
    net user testuser03 /logonpasswordchg:yes

[Screenshot](forced-pass-change.png)

--------------------------------------------------
TASK 3: Disable and Re-enable Account
--------------------------------------------------
Commands:
    net user testuser03 /active:no
    net user testuser03 /active:yes

[Screenshot](user-disabled-enabled.png)

--------------------------------------------------
TASK 4: Delete User
--------------------------------------------------
Command:
    net user testuser03 /delete

[Screenshot](user-delete.png)

--------------------------------------------------
TASK 5: Add User to Administrators Group
--------------------------------------------------
Command:
    net localgroup administrators testuser02 /add

--------------------------------------------------
TASK 6: Create Folder + Assign NTFS Permissions
--------------------------------------------------
Commands:
    New-Item -Path "C:\Users\testuser02-docs" -ItemType Directory
    icacls "C:\Users\testuser02-docs" /grant testuser02:F

[Screenshot](user-folder-permissions.png)

--------------------------------------------------
NEXT STEP
--------------------------------------------------
Move on to Lab 5: Windows Security Tools (Firewall, Defender, and UAC)

