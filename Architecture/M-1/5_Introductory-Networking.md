# Technical Learning Report: Introductory Networking

| Attribute            | Details                                        |
| :------------------- | :--------------------------------------------- |
| **Platform**         | TryHackMe                                      |
| **Course Path**      | Networking        		|
| **Topic**            | Introductory Networking                        |

---

## Executive Summary
This report deconstructs the foundational archetypes of network communication and the diagnostic weaponry used to interrogate the grid. The analysis covers the theoretical OSI model, the functional TCP/IP suite, and the mechanics of encapsulation. Furthermore, it details the practical application of ICMP, routing diagnostics, domain registration audits, and the DNS hierarchy.

**Core Objectives Identified:**
1.  **Architectural Mapping:** Distinguishing between theoretical models for diagnostics and implemented engines for real-world traffic.
2.  **Data Persistence Logic:** Understanding the sequential wrapping of data units to ensure integrity across hardware boundaries.
3.  **Standardized Interrogation:** Utilizing industry-standard utilities to resolve host identities, geographic paths, and ownership metadata.

---

## Technical Analysis

### 01. The Archetypal Models (OSI vs. TCP/IP)
Network communication is governed by two primary frameworks that standardize how disparate systems interact.
*   **The OSI Model:** A seven-layer theoretical map used for detailed diagnostics. It enforces modular isolation, allowing changes in physical media (Layer 1) without disrupting application logic (Layer 7).
*   **The TCP/IP Model:** The operational engine of the modern internet. It is a more compact, four-layer version of the OSI model designed by the Department of Defense (DoD) for maximum survivability and resilience under systemic stress.
*   **Identity Duality:** Sovereignty on the grid relies on the bond between the permanent physical fingerprint (Layer 2: MAC address) and the dynamic logical name (Layer 3: IP address).

### 02. The Encapsulation Process
Communication is a systematic descent of user intent into physical matter. 
*   **Sequential Evolution:** Data moves from the application down the stack, becoming a **Segment** or **Datagram** (Layer 4), then a **Packet** (Layer 3), then a **Frame** (Layer 2), and finally raw binary **Bits** (Layer 1).
*   **De-encapsulation:** Upon reception, the target node reverses this process, stripping away metadata headers at each layer until the original application intent is revealed.
*   **Security Invariant:** Encapsulation provides an inherent layer of security by ensuring that each layer only interacts with its relevant metadata, preventing higher-level data corruption.

### 03. Networking Interrogation Tools
The "Vajra-Eye" of a network auditor is achieved through specialized diagnostic utilities that force the grid to reveal its state.
*   **Ping (ICMP Pulse):** A basic probe used to verify node vitality and latency. It acts as the heartbeat of a connection.
*   **Traceroute (Path Mapping):** A diagnostic that forces every intermediate router to identify itself by intentionally expiring packets. It provides a geographic and logical map of the internet's labyrinth.
*   **WHOIS (Registrar Audit):** A query protocol used to determine the ownership, registration dates, and nameserver technical details of a domain.
*   **Dig (DNS Forensic Probe):** A tool for interrogating the Domain Name System hierarchy. It provides high-resolution data on how domain names are translated into IP addresses and tracks the Time-to-Live (TTL) of those records.

---


## Task Completion and Evidence

### Task 2: The OSI Model
**Question:** Which layer would choose to send data over TCP or UDP?
**Answer:** 4
**Question:** Which layer checks received information for corruption?
**Answer:** 2
**Question:** In which layer would data be formatted for transmission?
**Answer:** 2
**Question:** Which layer transmits and receives raw data?
**Answer:** 1
**Question:** Which layer handles encryption, compression, or data transformation?
**Answer:** 6
**Question:** Which layer tracks communications between hosts?
**Answer:** 5
**Question:** Which layer accepts communication requests from applications?
**Answer:** 7
**Question:** Which layer handles logical addressing (IP)?
**Answer:** 3
**Question:** What are bite-sized pieces of data called over TCP?
**Answer:** Segments
**Question:** Which layer would the FTP protocol communicate with?
**Answer:** 7
**Question:** Which transport protocol is best suited for live video?
**Answer:** UDP

### Task 3: Encapsulation
**Question:** Data unit at Layer 2:
**Answer:** Frames
**Question:** Data unit at Layer 4 (UDP):
**Answer:** Datagrams
**Question:** Reciprocal process of receiving a message:
**Answer:** De-encapsulation
**Question:** Layer that adds a trailer during encapsulation:
**Answer:** Data Link
**Question:** Does encapsulation provide extra security?
**Answer:** Aye

### Task 4: The TCP/IP Model
**Question:** Which model was introduced first?
**Answer:** TCP/IP
**Question:** TCP/IP layer for OSI Transport functionality:
**Answer:** Transport
**Question:** TCP/IP layer for OSI Session functionality:
**Answer:** Application
**Question:** Network Interface layer covers Data Link and:
**Answer:** Physical
**Question:** Layer that handles routing:
**Answer:** Internet
**Question:** Nature of the TCP protocol:
**Answer:** Connection-based
**Question:** Meaning of SYN:
**Answer:** Synchronise
**Question:** Second step of the three-way handshake:
**Answer:** SYN/ACK
**Question:** Acknowledgement segment short name:
**Answer:** ACK

### Task 5: Networking Tools - Ping
**Question:** Command to ping BBC:
**Answer:** ping bbc.co.uk
**Question:** IPv4 address of muirlandoracle.co.uk:
**Answer:** 217.160.0.152
**Question:** Switch to change request interval:
**Answer:** -i
**Question:** Switch to restrict to IPv4:
**Answer:** -4
**Question:** Switch for verbose output:
**Answer:** -v

### Task 6: Networking Tools - Traceroute
**Question:** Switch to specify an interface:
**Answer:** -i
**Question:** Switch to use TCP SYN requests:
**Answer:** -T
**Question:** OSI Layer traceroute runs on by default (Windows):
**Answer:** Network (Internet)

### Task 7: Networking Tools - WHOIS
**Question:** Registrant postal code for facebook.com:
**Answer:** 94025
**Question:** First registration date for facebook.com:
**Answer:** 29/03/1997
**Question:** City of registrant for microsoft.com:
**Answer:** Redmond
**Question:** Golf course near Microsoft address:
**Answer:** Bellevue Golf Course
**Question:** Tech Email for microsoft.com:
**Answer:** msnhst@microsoft.com

### Task 8: Networking Tools - Dig
**Question:** DNS Full Name:
**Answer:** Domain Name System
**Question:** First DNS server type queried:
**Answer:** Recursive
**Question:** DNS server containing extension-specific records (.com):
**Answer:** Top-Level Domain
**Question:** The very first place a computer looks for IP mapping:
**Answer:** Hosts File
**Question:** Google's secondary public DNS IP:
**Answer:** 8.8.4.4
**Question:** Dig output for a 24-hour TTL:
**Answer:** 86400

---

## Final Conclusion
Network sovereignty is achieved through the systematic application of layered standards and diagnostic audits. By deconstructing the transition from logical intent to physical transmission and mastering the interrogation of the DNS hierarchy, an administrator ensures that the order of communication is maintained against systemic entropy. This module establishes the Logic-Engine required for advanced network defense and forensic pathfinding.

