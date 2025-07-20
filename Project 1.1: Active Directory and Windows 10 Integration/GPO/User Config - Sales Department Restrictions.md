### User Config - Sales Department Restrictions
##### Purpose: Configure user environment and restrictions for Sales department

```
Target: Users in Company → Users → Sales OU (jackie.brown, michael.rodriguez)
Type: User Configuration policy
```

##### Settings We'll Configure:
```
Disable Control Panel access (prevent system changes)
Hide specific drives (restrict access to system drives)
Set folder redirection for Documents folder
Configure Start menu restrictions
```
---
#### GPO Creation and Initial Settings
1. Navigate to **Group Policy Management**. *Run → gpmc.msc*
2. Inside `Group Policy Objects` OU, *Right-click → New*
3. For this demonstration we will *name it "User Config - Sales Department Restrictions" → click OK*
4. Back inside **Group Policy Management**, *Right-click newly created GPO → Edit → Action → Properties → Comment tab*
5. Here is an example comment. This documents in detail changes, etc for future reference.
```
User environment restrictions and configurations for Sales department.
- Disables Control Panel access
- Hides system drives (C:, D:)
- Redirects Documents to network location
- Restricts Start menu modifications
Created: [Today's Date]
Target: Sales OU users only
Type: User Configuration policy
```
![comment section](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20093844.png)
#### GPO Configuration
##### Control Panel Restrictions
1. Navigate to **Group Policy Management**, *Right-click GPO → Edit*
2. In the left panel, *Computer Configuration → Policies → Administrative Templates → Control Panel*
3. *Double-click "Prohibit access to Control Panel and PC settings" → Enable → OK*
![GPO1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20094011.png)
![GPO2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20094047.png)

##### Configure Drive Restrictions
1. Navigate to **Group Policy Management**, *Right-click GPO → Edit*
2. In the left panel, *Computer Configuration → Policies → Administrative Templates → Windows Components → File Explorer*
3. *Double-click "Hide these specified drives in My Computer" → Enable → Choose combination: Restrict C and D drives only → OK* (NOTE: Choosing "Restrict A, B, C and D drives" option is essentially the same thing, as A: and B: drives are usually not in operation.)
![GPO3](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20094502.png)
![GPO4](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20094726.png)
##### Configure Start Menu Restrictions
1. Navigate to **Group Policy Management**, *Right-click GPO → Edit*
2. In the left panel, *Computer Configuration → Policies → Administrative Templates → Start Menu and Task Bar*
3. *Double-click "Prevent changes to Task Bar and Start Menu Settings" → Enable → OK*
---
#### Link to OU
1. Navigate to **Group Policy Management**
2. *Right-click `Sales` OU → Link an Existing GPO*
3. Select the GPO. In this instance it is "User Config - Sales Department Restrictions" then "OK"
