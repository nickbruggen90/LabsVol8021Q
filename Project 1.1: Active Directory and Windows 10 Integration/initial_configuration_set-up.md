### Windows Server Creation & ADDS Initial Set-Up
This section covers creating a Windows Server 2025 domain controller for our Active Directory lab environment.
First we will need to create the Windows Server 2025 VM. Choose the following configuration for set-up:
1. VM Configuration:
```
NIC: Host-Only
RAM: 4GB
Disk Space: 40GB
CPUs: 1 processor 2 core preferably (1 processor 1 core will work)
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
(Alternatively, you can right click on This PC -> Properties -> Rename this PC)
Configure the network settings:  
```
a. Control Panel -> Network and Internet -> Network Sharing Center -> Change Adapter Settings -> right click on Ethernet0 and Properties  
b. Choose IPv4 Properties and input the following static IP information:
      IP Address: 192.168.83.150
      Subnet Mask: 255.255.255.0
      Default Gateway: 192.168.83.100 (pfSense)
      DNS: leave blank for now
```
Restart the PC to ensure the network settings were saved.  
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
6. When the installation succeeds and the VM restarts, look for a yellow flag in the top right corner and choose "Promote this server to a domain controller". And choose the following:
```
a. Add new forest, and choose a relevant name. In this instance we will choose testlab.local
b. Keep both DNS server and Global Catalog checked
c. DSRM password: choose the same password as you have been for this lab
d. Keep rest of the settings default
e. You should see that all prerequisites pass. And upon reboot, you should see AD DS and DNS roles.
```
7. Now we can go back into the IPv4 settings (step 4) and assign a DNS server, which will be this server itself. So set DNS to 127.0.0.1 and save.

---

### Creating Test Users and Groups
1. Here we will create  test user/employee and add them to a group.
```
a. Search for Active Directory Users and Computers
b. Right click testlab.local and create new Organizational Unit named "Employees"
c. Choose a password, and uncheck "User must change password at next logon"
d. Inside testlab.local creat a Group named "IT Support". Keep the Group Scope "Global" and Group Type "Security"
e. Apply and Ok
```
![user creation pic](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20161150.png)
![group creation pic](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20161543.png)

---

### Windows 10 Client Creation & Joining AD DS Domain
1. Now we will need to create the Client Windows VM to act as an employee/user connecting to the AD DS domain.
Upon the first bootup you will need to press any key to make it load from the CD (ISO).
```
NIC: Host-Only
RAM: 2GB
Disk Space: 40GB
CPUs: 1 processor 1 core
Name: CLIENT01
```
2. Choose "I don't have a license key" and you will need to choose Windows 10 Pro (Windows 10 Home doesn't allow you to connect to AD DS domains).  
![license key screenshot](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20183710.png)
3. Custom: Install Windows Only (advanced) and install. And choose the following:
```
      a. I don't have internet  
      b. Continue with limited setup  
      c. PC Name: CLIENT01  
      d. Choose a password (for simplicity purposes, stick with the same password throughout this lab)  
      e. I like to toggle No on all the privacy setting options, and not now to Cortana
```
4. Rename PC and Set Static IP:  
Use the search bar and search for "About Your PC" and in the top right choose "Rename this PC". Rename it CLIENT01. Let the VM restart.
(Alternatively, you can right click on This PC -> Properties -> Rename this PC)
![rename the pc](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20192952.png)
5. Configure the network settings:  
```
a. Control Panel -> Network and Internet -> Network Sharing Center -> Change Adapter Settings -> right click on Ethernet0 and Properties  
b. Choose IPv4 Properties and input the following static IP information:
      IP Address: 192.168.83.151
      Subnet Mask: 255.255.255.0
      Default Gateway: 192.168.83.100 (pfSense)
      DNS: 192.168.83.150 (DC01)
```
Restart the PC to ensure the network settings were saved.  
![cmd ipconfig](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20190509.png)  
6. *ping DC01* and *ping 192.168.83.150*
      a. Also perform nslook to ensure domain name/IP resolution
![ping results](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20190638.png)
![nslookup results](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20190708.png)  
7. Return to step 4, in the About this PC section, and scroll to the bottom and find Rename This PC (Advanced)
```
a. Select the Change button to change its domain (or workgroup)
b. Member of: Domain: testlab.local (NOT workgroup)
c. User Name: Administrator, Password: the password you chose for the Administrator account
d. Restart the VM and choose Other User in the bottom left corner, and login as testlab\jsmith
```
![admin login domain](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20191406.png)
![sucessful domain login](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20191546.png)
![jsmith login](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20191709.png)

---

### Confirmation
Return to DC01 and search for Active Directory Domain Services Users and Computers -> testlab.local -> Computers -> and you should see CLIENT01 listed.  
![confirmation](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20202550.png)
