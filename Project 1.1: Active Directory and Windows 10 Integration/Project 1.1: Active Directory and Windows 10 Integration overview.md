# 🏢 **Project 1.1: Active Directory & Windows 10 Integration Lab**
### 🎯 Objective  
Build a complete Windows Server 2025 Active Directory Domain Services environment with Windows 10 client integration, demonstrating enterprise user management, Group Policy configuration, and domain authentication workflows.

---
## 🧱 Lab Components  
| Component           | Purpose                                            |
|---------------------|----------------------------------------------------|
| **Windows Server 2025** | Domain Controller (DC01) with ADDS and DNS roles |
| **Windows 10 Pro**  | Domain-joined client workstation (CLIENT01)       |
| **Active Directory** | User/computer management and authentication        |
| **Group Policy**     | Centralized security and configuration management  |
| **DNS Integration**  | Domain name resolution and service location       |

> *Complete enterprise domain environment with realistic user scenarios and security policies.*

---
## 🔄 Workflow Overview  
1. **Domain Controller Setup:** Windows Server 2025 configured as primary DC with testlab.local domain
2. **Network Configuration:** Static IP assignments with proper DNS hierarchy (DC: 192.168.83.150, Client: 192.168.83.151)
3. **User Management:** Created organizational units, test users (jsmith), and security groups (IT Support)
4. **Client Integration:** Windows 10 Pro workstation successfully joined to domain with user authentication
5. **Group Policy Implementation:** Account lockout policies, password requirements, and network drive mapping
6. **Security Hardening:** Implemented enterprise-standard lockout thresholds and password complexity requirements

---
## 🔐 Security Policies Configured
- **Account Lockout:** 5 failed attempts, 30-minute lockout duration
- **Password Policies:** Complexity requirements and expiration settings
- **Network Drive Mapping:** Automated user drive assignments via GPO
- **Domain Authentication:** Centralized login with proper user/computer relationship verification
