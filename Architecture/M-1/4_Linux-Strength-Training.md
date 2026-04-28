# Technical Learning Report: Linux Strength Training

| Attribute            | Details                                        |
| :------------------- | :--------------------------------------------- |
| **Platform**         | TryHackMe                                      |
| **Course Path**      | Linux Fundamentals / Security Research         |
| **Topic**            | Linux Strength Training (Operations)  |

---

## Executive Summary
This report deconstructs the advanced operational and forensic capabilities of the Linux command line. Moving beyond basic navigation, the analysis focuses on granular data discovery, cryptographic integrity verification, the bypass of data obfuscation (encoding), and the systematic breaching of encrypted containers and relational databases.

**Core Objectives Identified:**
1.  **Precision Navigation:** Utilizing logical filters to isolate specific data objects based on metadata and internal content.
2.  **Cryptographic Forensics:** Identifying and reversing one-way hash functions and symmetric encryption shields.
3.  **Data Extraction:** Navigating structured query language (SQL) environments to retrieve encapsulated application data.

---

## Technical Analysis

### 01. Advanced Discovery and Navigation
Precise data location in a complex filesystem requires the use of metadata-aware search tools. 
*   **The Find Utility:** This tool allows for the extraction of absolute paths based on conditions such as file size, ownership, and timestamps. A critical technique for security researchers is the suppression of permission errors using `2>/dev/null`, which purifies the output of navigational noise.
*   **Content-Based Search:** Using `grep -iRl` allows an auditor to locate files based on internal keyword signatures rather than filenames.

### 02. Integrity and Encoding (Hashing and Base64)
Data representation and integrity are verified through hashing and encoding schemes.
*   **Hashing:** A one-way cryptographic function used for integrity checking. Algorithms like MD5, MD4, and SHA-1 are considered legacy/weak due to collision vulnerabilities, while SHA-256 remains the modern standard. Cracking these hashes involves brute-force simulation using wordlists and tools like John the Ripper.
*   **Encoding:** Base64 is used for binary-to-text representation. It is a reversible translation rather than a security shield. Decoding is performed via the `base64 -d` utility.

### 03. The Cryptographic Siege (GPG Encryption)
Symmetric encryption provides a shield for data using a private key. 
*   **GPG Encryption:** Utilizing `gpg` with the `--symmetric` flag and specific ciphers (e.g., AES-256) renders data unintelligible to those without the key.
*   **Bypassing Encryption:** If the key is lost or unknown, the auditor must first use `gpg2john` to translate the encrypted blob into a format compatible with brute-force tools. This converts a static "shield" into an active "target" for wordlist attacks.

### 04. Relational Database Forensics
Databases serve as the repository for application logic and sensitive records.
*   **SQL Interaction:** Reading local or remote SQL databases requires an understanding of relational structures.
*   **The Extraction Pipeline:** The process involves starting the database service, selecting the target context (`USE`), auditing the table structure (`DESCRIBE`), and finally extracting the records (`SELECT *`).

---

## Task Completion and Evidence

### Task 2: Finding Your Way Around Linux
*   **Question:** What is the correct option for finding files based on group?
*   **Answer:** `-group`
*   **Question:** Find a file for user "francis" with a size of 52kb in `/home/francis/`.
*   **Answer:** `find /home/francis -type f -user francis -size 52k`
*   **Question:** Search for a keyword in `/home/topson/chatlogs`.
*   **Answer File Found:** `2019-10-11`
*   **Flag Captured:** `Flag{81726350827fe53g}`

### Task 3: Working with Files
*   **Question:** Move all files in a directory to `/home/francis/logs`.
*   **Answer:** `mv * /home/francis/logs`
*   **Question:** Transfer `script.py` to a remote machine (`192.168.10.5`) as user "john".
*   **Answer:** `scp /home/james/Desktop/script.py john@192.168.10.5:/home/john/scripts`
*   **Question:** How would you rename a folder named `-logs` to `-newlogs`?
*   **Answer:** `mv -- -logs -newlogs`
    *   *Note: The `--` operator is used to stop the shell from interpreting the leading dash as a command argument.*
*   **Flag Captured:** `Flag{234@i4s87u5hbn$3}`

### Task 4: Hashing Introduction
*   **Question:** Crack the attached MD5 hash.
*   **Answer:** `secret123`
*   **Question:** Identify the hash type in `hashA.txt`.
*   **Answer:** `MD4` (Password: `admin`)
*   **Question:** Identify the hash type in `hashB.txt`.
*   **Answer:** `SHA-1` (Password: `letmein`)
*   **Question:** Crack `hashC.txt` using a `.mnf` wordlist.
*   **Answer:** `unacvaolipatnuggi`

### Task 5: Decoding Base64
*   **Question:** What tool allows for the decoding of base64 strings?
*   **Answer:** `base64`
*   **Flag Captured (Encoded.txt):** `john`

### Task 6 & 7: GPG Encryption and Cracking
*   **Question:** Encrypt `history_logs.txt` using the AES-128 scheme.
*   **Answer:** `gpg --cipher-algo AES-128 --symmetric history_logs.txt`
*   **Question:** Decrypt a GPG file.
*   **Answer:** `gpg filename.gpg`
*   **Question:** Crack the password for `personal.txt.gpg` using a wordlist reversed by `tac`.
*   **Answer:** `valamanezivonia`
*   **Flag Captured (Layer4.txt):** `Flag{B07$f854f5ghg4s37}`

### Task 8: Reading SQL Databases
*   **Action:** Logged into MySQL and queried the `employees.sql` database.
*   **Flag Captured:** `Flag{13490AB8}`

---

## Final Conclusion
Sovereignty over the Linux environment is achieved by the systematic deconstruction of data layers. By mastering advanced navigation, cryptographic reversing, and database extraction, an auditor transitions from a passive observer to an active forensic authority. The ability to bypass masks (encoding) and shatter shields (encryption) ensures that data integrity is always verifiable and secrets are always accessible.
