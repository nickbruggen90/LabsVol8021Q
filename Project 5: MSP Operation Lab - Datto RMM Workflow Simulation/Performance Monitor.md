### Performance Monitor
1. Press Windows+R and search perfmon.exe (this is a native Windows performance monitoring tool comparable to Datto RMMs "Monitoring" module).  
2. Under Data Collector Sets you can view (read the properties) of the User Defined (user created) sets or create Alert-based Collector Sets. This step will demonstrate how to create an alert-based collector set:
```
a. Data Collector Sets → User Defined → Right-click → New → Data Collector Set
b. Name it something appropriate, in this instance we will choose Client_A_Critical_Response
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
![alerts 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-20%20024320.png)
![alert 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20131707.png)  
4. We can create the following Data Collector Sets and define the appropriate parameters for each. Below is an example based on industry standards (refer to my Naming Convention worksheet for naming convention examples):
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
  c. LogicalDisk(C:)\% Free Space < 10

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
5. Now we can refer back to Step 4 with the outlined parameters and set the corresponding values. You are given the choice of Above or Below and the alert threshold in numeric value (notice in the third picture below, when choosing "% Free Disk" you must define the partition to monitor, in this case it is C: drive):  
![parameters/values 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20133610.png)
![parameters/values 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20133718.png)
![parameters/values 3](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20133756.png)
![parameters/values 4](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20134029.png)
6. This step will guide you through how to apply monitor-based Collector Sets rather than alert-based. We will create three collector sets based around different needs: Critical Systems, Network Services, Security Focused.
```
1. Right click on Monitoring Tools → Performance Monitor
2. Choose New → Data Collector Set
3. Assign it an appropriate name
```
Here are example parameters based on industry standards:  
Set 1: "Client_A_Critical_Systems"
```
a. CPU Monitoring:
Processor(_Total)\% Processor Time
Processor(_Total)\% User Time
System\Processor Queue Length

b. Memory Monitoring:
Memory\Available MBytes
Memory\% Committed Bytes In Use
Memory\Pages/sec

c. Disk Performance:
LogicalDisk(C:)\% Free Space
LogicalDisk(C:)\Avg. Disk Queue Length
LogicalDisk(C:)\% Disk Time
```
Set 2: "Client_B_Network_Services"
```
a. Network Monitoring:
Network Interface(*)\Bytes Total/sec
Network Interface(*)\Packets/sec
Network Interface(*)\Current Bandwidth

b. System Health:
System\System Up Time
System\Context Switches/sec
Process(_Total)\Handle Count
```
Set 3: "Client_C_Security_Focus"  
(lsass and winlogon are instances you can choose, similar to C: drive in Step 5)
```
a. Security & Services:
Process(lsass)\% Processor Time
Process(winlogon)\Handle Count
Server\Sessions Errored Out
```
![data collector set 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20122100.png)
![data collector set 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20122129.png)
![data collector set 3](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20122913.png)  
7. You can use the following PowerShell commands to view the available counters and their descriptions:
```
Get-Counter -ListSet * | Select-Object CounterSetName, Description
```
![powershell command](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%205%3A%20MSP%20Operation%20Lab%20-%20Datto%20RMM%20Workflow%20Simulation/Images/Screenshot%202025-06-19%20131215.png)
