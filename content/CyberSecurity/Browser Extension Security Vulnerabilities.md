TODO: https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP
TODO: CSP CORS CORP

https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html



## 1. Permissions Overreach[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#1-permissions-overreach "Permanent link")

An extension with broad permissions can access all tabs and browsing data. If the extension is compromised, an attacker can capture sensitive information from any website the user visits, including passwords and personal data.

## 2. Data Leakage[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#2-data-leakage "Permanent link")

An extension sending the URLs of all visited pages to a remote server can inadvertently leak sensitive information, especially if users visit banking or personal sites.

## 3. Cross-Site Scripting (XSS)[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#3-cross-site-scripting-xss "Permanent link")

User inputs can execute scripts in the page's context. An attacker could inject scripts that steal cookies, session tokens, or sensitive data.

## 4. Insecure Communication[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#4-insecure-communication "Permanent link")

Data sent over insecure HTTP can be intercepted by attackers on the same network, allowing them to capture sensitive information, such as tokens or personal data.

## 5. Code Injection[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#5-code-injection "Permanent link")

If an attacker controls the script URL, they can inject malicious code into the page, leading to data theft or manipulation of the page’s functionality.

## 6. Malicious Updates[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#6-malicious-updates "Permanent link")

If the update mechanism is compromised, attackers can push malicious code to users without their knowledge, potentially gaining control over their browsers.

## 7. Third-Party Dependencies[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#7-third-party-dependencies "Permanent link")

An extension relying on outdated third-party libraries may become vulnerable if those libraries have known security flaws that attackers can exploit.

## 8. Lack of Content Security Policy (CSP)[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#8-lack-of-content-security-policy-csp "Permanent link")

Without a strong CSP, attackers can inject untrusted content, increasing the risk of XSS and other attacks that manipulate the extension’s behavior.

## 9. Insecure Storage[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#9-insecure-storage "Permanent link")

If an attacker gains access to the local storage, they can easily retrieve sensitive information, such as tokens or user credentials, leading to unauthorized access.

## 10. Insufficient Privacy Controls[¶](https://cheatsheetseries.owasp.org/cheatsheets/Browser_Extension_Vulnerabilities_Cheat_Sheet.html#10-insufficient-privacy-controls "Permanent link")

Users may be unaware of how their data is being collected or used, leading to potential abuse of their information without consent or awareness.



