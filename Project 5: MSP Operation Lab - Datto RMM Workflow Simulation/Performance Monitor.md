### Performance Monitor
1. Press Windows+R and search perfmon.exe
2. Under Data Collector Sets you can view the User Defined (user created) sets or create Alert-based Collector Sets.
```
a. Data Collector Sets → User Defined → Right-click → New → Data Collector Set
b. Name it something appropriate, in this instance we will choose Client_A_Alerts
c. Tick "Performance Counter Alert"
d. We can choose what alerts to define here, in this instance we will choose the following for Critical Alerts:
  1a. CPU Usage > 90% sustained
  1b. Available Memory < 500 MB
  1c. Disk Free Space < 10%
  1d. Unexpected system reboots
e. We can choose what alerts to define here, in this instance we will choose the following for Warning Alerts:
  1a. CPU Usage > 75% sustained
  1b. Available Memory < 1 GB
  1c. Disk Free Space < 20%
```
![alerts 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20131627.png)
![alert 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20131707.png)
4. We can create the following Data Collector Sets and define the appropriate parameters
```
Client_A_Critical_Response: Immediate action needed
Client_A_Warning_Monitoring: Scheduled maintenance needed
Client_A_Performance_Baselines: Trend analysis and reporting
Client_B_Critical_Response: Immediate action needed
Client_B_Warning_Monitoring: Scheduled maintenance needed
Client_B_Performance_Baselines: Trend analysis and reporting
Client_C_Critical_Response: Immediate action needed
Client_C_Warning_Monitoring: Scheduled maintenance needed
Client_C_Performance_Baselines: Trend analysis and reporting
```


4. For now, right click on Monitoring Tools → Performance Monitor and choose New → Data Collector Set. And give it an appropriate name.
![new data collector set](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20122100.png)
![data collector set name](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20122129.png)
5. 
