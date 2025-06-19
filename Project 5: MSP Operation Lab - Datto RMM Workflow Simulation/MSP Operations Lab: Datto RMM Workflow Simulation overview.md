 # MSP Operations Lab: Datto RMM Workflow Simulation

---

## Key Accomplishments:
* Configured multi-client monitoring scenarios with industry-standard alert thresholds
* Simulated critical L1/L2 workflows including system health monitoring
* Demonstrated understanding of proactive monitoring that prevents issues before clients notice them
* Created documentation showing how Windows tools translate to enterprise RMM concepts

## Lab Objectives

**Primary Goal:** Understand core RMM functionality and L1/L2 technician workflows

**Simulated Environment:** Three client scenarios representing different MSP service levels:
* **Client A:** Small office (basic monitoring needs)
* **Client B:** Professional services (higher uptime requirements)
* **Client C:** Remote workers (security-focused monitoring)

## Monitoring Configuration

### Alert Thresholds (Industry Standard)

**Critical Alerts (Immediate L1/L2 Response):**
* CPU Usage > 90% sustained
* Available Memory < 500 MB
* Disk Free Space < 10%
* Unexpected system reboots

**Warning Alerts (Scheduled Response):**
* CPU Usage > 75% sustained
* Available Memory < 1 GB
* Disk Free Space < 20%

### Data Collector Sets Created
* **Client_A_Critical_Response:** Immediate action needed
* **Client_A_Warning_Monitoring:** Scheduled maintenance needed
* **Client_A_Performance_Baselines:** Trend analysis and reporting
* **Client_B_Critical_Response:** Immediate action needed
* **Client_B_Warning_Monitoring:** Scheduled maintenance needed
* **Client_B_Performance_Baselines:** Trend analysis and reporting
* **Client_C_Critical_Response:** Immediate action needed
* **Client_C_Warning_Monitoring:** Scheduled maintenance needed
* **Client_C_Performance_Baselines:** Trend analysis and reporting

## Tools Utilized
* **Performance Monitor:** Real-time system monitoring and alerting
* **Task Scheduler:** Automated maintenance and policy deployment
* **Event Viewer:** Log analysis and security monitoring
* **Remote Desktop/PowerShell:** Remote access and troubleshooting
