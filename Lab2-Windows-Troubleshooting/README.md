Lab 2 – Windows Troubleshooting Tools
=====================================

Lab Summary:
------------
This lab simulates a real-world Help Desk troubleshooting scenario. A user reports slow performance and startup delays. I act as the technician, using Windows' built-in tools to diagnose and document the issue.

Tasks:
------
1. System File Check (sfc)
2. Disk Health Check (chkdsk)
3. Review System Event Logs
4. Analyze and reduce startup programs
5. View crash history using Reliability Monitor
6. Document all findings and outcomes

Tools Used:
-----------
- PowerShell
- Event Viewer
- MSConfig
- Task Manager
- Reliability Monitor

--------------------------------------------------
TASK 1: Run System File Checker (SFC)
--------------------------------------------------
Command:
    sfc /scannow

Result:
- System scan completed successfully with no integrity violations.

[Screenshot:](sfc_scannow_result.png)

--------------------------------------------------
TASK 2: Run Check Disk (CHKDSK)
--------------------------------------------------
Command:
    chkdsk C:

Result:
- File system reported clean. No bad sectors.

[Screenshot:](chkdsk_result.png)

--------------------------------------------------
TASK 3: Check Event Viewer Logs
--------------------------------------------------
Steps:
- Opened Event Viewer > Windows Logs > System
- Found errors:
  - Event ID 20: Windows Failed to Install Notepad

[Screenshot:](event_viewer_errors.png)

--------------------------------------------------
TASK 4: Review Startup Applications
--------------------------------------------------
Tools:
- Task Manager (Startup tab)
- MSConfig (Services tab)

Result:
- Disabled OneNote auto-start

[Screenshot:](startup_apps_taskmgr.png)

--------------------------------------------------
TASK 5: Use Reliability Monitor
--------------------------------------------------
Steps:
- Viewed stability timeline
- Found Hardware crash.

[Screenshot:](reliability_monitor.png)

