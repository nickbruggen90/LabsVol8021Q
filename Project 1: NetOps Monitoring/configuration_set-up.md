### Virtual Network Editor
```
Inside VMWare Workstation Pro we need to change the virtual NIC settings to fit the IPAM schema of this lab.  
Refer here for IPAM.
```

### pfSense Creation and Initial Configuration
First we will create the pfSense VM with VMWare Workstation. Use the official pfSense CE .iso release. Choose the following configuration for set-up:
```
1. 2 NICs are needed:
    - NIC 1: Bridged
    - NIC 2: Host-Only
2. 2 GB RAM
3. 20 GB storage space
4. 2 processors
```
Once the VM boots up, pfSense will ask some configuration options. The ones you need to pay attention to are:
```
1. Auto UFS
2. MBR partition scheme
```
After the installation and initial bootup, pfSense will prompt you will a numbered menu. You are in the right spot.

##### Set the LAN IP:
Find the subnet associated with the virtual NIC:
```
1. In Windows cmd -> ipconfig
2. Look for VMNet1 NIC (VMWare uses the 192.168.83.0/24 subnet by default, but double check)
3. In pfSense menu, choose *Set Interface IPs*. Set the LAN interface (in this instance it is em1)
4. Choose an IP that is within VMNet1 NIC subnet (in this instance it will be 192.168.83.100/24)
```
![VMNet1 NIC output](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-28%20145426.png)
![pfSense IPs](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-28%20145701.png)

You are now able to log into the pfSense portal via the LAN IP you assigned (192.168.83.100).
Now we need to set up Ubuntu Server to act the Syslog Collector and SNMP Client, as well as create a Python script for SSH connection testing (and future automation).

---

### Ubuntu Server Creation and Configuration
The Ubuntu Server VM will be created with VMWare Workstation. Use the official Ubuntu Live Server .iso release.
```
1. 2 GB RAM
2. 2 processors
3. Host-Only network adapter
4. The default on the rest is fine
```
Once it boots up and you reach Network Configurations:
```
1. You will choose an IP within the subnet of the VMNet1 NIC (in this instance it will be 192.168.83.10/24)
2. The gateway will be the IP of the pfSense LAN - 192.168.83.100
3. Define a name server (8.8.8.8 for instance)
```
To populate the IP's of the Ubuntu Server, you may need to install net-tools:
```
1. sudo apt install net-tools
2. ifconfig -a
```
Next, let's install SNMP on the Ubuntu server. We will also need to allow SNMP on pfSense in future steps.
Inside Ubuntu Server VM:
```
sudo apt install snmp snmp-mibs-downloader
```
Alternatively, you can edit the /etc/snmp/snmp.conf file to make the output more readable.
```
#mibs :
```
![mibs output 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-29%20185249.png)
![mibs output 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-29%20185400.png)
  
Next, lets install Syslog and confirm it's active. Likewise, we will need to allow it on pfSense in future steps.
```
sudo apt update
sudo apt install rsyslog
sudo systemctl status rsyslog
```
![syslog active 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20071256.png)

We must also create and define log files and directories.
```
sudo mkdir /var/log
sudo touch /var/log/pfsense.log
sudo vim /etc/rsyslog.d/10-pfsense.conf
```
Add the following lines to the .conf file:
```
if ($fromhost-ip == '192.168.83.100') then /var/log/pfsense.log
& stop
```
Restart Syslog with *sudo systemctl restart rsyslog* - and also power down and power back up the entire VM for good measure.
While the VM is powered down, now is a good opportunity to create a shared folder between the VM and the host machine.
```
1. Open VM settings in VMWare Workstation and locate the Options tab at the top
2. Choose Share Folders and define the path
```
![shared folder 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20075236.png)

Inside Ubuntu we must also mount the shared folder.
```
sudo mkdir -p /mnt/hgfs
sudo vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other
```
If you run into permissions issues accessing the shared folder, you would need to unmount and remount, try:
```
id
sudo umount /mnt/hgfs
sudo mount -t fuse.vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other,uid=1000,gid=1000
```
*Command ‘id’ will bring up something like this - uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),...*

---

### Virtual Environment Creating and Installing Python
We will need to install Paramiko and SCP inside a virtual environment (VENV) to allow it to function.
```
sudo apt install python3-venv -y
python3 -m venv ~/netops-venv
source ~/netops-venv/bin/activate
which python
pip install --upgrade pip
pip install netmiko paramiko scp
deactivate
```
Now we must create a Paramiko Python script for testing. VS Code is a good option for writing code. Below is a sample Paramiko Python script.
```
#This script parses device inforamation using Python and Paramiko
import paramiko

hostname = '192.168.83.100'
username = 'admin'
password = 'pfsense'

ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())

commands = [
    'uptime',
    'hostname',
    'netstat -rn',
    'df -h',
    'ifconfig',
]

try:
    print("Connecting to pfSense...")
    ssh.connect(hostname, username=username, password=password)

    for cmd in commands:
        print(f"Executing command: {cmd}")
        stdin, stdout, stderr = ssh.exec_command(cmd)

        exit_status = stdout.channel.recv_exit_status()

        if exit_status == 0:
            output_lines = stdout.readlines()
            if output_lines:
                print("".join(output_lines))
            else:
                print("No output returned.")

        else:
            error_lines = stderr.readlines()
            print(f"Command failed with exit status {exit_status}.")
            print("".join(error_lines))
                
    ssh.close()
    print("Connection closed.")

except Exception as e:
    print(f"An error occurred: {e}")
```
To execute this script, we need to add the script to the shared folder for accessibility and allow for SSH connection through pfSense.
Return to Ubuntu CLI to confirm script is in the appropriate place.
```
ls -la /mnt/hgfs/"name of shared folder"
```
Let's save this test script as python.py 
Now we need to return to the pfSense GUI to allow Syslog, SNMP and SSH connections.

---

### Allowing pfSense Connections and Testing Python Script
We will define the Syslog server, allow for SSH connections and set up SNMP polling.  
Inside the pfSense GUI:  

Syslog:
```
1. Status tab -> System Logs -> Settings
2. Enable remote syslog server, and use the IP of the Ubuntu server and allow for Syslog UDP 514
3. 192.168.83.50:514
```
![syslog gui 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20082535.png)

SSH:
```
1. System tab -> Advanced -> Admin Access
2. Secure Shell -> Enable Secure Shell
```
![ssh gui 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20083019.png)

SNMP:
```
1. Services -> SNMP -> Enable the SNMP Daemon and its controls
2. Polling Port: 161
3. You can define the System Location, System Contacts and Read Community String as needed
4. Bind to LAN interface (in this instance it is the pfSense LAN)
```
The Read Community String is essentially a password shared by the server and the device being polled. This will be important later when needing to run the snmpwalk command to return output.

Let's return back to Ubuntu CLI to test Syslog funcationality, SNMP polling, Paramiko and the Python script through SSH connection.
```
tail -f /var/log/pfsense.log
```
![syslog output 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20090011.png)


```
snmpwalk -v2c -c public 192.168.83.100
```
![mibs output 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-29%20185249.png)
![mibs output 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-29%20185400.png)  
  
  
Paramiko and the Python script need to ran in the VENV where pip was installed.
```
source ~/netops-venv/bin/activate
python3 -c "import paramiko; print('test test test')"
python3 python.py
```
Paramiko example output:  
![paramiko 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20081524.png)

python.py output:
![python output 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20091301.png)

---


