### Event Viewer (Logging & Troubleshooting)
1. Press Windows+R and search eventvwr.msc (this is a native Windows logging tool comparable to Datto RMM's "Event Log Monitoring" and "Reports" modules).

2. Under Event Viewer you can view system logs, create custom views, and set up log subscriptions for centralized monitoring. This step will demonstrate how to create custom views for different client monitoring needs.  
We can create the following custom views based on MSP client tiers and troubleshooting needs:

**Client A (Basic Tier) - Essential Error Monitoring:**
```
Client_A_Critical_Errors: System crashes, boot failures, hardware issues
Client_A_Service_Failures: Critical service startup failures
Client_A_Security_Alerts: Basic security events and logon failures
```

**Client B (Professional Tier) - Enhanced Monitoring:**
```
Client_B_System_Health: Comprehensive system and application errors
Client_B_Performance_Issues: Performance-related warnings and errors
Client_B_Network_Problems: Network connectivity and authentication issues
Client_B_Storage_Alerts: Disk errors, file system issues, backup failures
```

**Client C (Premium Tier) - Advanced Security & Compliance:**
```
Client_C_Security_Audit: Comprehensive security event monitoring
Client_C_Compliance_Tracking: Policy changes, privilege escalation, data access
Client_C_Advanced_Threats: Suspicious activities, malware detection, intrusion attempts
Client_C_System_Forensics: Detailed system changes and administrative actions
```

3. Example Custom View Creation - Client_B_System_Health:
```
a. Event Viewer → Custom Views → Create Custom View
b. Filter: By log
c. Select Event logs:
   - Windows Logs: System, Application
   - Applications and Services Logs: Microsoft-Windows-Kernel-General/Admin
d. Event level: Critical, Error, Warning
e. Time range: Last 24 hours
f. Name: "Client_B_System_Health"
g. Description: "Critical system and application issues for professional tier monitoring"
```

4. Example Custom View Creation - Client_C_Security_Audit:
```
a. Event Viewer → Custom Views → Create Custom View
b. Filter: By log
c. Select Event logs:
   - Windows Logs: Security, System
   - Applications and Services Logs: Microsoft-Windows-Security-Auditing/Admin
d. Event level: Critical, Error, Warning
e. Event IDs: 4624, 4625, 4634, 4648, 4720, 4726, 4732, 4756
   (Logon success/failure, account management, privilege changes)
f. Time range: Last 7 days
g. Name: "Client_C_Security_Audit"
h. Description: "Security events and compliance monitoring for premium clients"
```

5. Event Log Subscription for Centralized Monitoring:
```
a. Event Viewer → Subscriptions → Create Subscription
b. Subscription name: "Client_A_Critical_Events"
c. Description: "Collect critical events from Client A workstations"
d. Destination log: Forwarded Events
e. Events to collect: Custom view (use previously created views)
f. Computer groups: Add target client machines
g. Configure advanced delivery optimization and retry settings
```

6. Key Event IDs for MSP Monitoring:
```
System Log:
- Event ID 6008: Unexpected system shutdown
- Event ID 1074: Planned system shutdown/restart
- Event ID 7034: Service crashed unexpectedly
- Event ID 41: System rebooted without cleanly shutting down

Application Log:
- Event ID 1000: Application error/crash
- Event ID 1002: Application hang
- Event ID 1001: Windows Error Reporting

Security Log:
- Event ID 4624: Successful logon
- Event ID 4625: Failed logon attempt
- Event ID 4634: Account logoff
- Event ID 4720: User account created
- Event ID 4726: User account deleted
```
