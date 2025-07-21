### Virtual Network Editor
```
Inside VMWare Workstation Pro we need to change the virtual NIC settings to fit the IPAM schema of this lab.  
Refer here for IPAM.
```
1. Inside VMWare Workstation Pro choose *Edit → Virtual Network Editor*
2. Click and highlight `VMNet1` and "Advanced Settings" towards the bottom.
3. Uncheck "Use local DHCP service to distribute IP address to VMs"
4. Define the Subnet IP as `192.168.83.224` and Subnet Mask as `192.168.83.248`

### pfSense Creation and Initial Configuration
1. First we will create the pfSense VM with VMWare Workstation. Use the official pfSense CE .iso release. Choose the following configuration for set-up:
```
2 NICs are needed:
  - NIC 1: Bridged
  - NIC 2: Host-Only
2 GB RAM
20 GB storage space
1 processor, 2 cores
```
2. Once the VM boots up, pfSense will ask input for configuration options. The ones you need to pay attention to are:
```
Auto UFS
MBR partition scheme
```
3. After the installation and initial bootup, pfSense CLI will prompt you will a numbered menu.
