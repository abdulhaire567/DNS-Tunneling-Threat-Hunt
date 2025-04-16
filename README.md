# DNS Tunneling Threat Hunt

## Overview

This project investigates the presence of **DNS tunneling**, a covert method used by attackers to bypass network restrictions and exfiltrate data. By analyzing packet captures (PCAP) and mapping the attack to the **MITRE ATT&CK** framework, encoded DNS queries were identified pointing to a suspicious domain. This indicates the use of a DNS tunneling tool, such as **iodine**. The goal is to demonstrate the ability to detect hidden command-and-control (C2) channels over DNS traffic.

---

## Utilities and Tools Used

- **Wireshark**: A tool for packet capturing and analysis.
- **MITRE ATT&CK**: A framework for mapping attack techniques.
- **Base32 Decoder**: For decoding base32-encoded DNS queries.
- **PCAP File**: [dns-tunnel-iodine.pcap]

---

## Environments Used

- **Windows**: The environment used for packet capture and analysis.

---

## Attack Scenario

In this scenario, the attacker is using DNS tunneling to establish a covert communication channel for data exfiltration. The DNS queries are encoded with data and sent to an external domain for exfiltration purposes.

## Step 1: Capturing Network Traffic
To begin, I started capturing network traffic using Wireshark. The focus was on DNS traffic as it's the most common protocol used in tunneling. The captured packets help us analyze whether suspicious patterns are present.

## Step 2: Filtering DNS Traffic
I applied a Wireshark filter to isolate DNS queries and identify any abnormal patterns, such as unusually long domain names or base32-encoded subdomains. This filter helps to capture unusually long DNS queries, which are characteristic of DNS tunneling.
The filter used was:
![Capture](https://github.com/abdulhaire567/DNS-Tunneling-Threat-Hunt/blob/main/Screenshot%202025-04-15%20172044.png)

## Step 3: Analyzing Suspicious DNS Queries
Upon reviewing the DNS traffic, I found unusually long subdomain names that appeared to contain Base32-encoded data. I stripped the subdomain to reveal the encoded data. This indicates that the attacker is using Base32 encoding to hide the data in the DNS query "pirate.sea"
![Capture](https://github.com/abdulhaire567/DNS-Tunneling-Threat-Hunt/blob/main/Screenshot%202025-04-15%20201149.png)

## Threat Hunt Report
I proceeded to make a threat hunt report with my findings and investigations using MITRE Attack Framework.

