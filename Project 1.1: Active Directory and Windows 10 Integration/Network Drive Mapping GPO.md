### Network Drive Mapping
1. Within Group Policy Management under testlab.local right click Group Policy Objects.
2. Choose "new" and name it "Network Drive Mappings"
![group policy management](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20180955.png)
3. Right click on the newly created GPO and "Edit". Here you can adjust a wide variety of account settings and permissiongs. In this walkthrough we will set up a shared network drive.
```
a. User Configuration ->
b. Preferences ->
c. Windows Settings ->
d. Drive Maps ->
e. right click on the empty space ->
f. New -> Mapped Drives
```
![new mapped drive](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20122324.png)
4. Next you will see a configuration pane. Fill out the following:
```
Action: Create
Location: \\DC01\Wallpapers
Reconnect: checked
Drive Letter: Z:
Label As: Company Wallpapers
toggle both "Show This Drive"
```
![new drive creation](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20180805.png)
5. Now you must link the GPO to the domain. Return to Group Policy Management. Right click on testlab.local and Link and Existing GPO.
![link GPO](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20181141.png)  
6. Confirm Z: is accessible on CLIENT01.  
![confirmation of Z:](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20124816.png)
