# 🧪 Project 4 Overview – VPN + NetOps Automation + Simulated NOC

## 🎯 Objective
Design and implement a simulated branch-to-HQ VPN lab using pfSense, paired with NetOps automation and NOC-style monitoring workflows. This lab demonstrates secure tunnel connectivity, device telemetry collection, and reactive automation using real-world tools and simulated RMM/PSA logic.

---

## 🧱 Lab Components
- **pfSense (HQ + Branch)** – Site-to-site VPN via IPsec or OpenVPN
- **Ubuntu Server** – Acts as centralized Ansible controller, syslog collector, SNMP poller
- **Ansible** – Automates config pushes, reachability checks, and log parsing
- **Syslog + SNMP** – Used for telemetry and event capture
- **Simulated RMM** – Custom scripts to detect issues and log alerts
- **Simulated PSA** – Ticketing emulation via Markdown/CSV/SQLite entries
- **Wireshark** – Validates network flows, VPN negotiation, and automation events

---

## 🔄 Workflow Summary
1. VPN tunnel is established between branch and HQ
2. Ansible periodically checks device health and VPN status
3. Syslog and SNMP output are monitored on the Ubuntu server
4. Custom scripts emulate RMM alerting and PSA ticket creation
5. All traffic and automation can be captured via Wireshark

---

## 🗂️ Future Integration Potential
- Real RMM platforms (e.g., NinjaOne)
- PSA platforms like HaloPSA
- NETCONF/RESTCONF for telemetry
- Email escalation and service mapping

