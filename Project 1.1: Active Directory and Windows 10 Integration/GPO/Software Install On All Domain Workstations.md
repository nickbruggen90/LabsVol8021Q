### Software Install On All Domain Workstations
##### Purpose: Automatically install Adobe Acrobat Reader on all domain workstations (you can replace Adobe with any software, this is an example)  
```
Target: All computers in the Workstations  
OU Type: Computer Configuration (installs regardless of who logs in)  
```
---

1. Create a folder to host the applications. In this instance, we will create SoftwareDistribution inside C:
2. Right-click → Properties → Sharing tab
3. Click "Advanced Sharing" button
4. Tick "Share This Folder" and choose Software$ as the share name
5. We will need to add permissions. Click the "Permissions" button in the same window as Share This Folder
6. Remove any existing groups or users, and add "Domain Admins" with Full Control and "Domain Users" with Read-only capabilities
7. 
