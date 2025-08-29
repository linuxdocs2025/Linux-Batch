# 🌐 OSI Model (Open Systems Interconnection)

## 📌 What is OSI Model?

The **OSI Model** is a **conceptual framework** that describes how data is transmitted over a network.
It divides communication into **7 layers**, where each layer has a specific role in data transmission.

---

## 📌 7 Layers of the OSI Model

### 1️⃣ **Physical Layer**

* Deals with **hardware transmission** of raw data (bits) over cables, Wi-Fi, fiber optics, etc.
* Responsible for voltage, signal rates, connectors, and physical topology.

👉 **Examples:**

* Ethernet cables, switches, hubs, Wi-Fi, fiber optics.
* Devices: Network Interface Card (NIC), repeater, modem.

---

### 2️⃣ **Data Link Layer**

* Provides **error detection and correction** for data frames.
* Ensures reliable transfer of data between two devices in the same network.
* Divided into **MAC (Media Access Control)** and **LLC (Logical Link Control)**.

👉 **Examples:**

* Ethernet, Wi-Fi (IEEE 802.11), ARP (Address Resolution Protocol).
* Devices: Switches, bridges.

---

### 3️⃣ **Network Layer**

* Responsible for **routing** packets from source to destination across networks.
* Uses **logical addressing (IP addresses)**.

👉 **Examples:**

* Protocols: **IP (IPv4/IPv6), ICMP, IPsec**.
* Devices: Routers, Layer 3 switches.

---

### 4️⃣ **Transport Layer**

* Ensures **end-to-end communication** and reliability.
* Provides **segmentation, flow control, and error recovery**.
* Can be **connection-oriented (TCP)** or **connectionless (UDP)**.

👉 **Examples:**

* Protocols: **TCP, UDP**.
* Use Cases:

  * TCP → Web browsing (HTTP/HTTPS), Email (SMTP, IMAP).
  * UDP → Video streaming, VoIP, online gaming.

---

### 5️⃣ **Session Layer**

* Manages and controls **sessions (connections)** between applications.
* Responsible for authentication, session checkpoints, and recovery.

👉 **Examples:**

* Protocols: NetBIOS, RPC (Remote Procedure Call), PPTP (VPN tunneling).
* Example: A user logging into a remote server (session established & maintained).

---

### 6️⃣ **Presentation Layer**

* Translates **data formats** between application and network.
* Handles **encryption, compression, and encoding**.

👉 **Examples:**

* Formats: JPEG, GIF, PNG, MP3, MP4, ASCII, EBCDIC.
* Encryption: SSL/TLS.
* Example: A website uses **HTTPS (TLS)** to encrypt communication.

---

### 7️⃣ **Application Layer**

* Closest to the end user, provides **network services directly to applications**.
* Responsible for communication between apps across networks.

👉 **Examples:**

* Protocols: HTTP/HTTPS, FTP, SMTP, POP3, DNS, DHCP.
* Applications: Web browsers, email clients, cloud apps.

---

## 📌 Example: Sending an Email (SMTP) via OSI Model

1. **Application Layer** → User writes an email (SMTP used).
2. **Presentation Layer** → Email text encoded, attachments compressed.
3. **Session Layer** → Session established between sender & email server.
4. **Transport Layer** → TCP ensures reliable delivery.
5. **Network Layer** → IP address of mail server resolved via DNS.
6. **Data Link Layer** → Ethernet/Wi-Fi ensures frame delivery.
7. **Physical Layer** → Bits transmitted as electrical signals/waves.

---

## 📌 Example: Opening a Website (HTTP over HTTPS)

1. **Application** → Browser sends an HTTP/HTTPS request.
2. **Presentation** → Data encrypted using SSL/TLS.
3. **Session** → Secure session maintained between browser & server.
4. **Transport** → TCP ensures reliable connection.
5. **Network** → IP routing finds the path to the server.
6. **Data Link** → MAC address ensures hop-to-hop delivery.
7. **Physical** → Data transmitted as signals over cable/Wi-Fi.

---

## 📌 OSI Model vs TCP/IP Model

| Feature       | OSI Model (7 Layers)       | TCP/IP Model (4 Layers)                          |
| ------------- | -------------------------- | ------------------------------------------------ |
| Layers        | 7 (Physical → Application) | 4 (Link, Internet, Transport, Application)       |
| Example Usage | Theoretical model          | Practical implementation (used in real networks) |
| Protocols     | ARP, IP, TCP, HTTP, etc.   | TCP, IP, HTTP, FTP, etc.                         |

---

