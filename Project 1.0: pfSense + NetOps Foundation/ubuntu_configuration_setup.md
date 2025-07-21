### Ubuntu Server Creation and Configuration
1. Create the Ubuntu VM inside **VMWare Workstation Pro**. Use the official Ubuntu Live Server .iso release.
```
2 GB RAM
1 processors, 2 cores
Host-Only network adapter
The default on the rest is fine
```

2. Once it boots up and you reach `Network Configurations`:
```
a. You will choose an IP within the subnet of the VMNet1 NIC. In this instance it will be 192.168.83.2/28)
b. The gateway will be the IP of the VLANs default gateway - 192.168.83.1
c. 8.8.8.8 will be the DNS server for this lab
```

3. Install `net-tools`. This installs network related CLI commands.
```
a. sudo apt install net-tools
b. ifconfig -a
```

4. Next, let's install SNMP on the Ubuntu server. We will also need to allow SNMP on pfSense in future steps. Inside the Ubuntu Server VM:
```
sudo apt install snmp snmp-mibs-downloader
```
`For human-readable format, you can comment out #mibs in the /etc/snmp/snmp.conf file → `
##### Before: 
![mibs output 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-29%20185249.png)
##### After:
![mibs output 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-29%20185400.png)

5. Next, lets install Syslog and confirm it's active. Similar with SNMP, we will need to allow it on pfSense in future steps.
```
sudo apt update
sudo apt install rsyslog
sudo systemctl status rsyslog
```
![syslog active 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20071256.png)

6. We must also create and define log files and directories.
```
sudo mkdir /var/log
sudo touch /var/log/pfsense.log
sudo vim /etc/rsyslog.d/10-pfsense.conf
```

7. Add the following lines to the .conf file:
```
if ($fromhost-ip == '192.168.83.226') then /var/log/pfsense.log
& stop
```

8. Restart Syslog with *sudo systemctl restart rsyslog* - and also power down the VM.
9. While the VM is powered down, now is a good opportunity to create a shared folder between the VM and the host machine.
```
a. Open VM settings in VMWare Workstation and locate the Options tab at the top
b. Choose Share Folders and define the path
```
![shared folder 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20075236.png)

9. Inside Ubuntu we must also mount the shared folder.
```
sudo mkdir -p /mnt/hgfs
sudo vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other
```

OPTIONAL: If you run into permissions issues accessing the shared folder, you would need to unmount and remount, try:
```
id
sudo umount /mnt/hgfs
sudo mount -t fuse.vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other,uid=1000,gid=1000
```
*Command ‘id’ will bring up something like this - uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),...*
