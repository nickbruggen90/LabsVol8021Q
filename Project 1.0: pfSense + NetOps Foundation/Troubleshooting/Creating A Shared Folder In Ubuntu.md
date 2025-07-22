### Creating A Shared Folder In Ubuntu
1. Open VM settings in **VMWare Workstation** and locate the `Options tab` at the top
2. Choose `Share Folders` and define the path
![shared folder 1](https://github.com/nickbruggen90/LabsVol8021Q/blob/main/Project%201%3A%20NetOps%20Monitoring/Images/Screenshot%202025-05-31%20075236.png)

Inside Ubuntu we must also mount the shared folder.
```
sudo mkdir -p /mnt/hgfs
sudo vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other
```
If you run into permissions issues accessing the shared folder, you would need to unmount and remount, try:
```
id
sudo umount /mnt/hgfs
sudo mount -t fuse.vmhgfs-fuse .host:/ /mnt/hgfs -o allow_other,uid=1000,gid=1000
```
NOTE: Command *id* will bring up something like this - `uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),...`

---
