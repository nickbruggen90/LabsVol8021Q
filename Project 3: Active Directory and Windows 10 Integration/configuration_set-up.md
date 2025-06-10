### Windows Server Creation & ADDS Initial Set-Up
First we will need to create the Windows Server 2025 VM. Choose the following configuration for set-up:
```
1. NIC: Host-Only
2. RAM: 4GB
3. Disk Space: 40GB
4. CPUs: 1, 2 core
5. Name: DC01
```
1. It will ask you for a license key, choose "I don't have a license". You get 180 day trial. Choose the version of Windows Server you downloaded (2019, 2022, 2025). In this case, it is Windows Server 2025. And choose the Standard version, NON-CORE.  
2. Once the server boots up, restart the VM and log in as Administrator.  
3. First thing you should do is change the password for Administrator. (For this lab I recommend using the same password throughout for simplicity).  
4. Use the search bar and search for "About Your PC" and in the top right choose "Rename this PC". Rename it DC01. Let the VM restart.  
