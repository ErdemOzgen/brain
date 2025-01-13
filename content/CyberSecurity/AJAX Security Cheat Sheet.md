
#### Use `.innerText` instead of `.innerHTML`

#### Don't use `eval()`, `new Function()` or other code evaluation tools[¶](https://cheatsheetseries.owasp.org/cheatsheets/AJAX_Security_Cheat_Sheet.html#dont-use-eval-new-function-or-other-code-evaluation-tools "Permanent link")

`eval()` function is evil, never use it. Needing to use eval usually indicates a problem in your design


#### Canonicalize data to consumer (read: encode before use)[¶](https://cheatsheetseries.owasp.org/cheatsheets/AJAX_Security_Cheat_Sheet.html#canonicalize-data-to-consumer-read-encode-before-use "Permanent link")

# Data Encoding

Data should be properly encoded before used in this manner to prevent injection style issues, and to make sure the logical meaning is preserved.


Data encoding is a fundamental practice in software development and data processing that involves converting data from one format into another. Proper encoding is essential to ensure data integrity, maintain its logical meaning, and, critically, to prevent various types of injection attacks that can compromise the security and functionality of applications.

### **1. Understanding Data Encoding**

**Data Encoding** refers to transforming data into a specific format using a set of rules. This transformation ensures that data is correctly interpreted and handled by different systems, applications, or components within an application. Encoding is context-dependent, meaning the method of encoding varies based on where and how the data is used.

### **2. Importance of Proper Data Encoding**

- **Security:** Prevents injection attacks (e.g., SQL injection, Cross-Site Scripting) by ensuring that user-supplied data cannot alter the intended logic of the application.
  
- **Data Integrity:** Maintains the original meaning and structure of the data when it is transmitted or stored, avoiding data corruption or misinterpretation.
  
- **Interoperability:** Ensures that data can be correctly processed by different systems or components, especially when dealing with various data formats and protocols.

### **3. Injection Attacks and How Encoding Prevents Them**

**Injection attacks** occur when an attacker supplies malicious input that is interpreted as part of a command or query, allowing them to manipulate the system. Proper encoding neutralizes these attacks by ensuring that user input is treated strictly as data, not as executable code.

#### **Common Injection Attacks:**

1. **SQL Injection:** Manipulating SQL queries by injecting malicious SQL code.
2. **Cross-Site Scripting (XSS):** Injecting malicious scripts into web pages viewed by other users.
3. **Command Injection:** Executing arbitrary commands on the host operating system via a vulnerable application.

#### **How Encoding Mitigates These Attacks:**

- **SQL Injection:** By using parameterized queries or prepared statements, which separate data from code, making it impossible for user input to alter the SQL command structure.
  
- **XSS:** By encoding special characters in user input before rendering them in the browser, preventing the browser from interpreting them as executable scripts.

### **4. Examples of Proper Encoding**

#### **a. SQL Injection Prevention**

**Incorrect Approach:**
```python
# Vulnerable Python code using string formatting
user_input = "1; DROP TABLE users;"
query = f"SELECT * FROM users WHERE id = {user_input}"
cursor.execute(query)
```
*If `user_input` is `1; DROP TABLE users;`, it will execute both the `SELECT` and `DROP` commands, causing data loss.*

**Proper Approach: Using Parameterized Queries**
```python
# Secure Python code using parameterized queries
user_input = "1; DROP TABLE users;"
query = "SELECT * FROM users WHERE id = %s"
cursor.execute(query, (user_input,))
```
*Here, `user_input` is treated strictly as data, preventing the execution of unintended SQL commands.*

#### **b. Cross-Site Scripting (XSS) Prevention**

**Incorrect Approach:**
```html
<!-- Vulnerable HTML code -->
<div>User comment: {{ user_comment }}</div>
```
*If `user_comment` contains `<script>alert('XSS')</script>`, the script will execute in the user's browser.*

**Proper Approach: HTML Encoding**
```html
<!-- Secure HTML code with encoding -->
<div>User comment: {{ user_comment | escape }}</div>
```
*Special characters like `<`, `>`, and `&` are converted to their HTML entity equivalents (`&lt;`, `&gt;`, `&amp;`), rendering the script harmless.*

#### **c. URL Encoding**

When incorporating user input into URLs, encoding ensures that special characters do not break the URL structure or introduce vulnerabilities.

