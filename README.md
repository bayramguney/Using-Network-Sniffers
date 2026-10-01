# Using-Network-Sniffers

# 🦈 Applied Lab: Using Network Sniffers with Wireshark

## 📌 Overview

In this lab, I explored the fundamentals of network packet capture and analysis using **Wireshark**, one of the most widely used network protocol analyzers in cybersecurity. I learned how to capture live network traffic, apply display filters, inspect protocol headers, analyze TCP and HTTP communications, and follow application-layer conversations to support network investigations.

This lab aligns with **CompTIA Security+ (SY0-701) Objective 4.9: Given a scenario, use data sources to support an investigation.**

---

## 🎯 Objectives

- Capture live network traffic using Wireshark
- Analyze Ethernet frames and network packets
- Apply Wireshark display filters
- Identify HTTP and DNS traffic
- Inspect TCP/IP protocol headers
- Analyze TCP flags
- Follow TCP and HTTP streams
- Investigate captured network communications

---

# 🖥️ Lab Environment

| Component | Description |
|-----------|-------------|
| Operating System | Kali Linux |
| Virtual Machine | KALI |
| User Account | root |
| Network Analyzer | Wireshark |
| Web Browser | Firefox |
| Test Websites | www.structureality.com, dvwa.structureality.com |

---

# 🔹 Part 1 – Capturing Network Traffic

Started a packet capture on the **eth0** network interface using Wireshark.

Generated network traffic by visiting:

- www.structureality.com

Stopped the capture and examined the collected traffic.

### Learned

- How Wireshark captures live traffic
- Selecting the correct network interface
- Starting and stopping packet captures
- Viewing captured frames

---

# 🔹 Part 2 – Understanding Packet Structure

Examined captured traffic using Wireshark's three-pane interface.

### Packet List

Displays every captured frame.

### Packet Details

Displays protocol headers including:

- Ethernet II
- IPv4
- TCP
- HTTP

### Packet Bytes

Displays:

- Raw hexadecimal data
- ASCII interpretation

Learned how protocol information is organized across multiple OSI layers.

---

# 🔹 Part 3 – Filtering HTTP Traffic

Applied the following display filter:

```text
http
```

Located the initial HTTP request from:

```
10.1.16.66
```

Identified the HTTP request:

```text
GET / HTTP/1.1
```

Verified the requested website inside the packet payload.

---

# 🔹 Part 4 – Investigating DNS Traffic

Used the display filter:

```text
dns
```

Observed DNS queries generated while accessing websites.

Learned how DNS resolves hostnames before HTTP communication begins.

---

# 🔹 Part 5 – Using Display Filters

Created multiple Wireshark display filters to isolate specific traffic.

### Destination IP

```text
ip.dst==10.1.16.66
```

Displays packets sent to the destination host.

---

### TTL Filter

```text
ip.ttl<128
```

Displays packets with a Time To Live (TTL) value below 128.

---

### TTL or ARP

```text
ip.ttl<128 or arp
```

Displays:

- Packets with TTL less than 128
- ARP traffic

---

### Excluding an IP Address

```text
ip.addr!=10.1.16.66
```

Displays packets that do not contain the specified IP address.

---

# 🔹 Part 6 – TCP Flag Analysis

Created display filters for TCP control flags.

### FIN Flag

```text
tcp.flags.fin == 1
```

Displays packets where the FIN flag is set.

---

### FIN Without ACK

```text
tcp.flags.fin == 1 and tcp.flags.ack == 0
```

Displays packets containing a FIN flag without an ACK flag.

---

### FIN Without SYN

```text
tcp.flags.fin == 1 and tcp.flags.syn == 0
```

Displays packets with FIN set while SYN is not set.

---

# 🔹 Part 7 – Following TCP Streams

Used Wireshark's **Follow TCP Stream** feature.

Located traffic containing:

```text
dvwa.structureality.com
```

Applied filter:

```text
tcp contains "dvwa.structureality.com"
```

Opened the TCP Stream to examine the complete client-server conversation.

Observed:

- Client requests
- Server responses
- Chronological TCP communication

---

# 🔹 Part 8 – Following HTTP Streams

Applied filter:

```text
http
```

Opened:

```
Analyze
→ Follow
→ HTTP Stream
```

Examined the complete HTTP conversation in readable ASCII format.

Located the HTML response:

```html
<h1>Welcome to Damn Vulnerable Web Application!</h1>
```

Observed how HTTP traffic can be inspected when communications are unencrypted.

---

# 🛠️ Tools & Technologies

- Kali Linux
- Wireshark
- Firefox
- Ethernet
- IPv4
- TCP
- HTTP
- DNS
- ARP

---

# 🔎 Wireshark Display Filters Used

| Filter | Purpose |
|---------|---------|
| `http` | Display HTTP traffic |
| `dns` | Display DNS traffic |
| `ip.dst==10.1.16.66` | Destination IP filter |
| `ip.ttl<128` | TTL less than 128 |
| `ip.ttl<128 or arp` | TTL or ARP traffic |
| `ip.addr!=10.1.16.66` | Exclude IP address |
| `tcp.flags.fin == 1` | FIN flag packets |
| `tcp.flags.fin == 1 and tcp.flags.syn == 0` | FIN without SYN |
| `tcp contains "dvwa.structureality.com"` | Find TCP conversation |

---

# 🔒 Security Concepts

- Packet Capture
- Network Sniffing
- Protocol Analysis
- Traffic Monitoring
- Packet Inspection
- Network Forensics
- TCP/IP
- Ethernet Frames
- HTTP Analysis
- DNS Analysis
- ARP Analysis
- Display Filters
- TCP Flags
- OSI Model
- Incident Investigation

---

# 📚 CompTIA Security+ Skills Demonstrated

- Network traffic analysis
- Packet capture
- Packet inspection
- Network troubleshooting
- HTTP investigation
- DNS analysis
- Protocol identification
- TCP flag analysis
- Network forensics
- Data source investigation

---

# ✅ Skills Demonstrated

- Captured live network traffic
- Analyzed Ethernet and IP packets
- Inspected protocol headers
- Used Wireshark display filters
- Investigated HTTP communications
- Examined DNS traffic
- Analyzed TCP control flags
- Followed TCP streams
- Followed HTTP streams
- Interpreted packet payloads
- Identified network communications
- Investigated application-layer traffic

---

# 📖 Key Takeaways

This lab provided hands-on experience using Wireshark to capture and analyze network traffic. I learned how to filter packets, inspect protocol headers, analyze TCP flags, investigate DNS and HTTP communications, and follow TCP and HTTP streams to understand client-server interactions. These skills are essential for network troubleshooting, incident response, digital forensics, and security operations.

---

