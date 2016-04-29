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
e2fsck -fy /dev/mapper/volumenametoshrink
resize2fs -p /dev/mapper/volumenametoshrink 40G
lvreduce -L 40G /dev/mapper/volumenametoshrink
e2fsck -fy /dev/mapper/volumenametoshrink

lvextend -l +100%FREE /dev/mapper/volumenametoextend
resize2fs -p /dev/mapper/volumenametoextend
```
