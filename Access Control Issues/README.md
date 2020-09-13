#### Sensitive Files Access
```
http://sub.target.com/web/admin/ --> 302 Redirect -> Main domain
http://sub.target.com/web/aDmiN/ --> 200 Ok -> Admin login page
http://sub.target.com/web/aDmiN/FUZZ --> Critical Sensitive Files
```
