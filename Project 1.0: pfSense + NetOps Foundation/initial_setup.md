### pfSense Creation and Initial Configuration
First we will create the pfSense VM with VMWare Workstation. Use the official pfSense CE .iso release. Choose the following configuration for set-up:
```
1. 2 NICs are needed:
    - NIC 1: Bridged
    - NIC 2: Host-Only
2. 2 GB RAM
3. 20 GB storage space
4. 2 processors
```
Once the VM boots up, pfSense will ask some configuration options. The ones you need to pay attention to are:
```
1. Auto UFS
2. MBR partition scheme
```
After the installation and initial bootup, pfSense will prompt you will a numbered menu. You are in the right spot.
