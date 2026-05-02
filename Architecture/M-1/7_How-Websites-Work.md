# Technical Learning Report: How Websites Work

| Attribute            | Details                                        |
| :------------------- | :--------------------------------------------- |
| **Platform**         | TryHackMe                                      |
| **Course Path**      | Introduction to Web Development                |
| **Topic**            | How Websites Work (Architecture & Security)    |

---

## Executive Summary
This report deconstructs the foundational mechanics of web applications, focusing on the interaction between client-side browsers and remote servers. The analysis explores the structural role of HTML, the dynamic capabilities of JavaScript, and the inherent security risks associated with frontend transparency. Key vulnerabilities analyzed include the accidental exposure of sensitive data in source code and the subversion of page logic through HTML injection.

**Core Objectives Identified:**
1.  **Frontend/Backend Duality:** Distinguishing between rendered components (client-side) and processed requests (server-side).
2.  **Structural Governance:** Mastering the Document Object Model (DOM) through HTML elements and attributes.
3.  **Input Integrity:** Evaluating the critical necessity of input sanitization to prevent the collapse of the boundary between data and instruction.

---

## Technical Analysis

### 01. The Blueprint: Web Architecture
Web applications operate on a request-response model. The **Front End** (Client-Side) is the component rendered by the user's browser, while the **Back End** (Server-Side) processes logic and serves data. 
*   **The Transparency :** Because the frontend is interpreted locally by the browser, the entire structural blueprint (HTML) and logic engine (JavaScript) are fully visible to the end-user. This visibility serves as the primary starting point for any web-based security interrogation.

### 02. Structural Skeleton (HTML)
HTML (HyperText Markup Language) defines the hierarchy and structure of a page.
*   **Elements and Tags:** Building blocks like `<h1>` (headings) and `<p>` (paragraphs) categorize content.
*   **Attributes:** Metadata like `src` (specifying image locations) or `id` (providing unique identifiers) allow the browser and scripts to interact with specific components.
*   **Forensic Reality:** Developers often leave artifacts in HTML comments that remain invisible on the rendered page but are accessible via "View Page Source."

### 03. Functional Engine (JavaScript)
JavaScript (JS) transforms static structure into an interactive experience.
*   **Dynamic Updates:** JS allows real-time manipulation of the DOM without requiring a full page refresh.
*   **Event-Driven Logic:** Functionality is triggered by user interactions, such as `onclick` or `onhover`.
*   **Security Principle:** Logic placed solely in client-side JavaScript is fundamentally untrusted, as users can modify or bypass these scripts within their own browser environments.

### 04. The Breach: Exposure and Injection
Security failures in web applications often stem from a lack of strict boundaries between developer intent and user control.
*   **Sensitive Data Exposure:** Occurs when clear-text information—such as credentials or administrative links—is accidentally included in the frontend source code. This represents a failure in information lifecycle management.
*   **HTML Injection:** A vulnerability arising from the lack of input sanitization. When a website displays unfiltered user input, the browser may interpret that data as executable HTML or JavaScript code. This allows an adversary to redefine the page’s appearance or functionality by injecting malicious tags.

---

## Task Completion and Evidence

### Task 1: How Websites Work
*   **Question:** What term best describes the component of a web application rendered by your browser?
*   **Answer:** Front End

### Task 2: HTML
*   **Question:** Fix the broken image on the cat website to reveal the hidden text.
*   **Answer:** HTMLHERO
*   **Question:** Add a dog image (img/dog-1.png) on line 11. What is the text in the dog image?
*   **Answer:** DOGHTML

### Task 3: JavaScript
*   **Question:** Add JavaScript to change the "demo" element's content to "Hack the Planet".
*   **Answer:** JSISFUN
*   **Question:** Add a button that changes the element's text to "Button Clicked".
*   **Answer:** No answer needed (Practical exercise completed).

### Task 4: Sensitive Data Exposure
*   **Question:** View the provided website link. What is the password hidden in the source code?
*   **Answer:** testpasswd

### Task 5: HTML Injection
*   **Question:** Inject HTML to show a malicious link to `http://hacker.com`.
*   **Answer:** HTML_INJ3CTI0N

---

## Final Conclusion
Sovereignty over a web environment requires a "Zero Trust" approach toward the client. Because the frontend is a transparent skeleton, security cannot rely on obfuscation or client-side logic. Effective defense is achieved only through rigorous server-side sanitization of all user inputs and the systematic removal of sensitive metadata from the public source code.

