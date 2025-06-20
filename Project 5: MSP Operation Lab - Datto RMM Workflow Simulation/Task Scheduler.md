### Task Scheduler (Automation)
1. Press Windows+R and search taskschd.msc (this is a native Windows automation tool comparable to Datto RMM's "Automation Policies" module).

2. Under Task Scheduler Library you can view existing scheduled tasks or create new automated maintenance routines. This step will demonstrate how to create automated tasks for different client tiers:

```
a. Task Scheduler → Task Scheduler Library → Right-click → Create Basic Task
b. Name it something appropriate based on client and function (refer to Step 3 and my Naming Convention worksheet)
c. Choose trigger frequency (Daily, Weekly, Monthly)
d. Define the action (Start a program, script, or command)
e. Set conditions and settings for reliability
```

3. We can create the following automated tasks based on MSP client tiers and industry standards:

**Client A (Basic Tier) - Essential Maintenance:**
```
Client_A_Daily_DiskCleanup: Automated disk space management
Client_A_Weekly_TempCleanup: Clear temporary files and cache
Client_A_Monthly_SystemScan: Basic system file integrity check
```

**Client B (Professional Tier) - Enhanced Automation:**
```
Client_B_Daily_DiskCleanup: Automated disk space management
Client_B_Daily_ServiceMonitor: Restart critical services if stopped
Client_B_Weekly_SystemOptimization: Defrag and system file check
Client_B_Monthly_SecurityScan: Comprehensive system health check
```

**Client C (Premium Tier) - Advanced Security & Compliance:**
```
Client_C_Daily_SecurityCleanup: Security-focused maintenance
Client_C_Daily_ServiceMonitor: Monitor and restart security services
Client_C_Weekly_ComplianceCheck: System file and registry validation
Client_C_Monthly_FullSystemAudit: Complete security and performance audit
```

IMPORTANT: Setting Up Disk Cleanup Profiles First
Before creating automated tasks, you must define cleanup profiles using sageset:

a. Open Command Prompt as Administrator
b. Run: cleanmgr /sageset:1
c. Check the items you want automated cleanup to include:
   ✅ Temporary files
   ✅ Temporary Internet Files  
   ✅ Recycle Bin
   ✅ Downloads folder (optional - be careful with client data)
   ✅ System cache and log files
d. Click OK to save Profile 1
e. Repeat for different profiles: /sageset:2 (aggressive), /sageset:3 (conservative)

4. Example Task Creation - Client_B_Daily_DiskCleanup:
```
a. Task Scheduler → Create Basic Task
b. Name: "Client_B_Daily_DiskCleanup"
c. Description: "Automated disk cleanup for professional tier client"
d. Trigger: Daily at 2:00 AM
e. Action: Start a program
   - Program: cleanmgr.exe
   - Arguments: /d C: /sagerun:1
f. Conditions: Only run if computer is idle for 10 minutes
g. Settings: Allow task to be run on demand, restart if fails
```

5. Example Task Creation - Client_B_Weekly_SystemOptimization:
```
a. Task Scheduler → Create Basic Task
b. Name: "Client_B_Weekly_SystemScan"
c. Description: "Weekly system file integrity check"
d. Trigger: Weekly on Sunday at 3:00 AM
e. Action: Start a program
   - Program: cmd.exe
   - Arguments: /c sfc /scannow
f. Conditions: Only run if on AC power
g. Settings: Run with highest privileges
```

6. Example Task Creation - Client_C_Daily_ServiceMonitor:
```
a. Task Scheduler → Create Basic Task
b. Name: "Client_C_Service_Monitor"
c. Description: "Monitor and restart critical services"
d. Trigger: Daily every 4 hours
e. Action: Start a program
   - Program: powershell.exe
   - Arguments: -Command "Get-Service -Name 'Spooler','BITS','Themes' | Where-Object {$_.Status -eq 'Stopped'} | Start-Service"
f. Conditions: Run whether user is logged on or not
g. Settings: Run with highest privileges, restart on failure
```

7. You can use the following PowerShell commands to view and manage scheduled tasks programmatically:
```
# View all scheduled tasks
Get-ScheduledTask | Select-Object TaskName, State, Author

# View specific task details
Get-ScheduledTask -TaskName "Client_B_Daily_DiskCleanup" | Format-List

# Create a new scheduled task via PowerShell
$Action = New-ScheduledTaskAction -Execute 'cleanmgr.exe' -Argument '/d C: /sagerun:1'
$Trigger = New-ScheduledTaskTrigger -Daily -At 2:00AM
Register-ScheduledTask -Action $Action -Trigger $Trigger -TaskName "PowerShell_DiskCleanup" -Description "Automated cleanup via PowerShell"
```

8. Business Value - MSP Automation Benefits:
```
Critical Tier Tasks: Immediate response to system issues (service restarts, disk space alerts)
Warning Tier Tasks: Scheduled maintenance during off-hours (weekly scans, optimization)
Baseline Tier Tasks: Proactive system health (monthly audits, compliance checks)

This automation prevents "my computer is slow" calls by maintaining systems proactively.
Different client tiers receive appropriate levels of automated maintenance based on their SLA.
Scheduled tasks run during off-hours to minimize business disruption.
Automated remediation reduces manual intervention and improves response times.
```
