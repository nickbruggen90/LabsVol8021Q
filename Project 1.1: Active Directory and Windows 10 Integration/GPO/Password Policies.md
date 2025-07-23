### Modifying Password Policies
1. Navigate to **Group Policy Management**. Locate root domain, in this instance testlab.local. *Right-click → Group Policy Objects*
2. Choose ` "New" ` and name it ` "Domain Security Policies" `
![group policy management](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20205013.png)
![group policy object](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20065106.png)

3. *Right-click on the newly created GPO  → Edit*. Here you can adjust a wide variety of account settings and permissions. In this walkthrough we will edit the password settings.
![password settings](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20205154.png)


These are the password fields you can modify:
```
Enforce password history
Maximum password age
Minimum password age
Minimum password length
Minimum password length audit
Password must meet complexity requirements
Relax minimum password length limits
Store passwords using reversible encryption
```
4. Now you must link the GPO to the domain. Return to Group Policy Management. *Right-click → testlab.local → Link an Existing GPO*
![link GPO](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20205313.png)
