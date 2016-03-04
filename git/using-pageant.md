# Using pageant with eGit

Using pageant with eGit allows you to hold your private keys in memory so that you can use them whenever you are connecting to your git-server.

Add the user environment variable GIT_SSH and set it to the path of your plink.exe, e.g. "C:\Program Files (x86)\PuTTY\plink.exe".
You probably also need to add your git-server's Host Key to the registry:
```
plink -agent "git-server"
```
