Crack AES Zipped files
---------------------

```bash
#!/bin/bash
input="/path/to/your/password/list/rockyou.txt.clean"
while IFS= read -r var
do
7z e ./your-aes-zipped-file-here.zip -p$var
find . -maxdepth 1 -size 0c -exec rm {} \;
done < "$input"
```
