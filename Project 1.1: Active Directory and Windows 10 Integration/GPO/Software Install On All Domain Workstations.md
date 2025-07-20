### Software Install On All Domain Workstations
##### Purpose: Automatically install Adobe Acrobat Reader on all domain workstations (you can replace Adobe with any software, this is an example)  
```
Target: All computers in the Workstations  
OU Type: Computer Configuration (installs regardless of who logs in)  
```
---

1. Create a folder to host the applications. In this instance, we will create `SoftwareDistribution` inside `C:`
2. *Right-click → Properties → Sharing tab*
3. Click `"Advanced Sharing"` button
4. Tick `"Share This Folder"` and choose `Software$` as the share name
5. We will need to add permissions. Click the `"Permissions"` button in the same window as Share This Folder
6. Remove any existing groups or users, and add `"Domain Admins"` with Full Control and `"Domain Users"` with Read-only capabilities
7. Next we need to navigate to **Group Policy Management**. *Run → gpmc.msc* (or locate it in the start menu apps, or search)
8. In this instance we will create a Global GPO. It will be inherited by all child directories underneath it.
9. *Right-click → Create a GPO in this domain, and Link it here*
10. Name it `"Computer Config - Software Installation - Adobe Reader"`. Then you will see it populate under the root domain.
11. *Right-click the newly created GPO → Edit → Action → Properties → Comment tab*. Below is example comment:
```
Automatically installs Adobe Acrobat Reader on all workstations.
Created: [Today's Date]
Target: All computers in Workstations OU
Installation: Computer startup
``` 
12. Pressing `OK` will take you back to the "Computer Config - Software Installation - Adobe Reader" GPO Editor
13. Choose *Computer Configuration → Policies → Software Settings → Right-click Software Installation → New → Package*
14. In this simulation we will use File location: `\\DC01\Software$\AdobeReader.msi`, in your lab or production choose the desired executable
