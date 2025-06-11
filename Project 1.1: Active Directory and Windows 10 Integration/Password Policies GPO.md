### Modifying Password Policies
1. Within Group Policy Management under testlab.local right click Group Policy Objects.
2. Choose "New" and name it "Domain Security Policies"
![group policy management](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20205013.png)
![group policy object](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20065106.png)

4. Here you can find all the password setting you can adjust.
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
4. Now you must link the GPO to the domain.
![link GPO](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-10%20205313.png)
