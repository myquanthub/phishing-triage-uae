# UAE Phishing Triage Platform (NESA IR-04 Compliant)

> **Automated phishing detection & response for UAE entities (Emirates, Etihad, ADNOC, etc.)**  
> Built in 8 hours: Sentinel + XSOAR + CrowdStrike. **35K AED budget justified.**  
> ![NESA IR-04](https://img.shields.io/badge/NESA-IR--04%20Compliant-006600?style=flat-square)

## Overview
This repo delivers a **full NESA IR-04 pipeline** for phishing triage:
- **Primary Target:** Emirates (Project #3)
- **Standards:** NESA IR-04 (Incident Response – Phishing)
- **Tech:** Azure Sentinel, Palo Alto Cortex XSOAR, CrowdStrike Falcon
- **Private Sector Fit:** Yes (Aviation/Energy)
- **Loom Hours:** 8

Supports multiple UAE orgs – extendable to all 20 projects.

## Supported Projects
| # | Repo Name | Primary Gov Target | NESA/Standard | Private Fit | Loom Hrs |
|---|-----------|--------------------|---------------|-------------|----------|
| 3 | phishing-triage-emirates | Emirates | IR-04 | Yes | 8 |

(Coming: Etihad MCAS, ADNOC PAW, etc.)

## Quick Start (14-Step NESA Workflow)
Run in UAE North (NESA data sovereignty compliant).

### Step 1: Azure Login
```bash
az login --use-device-code
