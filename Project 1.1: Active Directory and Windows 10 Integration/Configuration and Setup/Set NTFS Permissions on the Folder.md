### Set NTFS Permissions on the Folder
1. Navigate to the folder storing your users/employees home directory. Use Windows+R and search \\[domain controller name]\[home directory folder]\. To find the hostname, use cmd with the command "hostname".
```
\\DC01\Users$
```
2. Right-click on the user/employee home directory → Security tab
![users$ directory](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20123248.png)  
3. Click Advanced towards the bottom
4. Disable Inheritance (This essentially isolates the folders permissions from the parent directory it's nested in.)
![disable inheritance](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20123330.png)  
![remove inheritance](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20123341.png)  
5. Now we will add the appropriate permissions so only Administrators, the employee themselves, and you can add additional permissions as required.
5. a. Click "Add" → Select a Principal. In this instance we will be working with employee Kenny Rogers.
![kenny rogers select](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20123421.png)  
6. You'll want the employee and Administrator to have full control. As well as applied to "This folder, subfolders and files".
![permissions panel](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-18%20123436.png)  
