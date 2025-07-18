### Account Lockout Policy
1. Within Group Policy Management under testlab.local right click Group Policy Objects.
2. Choose "new" and name it "Account Lockout Policy"
![group policy management](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20194312.png)
3. Right click on the newly created GPO and "Edit". Here you can adjust a wide variety of account settings and permissiongs. In this walkthrough we will look at the account lockout options.
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
5. Now you must link the GPO to the domain. Return to Group Policy Management. Right click on testlab.local and Link and Existing GPO.
![link GPO](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20194626.png)  
6. Ensure the GPO is "Enforced" and "Enabled", and "Domain Users" is added to Security Filtering.
```
a. Right-click on the GPO "Account Lockout Policy" you just linked under testlab.local
b. Choose Enforced and Link Enabled
```
![enforced/enabled](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20194819.png)
