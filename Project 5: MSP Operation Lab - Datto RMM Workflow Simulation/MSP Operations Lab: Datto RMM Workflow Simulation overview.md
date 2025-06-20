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
- **Weekly:** System file checks, optimization, compliance audits  
- **Monthly:** Full system health reports and security assessments

### Event Viewer (Reactive Troubleshooting)
**Custom Views for Each Client:**
- **Critical Events:** System crashes, service failures, security breaches
- **Security Audit:** Failed logins, account changes, privilege escalation
- **Performance Issues:** Application crashes, disk errors, network problems

## Business Value
**Prevents "My Computer is Slow" Calls:**
- Proactive monitoring catches issues before users notice
- Automated maintenance runs during off-hours  
- Different service levels match client SLA requirements
- Centralized logging enables quick root cause analysis

## Tools Mastered
* **Performance Monitor** → Real-time monitoring & alerting
* **Task Scheduler** → Automated maintenance & policy deployment  
* **Event Viewer** → Log analysis & security monitoring
* **PowerShell** → Automation & remote management

---
**Result:** Complete MSP operations workflow demonstrating readiness for L1/L2 technician role with understanding of monitoring, automation, and troubleshooting in multi-client environments.
