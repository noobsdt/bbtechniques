# 2FA Bypass Techniques

### Brute Force
### Password Reset/Email Change(2FA Disable)
```
- Assuming that you are able to perform email change or password reset for the victim user or make victim user do it by any means possible.
- 2FA is disabled after the email is changed or password is reset. This could
be an issue for some organizations. However, depends on case by case basis.
```

### Missing 2FA Code Integrity Validation
```
- Request a 2FA code from Attacker Account and use it for Victim Account.
```

### Direct Access
```
- Directly Navigate to the page which comes after 2FA or any other authenticated page of the application.
```

### 2FA Code Leakage in Response
```
- Request for 2FA code and capture Response of the Request.
- See the Response of this request and analyze if the 2FA Code is leaked.
```

### Response Manipulation
```
- Check Response of the 2FA Request.
- If you Observe “Success”:false
- Change this to “Success”:true and see if it bypass the 2FA
```

### Status Code Manipulation
```
- Change the Response Status Code to “200 OK” and see if it bypass the 2FA
- If the Response Status Code is 4XX like 401, 402, etc.
```

### 2FA Code Reusability
```
- Request a 2FA code and use it
- Also, try requesting multiple 2FA codes and see if previously requested Codes expire or not when a new code is requested
- Also, try to re-use the previously used code after long time duration say 1 day or more. That will be an potential issue as 1 day is enough duration to crack and guess a 6-digit 2FA code.
- Now, Re-use the 2FA code and if it is used successfully that’s an issue.
```

### 2FA Disable via CSRF Attack
```
- Navigate to 2FA Page and Click on Disable and capture this request with Burp Suite & Generate a CSRF PoC
- Send this PoC to the victim user and check if CSRF happens successfully and removes the 2FA from victim account.
- Also check if there is any authentication confirmation such as password or 2FA code required before disabling 2FA
```

### 2FA Disable via ClickJacking Attack
```
- Try to Iframe the page where the application allows a user to disable 2FA
- If Iframe is successful, try to perform a social engineering attack to manipulate victim to fall in your trap.
```

### Backup Code Abuse
```
- Apply same techniques used on 2FA such as Response/Status Code Manipulation, Brute-force, etc. to bypass Backup Codes and disable/reset 2FA.
```

### Enabling 2FA Doesn’t Expire Previous Session
```
- Login to the application in two different browsers and enable 2FA from 1st session.
- Use 2nd session and if it is not expired, it could be an issue if there is an insufficient session expiration issue. In this scenario if an attacker hijacks an active session before 2FA, it is possible to carry out all functions without a need for 2FA
```
### 2FA Refer Check Bypass
```
- Directly Navigate to the page which comes after 2FA or any other authenticated page of the application.
- If there is no success, change the refer header to the 2FA page URL. This may fool application to pretend as if the request came after satisfying 2FA Condition.
```

### JS File Analysis
```
- Rare but some JS Files may contain info about the 2FA Code.
```

### Bypass 2FA with Null or 000000
```
- Enter the code 000000 or null to bypass 2FA protection.
```
