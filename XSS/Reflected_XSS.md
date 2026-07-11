# Reflected Cross-Site Scripting (Reflected XSS)

## 📖 What is Reflected XSS?
<div align=justify>
Reflected XSS is a type of Cross-Site Scripting (XSS) vulnerability in which attacker-controlled input is immediately reflected back by the web application in its HTTP response without being safely handled. Instead of treating the input as plain text, the browser interprets it as HTML. If the reflected HTML contains executable JavaScript, the browser executes it.
<br><br>
The payload is returned as part of the application's response and is executed immediately when the vulnerable page is loaded.
</div>

## 🧪 Demonstration

### Normal Input

> 📷 **Screenshot:** DVWA page before injecting the payload.

![DVWA Reflected XSS Before Injection](/XSS/assets/Reflected_XSS%20Normal.png)
<br><br>
The application displays the user input normally.

### Injecting the Payload

Payload used:

```html
<script>alert(1)</script>
```
> 📷 **Screenshot:** Alert box after successful execution.

![DVWA Reflected XSS Before Injection](/XSS/assets/Reflected_XSS%20Injected.png)
<br><br>
When the payload is submitted, the application returns it in the HTTP response without safely handling it. The browser parses the response as HTML, encounters the `<script>` tag, and executes the JavaScript code inside it, resulting in the alert box being displayed.

## 🔍 Looking at the Page Source

> 📷 **Screenshot:** Page source with the reflected payload highlighted.

![DVWA Reflected XSS Before Injection](/XSS/assets/Reflected_XSS%20Page%20Source.png)
<br><br>
The highlighted section shows where the application inserted the user-controlled input into the HTML response. Because the payload was returned as HTML instead of plain text, the browser treated it as part of the webpage and executed the JavaScript contained inside the `<script>` tag.
