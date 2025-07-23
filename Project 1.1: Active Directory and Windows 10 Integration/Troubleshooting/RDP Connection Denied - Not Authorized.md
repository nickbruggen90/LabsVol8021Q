### RDP Connection Denied - Not Authorized
##### Purpose: To authorize user accounts to allow RDP connections. We are working from the domain controller in this walkthrough.
![example error](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-23%20113753.png)

---
1. In PowerShell remote into the CLI of workstation, in this instance it is "CLIENT01"  
`Enter-PSSession -ComputerName CLIENT01`  
If you get DNS resolution issues [Refer to this DNS Walkthrough here].
2. We need to allow this workstation RDP access and enable RDP firewall rule:
```
Set-ItemProperty -Path 'HKLM:\System\CurrentControlSet\Control\Terminal Server' -Name "fDenyTSConnections" -Value 0
Enable-NetFirewallRule -DisplayGroup "Remote Desktop"
```
3. This workstation also needs to be a part of the group that is permitted RDP access:
```
Get-LocalGroupMember -Group "Remote Desktop Users"
Add-LocalGroupMember -Group "Remote Desktop Users" -Member "testlab\kenny.rogers.it"
net localgroup "Remote Desktop Users" "testlab\kenny.rogers.it" /add
```
4. Now we need to add a domain-wide GPO. [Refer here for the step-by-step GPO setup]. Make sure to `gpupdate /force` from CLIENT01.
