# Lab 4: Network Printer Offline – Cannot Print

## Problem Summary

A user reported that the shared network printer appeared “offline” on their workstation and was unable to print from any application. The issue was isolated to the user's machine, as other employees were successfully printing to the same device. A network-level connectivity check confirmed the printer was reachable, indicating the problem was local to the workstation’s print configuration.

---

## Simulated Support Ticket

- **Ticket Number:** HD-22341  
- **User:** Liam Chen  
- **Department:** Finance  
- **Priority:** Medium  
- **Reported Via:** Email  
- **Operating System:** Windows 10 Pro  
- **Device:** Dell OptiPlex 7090 Desktop  
- **Printer Affected:** HP LaserJet Pro M404dn (Network Shared via Print Server)  
- **Printer Hostname/IP:** `FIN-PRN-01.australtech.local` / `10.0.5.25`  
- **Print Server:** `PRINTSRV01.australtech.local`

---

## Troubleshooting Steps

1. **Initial User Interview**  
   - User last printed successfully the previous day  
   - This morning, all print jobs stayed in the queue  
   - Printer appeared as “Offline” in Devices and Printers  
   - No success after restarting printer  

2. **Test from Another Device**  
   - Checked with a nearby user — printing worked for them  
   - Confirmed issue is isolated to Liam’s workstation  

3. **Network Connectivity Test**  
   - Remoted into Liam’s machine via Quick Assist  
   - Ran `ping 10.0.5.25`  
   - All replies successful — printer reachable over network  

4. **Remove and Re-Add Printer**  
   - Navigated to Control Panel > Devices and Printers  
   - Removed existing printer: `HP LaserJet Pro M404dn on PRINTSRV01`  
   - Re-added shared printer manually:
     ```
     \\PRINTSRV01\HP_LaserJet_Pro_M404dn
     ```
   - Drivers installed successfully  

5. **Test Print**  
   - Printed test page from Printer Properties  
   - Confirmed Excel and Word documents now print as expected  

---

## Resolution Summary

The printer appeared “offline” on the user's Windows 10 device due to a local spooler or driver sync issue with the shared print queue. Other users were unaffected, and the printer was reachable over the network. Removing and re-adding the shared printer connection from the print server resolved the issue.

---

## Skills Demonstrated

- User communication and scope isolation  
- Network connectivity testing (ping)  
- Shared printer configuration via UNC path  
- Windows 10 print management  
- Device-level troubleshooting and profile repair  
- Remote desktop support via Quick Assist
