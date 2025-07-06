# MSP Operations Lab: Datto RMM Workflow Simulation

## Lab Environment
**Three Client Scenarios (Different MSP Service Levels):**
* **Client A (Basic):** Small office - essential monitoring only
* **Client B (Professional):** Higher uptime requirements - enhanced automation  
* **Client C (Premium):** Security-focused - advanced compliance monitoring

## Technical Implementation

### Performance Monitor (Proactive Monitoring)
**Industry-Standard Alert Thresholds:**
- **Critical:** CPU >90%, Memory <500MB, Disk <10% (immediate L1/L2 response)
- **Warning:** CPU >75%, Memory <1GB, Disk <20% (scheduled maintenance)
- **Baseline:** Network/disk performance trends (capacity planning)

### Task Scheduler (Automation)
**Automated Maintenance by Client Tier:**
- **Daily:** Disk cleanup, service monitoring, security scans
- **Monthly:** Full system health reports and security assessments

### Event Viewer (Reactive Troubleshooting)
**Custom Views for Each Client:**
- **Critical Events:** System crashes, security breaches
- **Security Audit:** Failed logins, account changes
- **Performance Issues:** Application crashes, disk errors, network problems

## Tools Utilized
* **Performance Monitor** → Real-time monitoring and alerting
* **Task Scheduler** → Automated maintenance 
* **Event Viewer** → Log analysis and security monitoring
