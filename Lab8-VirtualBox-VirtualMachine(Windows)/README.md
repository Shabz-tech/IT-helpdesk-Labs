## Lab8 - Setting Up a Windows 10 Virtual Machine (demonstrates installation of Windows OS in a VM)

## Overview:
This lab covers the installation of Oracle VirtualBox, downloading necessary resources, and setting up a Windows 10 virtual machine. All tasks must be completed either on your personal laptop or a lab computer with an external hard drive and USB stick.

## Tools Required:
- Oracle VirtualBox
- Windows 10 ISO (from Azure for Education)

## Step-by-Step Instructions:

1. Download Windows 10 ISO fromm azure for education.

2. Creating a Windows 10 Virtual Machine in VirtualBox:
- Open VirtualBox and click “New”.
- Name your VM as: ShabtechWindowsVM
- Choose the install unattended option
- Select ISO Image
- Creat an account with admin rights.
- Set Memory Size: 4096 MB
- Set Processers: 2 core
- Choose “VDI” > “Dynamically Allocated” > set size to 80.00 GB
- Select “Create a virtual hard disk now” and click “Create”.
- VM will now appear in the left pane.

3. Configuring the VM Settings:
- Click “Settings” > “Storage”.
- Delete the Windows 10 ISO file from SATA 1 and 2 so that it boots from SATA 0.
- Go to “Network” > change Adapter 1 to “Host-only Adapter”.
- Click OK and then click “Start” to fire up the VM.

4. Installing Windows 10 in the VM:
- On startup, you’ll see "Loading files" and the Windows installer.
- Choose “Custom” (not Upgrade).
- Select English (US), and install now.
- Accept license terms.
- Use the default 80GB partition.
- After installation, system will restart automatically.

8. Configuring Desktop and Folder Settings:
- Right-click Desktop > Personalize > Themes > Desktop Icon Settings > check all five icons.
- Display Settings > Set resolution to 1440 x 900.
- Create a new folder > Open it:
  - View > Navigation Pane > Uncheck Navigation Pane.
  - View > List > Sort by Type.
  - View > Options > Show hidden files.
  - Uncheck “Hide extensions” > Apply to folders.

9. Shortcuts and Power Settings:
- In Cortana, type “pow” > right-click PowerShell > Pin to taskbar.
- Type “con” > right-click Control Panel > Pin to taskbar.
- Control Panel > Small icons > Power Options > Change plan settings > Set display off to 2 hours.
- Right-click “This PC” > Rename computer to: W10-SURNAME (e.g., W10-SMITH) > click Change.

10. TCP/IP Networking Configuration:
- Verify “Host-only” adapter is selected in VirtualBox.
- In Windows 10 VM:
  - Cortana > type “network” > Open Network & Sharing Center.
  - Change advanced settings > Turn on network discovery.
  - Click “Change adapter settings”.
  - Right-click “Ethernet0” > Properties.
  - Uncheck “TCP/IPv6” > Check “TCP/IPv4” > click Properties.
  - Set:
    - IP Address: 192.168.1.100
    - Subnet Mask: 255.255.255.0
    - DNS Server: 192.168.1.1
- Confirm settings using PowerShell:
  - Run ipconfig /all
  - Run ping 127.0.0.1 and ping 192.168.1.1
- Disable Windows Firewall for Domain Networks before testing ping.

## - Screenshots: 
[1.png]
[2.png]
[3.png]
[4.png]
[5.png]
[6.png]
[7.png]
