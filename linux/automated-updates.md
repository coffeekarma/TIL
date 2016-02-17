# Automated security updates

Given the track record of the Debian Security team in the last few years, I consider the risks of broken upgrades far less than the benefit of having automatic updates on seldom-visited systems.

To get automated updates running on a Debian system install the unattended-upgrades package:

```
sudo apt-get install unattended-upgrades
```

Add the following lines to /etc/apt/apt.conf:
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Unattended-Upgrade "1";
```
