# Technical Learning Report: OWASP Top 10 2025 - IAAA Failures

| Attribute            | Details                                        |
| :------------------- | :--------------------------------------------- |
| **Platform**         | TryHackMe                                      |
| **Course Path**      | Web Application Security / OWASP Top 10        |
| **Topic**            | IAAA Failures (A01, A07, A09)                  |

---

## Executive Summary
This report deconstructs the foundational **IAAA (Identity, Authentication, Authorisation, and Accountability)** security model and identifies critical vulnerabilities that arise when this chain is compromised. The analysis focuses on three specific categories from the **OWASP Top 10:2025**: Broken Access Control (A01), Authentication Failures (A07), and Logging & Alerting Failures (A09).

**Core Objectives Identified:**
1.  **Logical Integrity:** Understanding the sequential dependency of the IAAA framework.
2.  **Authorization Enforcement:** Analyzing Insecure Direct Object References (IDOR) and privilege escalation.
3.  **Authentication Resilience:** Examining logic flaws in identity binding and registration.
4.  **Forensic Observability:** Utilizing log analysis to identify brute-force patterns and unauthorized data access.

---

## Technical Analysis

### 01. The IAAA Framework
The IAAA model represents the lifecycle of a user's interaction with a system. Security is maintained only if every step is performed sequentially without bypass:
*   **Identity:** The unique claim of who the user is (e.g., a username).
*   **Authentication:** The verification of that claim (e.g., a password or MFA).
*   **Authorisation:** The determination of what the verified user is permitted to do.
*   **Accountability:** The permanent recording of all actions performed by the user.

### 02. Vulnerability Deep-Dive

#### A01: Broken Access Control (Authorization)
Access control failures occur when the server fails to verify if the authenticated user owns or is permitted to access a specific resource. 
*   **IDOR (Insecure Direct Object Reference):** An attacker manipulates input (like an account ID in a URL) to access resources belonging to other users.
*   **Horizontal Privilege Escalation:** Accessing the data of a user with the same privilege level.
*   **Vertical Privilege Escalation:** Accessing functions reserved for higher-level roles (e.g., an admin panel).

#### A07: Authentication Failures (Identification/Authentication)
These failures occur when the application cannot reliably verify the identity of a user. This often stems from logic flaws, such as case-insensitivity during database lookups that allow "account collisions," or a lack of rate-limiting which facilitates brute-force attacks.

#### A09: Logging & Alerting Failures (Accountability)
A failure in accountability means an attacker can operate within the system without leaving a detectable trail. Without proper logging of authentication events and endpoint access, incident response becomes impossible.

---

## Task Completion and Evidence

### Task 2: What is IAAA?
*   **Question:** What does IAAA stand for?
*   **Answer:** Identity, Authentication, Authorisation, Accountability

### Task 3: A01: Broken Access Control
*   **Question:** If you don't get access to more roles but can view the data of another users, what type of privilege escalation is this?
*   **Answer:** Horizontal
*   **Question:** What is the note you found when viewing the user's account who had more than $1 million?
*   **Answer:** THM{Found.the.Millionare!}

![FIGURE 01: Manipulating accountID parameters to perform an IDOR attack and extract sensitive user notes](Assets/image.png)

### Task 4: A07: Authentication Failures
*   **Question:** What is the flag on the admin user's dashboard?
*   **Answer:** THM{Account.confusion.FTW!}

![FIGURE 02: Exploiting registration logic flaws via username case-variation to bypass administrative authentication](Assets/image-1.png)

### Task 5: A09: Logging & Alerting Failures
*   **Question:** It looks like an attacker tried to perform a brute-force attack, what is the IP of the attacker?
*   **Answer:** 203.0.113.45

![FIGURE 03: Analyzing server access logs to identify source IP addresses involved in high-frequency failed login attempts](Assets/image-2.png)

*   **Question:** Looks like they were able to gain access to an account! What is the username associated with that account?
*   **Answer:** admin
*   **Question:** What action did the attacker try to do with the account? List the endpoint they accessed.
*   **Answer:** /supersecretadminstuff

![FIGURE 04: Forensic investigation of post-authentication logs to track unauthorized access to sensitive administrative endpoints](Assets/image-3.png)

---

## Final Conclusion
Security within a web application is only as strong as its weakest IAAA link. Failure to enforce **Authorization** leads to data leaks via IDOR (A01), while flawed **Authentication** logic permits account takeover (A07). Finally, the absence of **Accountability** via logging (A09) ensures that these breaches remain undetected. A robust security posture requires server-side validation of every request and an immutable audit trail for all high-value actions.