### Troubleshooting: Client Isn’t Receiving Group Policies Properly
If GPOs are not updating to the client in the Active Directory domain, you try the following for a quick resolution:
In a lab environment, or where you can easily access the client PC:
1. Make sure the client PC is correct. In cmd run -
```
whoami
```
2. Verify it is accessing the correct domain controller, and is populating the correct information for that controller. In cmd run -
```
nltest /dsgetdc:testlab.local
```
