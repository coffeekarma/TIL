# Remove unresponsive docker container

As a last resort, to remove containers where `docker kill` does not not work, use the following command to force the container shutdown: 

```
ps aux| grep PASTE_ID_HERE | grep -v grep | awk '{print $2}' | xargs kill -9
```