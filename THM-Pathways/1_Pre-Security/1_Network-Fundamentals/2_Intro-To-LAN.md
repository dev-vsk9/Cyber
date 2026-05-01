# Technical Learning Report: Intro to LAN

| Attribute            | Details                                        |
| :------------------- | :--------------------------------------------- |
| **Platform**         | TryHackMe                                      |
| **Course Path**      | Pre-Security / Network Fundamentals            |
| **Topic**            | Intro to LAN (Local Area Network)              |

---

## Executive Summary
This report deconstructs the architectural design and functional protocols of Local Area Networks (LANs). The analysis explores how physical topologies dictate network resilience, how subnetting establishes logical boundaries for security and efficiency, and how dynamic protocols like ARP and DHCP manage device identity and address allocation.

**Core Objectives Identified:**
1.  **Topological Analysis:** Evaluating the efficiency and failure points of Star, Bus, and Ring network designs.
2.  **Logical Segmentation:** Utilizing subnetting to divide a network into manageable, secure zones.
3.  **Dynamic Identity Binding:** Analyzing the mechanisms that resolve logical addresses to physical hardware and automate IP management.

---

## Technical Analysis

### 01. LAN Topologies and Hardware
The physical and logical layout of a network, known as its topology, determines its reliability and scalability.
*   **Star Topology:** The modern standard. Devices connect to a central hub or switch. This design prevents cascade failures; if one node or cable fails, the rest of the network remains operational. However, the central device represents a single point of failure.
*   **Bus Topology:** An older, cost-effective design where all devices share a single backbone cable. It is highly susceptible to bottlenecks and systemic failure if the main cable is severed.
*   **Ring Topology:** devices are connected in a loop. Data travels in one direction. While troubleshooting is straightforward, a single broken link destroys the entire circuit.
*   **The Switching Advantage:** Modern LANs prefer switches over hubs. A switch acts as an intelligent aggregator, tracking MAC addresses to send data only to the intended recipient, thereby reducing network noise and increasing performance.

### 02. Subnetting and Boundaries
Subnetting is the process of slicing a large network into smaller, autonomous subnets. 
*   **The Subnet Mask:** A 32-bit number (expressed in four octets ranging from 0-255) used to define the boundary between the network portion and the host portion of an IP address.
*   **Address Types:**
    *   **Network Address:** Identifies the start of the network.
    *   **Host Address:** Identifies a specific device within that network.
    *   **Default Gateway:** The "Exit" device (typically a router) that allows traffic to leave the local sanctuary for external networks.
*   **Security Principle:** Subnetting enhances security by preventing unauthorized communication between different departments or security zones (e.g., separating public Wi-Fi from internal banking systems).

### 03. The Dynamic Binding Protocols (ARP & DHCP)
Identity on a LAN is maintained through the constant resolution of logical names to physical bodies and the automated management of those names.

#### ARP (Address Resolution Protocol)
ARP is the bridge between Layer 3 (IP) and Layer 2 (MAC). 
*   **The Process:** When a device knows an IP but needs the physical MAC, it sends an **ARP Request** (a broadcast "shout" to all nodes). The owner responds with an **ARP Reply**.
*   **ARP Cache:** Devices store these mappings in a temporary ledger to avoid repetitive broadcasts. 
*   **Forensic Note:** Because ARP is stateless and trusts unrequested replies, it is a primary target for redirection attacks (ARP Spoofing).

#### DHCP (Dynamic Host Configuration Protocol)
DHCP automates the assignment of IP addresses, preventing the chaos of manual configuration errors.
*   **The D-O-R-A Cycle:**
    1.  **Discover:** The client looks for a server.
    2.  **Offer:** The server suggests an IP address.
    3.  **Request:** The client asks to use that IP.
    4.  **Acknowledgment (ACK):** The server confirms and finalizes the lease.

---

## Task Completion and Evidence

### Task 1: Introducing LAN Topologies
*   **Question:** What does LAN stand for?
*   **Answer:** Local Area Network
*   **Question:** What is the verb given to the job that Routers perform?
*   **Answer:** Routing
*   **Question:** What device is used to centrally connect multiple devices and transmit data to the correct location?
*   **Answer:** Switch
*   **Question:** What topology is cost-efficient to set up?
*   **Answer:** Bus Topology
*   **Question:** What topology is expensive to set up and maintain?
*   **Answer:** Star Topology
*   **Flag Captured:** `THM{TOPOLOGY_FLAWS}`

### Task 2: A Primer on Subnetting
*   **Question:** What is the technical term for dividing a network up into smaller pieces?
*   **Answer:** Subnetting
*   **Question:** How many bits are in a subnet mask?
*   **Answer:** 32
*   **Question:** What is the range of a section (octet) of a subnet mask?
*   **Answer:** 0-255
*   **Question:** What address is used to identify the start of a network?
*   **Answer:** Network Address
*   **Question:** What is the name used to identify the device responsible for sending data to another network?
*   **Answer:** Default Gateway

### Task 3: ARP
*   **Question:** What does ARP stand for?
*   **Answer:** Address Resolution Protocol
*   **Question:** What category of ARP Packet asks a device whether or not it has a specific IP address?
*   **Answer:** Request
*   **Question:** What address is used as a physical identifier for a device on a network?
*   **Answer:** MAC Address

### Task 4: DHCP
*   **Question:** What type of DHCP packet is used by a device to retrieve an IP address?
*   **Answer:** DHCP Discover
*   **Question:** What type of DHCP packet does a device send once it has been offered an IP address?
*   **Answer:** DHCP Request
*   **Question:** What is the last DHCP packet that is sent to a device from a DHCP server?
*   **Answer:** DHCP ACK

---

## Final Conclusion
LAN sovereignty is established through structured design and dynamic management. The physical Star topology provides resilience, while logical subnetting provides segmentation. Identity is resolved through ARP and assigned via the DHCP DORA cycle. A secure network is one where these "bindings" (IP to MAC) and "boundaries" (Subnets) are actively monitored and audited against unauthorized changes.