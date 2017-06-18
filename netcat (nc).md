Netcat - Redirect file or HTTP header to a port
-------------------------------------------
UDP redirect file to port 37
```
nc -v -u xxx.xxx.xxx.xxx 37 < ./file.txt
```
TCP redirect file to port 80
```
nc xxx.xxx.xxx.xxx 80 < ./file.txt
```
TCP redirect post-headers to port 80
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
