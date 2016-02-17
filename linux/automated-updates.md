# Automated security updates

Given the track record of the Debian Security team in the last few years, I consider the risks of broken upgrades far less than the benefit of having automatic updates on seldom-visited systems.

To get automated updates running on a Debian system install the unattended-upgrades package:

```
sudo apt-get install unattended-upgrades
```

Add the addresses who should be informed about updates to the configuration:
```
sudo vim /etc/apt/apt.conf.d/50unattended-upgrades

Unattended-Upgrade::Mail "root"; // Add the relevant mail addresses
``` 

To activate run:
```
sudo dpkg-reconfigure -plow unattended-upgrades
```

