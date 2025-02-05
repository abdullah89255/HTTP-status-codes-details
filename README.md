# HTTP-status-codes-details
HTTP status codes are standard responses given by web servers when a request is made to them. They indicate whether the request was successful, if there was an error, or if additional actions are needed. Here's a detailed breakdown of the categories and specific codes:

---

### **1xx Informational Responses**
These indicate that the server has received the request and is processing it.

- **100 Continue:** The client can continue with its request after receiving this interim response.
- **101 Switching Protocols:** The server is switching protocols as requested by the client (e.g., from HTTP to WebSocket).

---

### **2xx Success**
These indicate that the request was successfully received, understood, and accepted.

- **200 OK:** The request was successful, and the server returned the requested data.
- **201 Created:** The request was successful, and a new resource was created (commonly used in POST requests).
- **202 Accepted:** The request has been accepted for processing but is not yet completed.
- **204 No Content:** The request was successful, but the server is not returning any content.

---

### **3xx Redirection**
These indicate that further action is needed to complete the request.

- **301 Moved Permanently:** The resource has been moved to a new URL permanently.
- **302 Found:** The resource is temporarily located at a different URL.
- **304 Not Modified:** The resource has not been modified since the last request; the client can use its cached version.

---

### **4xx Client Errors**
These indicate issues caused by the client, such as a bad request or unauthorized access.

- **400 Bad Request:** The server cannot process the request due to a client error (e.g., malformed request syntax).
- **401 Unauthorized:** Authentication is required but not provided or invalid.
- **403 Forbidden:** The client does not have permission to access the resource.
- **404 Not Found:** The server cannot find the requested resource.
- **429 Too Many Requests:** The client has sent too many requests in a given time period (rate-limiting).

---

### **5xx Server Errors**
These indicate issues on the server’s side that prevent it from fulfilling the request.

- **500 Internal Server Error:** The server encountered an unexpected error.
- **502 Bad Gateway:** The server received an invalid response from an upstream server.
- **503 Service Unavailable:** The server is temporarily unavailable (overloaded or under maintenance).
- **504 Gateway Timeout:** The server did not receive a timely response from an upstream server.

---
---
---
Bypassing HTTP status codes typically means addressing the issue causing the response. Here's how to handle and resolve the most common HTTP status codes that might require action:

---

### **1xx Informational Responses**
- No bypass needed; these codes are temporary and indicate the server is processing your request.

---

### **2xx Success**
- These codes indicate the request was successful, so no bypass is needed.

---

### **3xx Redirection (e.g., 301, 302)**
To bypass redirections:
1. **Follow the Redirect:** Most browsers and HTTP clients automatically follow redirects. Ensure your client (e.g., cURL, Python requests) is configured to do so.
   - Example with `cURL`: Use `-L` to follow redirects.
2. **Direct Access:** If you know the new location, access it directly.
3. **Avoid Redirect Loops:** Inspect the redirection chain using debugging tools like cURL or browser dev tools to identify and fix loops.

---

### **4xx Client Errors (e.g., 401, 403, 404)**
- **401 Unauthorized:**
  1. Provide correct authentication credentials (username, password, or API token).
  2. Use a proxy or VPN if access is restricted by location.
  3. Contact the server administrator if you're supposed to have access.

- **403 Forbidden:**
  1. Check for permission issues on the resource.
  2. Use a VPN or proxy if your IP is blocked.
  3. Verify user-agent headers if the server blocks certain clients.
  4. Look for access tokens or referral headers required to access the resource.

