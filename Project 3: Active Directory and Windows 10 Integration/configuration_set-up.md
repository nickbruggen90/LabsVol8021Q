### Windows Server Creation & ADDS Initial Set-Up
First we will need to create the Windows Server 2025 VM. Choose the following configuration for set-up:
1. VM Configuration:
```
NIC: Host-Only
RAM: 4GB
Disk Space: 40GB
CPUs: 1, 2 core
Name: DC01
```
2. License Key:
```
a. It will ask you for a license key, choose "I don't have a license". You get 180 day trial.  
b. Choose the version of Windows Server you downloaded (2019, 2022, 2025). In this case, it is Windows Server 2025.  
c. And choose the Standard version, NON-CORE.
```
[insert license key screenshot]
3. Once the server boots up, restart the VM and log in as Administrator. First thing you should do is change the password for Administrator. (For this lab I recommend using the same password throughout for simplicity).
4. Rename PC and Set Static IP.  
Use the search bar and search for "About Your PC" and in the top right choose "Rename this PC". Rename it DC01. Let the VM restart.  
Configure the network settings:  
```
a. Control Panel -> Network and Internet -> Network Sharing Center -> Change Adapter Settings -> right click on Ethernet0 and Properties  
b. Choose IPv4 Properties and input the following static IP information:
  IP Address: 192.168.83.150
  Subnet Mask: 255.255.255.0
  Default Gateway: 192.168.83.100 (pfSense)
  DNS: leave blank for now
```
Restart the PC to ensure the static IP was set.
[insert cmd ipconfig]
5. Now we will add Active Directory Domain Services. In Server Manager choose:
```
Add roles and features
Role-based or feature-based installation
Ensure the DC01 IP address is 192.168.83.150 (the static one we set)
Check Active Directory Domain Services and Add Feature
Skip through the next optional features for now, and install
```
