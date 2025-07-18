### Manual User Creation
1. Open Active Directory Users and Computers
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
4. b. Here is an example of a standard **Password** parameters:
```
Set temporary password: TempPass123!
✅ Check "User must change password at next logon"
❌ Uncheck "User cannot change password"
❌ Uncheck "Password never expires"
❌ Uncheck "Account is disabled"
```
5. After you apply the **Password** parameters, navigate to the newly created user under the OU it was created under.  
Right-click the user → Properties
7. a. Here is an example of the **General** tab:
```
Description: Regional Sales Manager - Sales
Office: Building A, Floor 2, Room 205
Telephone: (555) 234-5678
Email: michael.rodriguez@test.lab
```
7. b. Here is an example of the **Account** tab:
```
Verify User logon name: michael.rodriguez@testlab.local
Account options: Normal account
Account expires: Never
```
7. c. Here is an example of the **Profile** tab: !!!!!!LINK TO “CREATING A SHARED NETWORK FOLDER”
```
Profile path: \\DC01\Profiles$\michael.rodriguez
Home folder: Connect Z: to \\DC01\Users$\michael.rodriguez
```
7. d. Here is an example of the **Organizational** tab:
```
Title: Regional Sales Manager
Department: Sales
Company: testlab
```
