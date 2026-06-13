# Network Scanning & Host Enumeration with Nmap

## Overview

This project demonstrates a structured network assessment conducted using Nmap within an authorized lab environment. The objective was to identify active hosts, enumerate exposed services, determine operating system characteristics, analyze TCP and UDP attack surfaces, validate potential vulnerabilities, and document security findings through a professional assessment methodology.

The project reflects activities commonly performed by Security Operations Center (SOC) Analysts, Cybersecurity Analysts, Vulnerability Management Analysts, Network Security Engineers, and Penetration Testers during reconnaissance and security validation activities.

---

## Recruiter Highlights

This project demonstrates:

* Network Discovery and Asset Identification
* Host Enumeration using Nmap
* Service and Port Enumeration
* Operating System Fingerprinting
* TCP and UDP Analysis
* Vulnerability Assessment using Nmap NSE
* False Positive Validation
* Security Reporting and Documentation
* Risk Assessment and Remediation Planning

---

## Project Objectives

The assessment was designed to:

* Discover active hosts within an authorized network
* Identify exposed services and listening ports
* Determine operating system characteristics of target devices
* Analyze TCP and UDP attack surfaces
* Validate vulnerability scan findings
* Distinguish genuine findings from false positives
* Develop remediation recommendations based on identified risks

---

## Technologies Used

| Technology                  | Purpose                               |
| --------------------------- | ------------------------------------- |
| Nmap                        | Network discovery and enumeration     |
| Nmap Scripting Engine (NSE) | Vulnerability assessment              |
| PowerShell                  | Command execution and data collection |
| TCP/IP Networking           | Protocol analysis                     |
| Markdown                    | Documentation and reporting           |

---

## Assessment Methodology

### Phase 1 – Host Discovery

A host discovery scan was conducted to identify active devices within the authorized subnet. This phase established a baseline inventory of reachable systems and helped determine which devices required further investigation.

### Phase 2 – Service Enumeration

Identified hosts were scanned to determine exposed services and listening ports. Service fingerprinting was performed to identify technologies and protocols running on the target systems.

### Phase 3 – Operating System Detection

Operating system fingerprinting techniques were used to determine the likely operating system and device type. The results were correlated with vendor information and service characteristics to improve confidence in the findings.

### Phase 4 – TCP Analysis

TCP SYN scanning was performed to validate exposed services and compare results against service enumeration findings. This helped confirm the accuracy of identified ports and services.

### Phase 5 – UDP Analysis

UDP scanning was conducted to identify exposed UDP services and evaluate filtering behavior. Particular attention was given to interpreting open, closed, and open|filtered states due to the connectionless nature of UDP communications.

### Phase 6 – Port-State Validation

Port-state reasoning analysis was performed to understand how Nmap classified ports as open, closed, or filtered. Response characteristics such as SYN-ACK and RST packets were reviewed to validate scan results.

### Phase 7 – Vulnerability Assessment

Nmap NSE vulnerability scripts were executed against authorized targets to identify potential weaknesses. Findings were validated through additional analysis to reduce the likelihood of false positives.

---

## Nmap Commands Executed

| Activity                   | Command                        |
| -------------------------- | ------------------------------ |
| Host Discovery             | nmap -sn 192.168.1.0/24        |
| Service Detection          | nmap -sV 192.168.1.1           |
| Operating System Detection | nmap -O 192.168.1.1            |
| TCP SYN Scan               | nmap -sS 192.168.1.1           |
| UDP Scan                   | nmap -sU 192.168.1.1           |
| Port-State Analysis        | nmap --reason -p- 192.168.1.1  |
| Vulnerability Scan         | nmap --script vuln 192.168.1.1 |

---

## Key Findings

### Host Discovery

Multiple active hosts were identified within the local network. The discovered devices included network infrastructure components and endpoint systems.

### Service Enumeration

The primary target exposed the following services:

| Port | Service | Purpose                         |
| ---- | ------- | ------------------------------- |
| 53   | DNS     | Name resolution                 |
| 80   | HTTP    | Administrative web interface    |
| 443  | HTTPS   | Secure administrative interface |

The observed services aligned with expected router functionality.

### Operating System Detection

Operating system fingerprinting suggested that the target device was running a Linux-based embedded operating system. Vendor information and service behavior supported this assessment.

### TCP Analysis

TCP SYN scan results matched the service detection results, confirming the presence of DNS, HTTP, and HTTPS services while demonstrating that the majority of TCP ports were closed.

### UDP Analysis

UDP scanning confirmed DNS functionality on port 53/UDP. Several additional ports were reported as open|filtered due to a lack of response, which is common during UDP enumeration and requires careful interpretation.

### Vulnerability Assessment

The vulnerability assessment identified a potential Slowloris Denial-of-Service condition affecting the web management interfaces.

| Finding                 | Port    | Reference     |
| ----------------------- | ------- | ------------- |
| Slowloris DoS Candidate | 80/TCP  | CVE-2007-6750 |
| Slowloris DoS Candidate | 443/TCP | CVE-2007-6750 |

Because embedded network devices frequently return incomplete service information, these findings were treated as candidates requiring validation rather than confirmed vulnerabilities.

---

## Security Analysis

The assessment revealed a relatively small attack surface with only essential management services exposed.

Positive observations included:

* No FTP services detected
* No Telnet services detected
* No unnecessary remote administration protocols observed
* Majority of TCP ports closed
* DNS exposure consistent with router functionality

The primary risk area involved the administrative web interfaces exposed through HTTP and HTTPS.

The project reinforced the importance of validating automated vulnerability findings before treating them as confirmed security issues.

---

## Remediation Recommendations

### High Priority

* Disable remote administration from untrusted networks
* Restrict management interfaces to authorized hosts
* Apply the latest firmware updates
* Enforce strong administrative credentials

### Medium Priority

* Enable anti-DoS protection mechanisms where available
* Configure connection timeout settings
* Review exposed services periodically
* Implement network segmentation where appropriate

### Continuous Improvement

* Perform periodic network scans
* Maintain an accurate asset inventory
* Investigate unfamiliar devices promptly
* Establish a baseline for future comparisons

---

## Skills Demonstrated

### Technical Skills

* Network Discovery
* Host Enumeration
* Service Identification
* OS Fingerprinting
* TCP Analysis
* UDP Analysis
* Vulnerability Assessment
* Vulnerability Validation
* Security Documentation

### Analyst Skills

* Threat Identification
* Security Investigation
* Evidence Collection
* Risk Assessment
* Critical Thinking
* False Positive Analysis
* Remediation Planning

---

## Key Lessons Learned

* UDP scan results require careful interpretation due to the connectionless nature of the protocol.
* Automated vulnerability scans should always be validated before escalation.
* Service enumeration and OS fingerprinting are more reliable when correlated together.
* Effective security assessments require both technical evidence and analyst judgment.
* Proper documentation is essential for communicating findings and recommendations.

---

## Ethical Statement

All scanning activities were conducted exclusively within an authorized lab environment. No unauthorized systems, networks, or third-party infrastructure were targeted during this assessment.


Cybersecurity Analyst | Network Security | Vulnerability Assessment | Security Operations
