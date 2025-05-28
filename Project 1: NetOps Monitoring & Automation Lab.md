# 🧪 **Project 1: NetOps Monitoring & Automation Lab**

### 🎯 Objective  
Build a virtual lab simulating a secure network environment with centralized logging, SNMP telemetry, packet analysis, and Python-driven automation workflows using pfSense, Ubuntu, rsyslog, Paramiko, and Wireshark.

---

## 🧱 Lab Components  

| Component           | Purpose                                            |
|---------------------|----------------------------------------------------|
| **VMWare Workstation**       | Hypervisor             |
| **pfSense VM**       | Firewall, DHCP, and Syslog/SNMP source             |
| **Ubuntu Server**    | rsyslog collector + SNMP client + Python scripts   |
| **Wireshark**        | Live packet analysis and traffic validation        |
| **Python Tooling**   | Automation using Paramiko, and syslog parsing |

> *LibreNMS will be added as a Docker container in Phase 4 for GUI-based monitoring.*

---

## 🔄 Workflow Overview  

1. pfSense acts as the central firewall and telemetry source  
2. Ubuntu receives logs over Syslog (UDP 514) and stores them in `/var/log/pfsense.log`  
3. SNMP is enabled on pfSense and verified via `snmpwalk` from Ubuntu  
4. Python scripts parse logs and automate network checks via SSH (Paramiko)  
5. Wireshark captures traffic including syslog, SNMP, DHCP, and VPN (future
