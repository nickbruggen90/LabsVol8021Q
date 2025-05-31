### 🧱Pilot Project Title:  
## Web Server + WAF + Kali
---
#### 🎯 Goal:  
Simulate a real-world enterprise network that includes:
- A real Ubuntu VM hosting a DVWA  
- A WAF (SafeLine) protecting that server  
- A Kali VM simulating users or attackers  

#### 🧩 Lab Components:
- Ubuntu VM (on desktop):
  - Apache + VirtualHost for DVWA
  - Static IP 
  - SafeLine WAF installed
- Kali VM (on laptop):
  - External simulation
  - Runs scans, attacks, and ping tests
- SafeLine WAF Portal:
  - Protects apps via reverse proxy
  - Handles domain dvwa.server.local
