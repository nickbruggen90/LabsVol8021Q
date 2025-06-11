### Troubleshooting: Client Isn’t Receiving Group Policies Properly (lab and production)
If GPOs are not updating to the client in the Active Directory domain (shown below), try the following troubleshooting steps.
Regardless if your working in a lab environment or production, make sure the user is a part of the security group, and that group is added to the GPO.
![gpresults output](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20095437.png)
![user group verification](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20112029.png)
![group/GPO verification](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20102411.png)

---

#### Lab Troubleshooting:
In a lab environment, or where you can easily access the client PC:
1. Make sure the client PC is correct. In cmd run -
```
whoami
```
![whoami results](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20102455.png)  
2. Verify it is accessing the correct domain controller, and is populating the correct information for that controller. In cmd run -
```
nltest /dsgetdc:testlab.local
```
![nltest results](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20102535.png)  
3. Verify Group Policy Client is "Running" and set to "Automatic". Search for run and type in "services.msc" and look for Group Policy Client.
![services.msc output](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20102619.png)  
4. Return to the domain controller (DC01) and within Group Policy Management ensure the GPO is "Enabled" and "Enforced".
![DC enabled/enforced](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20102731.png)

5. When in a lab environment, you can return to the CLIENT01 PC and force a GPO update and verify the policies were applied in cmd with -
```
gpupdate /force
gpresults /r
```

---

#### Production Troubleshooting:
In production, Active Directory relies on automatic refresh timers. Below are some common time frames for polices:
```
Computer Policies: every 90 minutes, with random 0-30 minute offsets
User Policies: every 90 minutes
Domain Controllers: every 5 minutes
Security Policies: every 16 hours regardless of
```
If you require immediate policy updates, consider the following:
```
a. Within Group Policy Management, some versions allow a right-click and a drop down menu to select "Force Update Remotely"
b. Use the Powershell command: Invoke-GPUpdate -Computer "CLIENT01" -Force
c. SCCM/Intune offers a "Push Policy Update" option
d. Reboot during maintenance hours
c. Remote in and execute gpupdate /force in emergencies
```
![example 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20105101.png)
