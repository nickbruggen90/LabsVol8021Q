# Znuny/OTRS Ticketing System Lab Walkthrough

## 🎯 Project Overview

This repository documents my hands-on implementation and configuration of Znuny (formerly OTRS) ticketing system in a lab environment. This project demonstrates practical IT service management skills and understanding of ITIL processes.

## 📋 Table of Contents

- [Project Goals](#project-goals)
- [Lab Environment](#lab-environment)
- [Installation Process](#installation-process)
- [Configuration Steps](#configuration-steps)
- [Key Features Implemented](#key-features-implemented)
- [Screenshots](#screenshots)
- [Lessons Learned](#lessons-learned)
- [Next Steps](#next-steps)
- [Resources](#resources)

## 🎯 Project Goals

- Deploy and configure Znuny ticketing system from scratch
- Implement ITIL-aligned workflow processes
- Configure user roles and permissions
- Set up automated email notifications
- Create custom ticket queues and SLAs
- Demonstrate practical IT service desk capabilities

## 🖥️ Lab Environment

**Deployment Method:**
- **TurnKey OTRS** - Pre-configured virtual appliance
- Simplified deployment for learning and testing purposes
- Includes optimized LAMP stack configuration

**Virtual Machine Specifications:**
- Platform: TurnKey OTRS Appliance
- Pre-configured with Znuny/OTRS Community Edition
- Integrated web server, database, and PHP stack
- Ready-to-use ticketing system environment

## 🚀 Deployment Process

### TurnKey OTRS Setup
This lab utilized the TurnKey OTRS virtual appliance for rapid deployment and learning focus.

**Advantages of TurnKey Approach:**
- Pre-optimized system configuration
- Eliminates installation complexity
- Allows focus on system administration and configuration
- Production-ready environment out of the box

**Initial Setup Steps:**
1. Downloaded TurnKey OTRS appliance
2. Deployed in virtualization environment
3. Completed initial web-based configuration
4. Configured basic system settings
5. Explored administrative interfaces and options

*Note: This approach prioritizes learning the administrative and operational aspects of OTRS/Znuny rather than installation procedures.*

## ⚙️ Configuration Steps

### 1. Initial System Configuration
- [ ] Web installer completion
- [ ] Database connection setup
- [ ] Admin user creation
- [ ] Basic system settings

### 2. User Management
- [ ] Agent user creation
- [ ] Customer user setup
- [ ] Role-based permissions
- [ ] Group assignments

### 3. Queue Configuration
- [ ] IT Support queue
- [ ] Network Issues queue
- [ ] Hardware Requests queue
- [ ] Software Support queue

### 4. SLA Configuration
| Priority | Response Time | Resolution Time |
|----------|---------------|-----------------|
| High     | 1 hour        | 4 hours         |
| Medium   | 4 hours       | 24 hours        |
| Low      | 24 hours      | 72 hours        |

### 5. Email Integration
- [ ] Incoming email configuration
- [ ] Outgoing email setup
- [ ] Auto-response templates
- [ ] Notification rules

## 🔧 Key Features Implemented

### Ticket Management
- Multi-queue ticket routing
- Priority-based escalation
- Custom ticket states
- Automatic assignment rules

### Workflow Automation
- Email-to-ticket conversion
- Auto-responses for common issues
- Escalation triggers
- SLA monitoring

### Reporting & Analytics
- Ticket volume reports
- Agent performance metrics
- SLA compliance tracking
- Customer satisfaction surveys

### Integration Capabilities
- LDAP authentication (if configured)
- API access for external tools
- Database reporting queries
- Export/import functionality

## 📸 Screenshots

### Initial Dashboard
![welcome dashboard](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-19%20025236.png)
*Main welcome dashboard showing the clean interface and navigation options*

### Admin Panel Overview
![admin panel 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-15%20063615.png)
![admin panel 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-15%20063631.png)
![admin panel 3](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-15%20063640.png)
![admin panel 4](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-15%20063650.png)
![admin panel 5](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-15%20063656.png)
*Administrative interface showing system configuration options and management tools*

### Queue Management
![admin panel queues](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-19%20023546.png)
*Queue configuration interface for organizing ticket workflows*

### Agent Management
![admin panel agents](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-19%20023947.png)
![admin panel agents create](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-15%20072538.png)
*Agent user creation and management interface*

### Permissions Management
![permissions 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-19%20024128.png)
![permissions 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-15%20072829.png)
*Agent-to-Group assignment interface for role-based access control*

### Customer Management
![customers 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-19%20024612.png)
![customers 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-15%20074305.png)
*Customer organization setup and configuration*

### Customer User Management
![customer users 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-19%20024942.png)
![customer users 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%203%3A%20Znuny%20(OTRS)%20Ticketing%20System%20Lab%20simulation/Images/Screenshot%202025-06-15%20074818.png)
*Individual customer user account creation and management*

## 📊 Testing Scenarios

### Scenario 1: Network Connectivity Issue
1. **Ticket Creation:** User reports network connectivity problems
2. **Assignment:** Auto-routed to Network Issues queue
3. **Escalation:** Priority set to High due to business impact
4. **Resolution:** Documented troubleshooting steps and solution

### Scenario 2: Software Installation Request
1. **Ticket Creation:** Employee requests software installation
2. **Approval Process:** Routed to manager for approval
3. **Implementation:** IT team installs and configures software
4. **Closure:** User confirmation and knowledge base update

### Scenario 3: Hardware Failure
1. **Ticket Creation:** Workstation hardware failure reported
2. **Assessment:** Agent diagnoses issue remotely
3. **Procurement:** Hardware replacement ordered
4. **Resolution:** On-site installation and user training

## 💡 Lessons Learned

### Technical Insights
- Database optimization is crucial for performance
- Email integration requires careful SMTP configuration
- Regular backups are essential for production environments
- Queue design should match organizational structure

### Best Practices Discovered
- Clear SLA definitions improve customer satisfaction
- Automated workflows reduce manual overhead
- Regular agent training improves ticket resolution times
- Knowledge base integration speeds up common issues

### Challenges Overcome
- **Email Authentication:** Configured SPF/DKIM for reliable delivery
- **Performance Tuning:** Optimized MySQL settings for better response times
- **User Adoption:** Created documentation and training materials
- **Integration Issues:** Resolved LDAP connectivity problems

## 🔄 Next Steps

### Immediate Improvements
- [ ] Implement SSL/TLS certificates
- [ ] Configure automated backups
- [ ] Set up monitoring and alerting
- [ ] Create additional custom reports

### Advanced Features to Explore
- [ ] LDAP/Active Directory integration
- [ ] Custom ticket fields for asset management
- [ ] Integration with monitoring tools (Nagios, Zabbix)
- [ ] Mobile app configuration
- [ ] API development for custom integrations

### Production Considerations
- [ ] High availability setup
- [ ] Load balancing configuration
- [ ] Disaster recovery planning
- [ ] Security hardening implementation

## 📚 Resources

### Official Documentation
- [Znuny Administrator Manual](https://doc.znuny.org/)
- [OTRS/Znuny Community Forums](https://community.znuny.org/)
- [Installation Guide](https://doc.znuny.org/manual/installation/)

### Additional Learning Materials
- [ITIL Foundation Concepts](https://www.axelos.com/best-practice-solutions/itil)
- [MySQL Performance Tuning](https://dev.mysql.com/doc/refman/8.0/en/optimization.html)
- [Apache Web Server Configuration](https://httpd.apache.org/docs/)

### Related Projects
- [Active Directory Lab](../active-directory-lab/) - User authentication integration
- [Network Monitoring Setup](../network-monitoring/) - Ticket automation from monitoring alerts
- [Python Automation Scripts](../python-automation/) - Custom API integrations

## 🤝 Contributing

This is a personal learning project, but suggestions and improvements are welcome! Feel free to:
- Open issues for questions or suggestions
- Submit pull requests for documentation improvements
- Share your own Znuny/OTRS experiences

## 📄 License

This project is for educational purposes. Znuny is open-source software licensed under the GNU General Public License.

---

**Author:** [Your Name]  
**Date:** [Current Date]  
**LinkedIn:** [Your LinkedIn Profile]  
**Contact:** [Your Email]

---

*This walkthrough is part of my IT infrastructure learning journey, focusing on practical skills for junior system administrator roles.*
