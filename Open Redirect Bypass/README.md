### 1. Common bypass techniques
```
http:http:evil.com
http:/evil%252ecom
///www.x.com@evil.com
```

### 2. If server accept subdomain
```
-> Use null byte character
google.com%00.target.com
google.com%FF.target.com
```
```
-> Use unrecogniged character (japanese, turkish etc. character)
google.com[unrecogniged_character].target.com
```

### 3. Convert any IP to decimal, hexadecimal or octal.
```
-> Decimal
/path?redirect=//2130706433
```
```
-> Hexadecimal
/path?redirect=//0x7f000001
```

Try dot or dotless both pattern.
