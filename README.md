# Network Protocols — Part 1  
*A SOC Analyst Learning Note*  

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

## 📝 Next Steps  

This is **Part 1: Network Protocols**.  
Coming soon:  
- **Part 2: ARP & MAC Concepts**  
- **Part 3: Advanced Packet Analysis with Wireshark**  

---

👩‍💻 *Author: Irem*  
Learning journey towards becoming a **SOC Analyst** 🚀  

