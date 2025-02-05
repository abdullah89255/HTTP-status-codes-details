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

Would you like further explanations on specific codes or how to handle them?
