### Manual User Creation
1. Open Active Directory Users and Computers
[ADUC pic]
2. In this instance we will create a new user in Sales. You can find the repo on OU Creation !!!!!!here.
3. Right click the Sales OU → New → User  
4. a. Here is an example of the **New User** parameters:
```
First name: Michael
Initials: J 
Last name: Rodriguez 
Full name: Michael J Rodriguez 
User logon name: michael.rodriguez@testlab.local 
User logon name (pre-Windows 2000): TESTLAB\michael.rodriguez
```
![new user pic](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20095427.png)  
4. b. Here is an example of a standard **Password** parameters:
```
Set temporary password: TempPass123!
✅ Check "User must change password at next logon"
❌ Uncheck "User cannot change password"
❌ Uncheck "Password never expires"
❌ Uncheck "Account is disabled"
```
![passwords](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20095443.png)  
5. After you apply the **Password** parameters, navigate to the newly created user under the OU it was created under.  
Right-click the user → Properties  
5. a. Here is an example of the **General** tab:
```
Description: Regional Sales Manager - Sales
Office: Building A, Floor 2, Room 205
Telephone: (555) 234-5678
Email: michael.rodriguez@test.lab
```
![general tab](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20095536.png)  
5. b. Here is an example of the **Account** tab:
```
Verify User logon name: michael.rodriguez@testlab.local
Account options: Normal account
Account expires: Never
```
![account tab](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20095701.png)  
5. c. Here is an example of the **Profile** tab:  
*If you get an error that looks like [this](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20110507.png), then follow [this troubleshooting guide](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Quickguide%3A%20Network%20Share%20Creation%20%26%20Troubleshooting)*
```
Profile path: \\DC01\Profiles$\michael.rodriguez
Home folder: Connect Z: to \\DC01\Users$\michael.rodriguez
```
![profile tab](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20102423.png)  
5. d. Here is an example of the **Organizational** tab:
```
Title: Regional Sales Manager
Department: Sales
Company: testlab
```
