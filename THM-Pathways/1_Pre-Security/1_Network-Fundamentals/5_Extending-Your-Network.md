# Technical Learning Report: Extending Your Network

| Attribute            | Details                                        |
| :------------------- | :--------------------------------------------- |
| **Platform**         | TryHackMe                                      |
| **Course Path**      | Pre-Security / Network Fundamentals            |
| **Topic**            | Extending Your Network                         |

---

## Executive Summary
This report deconstructs the methodologies used to extend network boundaries while maintaining security integrity. The analysis focuses on the transition from private intranets to public-facing services, the implementation of rigorous filtering through firewalls, and the creation of secure logical overlays via Virtual Private Networks (VPNs).

**Core Objectives Identified:**
1.  **Boundary Transition:** Mapping external requests to internal resources through Network Address Translation (NAT) derivatives.
2.  **Filtering Logic:** Categorizing firewall architectures based on their depth of packet and connection inspection.
3.  **Secure Tunneling:** Evaluating protocols that facilitate private communication over untrusted public infrastructure.
4.  **Hardware Segmentation:** Distinguishing between physical and logical isolation within Local Area Network (LAN) environments.

---

## Technical Analysis

### 01. Boundary Access: Port Forwarding
Port forwarding acts as a directional pointer configured at the network gateway (router). Because private IP addresses are non-routable on the global internet, port forwarding creates a static map that redirects specific inbound traffic from a public-facing port to a designated internal host. This effectively transforms an isolated intranet service into a globally accessible resource.

### 02. Perimeter Defense: Firewall Architectures
Firewalls serve as the primary defensive barrier, performing deep packet inspection to permit or deny traffic based on a predefined security policy. They primarily operate at Layer 3 (Network) and Layer 4 (Transport) of the OSI model.

*   **Stateless Firewalls:** These utilize static rules to inspect individual packets in isolation. They are highly efficient for handling high-volume traffic but lack the context of the overall connection state.
*   **Stateful Firewalls:** These track the entire lifecycle of a connection. By monitoring the behavior and history of a session, they can dynamically allow or block traffic based on whether the communication follows a legitimate established pattern.

### 03. Secure Extensions: VPN Technology
Virtual Private Networks (VPNs) create an encrypted "tunnel" across public infrastructure, allowing remote nodes to appear as part of a local private network. 
*   **PPP (Point-to-Point Protocol):** A foundational technology used for authentication and data encryption.
*   **IPSec (Internet Protocol Security):** A robust framework that encrypts data within the existing IP framework, providing strong security for site-to-site and remote access connections.

### 04. LAN Infrastructure and Segmentation
Modern LAN environments rely on a hierarchy of hardware to manage data flow:
*   **Routers:** Dedicated Layer 3 devices responsible for "routing"—the process of determining the optimal path for data to travel between disparate networks.
*   **Switches:** Devices that facilitate internal connectivity. While Layer 2 switches use MAC addresses for local delivery, Layer 3 switches possess the sophisticated logic required to perform routing functions.
*   **VLANs (Virtual LANs):** A logical segmentation technique that partitions a single physical switch into multiple isolated networks, ensuring that sensitive departments (e.g., Accounting) remain inaccessible to others (e.g., Sales).

---

## Task Completion and Evidence

### Task 1: Introduction to Port Forwarding
*   **Question:** What is the name of the device that is used to configure port forwarding?
*   **Answer:** Router

### Task 2: Firewalls 101
*   **Question:** What layers of the OSI model do firewalls operate at?
*   **Answer:** 3 & 4
*   **Question:** What category of firewall inspects the entire connection?
*   **Answer:** Stateful
*   **Question:** What category of firewall inspects individual packets?
*   **Answer:** Stateless

### Task 3: Practical - Firewall
Implementation of firewall rules to distinguish between legitimate service traffic and malicious intrusion attempts.
![FIGURE 01: Configuring firewall rules to filter malicious traffic based on protocol standards](Assets/EYN-FIREWALL.png)
*   **Flag Captured:** THM{FIREWALLS_RULE}

### Task 4: VPN Basics
*   **Question:** What VPN technology only encrypts and provides the authentication of data?
*   **Answer:** PPP
*   **Question:** What VPN technology uses the IP framework?
*   **Answer:** IPSec

### Task 5: LAN Networking Devices
*   **Question:** What is the verb for the action that a router does?
*   **Answer:** Routing
*   **Question:** What are the two different layers of switches?
*   **Answer:** Layer 2, Layer 3

### Task 6: Practical - Network Simulator
Verification of end-to-end connectivity and protocol handshake sequences within a simulated environment.
![FIGURE 02: Network simulation demonstrating end-to-end packet delivery and connection handshakes](Assets/EYN-FLAG.png)
*   **Flag Captured:** THM{YOU'VE_GOT_DATA}
*   **Question:** How many HANDSHAKE entries are there in the Network Log?
*   **Answer:** 5

---

## Final Conclusion
Extending a network safely requires a layered approach. Connectivity is established through routing and port forwarding, while security is maintained through firewall inspection and VPN encryption. The ultimate goal of these technologies is to ensure that logical boundaries remain intact even when physical infrastructure is shared or expanded.