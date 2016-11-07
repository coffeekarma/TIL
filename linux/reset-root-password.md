# Reset forgotten root password

1. reboot and hold shift to get into grub menu
2. select a recovery option and press e to edit parameters
3. add init=/bin/sh to kernel line (usually starting with linux ...) 
4. press CTRL-X to boot with the changes
5. remount in write mode: mount -rw -o remount /
6. passwd root -> Change root password
7. reboot again into normal mode

