# Lab 3: Password Reset Loop in Hybrid Active Directory Environment

## Problem Summary

A user reported being unable to log into their domain-joined Windows 10 laptop after resetting their password using the company’s self-service Azure AD portal. Despite confirming the new password worked on Office 365 apps via mobile, login attempts on the laptop returned “Incorrect password” errors.

The issue occurred in a hybrid Active Directory environment with Azure AD Connect syncing identities between on-prem and Azure.

---

## Simulated Support Ticket

- **Ticket Number:** HD-22319  
- **User:** Emily Taylor  
- **Department:** Sales  
- **Priority:** High  
- **Reported Via:** Phone Call  
- **Operating System:** Windows 10 Pro (Domain-Joined)  
- **Device:** HP EliteBook 840 G5  
- **Office Location:** Melbourne Office  
- **Environment:** Hybrid AD (On-Prem + Azure AD Connect)  

---

## Troubleshooting Steps

1. **Initial User Interview**  
   - User reset password at 8:15 AM via Azure SSPR  
   - Verified new password worked on mobile apps (Outlook, Teams)  
   - Laptop login returned "Incorrect password" repeatedly  

2. **Admin-side Diagnostics**  
   - Forced delta sync from on-prem AD to Azure AD with powershell
     Command: Start-ADSyncSyncCycle -PolicyType Delta
     
   - Result: Success — but issue persisted  

3. **Remote Connection to Device**  
   - Used Quick Assist to connect remotely  
   - Observed login failure firsthand  
   - Rebooted into Safe Mode with Networking  
   - Logged in using local admin account  

4. **Check Domain Join Status**  
   - Navigated to: Settings > Accounts > Access work or school 
   - Device was domain-joined but last successful sync: 5 days ago (stale)  

5. **Flushed Cached Credentials**  
   - Removed entries from **Credential Manager**  
   - Ran PowerShell commands:
     cmdkey /list
     cmdkey /delete /ras
     klist purge

   - Cleared Kerberos tokens and cached logins  

6. **Reauthentication Test**  
   - User re-entered new password  
   - Login successful  

7. **Post-resolution Validation**  
   - Verified Outlook and Teams access  
   - Ran dsregcmd /status to confirm hybrid join  
   - Ensured device is syncing properly and activated  

---

## Resolution Summary

The issue was caused by stale cached credentials on the user’s laptop after an Azure-only password reset. Although Azure accepted the new password, the domain-joined laptop was relying on outdated local cache due to lack of recent domain sync. Clearing cached credentials forced the machine to reauthenticate against updated domain records, allowing successful login.

---

## Skills Demonstrated

- Azure AD + On-Prem Active Directory troubleshooting  
- Credential Manager and Kerberos token management  
- PowerShell command-line diagnostics  
- Remote troubleshooting using Quick Assist  
- Windows account and domain trust validation  

---

