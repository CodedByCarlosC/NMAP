🔎 Nmap: The Basics – Hands-On Lab
📘 Overview

This repository documents my hands-on learning of Nmap fundamentals through a TryHackMe lab environment.
The focus of this project was to understand how network scanning works at a practical level — from discovering live hosts to identifying open ports, running services, operating systems, and controlling scan behavior.
Nmap is one of the most essential tools in cybersecurity, used in penetration testing, network auditing, asset discovery, and incident response.
This lab strengthened my understanding of how systems respond to active probing and how reconnaissance is performed in real-world environments.

🧠 Topics Covered
🔹 Host Discovery

Used -sn for ping scans (host discovery only)
Learned differences between:
Local network scanning (ARP-based)
Remote network scanning (ICMP/TCP probes)
Reviewed how firewalls affect host detection
Used -sL to list targets without scanning

![image ult](https://github.com/CodedByCarlosC/NMAP/blob/127e70740e4791c0c0bee2d8eec82ac5372ff1f5/-sL%20for%20list%20of%20IP.PNG)


Key Insight:
Nmap adapts its host discovery method depending on network proximity and routing.

🔹 TCP Port Scanning
Connect Scan (-sT)
Completes full TCP three-way handshake
Default when not running as root
More easily logged/detected
SYN Scan (-sS) – Stealth
Sends SYN packet only
Does not complete handshake
Less noisy than connect scan
Requires root privileges
Port Selection
Default scans top 1000 ports

-F scans top 100 ports

-p1-1023 scans well-known ports

-p- scans all 65,535 ports

🔹 UDP Scanning
Used -sU to identify services running on UDP
Observed ICMP “port unreachable” responses
Compared behavior differences between TCP and UDP scanning
Recognized UDP scanning is slower and often noisier

🔹 OS Detection

Used -O to perform OS fingerprinting
Learned detection is based on response analysis
Observed how Nmap estimates kernel versions
Understood that OS detection is probabilistic, not exact

🔹 Service & Version Detection

Used -sV to detect:
Service names
Service versions
Sometimes OS hints
Used -A to combine:
OS detection
Version detection
Traceroute
Additional scanning features

Key Insight:
Service enumeration provides critical intelligence during reconnaissance.

🔹 Scan Timing & Control

Explored timing templates:
-T0 Paranoid
-T1 Sneaky
-T2 Polite
-T3 Normal (default)
-T4 Aggressive
-T5 Insane

Reviewed advanced controls:
--min-rate
--max-rate
--min-parallelism
--max-parallelism
--host-timeout

Key Insight:
Scan speed directly impacts detectability and reliability.

🔹 Verbosity & Debugging
Used -v, -vv for increased scan visibility
Used -d for debugging-level output
Observed how Nmap stages progress during scans

🔹 Saving Scan Reports
Used output options:
-oN → Normal output
-oX → XML output
-oG → Grepable output
-oA → All major formats

![image ult](https://github.com/CodedByCarlosC/NMAP/blob/127e70740e4791c0c0bee2d8eec82ac5372ff1f5/options%20rhosts%20set.PNG)

Learned importance of structured reporting for:
Documentation
Automation
SIEM integration
Investigation workflows

🔐 Privilege Considerations
Running Nmap with sudo enables:
SYN scans (-sS)
Advanced packet crafting
Full feature set
Running without root privileges defaults to:
Connect scans (-sT)
Limited scanning capabilities

🛡️ Security Takeaways
Different scan types leave different forensic footprints
Timing control can impact IDS/IPS detection
OS detection relies on fingerprinting behavior
Service version detection exposes potential attack surfaces
Proper reporting is essential for professional workflows

📌 Why This Matters for Cybersecurity
Nmap is foundational for:
Penetration testing
Network reconnaissance
Asset discovery
Vulnerability assessment
Incident response investigations
Understanding how Nmap works internally improves both offensive and defensive security awareness.
This lab strengthened my ability to analyze how systems respond to probing and how attackers enumerate environments.

![image ult](https://github.com/CodedByCarlosC/NMAP/blob/127e70740e4791c0c0bee2d8eec82ac5372ff1f5/nmap%20vuln.PNG)
