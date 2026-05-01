# Technical Learning Report: The OSI Model

| Attribute            | Details                                        |
| :------------------- | :--------------------------------------------- |
| **Platform**         | TryHackMe                                      |
| **Course Path**      | Pre-Security / Network Fundamentals            |
| **Topic**            | The OSI Model (Open Systems Interconnection)   |

---

## Executive Summary
This report deconstructs the Open Systems Interconnection (OSI) model, a standardized seven-layer framework that governs how data is handled across a network. The analysis explores the transition from raw electrical signals at the physical layer to high-level user interactions at the application layer, focusing on the specialized roles of each layer in ensuring data integrity, pathfinding, and standardization.

**Core Objectives Identified:**
1.  **Standardization of Flow:** Analyzing how modular layers prevent vendor incompatibility and systemic troubleshooting blindness.
2.  **Encapsulation Logic:** Distinguishing between the "Lower Triad" (Addressing and Hardware) and the "Upper Quadrant" (Logic and Presentation).
3.  **Protocol Reliability:** Evaluating the trade-off between guaranteed data accuracy (TCP) and high-velocity transmission (UDP).

---

## Technical Analysis

### 01. The Lower Layers (Layers 1–3)
The lower layers serve as the physical and logical foundation of a network connection. Reliability here is a prerequisite for all higher-level communication.
*   **Layer 1 (Physical):** Governs hardware components and electrical signals. Data is transmitted as binary (1s and 0s) across media such as Ethernet cables.
*   **Layer 2 (Data Link):** Manages physical addressing. Every device is identified by a unique Media Access Control (MAC) address burnt into its Network Interface Card (NIC). 
*   **Layer 3 (Network):** Responsible for routing and pathfinding. This layer uses IP addresses to determine the most optimal path across disparate networks using protocols such as OSPF and RIP.

### 02. The Upper Layers (Layers 4–7)
The upper layers focus on the maintenance of meaning and the interface between human intent and machine logic.
*   **Layer 4 (Transport):** Determines how data is transmitted. It chooses between Transmission Control Protocol (TCP) for guaranteed accuracy (essential for email and downloads) and User Datagram Protocol (UDP) for speed (essential for video streaming).
*   **Layer 5 (Session):** Manages the lifecycle of a connection. When a connection is successfully established, a "session" is created to synchronize and maintain the dialogue.
*   **Layer 6 (Presentation):** Acts as a translator. It ensures that data is formatted correctly, compressed, and encrypted (e.g., HTTPS) so the application layer can process it.
*   **Layer 7 (Application):** The interface users interact with directly through software. It provides the protocols and rules for web browsers, email clients, and other Graphical User Interfaces (GUI).

---

## Task Completion and Evidence

### Task 2: Layer 1 - Physical
*   **Question:** What is the name of this Layer?
*   **Answer:** Physical
*   **Question:** What is the name of the numbering system that is both 0's and 1's?
*   **Answer:** Binary
*   **Question:** What is the name of the cables that are used to connect devices?
*   **Answer:** Ethernet Cables

### Task 3: Layer 2 - Data Link
*   **Question:** What is the name of this Layer?
*   **Answer:** Data Link
*   **Question:** What is the name of the piece of hardware that all networked devices come with?
*   **Answer:** Network Interface Card

### Task 4: Layer 3 - Network
*   **Question:** What is the name of this Layer?
*   **Answer:** Network
*   **Question:** Will packets take the most optimal route across a network? (Y/N)
*   **Answer:** Y
*   **Question:** What does the acronym "OSPF" stand for?
*   **Answer:** Open Shortest Path First
*   **Question:** What does the acronym "RIP" stand for?
*   **Answer:** Routing Information Protocol
*   **Question:** What type of addresses are dealt with at this layer?
*   **Answer:** IP Addresses

### Task 5: Layer 4 - Transport
*   **Question:** What is the name of this Layer?
*   **Answer:** Transport
*   **Question:** What does TCP stand for?
*   **Answer:** Transmission Control Protocol
*   **Question:** What does UDP stand for?
*   **Answer:** User Datagram Protocol
*   **Question:** What protocol guarantees the accuracy of data?
*   **Answer:** TCP
*   **Question:** What protocol doesn't care if data is received or not by the other device?
*   **Answer:** UDP
*   **Question:** What protocol would an application such as an email client use?
*   **Answer:** TCP
*   **Question:** What protocol would an application that downloads files use?
*   **Answer:** TCP
*   **Question:** What protocol would an application that streams video use?
*   **Answer:** UDP

### Task 6: Layer 5 - Session
*   **Question:** What is the name of this layer?
*   **Answer:** Session
*   **Question:** What is the technical term for when a connection is successfully established?
*   **Answer:** Session

### Task 7: Layer 6 - Presentation
*   **Question:** What is the name of this Layer?
*   **Answer:** Presentation
*   **Question:** What is the main purpose that this Layer acts as?
*   **Answer:** Translator

### Task 8: Layer 7 - Application
*   **Question:** What is the name of this Layer?
*   **Answer:** Application
*   **Question:** What is the technical term that is given to the name of the software that users interact with?
*   **Answer:** Graphical User Interface

---

## Final Conclusion
The OSI model establishes a vertical dependency where no layer can function correctly if the layer below it fails. Troubleshooting necessarily begins at the physical foundation and ascends toward the application. Mastery of this model allows an auditor to isolate failures by distinguishing between hardware issues (Layers 1–2), routing logic (Layer 3), or data presentation and software errors (Layers 6–7).

