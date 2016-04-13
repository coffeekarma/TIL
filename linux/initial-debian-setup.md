# Initial debian setup

Setup steps after login into a new debian root server / VM for the first time.

  - edit /etc/hostname -> configure hostname
  - edit /etc/network/interfaces -> configure network, ip, gateway
  - configure proxy in /etc/apt/apt.conf (eg. http://domain\user:password@proxy:80)
  - apt-get install ssh sudo su 
  - vim (editor of your choice) /etc/sudoers.d/sudopolicy :
   ```bash
   # Cmnd alias specification
   Cmnd_Alias     SU = /usr/bin/su, /bin/su
   Cmnd_Alias     SHELLS = /usr/bin/sh, /usr/bin/csh, /usr/bin/ksh, \
                                   /usr/local/bin/tcsh, /usr/bin/rsh, \
                                   /usr/local/bin/zsh
    
   #no passwd for all users because of ssh-certificate-auth
   %sudo   ALL=(ALL:ALL)NOPASSWD:ALL,!SU,!SHELLS
   ```
  - add users (write a reusable script): 
   ```bash
   adduser --disabled-password --shell /bin/bash USERNAME
   adduser USERNAME sudo
   mkdir /home/USERNAME/.ssh
   ##add key
   editor /home/USERNAME/.ssh/authorized_keys
   chmod 600 /home/USERNAME/.ssh/authorized_keys
   chmod 700 /home/USERNAME/.ssh
   chown -hR USERNAME:USERNAME /home/USERNAME/.ssh
   ```
  
  - edit /etc/ssh/sshd_config: "PasswordAuthentication no“, "PermitRootLogin no"
  - login with user 
  - sudo passwd root -> change root password
  

