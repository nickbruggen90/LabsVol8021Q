# **Pilot Project: Web Server + WAF + Kali Security Lab**
### Objective  
Simulate a real-world enterprise security environment demonstrating web application protection, threat detection, and penetration testing workflows using DVWA, SafeLine WAF, and Kali Linux in a controlled multi-device setup.

---
## Lab Components  
| Component           | Purpose                                            |
|---------------------|----------------------------------------------------|
| **Ubuntu VM**       | Web server hosting DVWA with Apache/VirtualHost   |
| **SafeLine WAF**    | Reverse proxy protection and threat filtering     |
| **Kali Linux VM**   | External attacker simulation and security testing |
| **DVWA Application** | Deliberately vulnerable web app for testing       |
| **Multi-Device Setup** | Desktop (server) + Laptop (attacker) configuration |

> *Enterprise security simulation with real web application protection and penetration testing scenarios.*

---
## Workflow Overview  
1. **Web Server Deployment:** Ubuntu hosting DVWA via Apache with static IP configuration
2. **WAF Implementation:** SafeLine reverse proxy protecting dvwa.server.local domain
3. **External Threat Simulation:** Kali VM conducting scans, attacks, and reconnaissance
4. **Security Monitoring:** WAF portal analyzing and blocking malicious traffic patterns
5. **Attack Validation:** Real-world penetration testing against protected web applications
6. **Defense Analysis:** Reviewing WAF logs and protection effectiveness against various attack vectors
