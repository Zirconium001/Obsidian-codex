# 🛡️ Defensive Security — Introduction

> An overview of the core concepts, tasks, and terminology that define the defensive side of cybersecurity.

---

## Table of Contents

- [Overview](#overview)
- [Core Defensive Tasks](#core-defensive-tasks)
- [Key Terms & Domains](#key-terms--domains)
  - [Security Operations Center (SOC)](#1-security-operations-center-soc)
  - [Threat Intelligence](#2-threat-intelligence)
  - [Digital Forensics and Incident Response (DFIR)](#3-digital-forensics-and-incident-response-dfir)
  - [Malware Analysis](#4-malware-analysis)
- [Types of Malware](#types-of-malware)
- [Malware Analysis Techniques](#malware-analysis-techniques)

---

## Overview

Defensive security focuses on **protecting systems, networks, and data** from unauthorized access, attacks, and damage. Unlike offensive security (which involves actively probing for vulnerabilities), defensive security is concerned with prevention, detection, and response.

---

## Core Defensive Tasks

| # | Task | Description |
|---|------|-------------|
| 1 | **User Cyber Security Awareness** | Training users about cyber security to protect against attacks targeting their systems and behaviour. |
| 2 | **Asset Documentation & Management** | Identifying and maintaining an inventory of all systems and devices that need to be managed and protected. |
| 3 | **Updating & Patching Systems** | Ensuring computers, servers, and network devices are up to date and patched against known vulnerabilities. |
| 4 | **Preventative Security Devices** | Deploying firewalls and Intrusion Prevention Systems (IPS) to control and block malicious network traffic. |
| 5 | **Logging & Monitoring** | Setting up logging and monitoring infrastructure to detect malicious activities, intrusions, and unauthorized devices. |

### Notes on Preventative Devices

- **Firewall** — Controls what network traffic is permitted to enter or leave a system or network.
- **Intrusion Prevention System (IPS)** — Actively blocks network traffic that matches known attack signatures or predefined rules.

---

## Key Terms & Domains

### 1. Security Operations Center (SOC)

A **SOC** is a dedicated team of cyber security professionals responsible for continuously monitoring a network and its systems for malicious events. They serve as the frontline defense in identifying and responding to threats in real time.

---

### 2. Threat Intelligence

Threat Intelligence involves collecting and analyzing information about existing and emerging threats. This enables organizations to make informed decisions and proactively defend against attacks before they occur.

---

### 3. Digital Forensics and Incident Response (DFIR)

**DFIR** combines two closely related disciplines:

- **Digital Forensics** — The investigation of cyber incidents by analyzing digital evidence (files, logs, system artifacts) to understand what happened, when, and how.
- **Incident Response** — The structured process of detecting, containing, eradicating, and recovering from a security incident.

---

### 4. Malware Analysis

**Malware** (malicious software) refers to any program, document, or file designed to cause harm. Malware analysis is the practice of studying malicious software to understand its behavior, origin, and impact.

---

## Types of Malware

| Type | Description |
|------|-------------|
| 🦠 **Virus** | A piece of code that attaches itself to a program and spreads from computer to computer. It alters, overwrites, and deletes files — causing slowdowns or rendering a system unusable. |
| 🐴 **Trojan Horse** | Disguises itself as legitimate or desirable software while hiding malicious functionality. Example: a fake video player that grants the attacker full control of the victim's system. |
| 🔒 **Ransomware** | Encrypts the victim's files, making them inaccessible without the decryption password. The attacker demands a monetary "ransom" in exchange for the key. |

---

## Malware Analysis Techniques

### 🔬 Static Analysis

Inspects the malicious program **without executing it**.

- Examines the code, file structure, and embedded strings directly.
- Requires solid knowledge of **assembly language** (the processor's low-level instruction set).
- Safer, as the malware is never run.

### ⚙️ Dynamic Analysis

Runs the malware in a **controlled, isolated environment** and monitors its behavior.

- Observes real-time actions: file modifications, network calls, registry changes, etc.
- More accessible than static analysis but requires a safe sandbox environment to prevent actual damage.

---

## Summary

Defensive security is a multi-layered discipline spanning awareness training, infrastructure hardening, threat monitoring, and incident response. Understanding the tools, teams, and threats involved — including the various forms of malware and how to analyze them — is foundational to building a resilient security posture.

---

*Room: Defensive Security Introduction*
