# Technical Learning Report: Web Application Basics

| Attribute            | Details                                        |
| :------------------- | :--------------------------------------------- |
| **Platform**         | TryHackMe                                      |
| **Course Path**      | Web Development                 		        |
| **Topic**            | Web Application Basics                         |

---

## Executive Summary
This report deconstructs the fundamental architecture of web applications, focusing on the Request-Response cycle of the HTTP protocol. The analysis explores the anatomy of the Uniform Resource Locator (URL), the structural requirements of HTTP messages, the functional differences between request methods, and the categorical logic of server status codes. Finally, it examines the implementation of security headers as a critical mechanism for hardening the client-side execution environment.

**Core Objectives Identified:**
1.  **Structural Integrity:** Analyzing the four-part requirement of HTTP messages to ensure proper parsing by the server and browser.
2.  **State Management:** Understanding how cookies and headers provide persistence within a stateless communication framework.
3.  **Client-Side Hardening:** Utilizing specialized security directives to mitigate attack vectors such as Cross-Site Scripting (XSS) and protocol downgrades.

---

## Technical Analysis

### 01. Uniform Resource Locator (URL)
The Uniform Resource Locator (URL) acts as a roadmap for the browser. It consists of a **Scheme** (defining the protocol, usually HTTP or HTTPS), a **Host** (identifying the target server), a **Path** (pointing to the specific resource), and a **Query String** (providing variable data). A key security risk identified is "Typosquatting," where malicious domains mimic legitimate ones to deceive users.

### 02. The Anatomy of an HTTP Message
Every HTTP message, whether a request or a response, follows a rigid four-part structure:
*   **Start Line:** Identifies the method/version or status.
*   **Headers:** Key-value pairs providing metadata and instructions.
*   **Empty Line:** A mandatory vacuum that separates instructions from data.
*   **Body:** The actual payload (HTML, JSON, or form data).
The "Empty Line" is the essential barrier; its absence leads to systemic misinterpretation of the data payload as executable logic.

### 03. The Dialogue: Requests and Responses
Web interaction is a dialogue defined by specific verbs and categorical feedback.
*   **Request Methods:** Verbs like `GET` are used for safe data retrieval, while `POST`, `PUT`, and `PATCH` are used for state changes. Security requires that sensitive methods (like `TRACE` or `DELETE`) are strictly gated or disabled.
*   **Status Codes:** Three-digit indicators that classify the outcome of a request.
    *   **2xx (Success):** The request was fulfilled.
    *   **3xx (Redirection):** The target has moved.
    *   **4xx (Client Error):** The request was malformed or unauthorized (e.g., 404 Not Found).
    *   **5xx (Server Error):** The backend logic has collapsed.

### 04. Security Headers and Hardening
Because browsers are inherently "naive" and trust server responses, security headers are used to constrain browser behavior:
*   **Content-Security-Policy (CSP):** Prevents XSS by whitelisting trusted sources for scripts.
*   **Strict-Transport-Security (HSTS):** Mandates an encrypted connection, preventing protocol downgrades.
*   **X-Content-Type-Options (nosniff):** Forces the browser to strictly follow the provided Content-Type, preventing it from "guessing" data into executable code.

---

## Task Completion and Evidence

### Task 2: Web Application Overview
*   **Question:** What component filters dangerous requests away from the web server?
*   **Answer:** WAF
*   **Question:** What is the brain of a front-end organism, enabling decisions?
*   **Answer:** JavaScript

### Task 3: Uniform Resource Locator (URL)
*   **Question:** Which part of the URL points to the specific file or page being accessed?
*   **Answer:** Path
*   **Question:** Which part of the URL starts with a hash (#)?
*   **Answer:** Fragment
*   **Question:** What is the most common port for the HTTPS scheme?
*   **Answer:** 443

### Task 4: HTTP Messages
*   **Question:** Which type of HTTP message is sent by the user to trigger actions?
*   **Answer:** HTTP Request
*   **Question:** What part of an HTTP message provides extra info in key-value pairs?
*   **Answer:** Headers
*   **Question:** What separates the headers from the body in an HTTP message?
*   **Answer:** Empty Line

### Task 5 & 6: Request Anatomy
*   **Question:** What is the first part of an HTTP request, containing the method, path, and version?
*   **Answer:** Request Line
*   **Question:** Which HTTP method is used to fetch data without making changes?
*   **Answer:** GET
*   **Question:** Which HTTP method is used to partially update a resource?
*   **Answer:** PATCH
*   **Question:** Which HTTP method retrieves only headers and not the full content?
*   **Answer:** HEAD
*   **Question:** Which HTTP version introduced the QUIC protocol for faster connections?
*   **Answer:** HTTP/3
*   **Question:** Which request header shares info about the browser making the request?
*   **Answer:** User-Agent
*   **Question:** Which request header indicates the URL the request came from?
*   **Answer:** Referer
*   **Question:** Which request body format is used for uploading files or images?
*   **Answer:** multipart/form-data

### Task 7 & 8: Response Anatomy
*   **Question:** What is the first line of an HTTP response, including the version, status code, and reason phrase?
*   **Answer:** Status Line
*   **Question:** Which status code category indicates a problem with the user’s request?
*   **Answer:** Client Error Responses (400-499)
*   **Question:** Which status code means the requested resource has been permanently moved to a new URL?
*   **Answer:** 301
*   **Question:** Which response header tells the client what kind of content they’re getting?
*   **Answer:** Content-Type
*   **Question:** Which response header allows the server to send cookies to the client?
*   **Answer:** Set-Cookie
*   **Question:** What two flags help keep cookies secure?
*   **Answer:** HttpOnly and Secure
*   **Question:** Where does the actual data (HTML, JSON, images) live in an HTTP response?
*   **Answer:** Response Body

### Task 9: Security Headers
*   **Question:** Which security header helps mitigate against Cross-Site Scripting (XSS)?
*   **Answer:** Content-Security-Policy
*   **Question:** Which security header ensures browsers always connect over HTTPS?
*   **Answer:** Strict-Transport-Security
*   **Question:** Which security header directive prevents the browser from guessing the MIME type?
*   **Answer:** nosniff
*   **Question:** Which referrer policy only sends information if the protocol stays the same?
*   **Answer:** strict-origin

### Task 10: Practical Task
*   **Action:** Successfully simulated a sequence of HTTP GET and POST requests using the web emulator.
*   **Flag Captured:** `THM{HTTP_MESSAGES_MASTERED}`

---

## Final Conclusion
The security of a web application is predicated on the strict validation of the HTTP dialogue. By understanding the anatomy of messages and the categorical logic of status codes, an administrator can identify systemic failures and logic gaps. Implementation of security headers provides the final "Vajra-Shield," ensuring that even if the application logic is interrogated, the browser remains constrained within a safe execution policy.