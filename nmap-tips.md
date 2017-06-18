Parse IP addresses from nmap and send output to tools
-----------------
Note: Could use almost any variable for "/https/" - run up to the awk command to find a good variable
```
nmap -PN -p 443 --open -oG - xxx.xxx.xxx.xxx/24 | awk '/https/{print $2}' | while read IP; do ./testssl.sh $IP | aha > $IP-ssl-audit.html ; done
```

