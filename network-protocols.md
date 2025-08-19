# Network Protocols

Understanding network protocols is fundamental for SOC analysts.  
Most security alerts and attacks leave their footprints in network traffic.  
By mastering the basics, you’ll detect threats faster.  

---

## 🔹 TCP vs UDP

**TCP (Transmission Control Protocol)**  
- ✅ Connection-based (handshake required)  
- ✅ Reliable — guarantees ordered delivery  
- ✅ Suitable for large file transfers  
- ❌ Slightly slower due to error-checking  

**UDP (User Datagram Protocol)**  
- ✅ Connectionless (no handshake)  
- ✅ Faster, lightweight  
- ✅ Used in DNS, VoIP, streaming  
- ❌ No guarantee of delivery  

**Why it matters for SOC:**  
- TCP anomalies → brute force attempts, exfiltration  
- UDP anomalies → DNS tunneling, malware beaconing  

---

## 🔹 Common Ports & Their Functions

| Port | Protocol | Function | SOC Relevance |
|------|----------|----------|---------------|
| **21** | FTP | File transfer | Often exploited for credential theft |
| **22** | SSH | Secure remote login | Monitor for brute force attempts |
| **23** | Telnet | Remote login (insecure) | Deprecated but still seen in IoT attacks |
| **25** | SMTP | Outgoing email | Spam / phishing detection |
| **53** | DNS | Domain resolution | DNS tunneling, C2 detection |
| **80** | HTTP | Web browsing (unencrypted) | Malware delivery, cleartext data |
| **110** | POP3 | Email retrieval | Legacy usage |
| **139** | NetBIOS | LAN communication | Reconnaissance, lateral movement |
| **143** | IMAP | Email sync | Email-based attacks |
| **443** | HTTPS (SSL/TLS) | Secure web browsing | Encrypted malware traffic, phishing sites |
| **445** | SMB | File sharing | Ransomware lateral spread |
| **3306** | MySQL | Database access | Database exfiltration |
| **3389** | RDP | Remote desktop | Unauthorized access, ransomware |

---

## 🔹 Why This Matters for SOC Analysts

- 📌 **Unusual DNS queries** → possible tunneling or malware beaconing  
- 📌 **Failed SSH logins** → brute-force attempt  
- 📌 **Unexpected SMB traffic** → lateral movement within network  
- 📌 **Suspicious RDP connections** → unauthorized remote access  

---

## 🔹 ARP and MAC Concepts  

### 🛰️ ARP (Address Resolution Protocol)  
- Resolves **IP addresses into MAC addresses** within the same LAN.  
- **Workflow:**  
  1. Device checks its **ARP cache**.  
  2. If no entry is found, it sends an **ARP Request** → *“Who has this IP? Tell me your MAC.”*  
  3. The device with that IP responds with an **ARP Reply** (its MAC address).  

**SOC Relevance:**  
- Very important in **Wireshark packet analysis**.  
- **Suspicious Indicators (ARP Poisoning):**  
  - Multiple MACs bound to one IP  
  - Unusual or frequent ARP replies  
  - Sudden redirection of traffic  
- Often used in **Man-in-the-Middle (MITM)** attacks.  

---

### 💻 MAC Address (Media Access Control)  
- A **unique 48-bit identifier** assigned to each network interface card (NIC).  
- Format: `00:1A:2B:3C:4D:5E`  

**Structure:**  
- First 3 bytes → **OUI (Organizationally Unique Identifier)** = vendor code (e.g., Intel, Cisco).  
- Last 3 bytes → **UAA (Universally Administered Address)** = device-specific identifier.  

**Functions:**  
- Identifies devices uniquely in a LAN.  
- Helps prevent unwanted access (e.g., via **MAC filtering**).  
- Used for device tracking and security monitoring.  

---

### 🛠️ How to Find MAC Address
1. Open the **search bar** on your device.  
2. Type `"cmd"` and open the Command Prompt.  
3. Run: ipconfig /all
4. Look for the line labeled **“Physical Address”** → this is your MAC.  

✅ Example: `00:1A:2B:3C:4D:5E`  
- `00:1A:2B` → Vendor (Intel)  
- `3C:4D:5E` → Unique device part  

---



