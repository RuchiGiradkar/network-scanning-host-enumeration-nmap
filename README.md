# Network Scanning & Host Enumeration with Nmap

## Project Overview

This project demonstrates a structured network discovery and host enumeration assessment using Nmap within an authorized lab environment.

The objective was to identify active hosts, enumerate exposed services, determine operating system characteristics, analyze TCP and UDP exposure, validate potential vulnerabilities, and document security findings using an analyst-driven methodology.

The project reflects activities commonly performed by:

* SOC Analysts
* Cybersecurity Analysts
* Vulnerability Analysts
* Network Security Engineers
* Penetration Testers

---

## Objectives

The assessment was designed to:

* Discover active hosts on the network
* Identify exposed services and ports
* Determine operating system characteristics
* Analyze TCP and UDP attack surfaces
* Validate vulnerability scan findings
* Differentiate genuine findings from false positives
* Produce remediation recommendations

---

## Technologies Used

| Tool               | Purpose                        |
| ------------------ | ------------------------------ |
| Nmap               | Host discovery and enumeration |
| NSE Scripts        | Vulnerability scanning         |
| Windows PowerShell | Command execution              |
| TCP/IP Networking  | Protocol analysis              |
| Markdown           | Reporting and documentation    |

---

## Assessment Methodology

### Phase 1 – Host Discovery

Identify active devices within the authorized subnet.

```bash
nmap -sn <subnet>/24
```

### Phase 2 – Service Enumeration

Identify exposed ports and running services.

```bash
nmap -sV <target>
```

### Phase 3 – Operating System Detection

Determine likely operating system characteristics.

```bash
nmap -O <target>
```

### Phase 4 – TCP SYN Scanning

Validate open TCP services.

```bash
nmap -sS <target>
```

### Phase 5 – UDP Enumeration

Identify exposed UDP services.

```bash
nmap -sU <target>
```

### Phase 6 – Port-State Analysis

Analyze why ports are classified as open, closed, or filtered.

```bash
nmap --reason -p- <target>
```

### Phase 7 – Vulnerability Assessment

Execute lightweight Nmap NSE vulnerability checks.

```bash
nmap --script vuln <target>
```

---

## Key Findings

### Host Discovery

Several active hosts were identified on the local network.

### Service Enumeration

The primary target exposed:

* DNS (53)
* HTTP (80)
* HTTPS (443)

These services were consistent with expected router functionality.

### Operating System Detection

OS fingerprinting indicated a Linux-based embedded device.

### TCP SYN Analysis

Open ports identified during SYN scanning matched the service detection results, confirming consistency.

### UDP Analysis

UDP scanning confirmed DNS functionality while several ports remained in an open|filtered state due to the nature of UDP communications.

### Vulnerability Assessment

Nmap identified potential Slowloris DoS exposure on:

* Port 80 (HTTP)
* Port 443 (HTTPS)

The findings were manually reviewed because embedded devices frequently generate false positives during automated vulnerability scanning.

---

## Security Analysis

The exposed services were consistent with the expected functionality of a router platform.

No unexpected services such as:

* FTP
* Telnet
* RDP
* SMB administration interfaces

were observed on the primary target.

The assessment highlighted the importance of validating automated vulnerability findings before escalation.

---

## Remediation Recommendations

1. Disable remote administration where possible.
2. Restrict management interfaces to trusted hosts.
3. Keep firmware updated.
4. Enable anti-DoS protections.
5. Implement monitoring for unfamiliar devices.
6. Periodically review exposed services.

---

## Skills Demonstrated

* Network Discovery
* Host Enumeration
* Service Identification
* OS Fingerprinting
* TCP/UDP Analysis
* Vulnerability Validation
* Security Reporting
* Risk Assessment
* Remediation Planning

---

## Ethical Statement

All scanning activities were conducted within an authorized lab environment. No unauthorized systems or networks were scanned.

---

## Author

Ruchi

Cybersecurity Analyst | Network Security | Vulnerability Assessment | Security Operations
