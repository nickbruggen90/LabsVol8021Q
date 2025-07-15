### Troubleshooting: Common Drive Mapping Issues
Problem: GPO configured but drive not mapping?
1. Verify GPO is applied on CLIENT01. Using the commands below, you will see "Network Drive Mappings", and that signifies the policy is applied. If you do not, try these following troubleshooting steps.
```
gpupdate /force
gpresult /r
```
![gpresult output](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20125147.png)  
2. Verify the folder is present and viewable. In cmd run:
```
dir \\DC01\Wallpapers
```
![dir output](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20124224.png)  
2.1. Alternatively, you can run the Powershell command:
```
Get-WmiObject -Class Win32_LogicalDisk | Where-Object {$_.DriveType -eq 4}
```
![powershell output](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20125106.png)  
2.2. As a third option, you can run the findstring command inside cmd:
```
gpresult /r | findstr -i "drive"
```
![gpresults findstr output](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20125225.png)  
3. Inside DC01 confirm the folder is being shared with the right settings:
```
a. Navigate to This PC ->
b. Right click on Wallpapers folder ->
c. Advanced Sharing button ->
d. Check "Share This Folder" -> click Permissions
e. Add -> Domain Users -> Apply
```
![shared folder confirmation](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20124345.png)
4. The best way to verify the GPOs are applied on CLIENT01 via DC01 would be to use the Group Policy Results Wizard.
```
a. Inside Group Policy Management, locate Group Policy Results at the bottom
b. Right-click -> Group Policy Results Wizard
c. Choose "Another Computer" and input: testlab\CLIENT01
d. In the "User Selection" window choose testlab\jsmith
c. Then it will print out a comprehensive report of the GPOs and policies for jsmith on CLIENT01
```
![group policy wizard 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20125724.png)
![group policy wizard 2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20125734.png)
![group policy wizard 3](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20125743.png)
![group policy output](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images/Screenshot%202025-06-11%20125855.png)
