### DNS Record Management
1. Navigate to *Run → dnsmgmt.msc*
2. In the left column, *DC01 → Forward Lookup Zone → testlab.local
3. Here you can create DNS records (A, AAAA, CNAME, MX)
4. In this instance we will create a DNS A record, which points a FQDN to an IPv4 address.
5. *Right-click → New Host (A or AAAA)*
6. For this demonstration we will make the A record point a file server
```
Name: fileserver
IP Address: 192.168.83.149
✅Check "Create Associated Pointer (PTR) record"
```
