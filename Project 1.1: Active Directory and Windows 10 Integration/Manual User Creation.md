### Manual User Creation
1. Open Active Directory Users and Computers
2. In this instance we will create a new user in Sales. You can find the repo on OU Creation here.
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
4. b. Here is an example of a standard **Password** parameters:
```
Set temporary password: TempPass123!
✅ Check "User must change password at next logon"
❌ Uncheck "User cannot change password"
❌ Uncheck "Password never expires"
❌ Uncheck "Account is disabled"
```
5. After you apply the **Password** parameters, navigate to the newly created user under the OU it was created under. Right-click the user → Properties
6. a. Here is an example of the **General** tab:
