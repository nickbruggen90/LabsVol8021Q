### Quickguide: Network Share Creation & Troubleshooting
#### Overview
Quick troubleshooting guide for creating and fixing network shares in Active Directory environments. Covers the most common issues when setting up home directories, shared drives, and network resources.

---
#### Share Creation Process
1. Navigate to desired shared folder location. In this instance it will be C:
2. Create the folder. In this tutorial we will use the Users folder as an example. (Note: full path: *C:\Users*)
3. Right-click on the new folder (or in this case Users) → Properties
4. Sharing tab → Advanced Sharing
5. ✅ Check "Share this folder"
6. Choose the share name as: Users$ ($ makes it hidden)
7. Choose Permissions
8. Add the appropriate users or accounts. In this instance we will add all the Administrator accounts. You can navigate to an employee inside of the Users folder, follow this step but add the employee as well for instance.
9. Choose full change, change, read
[permissions](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20191422.png)
10. Apply, ok and confirm all changes

---
