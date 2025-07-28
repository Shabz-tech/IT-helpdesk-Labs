# Windows Server 2019: Active Directory, DNS, and User/Group Management

## Overview

This lab documents my hands-on experience setting up and configuring **Active Directory Domain Services (AD DS)** and **DNS** on **Windows Server 2019**, as well as creating domain users and groups. These are foundational skills for system administration and enterprise IT environments.

This project was completed in a virtual environment as part of structured lab exercises simulating real-world IT infrastructure.

---

## What I Configured

### Active Directory & DNS Installation

- Installed **Active Directory Domain Services (AD DS)** and **DNS Server** roles using Server Manager
- Promoted the server to a **Domain Controller**
- Created a **new forest** and domain 
- Set both **Forest Functional Level** and **Domain Functional Level** to Windows Server 2016
- Used a secure admin password for DSRM 
- Accepted default file locations and completed installation with reboot

### DNS Configuration (via AD DS install)

- DNS role was installed simultaneously with AD DS (required for domain controller functionality)
- Allowed default delegation settings (skipped manual DNS zone setup)
- Verified successful installation via Server Manager and DNS MMC

---

## Domain User and Group Management

### Created Domain Users

- Used **Active Directory Users and Computers (ADUC)** MMC
- Created multiple users under the Users container 
- Configured account settings:
  - User cannot change password
  - Password never expires
- Assigned secure password:
- Verified user logon format 

### Created Security Groups

- Created domain groups: Supervisor and Staff
- Chose **Global scope** and **Security type**
- Groups created under the Supervisor container in ADUC

### Assigned Users to Groups

- Assigned users to the appropriate groups via the group’s **Properties > Members** tab
- Used **Check Names** to ensure proper lookup and resolution
- Applied and saved changes

---

## Tools Used

- Windows Server 2019 (Virtual Machine)
- Server Manager
- Active Directory Users and Computers (dsa.msc)
- DNS Manager
- PowerShell (light usage)
- Hyper-V / VMware / VirtualBox (local environment)
