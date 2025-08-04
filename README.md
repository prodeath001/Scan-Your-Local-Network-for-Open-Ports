This project provides a comprehensive guide for scanning local networks for open ports, analyzing captured traffic, and identifying vulnerabilities using tools like Nmap, Wireshark, and SearchSploit.

---

Project Setup (Virtual Environment)

This task was performed in a virtualized lab using **VirtualBox** with the following machines:

- Attacker Machine: Parrot Security OS
  - Used for scanning (Nmap), capturing packets (tcpdump), and analyzing traffic (Wireshark).
  
- Target Machine: Metasploitable2  
  - A vulnerable Linux VM simulating real-world insecure services.

These virtual machines were configured on a **host-only** or **NAT** network to safely conduct internal scans and packet analysis without impacting external systems.

---

Table of Contents

- About Nmap
- Installation
  - Windows
  - Linux
- Basic Nmap Usage
- Finding Vulnerabilities with SearchSploit 
- Wireshark Packet Analysis Guide

---

 About Nmap

Nmap is a powerful open-source tool used for network discovery and security auditing.

---

 Installation

 Windows

1. Download Nmap from the official site: https://nmap.org/download.html  
2. Follow the installer steps.

 Linux

bash
sudo apt update
sudo apt install nmap
Basic Nmap Usage
Identify your IP range using:

bash
Copy
Edit
ip a
Run a TCP SYN scan:

bash
Copy
Edit
nmap -sS 192.168.x.0/24
Save results:

bash
Copy
Edit
nmap -oN scan_results.txt 192.168.x.0/24
Finding Vulnerabilities with SearchSploit
After discovering open ports and services:

Use searchsploit to look up known vulnerabilities:

bash
Copy
Edit
searchsploit <service/version>
Alternatively, refer to https://www.exploit-db.com.

Wireshark Packet Analysis Guide
This guide walks through analyzing .pcap captures using Wireshark to identify services running on open ports.

 Prerequisites
Wireshark installed

A .pcap or .pcapng file (captured using tcpdump or Wireshark)

Basic understanding of TCP/IP protocols

Steps to Analyze Packet Capture
Open Wireshark and Load the Capture File

Launch Wireshark

File > Open > Select your .pcap file

Identify Target Ports
Refer to Nmap scan results. Example ports:

22 – SSH

80 – HTTP

443 – HTTPS

53 – DNS

3306 – MySQL

Filter Packets by Port
Use display filters:

wireshark
Copy
Edit
tcp.port == 22
Analyze the Protocol Column
Wireshark auto-detects protocols like HTTP, DNS, TLS.

Follow TCP/UDP Streams

Right-click a packet

Follow > TCP Stream or UDP Stream

Review conversations for service behavior or banners

Inspect Packet Details
Expand layers:

Ethernet II

IP

TCP/UDP

Application protocols (e.g., HTTP, SSH)
Look for:

Headers

Payload

Hostnames

Request types (GET, POST, QUERY)

Research Unknown Ports
If protocol is unidentified:

Google: what service runs on port <port_number>

Use:

IANA Port Registry

SpeedGuide Port Database

Use searchsploit to identify known vulnerabilities related to the services found.
