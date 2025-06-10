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
![license key screenshot](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20140539.png)  
3. Once the server boots up, restart the VM and log in as Administrator. First thing you should do is change the password for Administrator. (For this lab I recommend using the same password throughout for simplicity).
4. Rename PC and Set Static IP:  
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
![cmd ipconfig](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20144719.png)
5. Now we will add Active Directory Domain Services. In Server Manager choose:
```
a. Add roles and features
b. Role-based or feature-based installation
c. Ensure the DC01 IP address is 192.168.83.150 (the static one we set)
d. Check Active Directory Domain Services and Add Feature
e. Skip through the next optional features for now, and install
```
![yellow flag picture](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20151452.png)
6. When the installation succeeds and the VM restarts, look for a yellow flag in the top right corner and choose "Promotoe this server to a domain controller". And choose the following:
```
a. Add new forest, and choose a relavent name. In this instance we will choose testlab.local
b. Keep both DNS server and Global Catalog checked
c. DSRM password: choose the same password as you have been for this lab
d. Keep rest of the settings default
e. You should see that all prerequisites pass
```

