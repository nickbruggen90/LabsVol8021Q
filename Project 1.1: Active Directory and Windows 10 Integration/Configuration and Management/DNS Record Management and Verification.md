### DNS Record Management and Verification
##### Configuration
1. Navigate to *Run → dnsmgmt.msc*
2. In the left column, *DC01 → Forward Lookup Zone → testlab.local*
![dsnmgmt.msc](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20132415.png)
3. Here you can create DNS records (A, AAAA, CNAME, MX)
4. In this instance we will create a DNS A record, which points a FQDN to an IPv4 address.
5. *Right-click → New Host (A or AAAA)*
6. For this demonstration we will make the A record point a file server
```
Name: fileserver
IP Address: 192.168.83.149
✅Check "Create Associated Pointer (PTR) record"
```
![fileserver dns](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20132824.png)

---
##### Verification
1. On the client side, navigate to `cmd`
2. Use the following commands to verify the DNS records are working:
```
nslookup DC01
ping DC01
nslookup testlab.local
```
![verification1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20145523.png)
![verification2](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20145544.png)
![verification3](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201.1%3A%20Active%20Directory%20and%20Windows%2010%20Integration/Images2/Screenshot%202025-07-20%20145616.png)
