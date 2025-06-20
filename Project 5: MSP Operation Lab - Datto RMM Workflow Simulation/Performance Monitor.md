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
e. And we will choose the following for Warning Alerts:
  1a. CPU Usage > 75% sustained
  1b. Available Memory < 1 GB
  1c. Disk Free Space < 20%
```
![alerts 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20131627.png)
![alert 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20131707.png)  
4. We can create the following Data Collector Sets and define the appropriate parameters. Below is example:
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
```
1. Client_A_Critical_Response
  a. Processor(_Total)\% Processor Time > 90
  b. Memory\Available MBytes < 500
  c. LogicalDisk(C:)\% Free Space < 10

2. Client_B_Critical_Response
  a. Processor(_Total)\% Processor Time > 90
  b. Memory\Available MBytes < 500
  c. LogicalDisk(C:)\% Free Space < 10

3. Client_C_Critical_Response
  a. Processor(_Total)\% Processor Time > 90
  b. Memory\Available MBytes < 500
  c LogicalDisk(C:)\% Free Space < 10

4. Client_A_Warning_Monitoring
  a. Processor(_Total)\% Processor Time > 75
  b. Memory\Available MBytes < 1000
  c. LogicalDisk(C:)\% Free Space < 20
  d. LogicalDisk(C:)\Avg. Disk Queue Length > 2

5. Client_B_Warning_Monitoring
  a. Processor(_Total)\% Processor Time > 75
  b. Memory\Available MBytes < 1000
  c. LogicalDisk(C:)\% Free Space < 20
  d. LogicalDisk(C:)\Avg. Disk Queue Length > 2

6. Client_C_Warning_Monitoring
  a. Processor(_Total)\% Processor Time > 75
  b. Memory\Available MBytes < 1000
  c. LogicalDisk(C:)\% Free Space < 20
  d. LogicalDisk(C:)\Avg. Disk Queue Length > 2

7. Client_A_Performance_Baselines
  a. Network Interface(*)\Bytes Total/sec → No alert (monitoring only)
  b. System\Processor Queue Length → No alert (monitoring only)
  c. Memory\Pages/sec → No alert (monitoring only)
  d. LogicalDisk(*)\% Disk Time → No alert (monitoring only)


8. Client_B_Performance_Baselines
  a. Network Interface(*)\Bytes Total/sec → No alert (monitoring only)
  b. System\Processor Queue Length → No alert (monitoring only)
  c. Memory\Pages/sec → No alert (monitoring only)
  d. LogicalDisk(*)\% Disk Time → No alert (monitoring only)


9. Client_C_Performance_Baselines
  a. Network Interface(*)\Bytes Total/sec → No alert (monitoring only)
  b. System\Processor Queue Length → No alert (monitoring only)
  c. Memory\Pages/sec → No alert (monitoring only)
  d. LogicalDisk(*)\% Disk Time → No alert (monitoring only)
```
5. This step will guide you through how to apply and set the desired parameters:
```
1. Right click on Monitoring Tools →
2. Performance Monitor and choose New → Data Collector Set.
3. Assign  it an appropriate name
```
![new data collector set](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20122100.png)
![data collector set name](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20122129.png)
6. 
