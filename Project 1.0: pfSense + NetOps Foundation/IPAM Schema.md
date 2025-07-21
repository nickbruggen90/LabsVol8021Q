# Lab IPAM Schema - Current and Planned Devices Only

## 🌐 **Lab Overview**
**Current Networks:** 4 segments (Management/WAN + 3 branches)  
**Architecture:** Multi-VMnet approach (no VLAN tagging)  
**Current Focus:** Branch 1 implementation and device migration

---

## 📋 **VMnet Allocation - Current Lab**

| VMnet | Branch | Purpose | Subnet | Gateway | DHCP | pfSense Interface | Status |
|---|---|---|---|---|---|---|---|
| **VMnet0** | All | WAN/Internet | Bridged | - | No | WAN interfaces | Active |
| **VMnet1** | Branch 1 | Infrastructure | 192.168.83.224/29 | 192.168.83.226 | No | em1 (LAN) | **Active** |
| **VMnet2** | Branch 1 | Linux Servers | 192.168.83.0/28 | 192.168.83.1 | No | em2 (OPT1) | **Active** |
| **VMnet3** | Branch 1 | Linux Clients | 192.168.83.32/27 | 192.168.83.33 | Yes | em3 (OPT2) | Planned |
| **VMnet4** | Branch 1 | Windows Servers | 192.168.83.64/28 | 192.168.83.65 | No | em4 (OPT3) | Planned |
| **VMnet5** | Branch 1 | Windows Clients | 192.168.83.96/27 | 192.168.83.97 | Yes | em5 (OPT4) | Planned |
| **VMnet8** | Branch 2 | Infrastructure | 192.168.84.224/29 | 192.168.84.226 | No | em1 (LAN) | Future |
| **VMnet10** | Branch 2 | Linux Clients | 192.168.84.32/27 | 192.168.84.33 | Yes | em3 (OPT2) | Future |
| **VMnet15** | Sophos | Infrastructure | 192.168.85.224/29 | 192.168.85.226 | No | em1 (LAN) | Future |

---

## 🏢 **Branch 1 - Primary Lab (192.168.83.0/24)**

### **VMnet1: Infrastructure (192.168.83.224/29) - ACTIVE**
| IP Address | Device | Purpose | Status |
|---|---|---|---|
| 192.168.83.225 | VMware Host Adapter | Management | Auto |
| 192.168.83.226 | pfSense Branch 1 LAN | Router/Firewall | **Active** |

### **VMnet2: Linux Servers (192.168.83.0/28) - ACTIVE**
| IP Address | Device | Purpose | Status |
|---|---|---|---|
| 192.168.83.1 | pfSense OPT1 Gateway | Gateway | **Active** |
| 192.168.83.2 | Ubuntu Server | Linux Infrastructure | **Active** |

### **VMnet3: Linux Clients (192.168.83.32/27) - PLANNED**
| IP Address | Device | Purpose | Status |
|---|---|---|---|
| 192.168.83.33 | pfSense OPT2 Gateway | Gateway | Planned |
| 192.168.83.34 | Kali Linux | Penetration Testing | **Migrate from .51** |
| 192.168.83.35 | Ubuntu Client | Linux Workstation | **Migrate from .52** |
| 192.168.83.45-62 | DHCP Pool | Dynamic Clients | Planned |

### **VMnet4: Windows Servers (192.168.83.64/28) - PLANNED**
| IP Address | Device | Purpose | Status |
|---|---|---|---|
| 192.168.83.65 | pfSense OPT3 Gateway | Gateway | Planned |
| 192.168.83.66 | Windows Server 2025 | Domain Controller | **Migrate from .150** |

### **VMnet5: Windows Clients (192.168.83.96/27) - PLANNED**
| IP Address | Device | Purpose | Status |
|---|---|---|---|
| 192.168.83.97 | pfSense OPT4 Gateway | Gateway | Planned |
| 192.168.83.98 | Windows 10 Client | Domain Workstation | **Migrate from .151** |
| 192.168.83.110-126 | DHCP Pool | Dynamic Clients | Planned |

