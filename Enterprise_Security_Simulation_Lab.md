### 🧱 Project Title:  
## Enterprise Security Simulation Lab — Web Server + WAF + GNS3 Topology
---
#### 🎯 Goal:  
Simulate a real-world enterprise network that includes:
- A real Ubuntu VM hosting a website (Linktree or DVWA)  
- A WAF (SafeLine) protecting that server  
- A virtualized network in GNS3 (VyOS routers/switches)  
- An external Kali laptop simulating users or attackers  
- Python monitoring scripts (future Substack content)  

#### 🧩 Lab Components:
- Ubuntu VM (on desktop):
  - Apache + VirtualHost for linktree or DVWA
  - Static IP (e.g., 192.168.4.120)
  - SafeLine WAF installed
- Kali VM (on laptop):
  - External simulation
  - Runs scans, attacks, and ping tests
- GNS3 Lab:
  - VyOS routers & switches (in GNS3 VM)
  - Cloud node bound to desktop NIC
  - Connected to Ubuntu VM (via Cloud Node)
- SafeLine WAF Portal:
  - Protects apps via reverse proxy
  - Handles domains like server.local and dvwa.server.local
