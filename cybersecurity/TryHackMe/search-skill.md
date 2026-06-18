# 



---

## Table of Contents

1. [Shodan](#1-shodan)
2. [VirusTotal](#2-virustotal)
3. [CVE — Vulnerability Databases](#3-cve--vulnerability-databases)
4. [Technical Documentation](#4-technical-documentation)
5. [GitHub](#5-github)

---

## 1. Shodan

**TryScanMe** · [shodan.io](https://www.shodan.io)

Shodan continuously scans the public internet for networked devices — routers, industrial control systems, traffic cameras, exposed servers, and more. It indexes what's running on them and where.

**Use case:** Searching for `apache 2.4.1` returns a list of servers advertising that version in their HTTP headers, broken down by country, organisation, and port. When paired with a known CVE affecting that version, this becomes a powerful recon tool during penetration tests and vulnerability assessments.

---

## 2. VirusTotal

**TryDetectMe** · [virustotal.com](https://www.virustotal.com)

VirusTotal aggregates results from over 70 antivirus engines and website scanners into a single interface. Submit a file, URL, domain, or file hash to get a consensus on whether it has been flagged as malicious.

**Use case:** Widely used in blue team operations for quickly assessing suspicious files and links, as well as for tracking intelligence on emerging threats.

> **Note:** VirusTotal is a useful signal, not a verdict. A clean result does not guarantee a file is safe.

---

## 3. CVE — Vulnerability Databases

**Common Vulnerabilities and Exposures** · [cve.mitre.org](https://cve.mitre.org) · [nvd.nist.gov](https://nvd.nist.gov)

The CVE programme is the industry's closest equivalent to a universal dictionary of known security vulnerabilities. Each confirmed vulnerability is assigned a unique identifier in the format:

```
CVE-YEAR-NUMBER   (e.g. CVE-2025-55182)
```

High-impact vulnerabilities may also receive a public moniker — such as **Heartbleed**, **Log4Shell**, or **EternalBlue** — for ease of reference.

### CVSS Scoring

Each CVE is assigned a **Common Vulnerability Scoring System (CVSS)** score based on:

| Factor | Description |
|---|---|
| **Impact** | What damage can exploitation lead to? |
| **Complexity** | How difficult is the vulnerability to exploit? |
| **Availability** | How accessible is the exploitation path? |

---

## 4. Technical Documentation

**MAN Pages & Official Docs**

Each major security tool or platform maintains its own official documentation. This is always the most reliable and up-to-date reference — more trustworthy than third-party tutorials or blog posts, which may be outdated or inaccurate.

**Best practice:** When in doubt, go to the source. Official docs cover edge cases, flags, and syntax changes that tutorials often miss.

---

## 5. GitHub

[github.com](https://www.github.com)

GitHub is a valuable resource for staying current on the latest threats and vulnerabilities. Security researchers frequently publish proof-of-concept (PoC) code, exploitation tools, and detailed technical write-ups — often faster than official disclosure channels.

**Use case:** Useful for finding PoC exploits for newly disclosed CVEs, reading detailed researcher write-ups, and tracking active threat tooling.

> ⚠️ **Caution:** Not all PoC repositories are reliable. Some are incomplete, some are intentionally broken, and occasionally a "PoC" is malicious itself. Always review and verify code before executing it in any environment.

---

## Quick Reference

| Tool | Primary Use | Type |
|---|---|---|
| Shodan | Internet-wide device & service recon | OSINT / Recon |
| VirusTotal | File, URL, and hash reputation checks | Threat Intelligence |
| CVE / NVD | Known vulnerability lookup & scoring | Vulnerability DB |
| Official Docs | Authoritative tool & platform reference | Documentation |
| GitHub | PoC code, research write-ups, threat tracking | Research / PoC |

---

*Maintained as part of the Room: Search skill module.*
