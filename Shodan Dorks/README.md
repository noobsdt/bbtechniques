### Find Spring Boot Servers
```
org:YOUR_TARGET http.favicon.hash:116323821
```

Spring Boot is an open source Java-based framework used to build stand-alone spring applications based on the concepts of micro services.

Spring Boot Actuator is a mechanism of interacting with them using a web interface. They are typically mapped to URL such as:
```
- https://target.com/env
- https://target.com/heapdump
- etc.
```

### Find RocketMQ Consoles
```
org:target.com http.title:rocketmq-console
```

From the exposed RocketMQ consoles we can for example find out:
```
- Additional hostnames and subdomains
- Internal IP addresses
- Log file locations
- Version details
- etc.
```
