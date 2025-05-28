### pfSense Creation and Initial Configuration
First we will create the pfSense VM with VMWare Workstation. Use the official pfSense CE release. Choose the following configuration for set-up.
```
1. 2 NICs are needed: have the first one be Bridged, and the second Host-Only
2. 2BG RAM
3. 20GB storage space
4. 2 processors
Once the VM boots up, pfSense will ask some configuration options. The ones you need to pay attention to are:
6. Auto UFS
7. MBR
```
After the installation and initial bootup, pfSense will prompt you will a numbered menu. You are in the right spot.
Find the subnet associated with the virtual NIC.
1. Windows cmd -> ipconfig
2. Look for VMNet1 NIC (VMWare uses the 192.168.83.0/24 subnet by default, but double check)
3. Choose to Set Interface IPs from pfSense home screen. And choose the LAN interface (in this instance it is em1)
4. Change the LAN interface on pfSense to an IP within VMNet1 NIC subnet (in this instance it will be 192.168.83.100/24)
You are now able to log into the pfSense portal via the LAN IP you assigned (192.168.83.100).
Now we need to set up Ubuntu Server to act the Syslog Collector and SNMP Client.

### Ubuntu Server Creation and Configuration
The Ubuntu Server VM will be created with VMWare Workstation. Use the official Ubuntu Live Server .iso
1. 2 GB RAM
2. 2 processors
3. Host-Only network adapter
4. The default on the rest is fine
Once it boots up and you reach Network Configurations
1. You will choose an IP within the subnet of the VMNet1 NIC. In this instance it will be 192.168.83.10/24
2. The gateway will be the IP of the pfSense LAN - 192.168.83.100
3. Ping the default gateway and a name server (8.8.8.8 for instance)
(To populate the IP's of the Ubuntu Server, you may need to install net-tools)
  1. sudo apt install net-tools
  2. ifconfig /all

