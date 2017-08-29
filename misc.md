Windows verify Checksums
---------------------------------------------------------
```bash
certUtil -hashfile pathToFileToCheck [MD2 MD4 MD5 SHA1 SHA256 SHA384 SHA512]

```
DIG Zone Transfer
---------------------------------------------------------
```bash
dig axfr yourdomain.org
```
Extract GIT .pack files
---------------------------------------------------------
```bash
pigz -d -z test.zz
```
Set and unset system proxy settings
---------------------------------------------------------
```bash
# Unsets system wide proxy settings
# because chrome and chromium are too dumb to use there own proxy and would rather use
# the system proxy that screws everything up once it has been enabled.

# Show proxy settings
env | grep proxy

# Bulk set or unset proxy settings
export {http,https,ftp}_proxy="http://127.0.0.1:8080"
unset {http,https,ftp}_proxy
export {HTTP,HTTPS,FTP}_PROXY="http://127.0.0.1:8080"
unset {HTTP,HTTPS,FTP}_PROXY

# Individually set or unset proxy
# to set
export http_proxy='http://127.0.0.1:8080'    
export https_proxy='https://127.0.0.1:8080'

# to unset
unset HTTP_PROXY
unset https_proxy
unset http_proxy
unset HTTPS_PROXY
```

# Windows Verify Checksums

```