---

## 🏢 **Branch 2 - Secondary Lab (192.168.84.0/24)**

### **VMnet8: Infrastructure (192.168.84.224/29) - FUTURE**
| IP Address | Device | Purpose | Status |
|---|---|---|---|
| 192.168.84.226 | pfSense Branch 2 LAN | Router/Firewall | Future |

### **VMnet10: Linux Clients (192.168.84.32/27) - FUTURE**
| IP Address | Device | Purpose | Status |
|---|---|---|---|
| 192.168.84.33 | pfSense OPT2 Gateway | Gateway | Future |
| 192.168.84.35 | Ubuntu Client | Linux Workstation | **Migrate from .52** |

---

## 🛡️ **Sophos Lab (192.168.85.0/24)**

### **VMnet15: Infrastructure (192.168.85.224/29) - FUTURE**
| IP Address | Device | Purpose | Status |
|---|---|---|---|
| 192.168.85.226 | Sophos XG LAN | Firewall Testing | Future |

---

## 🔗 **WAN Network (192.168.19.0/24)**
| IP Address | Device | Purpose | Status |
|---|---|---|---|
| 192.168.19.2 | WAN Gateway | Internet Router | Active |
| 192.168.19.128 | pfSense Branch 2 WAN | WAN Interface | Active |
| 192.168.19.129 | pfSense Branch 1 WAN | WAN Interface | **Active** |
| 192.168.19.135 | Sophos XG WAN | WAN Interface | Active |

---

## 📋 **Device Migration Plan**

### **Current Device Locations:**
| Device | Current IP | Current Network | Target VMnet | Target IP | Priority |
|---|---|---|---|---|---|
| Ubuntu Server | 192.168.83.2 | VMnet2 | VMnet2 | 192.168.83.2 | ✅ **Complete** |
| Kali Linux | 192.168.83.51 | Flat network | VMnet3 | 192.168.83.34 | **High** |
| Ubuntu Client | 192.168.83.52 | Flat network | VMnet3 | 192.168.83.35 | **High** |
| Windows Server 2025 | 192.168.83.150 | Flat network | VMnet4 | 192.168.83.66 | **High** |
| Windows 10 Client | 192.168.83.151 | Flat network | VMnet5 | 192.168.83.98 | **High** |
| Branch 2 Ubuntu | 192.168.84.52 | Flat network | VMnet10 | 192.168.84.35 | **Medium** |

### **pfSense Configuration Status:**
| Interface | VMnet | IP Address | Status | Firewall Rules |
|---|---|---|---|---|
| WAN (em0) | VMnet0 | 192.168.19.129 | ✅ Active | Default |
| LAN (em1) | VMnet1 | 192.168.83.226/29 | ✅ Active | Default |
| OPT1 (em2) | VMnet2 | 192.168.83.1/28 | ✅ Active | ✅ OPT1 net to Any |
| OPT2 (em3) | VMnet3 | - | ❌ Not configured | ❌ Pending |
| OPT3 (em4) | VMnet4 | - | ❌ Not configured | ❌ Pending |
| OPT4 (em5) | VMnet5 | - | ❌ Not configured | ❌ Pending |

---

## 📊 **Current Lab Statistics**

### **Network Utilization:**
| Network | Total IPs | Current Devices | Available | Next Priority |
|---|---|---|---|---|
| Branch 1 | 256 | 2 | 254 | Migrate remaining 4 devices |
| Branch 2 | 256 | 1 | 255 | Future expansion |
| Sophos | 256 | 0 | 256 | Future testing |

### **Implementation Status:**
- ✅ **Working:** Ubuntu Server on VMnet2 with full connectivity
- 🔄 **Next:** Configure VMnet3 and migrate Linux clients
- 📋 **Planned:** VMnet4-5 for Windows environment
- 🔮 **Future:** Branch 2 and Sophos lab expansion

This IPAM focuses only on what's actually in your lab or specifically planned for immediate implementation.
