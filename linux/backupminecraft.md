# Minecraft backup script
```
#!/bin/bash
date=$(date +%F)
filename=${date}_backup

#stop server
tmux send -t 0 "say Server wird für das tägliche Backup in 60 Sekunden heruntergefahren" c-M\;
sleep 60
tmux send -t 0 "stop" c-M\;
sleep 20 

#backup 
rsync -arv --exclude 'plugins/dynmap' /root/minecraft /root/backup/$filename
tar -zcvf /root/backup/${filename}.tar.gz /root/backup/$filename
rm -rf /root/backup/$filename

# start server again
tmux send -t 0 "./launch.sh" c-M\;

# remove files older than 7 days
find /root/backup/ -type f -mtime +7 -exec rm -f {} \;
```