**Example:**
```python
import urllib.parse

user_input = "John Doe & Sons"
encoded_input = urllib.parse.quote(user_input)
url = f"https://example.com/search?query={encoded_input}"
# Resulting URL: https://example.com/search?query=John%20Doe%20%26%20Sons
```
*Spaces are encoded as `%20` and `&` as `%26`, preserving the integrity of the URL.*

### **5. Preserving Logical Meaning Through Encoding**

Proper encoding not only secures data but also preserves its intended meaning across different systems and contexts.

**Example: Handling Unicode Characters**

Suppose a user inputs the string `"Café Münchën"`.

- **Without Proper Encoding:** Systems that do not support Unicode may misinterpret or corrupt the data.
  
- **With Proper Encoding (e.g., UTF-8):** The data is accurately represented and maintained across different platforms and applications.

**Implementation:**
```python
# Encoding a string in UTF-8
user_input = "Café Münchën"
encoded_input = user_input.encode('utf-8')
# encoded_input: b'Caf\xc3\xa9 M\xc3\xbcnch\xc3\xabn'
```

### **6. Best Practices for Data Encoding**

1. **Contextual Encoding:** Always encode data based on the context in which it will be used (e.g., HTML, SQL, URLs).
   
2. **Use Built-in Functions and Libraries:** Most programming languages and frameworks provide robust encoding functions. Utilize them instead of writing custom encoding logic.
   
3. **Validate and Sanitize Input:** While encoding is crucial, also implement input validation to ensure data meets expected formats and constraints.
   
4. **Stay Updated:** Keep abreast of the latest security practices and encoding standards to protect against emerging threats.

5. **Use Prepared Statements:** Especially for SQL, use prepared statements or ORM (Object-Relational Mapping) tools that handle encoding and parameterization automatically.

### **7. Additional Examples**

#### **a. JSON Encoding**

When sending data in JSON format, encoding ensures that the JSON structure remains intact.

**Example:**
```python
import json

data = {
    "name": "John Doe",
    "bio": "Loves coding in <Python> & \"JavaScript\"."
}

json_data = json.dumps(data)
# json_data: '{"name": "John Doe", "bio": "Loves coding in <Python> & \\"JavaScript\\"."}'
```
*Special characters like quotes are escaped to maintain valid JSON syntax.*

#### **b. XML Encoding**

Similar to HTML encoding, XML encoding ensures that data does not interfere with XML structure.

**Example:**
```xml
<!-- Properly encoded XML -->
<user>
    <name>John &amp; Jane</name>
    <bio>Loves coding in &lt;Python&gt; and "JavaScript".</bio>
</user>
```
*Characters like `&`, `<`, and `>` are encoded as `&amp;`, `&lt;`, and `&gt;` respectively.*

### **8. Conclusion** for Data encoding

Proper data encoding is a critical aspect of developing secure and reliable applications. It serves as a defense mechanism against various injection attacks by ensuring that user-supplied data is correctly interpreted and does not interfere with the application's logic or data structures. Additionally, encoding preserves the logical meaning of data across different systems and contexts, maintaining data integrity and interoperability. By adhering to best practices in data encoding, developers can build robust applications that are both secure and efficient.




# Don't rely on client logic for security[¶](https://cheatsheetseries.owasp.org/cheatsheets/AJAX_Security_Cheat_Sheet.html#dont-rely-on-client-logic-for-security "Permanent link")

Don't forget that the user controls the client-side logic. A number of browser plugins are available to set breakpoints, skip code, change values, etc. Never rely on client logic for security.


# Don't rely on client business logic

Just like the security one, make sure any interesting business rules/logic is duplicated on the server side lest a user bypasses needed logic and does something silly, or worse, costly.

# Avoid Writing Serialization Code


## Examples of Serialization Frameworks**

### **a. JSON Serialization**

**Languages and Frameworks:**
- **Python:** `json` module
- **JavaScript:** `JSON.stringify` and `JSON.parse`
- **Java:** Jackson, Gson
- **C#:** Newtonsoft.Json (Json.NET)

**Example in Python:**

*Using Custom Serialization (Vulnerable):*
```python
import json

class User:
    def __init__(self, username, role):
        self.username = username
        self.role = role

def serialize_user(user):
    return f"{user.username}:{user.role}"

def deserialize_user(data):
    username, role = data.split(":")
    return User(username, role)

# Potential Security Issue: No validation on input data
```

*Using `json` Module (Secure):*
```python
import json

class User:
    def __init__(self, username, role):
        self.username = username
        self.role = role

def serialize_user(user):
    return json.dumps(user.__dict__)

def deserialize_user(data):
    try:
        obj = json.loads(data)
        # Validate data before creating User instance
        if 'username' in obj and 'role' in obj:
            return User(obj['username'], obj['role'])
    except json.JSONDecodeError:
        # Handle invalid JSON
        pass
    return None
```

