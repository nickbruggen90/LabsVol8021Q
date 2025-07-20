### User Config - Sales Department Restrictions
##### Purpose: Configure user environment and restrictions for Sales department
```
Target: Users in Company > Users > Sales OU (kenny.rogers, michael.rodriguez)
Type: User Configuration policy
```
---

##### GPO Creation and Initial Settings:
```
Disable Control Panel access (prevent system changes)
Hide specific drives (restrict access to system drives)
Set folder redirection for Documents folder
Configure Start menu restrictions
```
---

1. Navigate to Group Policy Management. Run → gpmc.msc
2. Inside `Group Policy Objects` OU, *Right-click → New
3. For this demonstration we will name it "User Config - Sales Department Restrictions" → click OK
4. Back inside Group Policy Management, *Right-click newly created GPO → Edit → Action → Properties → Comment tab
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
6.

