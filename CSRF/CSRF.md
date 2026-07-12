# Cross-Site Request Forgery (CSRF)

## 📖 What is CSRF?
<div align=justify>
Cross-Site Request Forgery (CSRF) is a web application vulnerability that allows an attacker to force an authenticated user into performing actions they never intended to perform.
<br><br>
The attack works because browsers automatically include cookies and other authentication information when sending requests to a website. If an application relies only on these credentials to verify a request, it cannot distinguish between a legitimate request made by the user and one crafted by an attacker.
</div>

## 🧪 Demonstration

### Normal Request

> 📷 **Screenshot:** Legitimate password change or vulnerable action.

![DVWA CSRF Before Injection](CSRF/assets/CSRF_Normal.png)
<br><br>
The user performs an action normally while logged into the application.


### Forged Request

> 📷 **Screenshot:** Malicious HTML page containing the forged request.

![DVWA CSRF While Injection](CSRF/assets/CSRF_Code.png)
<br><br>
The attacker creates a webpage that automatically sends a request to the vulnerable application.


### Victim Visits the Malicious Page

> 📷 **Screenshot:** Victim opening the malicious page.

![DVWA CSRF After Injection](CSRF/assets/CSRF_Action.png)
<br><br>
When the victim visits the attacker's webpage while still logged into the vulnerable application, the browser automatically includes the victim's session cookie with the request.


### Successful Request

> 📷 **Screenshot:** Successful password change or successful vulnerable action.

![DVWA CSRF Before Injection](CSRF/assets/CSRF_Injected.png)
<br><br>
Since the request contains the victim's valid session cookie, the application processes it as a legitimate request.


## 🔍 Why Does CSRF Work?

<div align=justify>
Browsers automatically attach cookies associated with a website whenever a request is sent to that website.

The vulnerable application assumes that every request containing a valid session cookie was intentionally made by the authenticated user. Since the forged request also includes the same session cookie, the server cannot distinguish it from a legitimate request and processes it successfully.
</div>

For a CSRF attack to succeed, the following conditions are usually required:

- The victim must be authenticated.
- The application must rely only on session cookies for authentication.
- The vulnerable request must not require additional verification, such as a CSRF token.
