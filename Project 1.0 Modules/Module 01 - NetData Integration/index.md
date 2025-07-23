### Module Overview
`This guide documents the complete implementation of NetData Cloud monitoring across a multi-device lab environment, transforming from zero monitoring to a centralized cloud-based NMS (Network Management System) monitoring 3+ nodes. We will be using Linux Client 192.168.83.3 as the monitoring workstation.`

---

1. First we will install NetData locally to monitor the NMS station itself. Input the following consecutive commands:
```
sudo apt update && sudo apt upgrade
sudo apt install netdata -y
```
2. NetData has a registered IANA port of `:19999`. After NetData installs, navigate to `http://localhost:19999`.
3. You will be given the choice to sign in or log in anonymously. Logging in anonymously will only give you monitoring of the local machine. You will need to create an account for Windows agent monitoring. The NetData Agent to monitor Windows is only available with their cloud-tier. 
