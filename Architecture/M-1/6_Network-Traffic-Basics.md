# Technical Learning Report: Network Traffic Basics

| Attribute            | Details                                        |
| :------------------- | :--------------------------------------------- |
| **Platform**         | TryHackMe                                      |
| **Course Path**      | Networking			                            |
| **Topic**            | Network Traffic Basics                         |

---

## Executive Summary
This report deconstructs the foundational principles of Network Traffic Analysis (NTA). The analysis focuses on the transition from high-level metadata logging to deep packet inspection (DPI), enabling the identification of hidden adversarial intent. By examining traffic sources, directional flows, and various capture methodologies, this report establishes a framework for forensic reconstruction and real-time threat detection.

**Core Objectives Identified:**
1.  **Observability vs. Logging:** Distinguishing between superficial connection logs and the forensic truth contained within packet payloads.
2.  **Traffic Directionality:** Analyzing North-South (perimeter-crossing) and East-West (internal/lateral) traffic patterns to identify unauthorized movement.
3.  **Capture Instrumentation:** Evaluating the technical trade-offs between hardware-based signal duplication (TAPs) and software-based port mirroring (SPAN).

---

## Technical Analysis

### 01. The Tactical Vigil: Protocol Observables
Effective traffic analysis requires visibility into every layer of the communication stack. While standard firewalls log connection attempts, NTA provides insight into the actual data being exchanged.
*   **Application Layer:** NTA reveals the payload—the actual content of the communication. This is critical for detecting DNS Tunneling, where command and control (C2) instructions are smuggled within encoded TXT records.
*   **Transport Layer:** By monitoring sequence numbers in TCP headers, analysts can detect session hijacking. Sudden, non-linear jumps in these increments indicate unauthorized packet injection.
*   **Internet Layer:** Analysis of fragment offsets and total length fields allows for the detection of fragmentation attacks, a technique used by adversaries to evade Intrusion Detection Systems (IDS).
*   **Link Layer:** Monitoring ARP traffic provides visibility into hardware identity. Inconsistencies between MAC addresses and IP mappings reveal potential ARP poisoning or identity spoofing.

### 02. Flow Mechanics and Directionality
Traffic is categorized by its source and its path through the network hierarchy.
*   **Sources:** Traffic originates from **Endpoints** (servers, workstations, IoT devices) and passes through **Intermediary Devices** (switches, routers, firewalls).
*   **North-South (N-S):** Traffic entering or exiting the LAN via the firewall. This is the traditional focus of perimeter security.
*   **East-West (E-W):** Traffic moving laterally within the LAN. This is often monitored less strictly but is vital for detecting an attacker's movement between internal systems following an initial breach.

### 03. Observation Methodologies
Capturing traffic requires the creation of a "mirror" of the data stream without disrupting production performance.
*   **Network TAP:** A physical, inline hardware device that duplicates electrical or optical signals. TAPs are passive, lossless, and have zero impact on network performance.
*   **Port Mirroring (SPAN):** A software-based approach configured on switches. While more flexible than TAPs, SPAN can result in packet loss if the switch's CPU becomes overwhelmed by high traffic volumes.
*   **Network Statistics:** Protocols like **NetFlow** and its vendor-neutral successor **IPFIX** provide a "shadow" of the traffic. They offer metadata (who, when, where) without the heavy storage requirements of full packet capture (which can require ~10.8 TB per day for a 1 Gbps line).

---

## Task Completion and Evidence

### Task 2: The Purpose of Network Traffic Analysis
*   **Question:** What is the name of the technique used to smuggle C2 commands via DNS?
*   **Answer:** DNS tunneling

### Task 3: What Network Traffic Can We Observe?
*   **Question:** What is the size of the ZIP attachment included in the HTTP response?
*   **Answer:** 10485760
*   **Question:** Which attack do attackers use to try to evade an IDS?
*   **Answer:** fragmentation
*   **Question:** What field in the TCP header can we use to detect session hijacking?
*   **Answer:** sequence number

### Task 4: Network Traffic Sources and Flows
*   **Question:** Which category of devices generates the most traffic in a network?
*   **Answer:** endpoint
*   **Question:** Before an SMB session can be established, which service needs to be contacted first for authentication?
*   **Answer:** kerberos
*   **Question:** What does TLS stand for?
*   **Answer:** Transport Layer Security

### Task 5: How Can We Observe Network Traffic?
*   **Practical Exercise 1 (HTTP Traffic):** Identified malicious payload through packet inspection.
*   **Flag Captured:** `THM{FoundTheMalware}`
*   **Practical Exercise 2 (DNS Traffic):** Decoded DNS TXT records to reveal hidden instructions.
*   **Flag Captured:** `THM{C2CommandFound}`

---

## Final Conclusion
Network Traffic Analysis is the only method to achieve absolute visibility into systemic intent. By deconstructing transient signals into forensic evidence, analysts can identify threats that bypass traditional perimeter defenses. Sovereignty over the network is attained when internal lateral flows (East-West) are monitored with the same rigor as external entry points (North-South), ensuring that no movement remains unobserved.

