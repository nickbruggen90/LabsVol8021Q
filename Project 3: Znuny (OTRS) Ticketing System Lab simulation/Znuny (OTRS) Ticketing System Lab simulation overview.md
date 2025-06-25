# 🎫 **Project 3: Znuny/OTRS Ticketing System Lab**
### 🎯 Objective  
Build an enterprise-grade help desk simulation demonstrating MSP ticketing workflows, role-based access controls, multi-client management, and professional incident response procedures using Znuny Community Edition.

## Project Goals

- Deploy and configure Znuny ticketing system from scratch
- Implement ITIL-aligned workflow processes
- Configure user roles and permissions
- Set up automated email notifications
- Create custom ticket queues and SLAs
- Demonstrate practical IT service desk capabilities

## 🖥️ Lab Environment

- **TurnKey OTRS** - Pre-configured virtual appliance

---
## 🧱 Lab Components  
| Component           | Purpose                                            |
|---------------------|----------------------------------------------------|
| **Znuny/OTRS CE**   | Core ticketing system and workflow engine         |
| **Agent Hierarchy** | L1, SUP-L2, NET-L2 with tiered permissions       |
| **Queue System**    | Specialized routing (NET-OPS, IT-SUPPORT, etc.)   |
| **Customer Base**   | Multi-department enterprise users (5 departments) |

> *System configured to mirror real MSP operations with proper documentation standards and business impact assessment.*

---
## 🔄 Workflow Overview  
1. **Customer Management:** Department-based user structure (ACCT-WILSON, HR-JONES, etc.)
2. **Ticket Creation:** 5 professional scenarios covering Critical to Low priority incidents  
3. **Queue Routing:** Automatic assignment based on issue type and expertise required
4. **Role Permissions:** Tiered access ensuring appropriate escalation and oversight
5. **State Management:** Professional workflow including pending-vendor, escalated, in-progress
6. **Documentation:** Enterprise-standard ticket details with impact statements and troubleshooting steps

### SLA Configuration
| Priority | Response Time | Resolution Time |
|----------|---------------|-----------------|
| High     | 1 hour        | 4 hours         |
| Medium   | 4 hours       | 24 hours        |
| Low      | 24 hours      | 72 hours        |
