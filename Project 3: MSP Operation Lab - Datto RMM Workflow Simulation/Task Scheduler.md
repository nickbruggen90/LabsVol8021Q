### Task Scheduler (Automation)
1. Press Windows+R and search taskschd.msc (this is a native Windows automation tool comparable to Datto RMM's "Automation Policies" module).

2. Under Task Scheduler Library you can view existing scheduled tasks or create new automated maintenance routines. This step will demonstrate how to create automated tasks for different client tiers:

```
a. Task Scheduler → Action → Create Task
b. Name it something appropriate based on client and function (refer to Step 3 and my Naming Convention worksheet)
c. Choose trigger frequency (Daily, Weekly, Monthly)
d. Define the action (Start a program, script, or command)
e. Set conditions and settings for reliability
```
![create task 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-20%20040559.png)

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

## **IMPORTANT: Setting Up Disk Cleanup Profiles First**
Before creating automated tasks, you must define cleanup profiles using sageset:

```
a. Open Command Prompt as Administrator
b. Run: cleanmgr /sageset:1
c. Check the items you want automated cleanup to include:
   1a. Temporary files
   2a. Temporary Internet Files  
   3a. Recycle Bin
   4a. System cache and log files
d. Click OK to save Profile 1
e. Repeat for different profiles: /sageset:2 (aggressive), /sageset:3 (conservative)
f. Repeating Step b. will show the applied parameters as well
```
![creating sageset 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-20%20035754.png)

4. Example Task Creation - Client_B_Daily_DiskCleanup:
```
a. Task Scheduler → Create Basic Task
b. Name: "Client_B_Daily_DiskCleanup"
c. Description: "Automated disk cleanup for professional tier client"
d. Tick "Whether user is logged on or not"
e. Trigger: Daily at 2:00 AM
f. Action: Start a program
   - Program: cleanmgr.exe
   - Arguments: /d C: /sagerun:1
g. Conditions: Only run if computer is idle for 10 minutes and uncheck "Stop if the computer ceases to be idle"
h. Settings: Allow task to be run on demand, restart if fails
```
![create task 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-20%20040638.png)
![create task 3](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-20%20040736.png)
![create task 4](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-20%20040934.png)
![create task 5](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-20%20041116.png)

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
![confirmation](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-20%20041130.png)


7. You can use the following PowerShell commands to view and manage scheduled tasks programmatically:
```
# View all scheduled tasks
Get-ScheduledTask | Select-Object TaskName, State, Author

# View specific task details
Get-ScheduledTask -TaskName "Client_B_Daily_DiskCleanup" | Format-List

```
![powershell output 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-20%20041502.png)

```
