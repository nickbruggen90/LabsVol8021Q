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


