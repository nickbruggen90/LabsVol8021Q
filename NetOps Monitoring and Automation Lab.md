# 🧪 **Project 1: NetOps Monitoring & Automation Lab**

### 🎯 Objective  
Design a GNS3-based lab simulating a secure branch office with VPN access, SNMP/Syslog monitoring, packet analysis, and Python-driven automation workflows.

---

## 🧱 Lab Components  
- **Cisco Router (IOSv/IOU)** – Core routing + SNMP/Syslog source  
- **pfSense Firewall** – VPN gateway (OpenVPN or IPSec)  
- **LibreNMS VM** – SNMP monitoring + Syslog collection  
- **Python VM** – Runs Netmiko + TraceNG scripts  
- **Wireshark** – For live packet capture and traffic analysis

---

## 🔄 Workflow Overview  
1. VPN tunnel established from client to pfSense firewall  
2. LibreNMS polls SNMP data and logs events via Syslog  
3. Python/TraceNG VM performs reachability tests and path tracing  
4. Netmiko scripts automate device queries and configuration  
5. Wireshark captures VPN, control, and test traffic for validation

---

## ✅ Skills Demonstrated  
- VPN tunnel configuration and testing  
- SNMP and Syslog server setup  
- Real-time network monitoring and alerting  
- Python-based network automation (Netmiko + TraceNG)  
- Packet analysis and telemetry interpretation

---

## 💼 Resume Version (2 lines)  
> Designed a GNS3-based lab simulating a secure branch office with VPN, SNMP/Syslog monitoring, packet analysis, and Python-driven automation. Integrated Cisco IOS, pfSense, LibreNMS, Netmiko, TraceNG, and Wireshark for full-stack NetOps visibility and control.
