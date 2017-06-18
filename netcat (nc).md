# Netcat - Redirect file or header to a port
UDP redirect file to port 37
nc -v -u xxx.xxx.xxx.xxx 37 < ./file.txt
TCP redirect file to port 80
nc xxx.xxx.xxx.xxx 80 < ./file.txt
TCP redirect post-headers to port 80
nc xxx.xxx.xxx.xxx 80 < ./post-headers.txt

# Netcat - Quick Listner
Start Listener
nc -l 3333
Connect to Listener
nc xxx.xxx.xxx.xxx 3333