### **b. XML Serialization**

**Languages and Frameworks:**
- **Java:** JAXB
- **C#:** System.Xml.Serialization

**Example in C#:**

*Using Custom Serialization (Vulnerable):*
```csharp
public string SerializeUser(User user)
{
    return $"{user.Username}:{user.Role}";
}

public User DeserializeUser(string data)
{
    var parts = data.Split(':');
    return new User(parts[0], parts[1]);
}

// Potential Security Issue: No validation or encoding
```

*Using `System.Xml.Serialization` (Secure):*
```csharp
using System.Xml.Serialization;
using System.IO;

public string SerializeUser(User user)
{
    XmlSerializer serializer = new XmlSerializer(typeof(User));
    using (StringWriter writer = new StringWriter())
    {
        serializer.Serialize(writer, user);
        return writer.ToString();
    }
}

public User DeserializeUser(string data)
{
    XmlSerializer serializer = new XmlSerializer(typeof(User));
    using (StringReader reader = new StringReader(data))
    {
        try
        {
            return (User)serializer.Deserialize(reader);
        }
        catch (InvalidOperationException)
        {
            // Handle invalid XML
            return null;
        }
    }
}
```

---

#### ** Best Practices for Serialization in Secure Applications**

1. **Use Trusted Frameworks:**
   - Always prefer established serialization libraries over custom implementations.
   
2. **Validate and Sanitize Input:**
   - Ensure that deserialized data is validated against expected schemas or data models.
   
3. **Implement Strict Type Controls:**
   - Restrict deserialization to known and trusted types to prevent object injection.
   
4. **Handle Exceptions Gracefully:**
   - Anticipate and manage errors during serialization/deserialization to avoid application crashes.
   
5. **Encrypt Sensitive Data:**
   - When serializing sensitive information, use encryption to protect data at rest and in transit.
   
6. **Use Serialization Formats with Built-in Security:**
   - Opt for formats that support data integrity and validation features, such as JSON Web Tokens (JWT) with signature verification.
   
7. **Stay Updated:**
   - Keep serialization libraries up-to-date to benefit from security patches and improvements.

---

#### Avoid building XML or JSON dynamically[¶](https://cheatsheetseries.owasp.org/cheatsheets/AJAX_Security_Cheat_Sheet.html#avoid-building-xml-or-json-dynamically "Permanent link")

Just like building HTML or SQL you will cause XML injection bugs, so stay away from this or at least use an encoding library or safe JSON or XML library to make attributes and element data safe.

- [XSS (Cross Site Scripting) Prevention](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
- [SQL Injection Prevention](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)



##### ALWAYS RETURN JSON WITH AN OBJECT ON THE OUTSIDE[¶](https://cheatsheetseries.owasp.org/cheatsheets/AJAX_Security_Cheat_Sheet.html#always-return-json-with-an-object-on-the-outside "Permanent link")

Always have the outside primitive be an object for JSON strings:

**Exploitable:**

`[{"object": "inside an array"}]`

**Not exploitable:**

`{"object": "not inside an array"}`

**Also not exploitable:**

`{"result": [{"object": "inside an array"}]}`


#### Avoid writing serialization code Server Side[¶](https://cheatsheetseries.owasp.org/cheatsheets/AJAX_Security_Cheat_Sheet.html#avoid-writing-serialization-code-server-side "Permanent link")

Remember ref vs. value types! Look for an existing library that has been reviewed.

#### Services can be called by users directly[¶](https://cheatsheetseries.owasp.org/cheatsheets/AJAX_Security_Cheat_Sheet.html#services-can-be-called-by-users-directly "Permanent link")

Even though you only expect your AJAX client side code to call those services the users can too.

Make sure you validate inputs and treat them like they are under user control (because they are!).

#### Avoid building XML or JSON by hand, use the framework[¶](https://cheatsheetseries.owasp.org/cheatsheets/AJAX_Security_Cheat_Sheet.html#avoid-building-xml-or-json-by-hand-use-the-framework "Permanent link")

Use the framework and be safe, do it by hand and have security issues.

#### Use JSON And XML Schema for Webservices[¶](https://cheatsheetseries.owasp.org/cheatsheets/AJAX_Security_Cheat_Sheet.html#use-json-and-xml-schema-for-webservices "Permanent link")

You need to use a third-party library to validate web services.