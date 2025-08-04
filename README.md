# Scan-Your-Local-Network-for-Open-Ports
Port scanning, TCP SYN scan, IP ranges, network reconnaissance, open ports, network security basics


 Nmap Installation & Scanning Guide

This project provides a step-by-step guide on installing and using **Nmap** for network scanning and vulnerability assessment using **SearchSploit**.

---

 Table of Contents

- About Nmap
- Installation
  - Windows
  - Linux
- Basic Nmap Usage
- Finding Vulnerabilities with SearchSploit
- Saving Scan Results







   Wireshark Packet Analysis Guide

This guide walks through the process of analyzing a packet capture using Wireshark to identify common services running on open ports found during a network scan.

---

 Prerequisites

- Wireshark installed
- A `.pcap` or `.pcapng` packet capture file from a scan (e.g., from Nmap or tcpdump)
- Basic knowledge of TCP/IP protocols

---

 Steps to Analyze Packet Capture

 1. Open Wireshark and Load the Capture File

- Launch Wireshark
- Navigate to `File > Open` and select your `.pcap` file

---

 2. Identify Target Ports

Use your prior scan (e.g., Nmap results) to identify open ports. Examples:
- Port 22 – SSH
- Port 80 – HTTP
- Port 443 – HTTPS
- Port 53 – DNS
- Port 3306 – MySQL

---

 3. Filter Packets by Port

Use Wireshark's display filters to isolate traffic:
wireshark
tcp.port == 22

4. Analyze the Protocol Column
Look at the "Protocol" column:

Wireshark often auto-detects protocols (e.g., HTTP, DNS, TLS).

This helps confirm the service running on a given port.

5. Follow TCP/UDP Streams
To analyze conversations:

Right-click a packet.

Select Follow > TCP Stream or UDP Stream.

Review the exchange to identify service behavior or banners.

6. Inspect Packet Details
Expand layers in the packet view:

Ethernet II

IP

TCP/UDP

Application protocol (e.g., HTTP, SSH)

Look for:

Headers

Payload data

Hostnames

Request types (e.g., GET, POST, QUERY)

7. Research Unknown Ports
If Wireshark doesn't label a protocol:

Google: what service runs on port <port_number>

Use:

IANA Port Registry

SpeedGuide Port Database
      
   Use searchsploit or exploit-db to check for known vulnerabilities.
