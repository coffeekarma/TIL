# Resize a logical volume 
(written for ext4 filesystems)

If the volume to resize is an important system directory like / or /var/ boot with a live CD:
```bash
vgchange -a y
```  
Otherwise boot like usual and unmount the volume: 
```bash
umount /dev/mapper/volumename
```  

Following steps apply for both variants:
```bash
e2fsck -fy /dev/mapper/volumename
resize2fs -p /dev/mapper/volumename 40G
lvreduce -L 40G /dev/mapper/volumename
e2fsck -fy /dev/mapper/volumename 

lvextend -l +100%FREE /dev/mapper/volumenametoextend
```
