# Analyse network traffic with tcp flow

```
tcpflow -p -c -i ens160 host lbdshop.prod.ecom.thalia.de | grep -C 30  warenkorb/size
```
