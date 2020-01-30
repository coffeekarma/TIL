# Analyse network traffic with tcp flow or wireshark

### tcpflow 
```
tcpflow -p -c -i ens160 host lbdshop.prod.ecom.thalia.de | grep -C 30  warenkorb/size
```
### tcpdump to local wireshark 
```
ssh um-haproxyfe1.prod.ecom.thalia.de "sudo tcpdump -U -s0 -i eno16780032 -w - 'dst port 10900'" | wireshark -o http.tcp.port:10900 -k -i -
```

