### Account Lockout Policy
1. Navigate to Group Policy Management
2. Locate root domain, in this instance it is testlab.local. Right-click → Create a GPO in this domain, and Link it here → name it "Account Lockout Policy"  
![group policy management](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20194312.png)
3. *Right click on the newly created GPO → Edit*. Here you can adjust a wide variety of account settings and permissions. In this walkthrough we will look at the account lockout options
```
a. Computer Configurations → 
b. Policies → 
c. Windows Settings → 
d. Security Settings → 
e. Account Policies → 
f. Account Lockout Policies
```
4. Edit the following fields:
```
Account Lockout Duration: 30 minutes
Account Lockout Threshold: 5 Invalid Logon Attempts
Reset Account Lockout Counter After: 30 minutes
```
![account lockout criteria](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20194543.png)  
5. Now you must link the GPO to the domain. Return to Group Policy Management. *Right-click → testlab.local → Link an Existing GPO
![link GPO](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20194626.png)  
6. Ensure the GPO is "Enforced" and "Enabled", and "Domain Users" is added to Security Filtering
```
a. *Right-click on the GPO "Account Lockout Policy" → tick Enforced and Link Enabled*
```
![enforced/enabled](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20194819.png)
