# Remove unresponsive docker container

As a last resort, to remove containers where `docker kill` does not not work, use the following command to force the docker runtime of the container to shutdown: 

```
ps aux| grep PASTE_ID_HERE | grep -v grep | awk '{print $2}' | xargs kill -9
```


# Finding sub processes 

Sometimes just killing the docker runtime isnt enough because of sub processes which wont get killed. To find these do the following:

1. Find out the docker id of the Container
2. Run following command to show all process ids of running subtasks of the container
```
cat /sys/fs/cgroup/memory/docker/**full-container-id**/tasks
```
