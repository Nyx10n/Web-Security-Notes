# DOM-Based Cross-Site Scripting (DOM XSS)

## 📖 What is DOM XSS?
<div align=justify>
DOM-Based Cross-Site Scripting (DOM XSS) is a type of Cross-Site Scripting (XSS) vulnerability in which the vulnerability exists entirely in the browser. Instead of the server returning malicious HTML, the webpage's JavaScript reads attacker-controlled input and inserts it into the page in an unsafe manner. If the inserted content contains executable JavaScript, the browser executes it.
<br><br>
Unlike Reflected and Stored XSS, where the server returns the malicious payload in its HTTP response, DOM XSS does not require the server to send malicious HTML. The server may return a completely normal page, but the page's own JavaScript creates the vulnerability by inserting attacker-controlled input into the DOM.
<br><br>
  
**Think of it this way:** In Reflected and Stored XSS, the **server** is responsible for sending the malicious content to the browser. In DOM XSS, the server sends a normal page—the browser's own JavaScript takes the attacker-controlled input and unknowingly inserts it into the webpage, creating the vulnerability.
</div>

## 🧠 Source and Sink

To understand DOM XSS, you first need to understand **Source** and **Sink**.

A **Source** is any location from which JavaScript reads attacker-controlled data. Some common sources include:

- `location.search`
- `location.hash`
- `document.URL`
- `document.referrer`
- `window.name`

For example:

```javascript
const input = location.hash;
```

Here, `location.hash` is the **source** because its value comes directly from the URL and can be controlled by an attacker.

A **Sink** is a JavaScript function or property that inserts data into the webpage. Some common sinks include:

- `innerHTML`
- `outerHTML`
- `document.write()`
- `insertAdjacentHTML()`

For example:

```javascript
document.getElementById("output").innerHTML = input;
```

Here, `innerHTML` is the **sink** because it inserts the data into the webpage as HTML.

A DOM XSS vulnerability occurs when attacker-controlled data from a **Source** reaches an unsafe **Sink** without being safely handled.


## 🧪 Demonstration

> 📷 **Screenshot:** DVWA DOM XSS page before injecting the payload.

![DVWA DOM-Based XSS Before Injection](/XSS/assets/DOM-Based%20Normal.png)

<br><br>
The page behaves normally before any malicious input is provided.


> 📷 **Screenshot:** Payload injected into the vulnerable page.

![DVWA DOM-Based XSS Before Injection](/XSS/assets/DOM-Based%20Injected.png)

<br><br>
## 🔍 Vulnerable JavaScript

> 📷 **Screenshot:** Vulnerable JavaScript highlighted.

![DVWA DOM-Based XSS Page Source](/XSS/assets/DOM-Based%20Page%20Source.png)

<br><br>
<div align=justify>
The highlighted JavaScript reads attacker-controlled input from a **Source** and passes it to an unsafe **Sink**. Because the input is inserted into the DOM without being safely handled, the browser treats it as part of the webpage and executes the malicious JavaScript.
</div>
<br>

> **Note:** The exact Source, Sink, and payload used in this demonstration are specific to DVWA and will be explained using the highlighted JavaScript shown above.