- **404 Not Found:**
  1. Double-check the URL for typos.
  2. Search for the content on the site using its search bar.
  3. Use an archive tool like [Wayback Machine](https://archive.org) to find the resource if it has been moved or deleted.

- **429 Too Many Requests:**
  1. Wait before sending more requests.
  2. Use rate-limiting techniques in your scripts or tools.
  3. Switch to a different IP using a proxy or VPN.

---

### **5xx Server Errors (e.g., 500, 502, 503, 504)**
- **500 Internal Server Error:**
  1. Report the issue to the website administrator.
  2. Retry the request later.

- **502 Bad Gateway:**
  1. Check your connection and retry the request.
  2. Use a VPN to connect through a different route.
  3. If you're the server admin, check your upstream server configuration.

- **503 Service Unavailable:**
  1. Wait until the server becomes available.
  2. Retry periodically.

- **504 Gateway Timeout:**
  1. Try a different network or a VPN to reroute traffic.
  2. If you're the admin, optimize server performance or check upstream connections.

---

### **Tools to Help Bypass or Debug**
1. **Browser Developer Tools:**
   - Inspect responses and headers.
2. **cURL or Postman:**
   - Debug API responses and test different request parameters.
3. **Proxies or VPNs:**
   - Bypass geographical or IP-based restrictions.
4. **Automation Scripts:**
   - Use Python, JavaScript, or other tools to handle redirects, retries, or header modifications.

Let me know if you need assistance with specific status codes or tools!
---
---
---


---

### **1xx Informational Responses**
- **Example Code:** `100 Continue`
- **What it means:** The server acknowledges the initial request and expects more data.
- **No action needed:** This is part of normal server behavior.

---

### **2xx Success**
- **Example Code:** `200 OK`
- **What it means:** The request was successful, and there’s no issue to resolve.
- **Action:** No bypass needed. Enjoy your success!

---

### **3xx Redirection**
#### **301 Moved Permanently**
- **What it means:** The requested URL has been permanently moved to a new location.
- **Solution:**
  1. **Follow the Redirect:** Most modern browsers and tools like Postman handle this automatically.
  2. **Direct Access:** If you know the new URL (provided in the `Location` header), use it directly.
  - **Example:**  
    Old URL: `http://example.com/page1`  
    New URL (301 redirect): `https://example.com/page2`

#### **302 Found**
- **What it means:** The resource is temporarily located at a new URL.
- **Solution:** Follow the redirect or use the temporary location provided in the response.

#### **Example Using cURL**
```bash
curl -L http://example.com
```

#### **304 Not Modified**
- **What it means:** The resource hasn’t changed since your last request.
- **Solution:** Use the cached version of the resource (handled by browsers automatically).

---

### **4xx Client Errors**
#### **401 Unauthorized**
- **What it means:** You need to provide valid credentials (username/password or token).
- **Solution:**
  1. **Provide Credentials:**  
     Example in cURL:
     ```bash
     curl -u username:password http://example.com/protected
     ```
  2. **API Tokens:** If the API requires a token:
     ```bash
     curl -H "Authorization: Bearer <your_token>" http://example.com/api
     ```
  3. **Proxy or VPN:** If access is restricted by IP or location.

---

#### **403 Forbidden**
- **What it means:** You’re not authorized to access the resource, even with valid credentials.
- **Solutions:**
  1. **Use a VPN/Proxy:** Some servers block IPs from certain regions.
  2. **Modify User-Agent Header:** Servers sometimes block requests from automated tools.
     - **Example:**
       ```bash
       curl -A "Mozilla/5.0" http://example.com
       ```

---

#### **404 Not Found**
- **What it means:** The resource doesn’t exist at the specified URL.
- **Solutions:**
  1. **Check URL:** Double-check for typos.
  2. **Use a Search Tool:** Try finding the resource using the site’s search or Google.
     - Example: `site:example.com resource-name`
  3. **Wayback Machine:** Access an archived version:
     - [https://archive.org](https://archive.org)

---

#### **429 Too Many Requests**
- **What it means:** The server is rate-limiting your requests.
- **Solutions:**
  1. **Wait:** Retry after the time specified in the `Retry-After` header.
  2. **Throttle Requests:** If using a script, add delays between requests.
     - Example in Python:
       ```python
       import time
       for url in urls:
           response = requests.get(url)
           time.sleep(2)  # Wait 2 seconds between requests
       ```
  3. **Change IP:** Use a proxy or VPN to switch your IP.

---

### **5xx Server Errors**
#### **500 Internal Server Error**
- **What it means:** There’s an issue with the server itself.
- **Solutions:**
  1. **Retry Later:** Temporary server issues often resolve themselves.
  2. **Contact Support:** Report the issue to the website administrator.
  3. **Debugging (for developers):** Check server logs for errors.

---

#### **502 Bad Gateway**
- **What it means:** The server acting as a gateway received an invalid response from the upstream server.
- **Solutions:**
  1. **Retry Later:** This is often temporary.
  2. **Check Connectivity (for admins):** Ensure upstream servers are reachable.

---

#### **503 Service Unavailable**
- **What it means:** The server is overloaded or down for maintenance.
- **Solutions:**
  1. **Retry:** Wait and try again later.
  2. **Use a Status Monitoring Tool:** Tools like [DownDetector](https://downdetector.com/) can confirm outages.

---

#### **504 Gateway Timeout**
- **What it means:** The server didn’t get a timely response from the upstream server.
- **Solutions:**
  1. **Retry Later:** Temporary connectivity issues may resolve.
  2. **Optimize Requests (for admins):** Reduce server load or increase timeout settings.

---

### **Practical Debugging Tools**
- **Browser Developer Tools:** Check the network tab for detailed responses.
- **Postman:** Send custom requests and analyze server responses.
- **cURL Examples:**
  - Follow Redirects: `curl -L http://example.com`
  - Add Headers: `curl -H "Authorization: Bearer <token>" http://example.com`
- **Python Script Example:**
  ```python
  import requests

  url = "http://example.com"
  headers = {"Authorization": "Bearer <token>"}

  response = requests.get(url, headers=headers)
  print(response.status_code, response.text)
  ```
---
---
---

Here are **advanced examples and strategies** for dealing with specific HTTP status codes, including handling them programmatically, debugging, and applying real-world solutions for bypassing or resolving issues.

---

### **Advanced Examples for HTTP Status Codes**

#### **1. 3xx Redirection (Advanced)**
#### Example: Handling a 301 Redirect in Python
When dealing with APIs or automated requests, you may need to follow redirects manually.

```python
import requests

url = "http://example.com/old-url"
response = requests.get(url, allow_redirects=False)  # Disable automatic redirects

if response.status_code == 301:
    new_url = response.headers.get("Location")  # Fetch new location
    redirected_response = requests.get(new_url)
    print(redirected_response.content)
```

#### Automate Redirect Handling with Custom Headers:
```python
response = requests.get(url, headers={"User-Agent": "Advanced-Bot/1.0"})
if response.history:  # Detect redirection chain
    print("Redirect history:", response.history)
```

---

#### **2. 401 Unauthorized (Advanced)**
**Example: OAuth 2.0 Authentication**
Some APIs require OAuth tokens. Here’s an example using Python with the `requests` library:

```python
import requests

auth_url = "https://example.com/oauth/token"
data = {
    "grant_type": "client_credentials",
    "client_id": "your_client_id",
    "client_secret": "your_client_secret",
}
# Obtain the token
auth_response = requests.post(auth_url, data=data)
token = auth_response.json().get("access_token")

# Use the token in API requests
api_url = "https://example.com/api/resource"
headers = {"Authorization": f"Bearer {token}"}
response = requests.get(api_url, headers=headers)
print(response.json())
```

---

#### **3. 403 Forbidden (Advanced)**
**Bypass IP-Based Restrictions**
If a server blocks requests based on location or IP:
1. Use a proxy server:
   ```bash
   curl -x http://proxyserver:port http://example.com
   ```
2. In Python:
   ```python
   proxies = {"http": "http://proxyserver:port", "https": "http://proxyserver:port"}
   response = requests.get("http://example.com", proxies=proxies)
   print(response.content)
   ```

**Modify Headers to Mimic a Browser:**
Some servers block non-browser requests. Add headers like `User-Agent` and `Referer`:
```python
headers = {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36",
    "Referer": "https://example.com",
}
response = requests.get("http://example.com/protected", headers=headers)
print(response.content)
```

---

#### **4. 404 Not Found (Advanced)**
**Check for Similar Resources**
Use web scraping to check for alternate URLs:
```python
from bs4 import BeautifulSoup
import requests

url = "http://example.com/nonexistent-page"
response = requests.get("http://example.com")
soup = BeautifulSoup(response.content, "html.parser")

# Find all links on the page
for link in soup.find_all("a", href=True):
    print(link["href"])
```

---

#### **5. 429 Too Many Requests (Advanced)**
**Rate-Limiting with Retry Logic**
Use `Retry` headers or implement exponential backoff:
```python
import time
import requests

url = "http://example.com/api"
for i in range(5):  # Attempt 5 retries
    response = requests.get(url)
    if response.status_code == 429:
        wait_time = int(response.headers.get("Retry-After", 2))  # Use Retry-After or fallback
        time.sleep(wait_time)
    else:
        break

print(response.status_code, response.text)
```

**IP Rotation Using Proxies:**
If you’re rate-limited by IP, rotate proxies:
```python
proxies_list = ["http://proxy1:port", "http://proxy2:port"]
for proxy in proxies_list:
    proxies = {"http": proxy, "https": proxy}
    response = requests.get(url, proxies=proxies)
    print(response.status_code)
```

---

#### **6. 500 Internal Server Error (Advanced)**
**Capture Debugging Info**
Sometimes, server errors are logged in response headers or payload:
```python
response = requests.get("http://example.com")
if response.status_code == 500:
    print("Headers:", response.headers)
    print("Content:", response.text)
```

**Simulate the Error in Postman:**
1. Send the same request with different payloads or headers to isolate the cause.
2. Use environment variables for dynamic testing.

---

#### **7. 503 Service Unavailable (Advanced)**
**Bypass Maintenance Mode**
If a site is under maintenance but still accessible via an API:
```python
headers = {"X-Maintenance-Bypass": "true"}
response = requests.get("http://example.com", headers=headers)
print(response.status_code)
```

---

#### **8. 504 Gateway Timeout (Advanced)**
**Optimize Timeout Settings:**
Extend the timeout for requests:
```python
response = requests.get("http://example.com", timeout=10)  # Timeout in seconds
```

**Retry Logic with Exponential Backoff:**
```python
import time
import requests

url = "http://example.com"
max_retries = 5
delay = 2  # Initial delay

for i in range(max_retries):
    try:
        response = requests.get(url, timeout=5)
        if response.status_code == 200:
            print(response.content)
            break
    except requests.exceptions.Timeout:
        print(f"Timeout occurred, retrying in {delay} seconds...")
        time.sleep(delay)
        delay *= 2  # Exponential backoff
```

---

### **Advanced Debugging Tools**
1. **Fiddler or Burp Suite:** Inspect and manipulate HTTP requests/responses.
2. **Wireshark:** Analyze network packets to debug requests.
3. **Browser Developer Tools:**
   - Check the `Network` tab for redirect chains, errors, or headers.
4. **Postman Advanced Features:**
   - Use environments to test dynamic variables.
   - Automate pre-request scripts for token handling.

---
---
---
Here are **even more advanced examples** for handling HTTP status codes in real-world scenarios, including multi-step processes, advanced automation, and dynamic error handling in production-level systems.

---

### **1. Handling 3xx Redirects with Complex Chains**
If a redirect chain spans multiple steps, you can log each step and decide whether to follow it programmatically.

**Example: Logging Redirect Chains**
```python
import requests

url = "http://example.com/redirect"
response = requests.get(url, allow_redirects=True)

# Log all redirects
for redirect in response.history:
    print(f"Redirected: {redirect.status_code} -> {redirect.headers['Location']}")

# Final response
print(f"Final URL: {response.url}")
```

**Custom Redirect Handling**
You can limit the number of redirects to avoid infinite loops:
```python
MAX_REDIRECTS = 5
redirects = 0

while redirects < MAX_REDIRECTS:
    response = requests.get(url, allow_redirects=False)
    if response.status_code in (301, 302):
        url = response.headers['Location']  # Update URL
        redirects += 1
    else:
        break

print(f"Final response: {response.status_code}, URL: {url}")
```

---

### **2. Advanced OAuth 2.0 for 401 Unauthorized**
When accessing APIs requiring OAuth 2.0, automate the process of refreshing expired tokens.

**Example: Token Refresh Workflow**
```python
import requests
import time

auth_url = "https://example.com/oauth/token"
api_url = "https://example.com/api/resource"

# Function to fetch or refresh token
def get_token():
    data = {
        "grant_type": "client_credentials",
        "client_id": "your_client_id",
        "client_secret": "your_client_secret"
    }
    response = requests.post(auth_url, data=data)
    token = response.json().get("access_token")
    expires_in = response.json().get("expires_in")
    return token, time.time() + expires_in

# Fetch initial token
token, expiry_time = get_token()

# Use token in requests and refresh if expired
headers = {"Authorization": f"Bearer {token}"}
response = requests.get(api_url, headers=headers)

if response.status_code == 401 or time.time() > expiry_time:
    token, expiry_time = get_token()
    headers["Authorization"] = f"Bearer {token}"
    response = requests.get(api_url, headers=headers)

print(response.json())
```

---

### **3. Bypassing 403 Forbidden with Custom Authentication**
When APIs require non-standard headers or tokens, craft custom requests dynamically.

**Example: Generating Signed Headers**
Some APIs require HMAC-signed headers for access.
```python
import hashlib
import hmac
import base64

api_secret = b"your_api_secret"
message = b"data_to_sign"

# Generate HMAC signature
signature = base64.b64encode(hmac.new(api_secret, message, hashlib.sha256).digest())

headers = {
    "Authorization": f"Signature {signature.decode()}",
    "Content-Type": "application/json"
}
response = requests.get("http://example.com/protected", headers=headers)
print(response.status_code, response.json())
```

---

### **4. Handling 404 with Dynamic Resource Discovery**
If a resource is missing, programmatically find alternate locations using sitemaps or API endpoints.

**Example: Using a Sitemap for Discovery**
```python
from bs4 import BeautifulSoup
import requests

url = "http://example.com/sitemap.xml"
response = requests.get(url)
soup = BeautifulSoup(response.content, "xml")

# Extract and test URLs from the sitemap
for loc in soup.find_all("loc"):
    test_url = loc.text
    res = requests.get(test_url)
    if res.status_code == 200:
        print(f"Resource found: {test_url}")
```

---

### **5. Handling 429 with Distributed Requesting**
Distribute requests across multiple IPs or servers to avoid rate limits.

**Example: Distributed Requests with Threading**
```python
import threading
import requests

proxies = ["http://proxy1:port", "http://proxy2:port", "http://proxy3:port"]
url = "http://example.com/api"

def fetch_with_proxy(proxy):
    response = requests.get(url, proxies={"http": proxy, "https": proxy})
    print(f"Proxy: {proxy}, Status: {response.status_code}")

threads = []
for proxy in proxies:
    thread = threading.Thread(target=fetch_with_proxy, args=(proxy,))
    threads.append(thread)
    thread.start()

for thread in threads:
    thread.join()
```

---

### **6. Handling 500 Errors with Auto-Recovery**
If a server is unreliable, implement retries with incremental backoff and monitoring.

**Example: Exponential Backoff with Retry**
```python
import time
import requests

url = "http://example.com/api"
max_retries = 5
retry_delay = 2  # Initial delay

for attempt in range(max_retries):
    try:
        response = requests.get(url)
        if response.status_code == 200:
            print(response.json())
            break
    except requests.exceptions.RequestException as e:
        print(f"Error: {e}")
        time.sleep(retry_delay)
        retry_delay *= 2  # Double the delay
else:
    print("Max retries reached. Check the server status.")
```

---

### **7. Bypassing 503 Service Unavailable with Circuit Breaker**
Prevent overloading failing servers by implementing a circuit breaker.

**Example: Circuit Breaker Pattern**
```python
class CircuitBreaker:
    def __init__(self, failure_threshold, reset_time):
        self.failure_threshold = failure_threshold
        self.reset_time = reset_time
        self.failures = 0
        self.last_failure_time = 0

    def call(self, func, *args, **kwargs):
        if self.failures >= self.failure_threshold and time.time() - self.last_failure_time < self.reset_time:
            print("Circuit open. Skipping request.")
            return None

        try:
            result = func(*args, **kwargs)
            self.failures = 0  # Reset failures on success
            return result
        except Exception as e:
            self.failures += 1
            self.last_failure_time = time.time()
            print(f"Failure: {e}")
            return None

# Example usage
cb = CircuitBreaker(failure_threshold=3, reset_time=60)
response = cb.call(requests.get, "http://example.com")
if response:
    print(response.status_code)
```

---

### **8. Debugging Complex Status Issues with Middleware**
For developers working with microservices, debug and log responses across the request chain.

**Middleware Example: Log All Status Codes**
```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.before_request
def log_request():
    print(f"Request: {request.method} {request.url}")

@app.after_request
def log_response(response):
    print(f"Response: {response.status_code}")
    return response

@app.route("/test")
def test():
    return jsonify({"message": "Hello, World!"})

if __name__ == "__main__":
    app.run(debug=True)
```

---

### Tools to Enhance Advanced Debugging
1. **AWS Lambda:** Automate retries and redirection handling in serverless workflows.
2. **Docker Containers:** Test with isolated configurations for debugging server-side issues.
3. **Fiddler/Burp Suite:** Inspect all headers, cookies, and response codes for complex APIs.
---

---

### **9. Advanced Header Manipulation and Dynamic Token Rotation**
Some APIs require headers that change dynamically or are encrypted.

**Example: JWT Token Generation and Inclusion**
```python
import jwt
import requests
import datetime

# Create JWT
private_key = "your_private_key"
payload = {
    "iss": "your_client_id",
    "exp": datetime.datetime.utcnow() + datetime.timedelta(minutes=30),
}
token = jwt.encode(payload, private_key, algorithm="RS256")

# Include in headers
headers = {
    "Authorization": f"Bearer {token}",
    "Content-Type": "application/json"
}
response = requests.get("http://example.com/protected-resource", headers=headers)
print(response.status_code, response.json())
```

---

### **10. Custom Caching for Frequent API Calls (Reducing 429 Errors)**
Reduce the load on an API by caching responses for a short duration.

**Example: Simple Local Cache Implementation**
```python
import time
import hashlib

cache = {}

def get_from_cache_or_request(url):
    cache_key = hashlib.md5(url.encode()).hexdigest()  # Generate a unique cache key
    current_time = time.time()

    # Check if cache exists and is valid
    if cache_key in cache and current_time - cache[cache_key]['time'] < 60:
        print("Returning cached response")
        return cache[cache_key]['response']

    # Fetch new response and cache it
    response = requests.get(url)
    cache[cache_key] = {"response": response, "time": current_time}
    return response

response = get_from_cache_or_request("http://example.com/api")
print(response.status_code, response.text)
```

---

### **11. Advanced Proxy Pooling with Randomized User-Agents**
Rotate both proxies and user-agents to avoid detection and bypass restrictions.

**Example: Proxy Pool with Random User-Agent Rotation**
```python
import random
import requests

proxies = ["http://proxy1:port", "http://proxy2:port", "http://proxy3:port"]
user_agents = [
    "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36",
    "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36",
    "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36"
]

def fetch_url(url):
    proxy = random.choice(proxies)
    user_agent = random.choice(user_agents)
    headers = {"User-Agent": user_agent}
    response = requests.get(url, proxies={"http": proxy, "https": proxy}, headers=headers)
    return response

response = fetch_url("http://example.com")
print(response.status_code, response.text)
```

---

### **12. Load Balancing with Multiple APIs**
If an API has multiple endpoints serving similar data, balance requests dynamically.

**Example: Round-Robin Load Balancing**
```python
import itertools

api_endpoints = ["http://api1.example.com", "http://api2.example.com", "http://api3.example.com"]
api_cycle = itertools.cycle(api_endpoints)  # Create a round-robin iterator

def fetch_data():
    url = next(api_cycle)  # Get the next API in the cycle
    response = requests.get(url)
    return response

for _ in range(5):  # Simulate 5 requests
    print(fetch_data().status_code)
```

---

### **13. Automating Debugging for 500 Errors**
Automatically analyze and log details about server errors for further debugging.

**Example: Error Reporting System**
```python
import requests

def log_error(response):
    error_details = {
        "url": response.url,
        "status_code": response.status_code,
        "headers": dict(response.headers),
        "body": response.text,
    }
    with open("error_log.txt", "a") as log_file:
        log_file.write(str(error_details) + "\n")

url = "http://example.com"
response = requests.get(url)
if response.status_code == 500:
    log_error(response)
```

---

### **14. Predictive Recovery for 503 Errors**
Predict downtime patterns using machine learning and automate recovery strategies.

**Example: Predict Downtime Using ML Libraries**
```python
import numpy as np
from sklearn.linear_model import LinearRegression

# Historical server response times and statuses
response_times = np.array([100, 200, 300, 500, 1000, 2000]).reshape(-1, 1)  # Response times in ms
statuses = np.array([200, 200, 200, 503, 503, 503])  # Status codes

# Train a model to predict failures
model = LinearRegression().fit(response_times, statuses)

# Predict the next response
next_response_time = np.array([[1500]])
predicted_status = model.predict(next_response_time)
print(f"Predicted Status: {predicted_status[0]}")
```

---

### **15. Advanced Circuit Breaker with Request Analysis**
Circuit breakers can log additional metadata and implement gradual recovery.

**Example: Advanced Circuit Breaker with Metadata Logging**
```python
class AdvancedCircuitBreaker:
    def __init__(self, failure_threshold, reset_time):
        self.failure_threshold = failure_threshold
        self.reset_time = reset_time
        self.failures = 0
        self.last_failure_time = 0
        self.metadata = []

    def call(self, func, *args, **kwargs):
        if self.failures >= self.failure_threshold and time.time() - self.last_failure_time < self.reset_time:
            print("Circuit open. Skipping request.")
            return None

        try:
            result = func(*args, **kwargs)
            self.failures = 0  # Reset failures on success
            return result
        except Exception as e:
            self.failures += 1
            self.last_failure_time = time.time()
            self.metadata.append({"error": str(e), "timestamp": time.time()})
            print(f"Failure: {e}")
            return None

cb = AdvancedCircuitBreaker(failure_threshold=3, reset_time=60)
response = cb.call(requests.get, "http://example.com")
if response:
    print(response.status_code)
```

---

### **16. Using WebSocket for Real-Time 101 Switching Protocols**
Use WebSockets for real-time communication where APIs rely on `101 Switching Protocols`.

**Example: WebSocket Implementation**
```python
import websocket

def on_message(ws, message):
    print("Received:", message)

def on_error(ws, error):
    print("Error:", error)

def on_close(ws, close_status_code, close_msg):
    print("Closed:", close_status_code, close_msg)

def on_open(ws):
    ws.send("Hello, Server!")

url = "ws://example.com/socket"
ws = websocket.WebSocketApp(url, on_message=on_message, on_error=on_error, on_close=on_close)
ws.on_open = on_open
ws.run_forever()
```

---

### **17. Custom Middleware for Microservices**
If you're working with microservices, intercept all HTTP requests/responses to add uniform logging, tracing, or retries.

**Example: Flask Middleware for Tracing**
```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.before_request
def log_request():
    print(f"Request Method: {request.method}, URL: {request.url}")

@app.after_request
def add_tracing(response):
    response.headers["X-Trace-ID"] = "unique-trace-id"
    return response

@app.route("/service")
def service():
    return jsonify({"message": "Hello from Microservice"})

if __name__ == "__main__":
    app.run(debug=True)
```

---

### Tools and Libraries for Advanced HTTP Handling
1. **Asyncio with aiohttp**: Handle large-scale asynchronous requests.
2. **Celery or RabbitMQ**: Queue failed requests for retry later.
3. **Prometheus/Grafana**: Monitor API request/response patterns visually.
4. **NGINX as API Gateway**: Cache responses, manage load balancing, and handle redirects.

---
Let’s dive even deeper with **more advanced HTTP techniques and scenarios**. These examples focus on **high-performance systems**, **distributed architectures**, and **resilient design patterns** for handling HTTP status codes and network-related challenges.

---

### **18. Asynchronous Requests at Scale (Concurrency with aiohttp)**

For handling thousands of requests concurrently, use Python's `aiohttp` with asyncio.

**Example: Concurrent Requests with aiohttp**
```python
import aiohttp
import asyncio

async def fetch(session, url):
    async with session.get(url) as response:
        print(f"URL: {url}, Status: {response.status}")
        return await response.text()

async def main():
    urls = [f"http://example.com/resource/{i}" for i in range(1, 101)]
    async with aiohttp.ClientSession() as session:
        tasks = [fetch(session, url) for url in urls]
        responses = await asyncio.gather(*tasks)
        print("All requests completed.")

asyncio.run(main())
```

---

### **19. Rate-Limited APIs with Token Bucket Algorithm**

Implement rate-limiting strategies for APIs to handle `429 Too Many Requests`.

**Example: Token Bucket Implementation**
```python
import time

class TokenBucket:
    def __init__(self, rate, capacity):
        self.rate = rate
        self.capacity = capacity
        self.tokens = capacity
        self.last_time = time.time()

    def allow_request(self):
        now = time.time()
        elapsed = now - self.last_time
        self.tokens = min(self.capacity, self.tokens + elapsed * self.rate)
        self.last_time = now

        if self.tokens >= 1:
            self.tokens -= 1
            return True
        return False

bucket = TokenBucket(rate=5, capacity=10)  # 5 requests/second with a burst of 10
while True:
    if bucket.allow_request():
        print("Request allowed at", time.time())
    else:
        print("Request denied. Rate limit hit.")
        time.sleep(0.1)
```

---

### **20. Implementing Retry Policies with Circuit Breaker**

Combine **retry logic** with a **circuit breaker** to handle transient `500` errors.

**Example: Retry with Circuit Breaker**
```python
import requests
import time

class CircuitBreaker:
    def __init__(self, failure_threshold, reset_timeout):
        self.failure_threshold = failure_threshold
        self.reset_timeout = reset_timeout
        self.failures = 0
        self.last_failure_time = None

    def call(self, func, *args, **kwargs):
        if self.failures >= self.failure_threshold:
            if time.time() - self.last_failure_time < self.reset_timeout:
                print("Circuit open. Request denied.")
                return None
            else:
                self.failures = 0  # Reset after timeout

        try:
            response = func(*args, **kwargs)
            self.failures = 0  # Reset on success
            return response
        except Exception as e:
            self.failures += 1
            self.last_failure_time = time.time()
            print(f"Request failed: {e}")
            return None

breaker = CircuitBreaker(failure_threshold=3, reset_timeout=10)

def api_request():
    response = requests.get("http://example.com/api")
    if response.status_code != 200:
        raise Exception(f"API Error: {response.status_code}")
    return response

for _ in range(10):
    time.sleep(1)
    result = breaker.call(api_request)
    if result:
        print(result.status_code)
```

---

### **21. Distributed Load Testing (Locust Example)**

Test your application’s scalability using distributed load testing tools like **Locust**.

**Example: Locust for HTTP Load Testing**
```python
# Save this as locustfile.py and run using `locust`
from locust import HttpUser, task, between

class LoadTestUser(HttpUser):
    wait_time = between(1, 5)

    @task
    def get_resource(self):
        self.client.get("/resource")
```

Run with:
```bash
locust -f locustfile.py --host=http://example.com
```

---

### **22. API Gateway for 503 Fallbacks (NGINX)**

Use **NGINX** to handle `503 Service Unavailable` with fallback strategies.

**Example: Fallback Proxy Configuration**
```nginx
server {
    listen 80;

    location / {
        proxy_pass http://primary_backend;
        error_page 503 @fallback;
    }

    location @fallback {
        proxy_pass http://secondary_backend;
    }
}
```

---

### **23. Automating Failover Across Multiple Regions**

Ensure your application automatically fails over to another region when a primary server fails.

**Example: Multi-Region Failover**
```python
import requests

regions = ["https://us.example.com", "https://eu.example.com", "https://apac.example.com"]

def fetch_from_region(regions):
    for region in regions:
        try:
            response = requests.get(region)
            if response.status_code == 200:
                print(f"Data fetched from {region}")
                return response.json()
        except requests.RequestException:
            print(f"Failed to fetch from {region}")
    raise Exception("All regions failed!")

fetch_from_region(regions)
```

---

### **24. Advanced WebSocket Error Handling**

Automatically reconnect WebSockets in case of disconnections (`1006 Abnormal Closure`).

**Example: WebSocket Auto-Reconnect**
```python
import websocket
import time

def connect():
    def on_message(ws, message):
        print("Received:", message)

    def on_error(ws, error):
        print("Error:", error)

    def on_close(ws, close_status_code, close_msg):
        print("Closed:", close_status_code, close_msg)

    def on_open(ws):
        ws.send("Hello, Server!")

    while True:
        try:
            ws = websocket.WebSocketApp(
                "ws://example.com/socket",
                on_message=on_message,
                on_error=on_error,
                on_close=on_close
            )
            ws.on_open = on_open
            ws.run_forever()
        except Exception as e:
            print(f"WebSocket error: {e}. Retrying in 5 seconds...")
            time.sleep(5)

connect()
```

---

### **25. Optimizing Performance with Persistent Connections**

Leverage persistent connections for high-performance requests.

**Example: HTTP Keep-Alive with requests.Session**
```python
import requests

session = requests.Session()  # Reuse TCP connections
session.headers.update({"User-Agent": "MyApp/1.0"})

response = session.get("http://example.com/resource")
print(response.status_code)

# Persistent session reuse
for i in range(5):
    response = session.get(f"http://example.com/resource/{i}")
    print(f"Request {i}: {response.status_code}")
```

---

### **26. Advanced Content-Based Routing**

Route requests dynamically based on response content (e.g., JSON keys).

**Example: Dynamic Routing Based on API Response**
```python
import requests

def route_request(data):
    if "type" in data and data["type"] == "error":
        return "http://error-handler.example.com"
    return "http://default-handler.example.com"

response = requests.get("http://example.com/api")
if response.status_code == 200:
    data = response.json()
    target_url = route_request(data)
    requests.post(target_url, json=data)
```

---

### **27. Serverless Request Workflow with AWS Lambda**

Trigger serverless functions dynamically for HTTP status code errors.

**Example: AWS Lambda Trigger for 500 Errors**
```python
import boto3

def handle_error(event):
    if event["statusCode"] == 500:
        lambda_client = boto3.client("lambda")
        lambda_client.invoke(
            FunctionName="ErrorHandlerFunction",
            InvocationType="Event",
            Payload=bytes(event)
        )
```

---

### **28. AI-Driven Monitoring for Status Code Analysis**

Integrate AI for analyzing trends in status codes.

**Example: AI-Powered Trend Analysis**
```python
from sklearn.linear_model import LogisticRegression
import numpy as np

# Simulated status code data
statuses = np.array([200, 200, 500, 200, 503, 500, 200])
timestamps = np.array([1, 2, 3, 4, 5, 6, 7]).reshape(-1, 1)

# Train logistic regression to predict failures
model = LogisticRegression().fit(timestamps, statuses)

# Predict future status
future_time = np.array([[8]])
predicted_status = model.predict(future_time)
print(f"Predicted Status for t=8: {predicted_status[0]}")
```

---

These examples showcase advanced techniques for resilient, scalable, and optimized HTTP workflows. Let me know if you'd like deeper examples in specific areas like **security**, **distributed systems**, or **real-time monitoring**!


