# Analysing the disc usage

Find the 10 largest files / folders: 
```
sudo du -a / | sort -n -r | head -n 10
``` 
For a human readable format:
``` 
du -hsx /* | sort -rh | head -10
``` 
