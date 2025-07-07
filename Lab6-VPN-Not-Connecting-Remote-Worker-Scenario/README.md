# Lab 5: VPN Not Connecting – Error 720 on Windows 10

## Problem Summary

A remote user was unable to connect to the company VPN using the built-in Windows 10 IKEv2 client. The connection attempt failed immediately with **Error 720: A connection to the remote computer could not be established**. The user required VPN access to internal legal systems while working from home.

---

## Simulated Support Ticket

- **Ticket Number:** HD-22366  
- **User:** Priya Kapoor  
- **Department:** Legal  
- **Priority:** High  
- **Reported Via:** IT Helpdesk Portal  
- **Device:** Surface Pro 7, Windows 10 Pro  
- **Connection Type:** Home Wi-Fi  
- **VPN Client:** Windows built-in VPN (IKEv2)  
- **VPN Endpoint:** vpn.australtech.local  
- **Issue:** VPN fails to connect with Error 720  

---

## Troubleshooting Steps

1. **User Interview**  
   - Last successful VPN connection two days ago  
   - No recent software or driver installs  
   - Error 720 occurs immediately on connection attempt  

2. **Remote Session Initiation**  
   - Connected to user’s device via Quick Assist  
   - Attempted to disconnect and reconnect VPN client  
   - Error 720 persisted  

3. **Device Manager Inspection**  
   - Checked Network Adapters → WAN Miniport (IKEv2) showed yellow warning icon  
   - Device status: This device cannot start. (Code 10)  
   - Indicates corrupted or malfunctioning WAN Miniport driver  

4. **Network Stack Reset via PowerShell**  
   - Ran commands as Administrator:
     netsh int ip reset
     netsh winsock reset
     netsh advfirewall reset
     Restart-Computer

   - Allowed machine to reboot  

5. **Post-Reboot Validation**  
   - Verified WAN Miniport (IKEv2) in Device Manager had no errors  
   - User reconnected VPN successfully  
   - Confirmed access to internal resources  

---

## ✅ Resolution Summary

The VPN Error 720 was caused by corrupted WAN Miniport drivers or networking stack components on the client machine. Resetting the TCP/IP stack, Winsock catalog, and firewall policies restored the drivers and network configuration. After a reboot, the VPN connection succeeded without error.

---

## 🛠️ Skills Demonstrated

- Effective user communication and remote troubleshooting  
- VPN client and Windows networking diagnostics  
- Device Manager and driver error analysis  
- PowerShell network reset commands  
- Use of Windows built-in VPN client  
- Problem isolation and remediation
