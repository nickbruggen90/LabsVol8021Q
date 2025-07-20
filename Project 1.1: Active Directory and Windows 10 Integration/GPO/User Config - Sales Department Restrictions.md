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
#### GPO Configuration
##### Control Panel Restrictions
1. Navigate to **Group Policy Management**, *Right-click GPO → Edit*
2. In the left panel, *Computer Configuration → Policies → Administrative Templates → Control Panel*
3. *Double-click "Prohibit access to Control Panel and PC settings" → Enable → OK*
##### Configure Drive Restrictions
1. Navigate to **Group Policy Management**, *Right-click GPO → Edit
2. In the left panel, *Computer Configuration → Policies → Administrative Templates → Windows Components → File Explorer*
3. *Double-click "Hide these specified drives in My Computer" → Enable → Choose combination: Restrict C and D drives only → OK* (NOTE: Choosing "Restrict A, B, C and D drives" option is essentially the same thing, as A: and B: drives are usually not in operation.)
4. 

