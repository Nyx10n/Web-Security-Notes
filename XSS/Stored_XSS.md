# Stored Cross-Site Scripting (Stored XSS)

## 📖 What is Stored XSS?
<div align=justify>
Stored XSS is a type of Cross-Site Scripting (XSS) vulnerability in which attacker-controlled input is stored by the web application and later included in its HTTP response without being safely handled. Instead of treating the stored input as plain text, the browser interprets it as HTML. If the stored HTML contains executable JavaScript, the browser executes it whenever the affected page is loaded.
<br><br>
The malicious payload remains stored until it is removed, allowing it to execute every time a user visits the vulnerable page.
</div>

## 🧪 Demonstration

### Normal Input

> 📷 **Screenshot:** DVWA Stored XSS page before injecting the payload.

![DVWA Stored XSS Before Injection](/XSS/assets/Stored_XSS%20Normal.png)
<br><br>
The application stores and displays the user input normally.


### Injecting the Payload

Payload used:

```html
<script>alert(1)</script>
```

> 📷 **Screenshot:** Alert box after loading the page.

![DVWA Stored XSS After Injection](/XSS/assets/Stored_XSS%20Injected.png)
<br><br>
When the payload is submitted, the application stores it. Whenever the page is loaded, the stored payload is included in the application's HTTP response. Since the browser parses the response as HTML, it encounters the `<script>` tag and executes the JavaScript code inside it.


## 🔍 Looking at the Page Source

> 📷 **Screenshot:** Page source with the stored payload highlighted.

![DVWA Stored XSS Before Injection](/XSS/assets/Stored_XSS%20Page%20Source.png)
<br><br>
The highlighted section shows where the application included the stored payload in the HTML response. Because the payload was returned as HTML instead of plain text, the browser treated it as part of the webpage and executed the JavaScript contained inside the `<script>` tag.
