# IPAM Schema - Project 1.0+
**Current Networks:** 4 segments (Management/WAN + 3 branches)  
**Architecture:** Multi-VMnet approach (no VLAN tagging)  

---

## **VMnet Allocation**

| VMnet | Branch | Purpose | Subnet | Gateway | DHCP | pfSense Interface |
|---|---|---|---|---|---|---|
| **VMnet0** | All | WAN/Internet | Bridged | - | No | WAN interfaces |
| **VMnet1** | Branch 1 | Infrastructure | 192.168.83.224/29 | 192.168.83.226 | No | em1 (LAN) |
| **VMnet2** | Branch 1 | Linux Servers | 192.168.83.0/28 | 192.168.83.1 | No | em2 (BR1_LNX_SRV) |
| **VMnet3** | Branch 1 | Linux Clients | 192.168.83.32/27 | 192.168.83.33 | Yes | em3 (BR1_LNX_CLI) |
| **VMnet4** | Branch 1 | Windows Servers | 192.168.83.64/28 | 192.168.83.65 | No | em4 (BR1_WIN_SRV) |
| **VMnet5** | Branch 1 | Windows Clients | 192.168.83.96/27 | 192.168.83.97 | Yes | em5 (BR1_WIN_CLI) |
| **VMnet8** | Branch 2 | Infrastructure | 192.168.84.224/29 | 192.168.84.226 | No | em1 (LAN) |
| **VMnet10** | Branch 2 | Linux Clients | 192.168.84.32/27 | 192.168.84.33 | Yes | em3 (BR2_LNX_CLI) |
| **VMnet15** | Sophos | Infrastructure | 192.168.85.224/29 | 192.168.85.226 | No | em1 (LAN) |

---

## **Branch 1 - (192.168.83.0/24)**

### **VMnet1: Infrastructure (192.168.83.224/29)**
| IP Address | Device | Purpose |
|---|---|---|
| 192.168.83.225 | VMware Host Adapter | Management |
| 192.168.83.226 | pfSense Branch 1 LAN | Router/Firewall |

### **VMnet2: Linux Servers (192.168.83.0/28)**
| IP Address | Device | Purpose |
|---|---|---|
| 192.168.83.1 | pfSense BR1_LNX_SRV Gateway | Gateway |
| 192.168.83.2 | Ubuntu Server | Linux Infrastructure |

### **VMnet3: Linux Clients (192.168.83.32/27)**
| IP Address | Device | Purpose |
|---|---|---|
| 192.168.83.33 | pfSense BR1_LNX_CLI Gateway | Gateway |
| 192.168.83.34 | Kali Linux | Penetration Testing |
| 192.168.83.35 | Ubuntu Client | Linux Workstation |
| 192.168.83.45-62 | DHCP Pool | Dynamic Clients |

### **VMnet4: Windows Servers (192.168.83.64/28)**
| IP Address | Device | Purpose |
|---|---|---|
| 192.168.83.65 | pfSense BR1_WIN_SRV Gateway | Gateway |
| 192.168.83.66 | Windows Server 2025 | Domain Controller |

### **VMnet5: Windows Clients (192.168.83.96/27)**
| IP Address | Device | Purpose |
|---|---|---|
| 192.168.83.97 | pfSense BR1_WIN_CLI Gateway | Gateway |
| 192.168.83.98 | Windows 10 Client | Domain Workstation |
| 192.168.83.110-126 | DHCP Pool | Dynamic Clients |

---

## **Branch 2 - (192.168.84.0/24)**

### **VMnet8: Infrastructure (192.168.84.224/29)**
| IP Address | Device | Purpose |
|---|---|---|
| 192.168.84.226 | pfSense Branch 2 LAN | Router/Firewall |

### **VMnet10: Linux Clients (192.168.84.32/27)**
| IP Address | Device | Purpose |
|---|---|---|
| 192.168.84.33 | pfSense BR2_LNX_CLI Gateway | Gateway |
| 192.168.84.35 | Ubuntu Client | Linux Workstation |

---

## **Sophos Lab - (192.168.85.0/24)**

### **VMnet15: Infrastructure (192.168.85.224/29)**
| IP Address | Device | Purpose |
|---|---|---|
| 192.168.85.226 | Sophos XG LAN | Firewall Testing |

---

## **WAN Network - (192.168.19.0/24)**
| IP Address | Device | Purpose |
|---|---|---|
| 192.168.19.2 | WAN Gateway | Internet Router |
| 192.168.19.128 | pfSense Branch 2 WAN | WAN Interface |
| 192.168.19.129 | pfSense Branch 1 WAN | WAN Interface |
| 192.168.19.135 | Sophos XG WAN | WAN Interface |

---

## **Device Deployment Plan**

### **Branch 1 Device Assignments:**
| Device | VMnet | IP Address | Purpose |
|---|---|---|---|
| pfSense Branch 1 | VMnet0/1/2/3/4/5 | Multi-homed | Router/Firewall |
| Ubuntu Server | VMnet2 | 192.168.83.2 | Linux Infrastructure |
| Kali Linux | VMnet3 | 192.168.83.34 | Penetration Testing |
| Ubuntu Client | VMnet3 | 192.168.83.35 | Linux Workstation |
| Windows Server 2025 | VMnet4 | 192.168.83.66 | Domain Controller |
| Windows 10 Client | VMnet5 | 192.168.83.98 | Domain Workstation |

### **Branch 2 Device Assignments:**
| Device | VMnet | IP Address | Purpose |
|---|---|---|---|
| pfSense Branch 2 | VMnet0/8/10 | Multi-homed | Router/Firewall |
| Ubuntu Client | VMnet10 | 192.168.84.35 | Linux Workstation |

### **Sophos Lab Device Assignments:**
| Device | VMnet | IP Address | Purpose |
|---|---|---|---|
| Sophos XG Firewall | VMnet0/15 | Multi-homed | Firewall Testing |

---

## **pfSense Configuration Requirements**

### **Branch 1 pfSense Interfaces:**
| Interface | VMnet | IP Address | Subnet | DHCP |
|---|---|---|---|---|
| WAN (em0) | VMnet0 | 192.168.19.129 | Bridged | No |
| LAN (em1) | VMnet1 | 192.168.83.226/29 | Infrastructure | No |
| BR1_LNX_SRV (em2) | VMnet2 | 192.168.83.1/28 | Linux Servers | No |
| BR1_LNX_CLI (em3) | VMnet3 | 192.168.83.33/27 | Linux Clients | Yes (.45-.62) |
| BR1_WIN_SRV (em4) | VMnet4 | 192.168.83.65/28 | Windows Servers | No |
| BR1_WIN_CLI (em5) | VMnet5 | 192.168.83.97/27 | Windows Clients | Yes (.110-.126) |

### **Branch 2 pfSense Interfaces:**
| Interface | VMnet | IP Address | Subnet | DHCP |
|---|---|---|---|---|
| WAN (em0) | VMnet0 | 192.168.19.128 | Bridged | No |
| LAN (em1) | VMnet8 | 192.168.84.226/29 | Infrastructure | No |
| BR2_LNX_CLI (em3) | VMnet10 | 192.168.84.33/27 | Linux Clients | Yes (.45-.62) |

---
This IPAM serves as the master blueprint for the complete Project 1.0+ build-out.
