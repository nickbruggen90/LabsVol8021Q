### Password Reset Procedures
#### When to Use:  
```
Individual password reset requests  
Forgotten password scenarios  
Urgent access needs  
User reports unable to log in
```
---

1. Navigate to **Active Directory Users and Computers**. One option is to navigate to run then input `dsa.msc`
![ADUC](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20090405.png)
2. Browse the OUs in the left column to find the user. Alternatively you can use the `"Find Users, Contacts and Groups"` search option.
3. *Right-click → Reset Password*  
![password reset](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-19%20123208.png)
#### Example Password Parameters
```
Enter new temporary password: TempReset123!
✅ Check "User must change password at next logon"
✅ Check "Unlock the user's account" (if applicable)
```
