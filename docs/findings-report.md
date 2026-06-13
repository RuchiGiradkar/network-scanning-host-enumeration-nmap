# Findings Report

## Executive Summary

An authorized network assessment was conducted using Nmap to identify active hosts, exposed services, operating system characteristics, and potential vulnerabilities.

The assessment revealed a limited attack surface with only a small number of expected management services exposed.

---

## Host Discovery Results

| Host             | Status                    |
| ---------------- | ------------------------- |
| Router           | Active                    |
| Windows Host     | Active                    |
| Additional Hosts | Minimal or non-responsive |

---

## Open TCP Services

| Port | Service | Risk   |
| ---- | ------- | ------ |
| 53   | DNS     | Low    |
| 80   | HTTP    | Medium |
| 443  | HTTPS   | Low    |

---

## Operating System Detection

Likely Linux-based embedded device.

Device type aligned with router functionality.

---

## Vulnerability Findings

### Finding 1

Slowloris DoS Candidate

Port:

80/tcp

Reference:

CVE-2007-6750

Status:

Potentially Vulnerable

Validation Required:

Yes

---

### Finding 2

Slowloris DoS Candidate

Port:

443/tcp

Reference:

CVE-2007-6750

Status:

Potentially Vulnerable

Validation Required:

Yes

---

## Analyst Conclusion

The assessment identified a minimal and expected exposure profile.

Potential vulnerability findings should be treated as informational until independently verified through additional testing and vendor documentation review.
