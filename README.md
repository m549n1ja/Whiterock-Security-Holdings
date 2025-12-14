# 🛡️ Whiterock Security Holdings: SOC Operations & Hybrid Defense Portfolio

## Start Here (5-minute review path)
If you only review a few items, start with:

1. **Architecture & Telemetry Blueprint:** [`00-Architecture-and-Telemetry/`](./00-Architecture-and-Telemetry/)
2. **Initial Access & Triage Evidence:** [`01-Initial-Access-Triage/`](./01-Initial-Access-Triage/)
3. **Identity Defense (AD/Kerberos) + Detections:** [`02-Identity-Defense/`](./02-Identity-Defense/)
4. **Purple Team Metrics (ATT&CK Coverage / Hit Rate):** [`09-Purple-Team-Metrics/`](./09-Purple-Team-Metrics/)
5. **Executive Capstone Summary:** [`10-Executive-Capstone/`](./10-Executive-Capstone/)

---

## Project Overview
This repository documents the construction, defense, and analysis of a high-fidelity enterprise environment, **Whiterock Security Holdings**, designed to simulate a modern corporate network undergoing a cloud migration.

The primary goal is to provide **evidence-grade artifacts** demonstrating proficiency across the full incident response lifecycle:
**Detection → Triage → Forensics → Containment/Hardening → Reporting**, aligned with advanced SANS certification outcomes.

---

## SANS Alignment and Key Certifications
This lab and its resulting artifacts cover the core objectives of the following certifications:

- **GCIH (SEC504):** Hacker Tools, Incident Handling, Triage, Malware, Web/API Attacks
- **GSOC (SEC450):** SOC Operations, Detection Engineering, Metrics, SOAR-style enrichment, Threat Hunting, False Positive Reduction
- **GCIA (SEC503):** Network Monitoring, Traffic Analysis, Zeek/Suricata Rule Writing, BPF Filters, Network Forensics
- **GSEC (SEC401):** Security Architecture, Defense-in-Depth, Vulnerability Management, IAM, Encryption, Network Visibility
- **GPCS (SEC510):** Cloud Security Controls, Cloud IAM, Ransomware Recovery, Multi-Cloud Logging, CSPM

---

## ⚙️ Whiterock Infrastructure Blueprint (Core Nodes)
The environment is built Linux-first so telemetry and security controls are operational before vulnerable Windows targets are introduced.

| Role | Hostname | IP Address | Wazuh ID | Purpose / Focus |
| :--- | :--- | :--- | :--- | :--- |
| **SIEM** | SOC-SIEM | 192.168.1.60 | N/A | Wazuh Manager / Indexer / Dashboard |
| **Analyst Workstation** | SOC-ADMIN | 192.168.1.61 | 001 | Triage, reporting, case management |
| **Network Sensor** | LINUX-ZEEK-04 | 192.168.1.64 | 004 | Zeek/Suricata NSM + PCAP evidence |
| **Domain Controller** | WIN-SERVER-08 | 192.168.1.68 | 008 | AD/GPO/Kerberos identity target |
| **Attacker** | KALI-ATTACK | 192.168.1.50 | N/A | SEC504 tooling & exploitation |

Full inventory (including management/DFIR workstations):  
- **Inventory (Markdown):** [`00-Architecture-and-Telemetry/INVENTORY.md`](./00-Architecture-and-Telemetry/INVENTORY.md)  
- **Inventory (CSV):** [`00-Architecture-and-Telemetry/inventory.csv`](./00-Architecture-and-Telemetry/inventory.csv)

---

## 📜 Project Artifacts & Storyline (The 10 Labs)
Each folder contains the scenario, evidence, configuration, and analysis for one phase of the breach/defense storyline.

1. [`01-Initial-Access-Triage/`](./01-Initial-Access-Triage/) — **Initial Foothold: Web & Phish Triage**
2. [`02-Identity-Defense/`](./02-Identity-Defense/) — **Identity Compromise & Lateral Movement**
3. [`03-Network-Forensics/`](./03-Network-Forensics/) — **Evasion & Network Tunneling Forensics**
4. [`04-Host-DFIR/`](./04-Host-DFIR/) — **Host Forensics: Memory & File Hashing**
5. [`05-Ransomware-Recovery/`](./05-Ransomware-Recovery/) — **Ransomware Simulation, Recovery & Hardening**
6. [`06-Zero-Trust-Architecture/`](./06-Zero-Trust-Architecture/) — **Zero Trust Policy Enforcement & Audit**
7. [`07-Cloud-SecOps/`](./07-Cloud-SecOps/) — **Cloud Logging, Detections & Investigation**
8. [`08-DevSecOps-and-VM/`](./08-DevSecOps-and-VM/) — **DevSecOps: Security as Code & Vulnerability Management**
9. [`09-Purple-Team-Metrics/`](./09-Purple-Team-Metrics/) — **Purple Team: ATT&CK Coverage Validation & Metrics**
10. [`10-Executive-Capstone/`](./10-Executive-Capstone/) — **Capstone: Integrated F3EAD Campaign & Executive Reporting**

---

## Evidence-Grade Standard (What “Done” Looks Like)
Each lab aims to include consistent, interview-ready artifacts:

- **Evidence:** screenshots, logs, PCAPs (sanitized), configs (redacted)
- **Integrity:** SHA256 hashes for key files + acquisition notes
- **Timeline:** clear “what happened / when / how validated”
- **Detections:** rules/queries added + test notes
- **Response:** containment + hardening actions + verification
- **Reporting:** analyst report + executive summary (where applicable)

Recommended structure inside each lab folder:
- `evidence/` • `detections/` • `configs/` • `report/`

---

## Safety & Publishing Notes
This repository is for **isolated lab use only**. Malware samples, raw memory images, and sensitive logs should be sanitized/redacted or represented by **hashes + acquisition notes** prior to publishing.


