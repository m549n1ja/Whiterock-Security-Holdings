# 🖥️ Physical Management and DFIR Hosts (M1 & M2)

This document defines the role, configuration, and forensic intent of the two **physical management and DFIR hosts** used within the Whiterock Security Holdings lab.

These systems are intentionally assigned **static IP addresses outside the Wazuh agent range (192.168.1.60–192.168.1.70)** to clearly separate monitoring targets from analyst and forensic workstations.

These hosts **do not run Wazuh agents** and are treated as trusted analysis systems.

---

## M1: NETFLOW-LOG (Management & High-Volume Analysis)

| Attribute | Detail |
| :--- | :--- |
| **Hostname** | `NETFLOW-LOG` |
| **IP Address** | `192.168.1.10` |
| **Role** | Packet Analysis, NetFlow Review, Log Correlation |
| **Physical Hardware** | Asus Zephyrus G16 |
| **Operating System** | Windows / Linux DFIR |
| **Primary Tools** | Wireshark, tshark, NetworkMiner, NetFlow Collector, Elastic/Splunk Forwarder (as needed) |
| **Primary Use Cases** | Large PCAP analysis, exported Zeek logs, offline log correlation |

**Purpose:**  
This workstation is used when packet captures or log datasets exceed the practical processing limits of the LINUX-ZEEK-04 sensor. It supports deep-dive network forensics and large-scale traffic analysis without impacting detection infrastructure.

**Primary Lab Support:**  
- Lab 03 – Network Forensics  
- Lab 09 – Purple Team Metrics

---

## M2: DFIR-HOST-PRO (Forensic Acquisition & Analysis)

| Attribute | Detail |
| :--- | :--- |
| **Hostname** | `DFIR-HOST-PRO` |
| **IP Address** | `192.168.1.11` |
| **Role** | Memory & Disk Forensic Analysis |
| **Physical Hardware** | Asus ZenBook OLED |
| **Operating System** | SIFT Workstation / REMnux (Bootable) |
| **Primary Tools** | Volatility 3, Autopsy, FTK Imager, X-Ways Forensics |
| **Primary Use Cases** | Memory dump analysis, disk image mounting, malware artifact review |

**Forensic Integrity Controls:**
- Analysis performed offline or in controlled network states
- SHA256 hashes calculated pre- and post-analysis
- No direct interaction with live compromised endpoints
- Dedicated environment to avoid contamination or tool conflicts

**Purpose:**  
This host is dedicated to high-fidelity forensic analysis of memory dumps and disk images collected from compromised endpoints (e.g., `WIN-USER-09`, `WIN-USER-10`). Its isolation ensures forensic soundness and repeatability.

**Primary Lab Support:**  
- Lab 04 – Host DFIR  
- Lab 05 – Ransomware Recovery

---

## Design Rationale
Physical hosts are used for management and DFIR tasks to avoid:
- Evidence contamination from shared VM snapshots
- Resource contention with detection infrastructure
- Forensic artifacts introduced by hypervisors

This design mirrors real-world SOC and DFIR separation-of-duties practices.
