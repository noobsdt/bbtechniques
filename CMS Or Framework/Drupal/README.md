## Access hidden sign-up page
```
/user/register
```

## Find hidden pages
Fuzz with Burp Suite Intruder (or any other similar tool) on ‘/node/$’ where ‘$’ is a number (from 1 to 500).
Chances are that we will find hidden pages (test, dev) which are not referenced by the search engines.
For example:
```
https://target.com/node/1
https://target.com/node/2
https://target.com/node/3
…
https://target.com/node/499
https://target.com/node/500
```
