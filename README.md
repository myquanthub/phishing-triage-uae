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

### Step 2: Create Resource Group + Log Analytics Workspace (LAW)
```bash
# Create RG in UAE North (available & NESA-compliant)
az group create \
  --name rg-phishing-emirates \
  --location uaenorth \
  --tags Project=phishing-triage-uae NESA=IR-04 Owner=you@emirates.ae

# Create LAW
az monitor log-analytics workspace create \
  --resource-group rg-phishing-emirates \
  --workspace-name law-phishing-emirates \
  --location uaenorth \
  --retention-time 90 \
  --query provisioningState -o tsv
### Step 3: Enable Microsoft Sentinel
**Portal (Recommended):**  
1. Azure Portal → Search "Microsoft Sentinel" → Create → Select `law-phishing-emirates` → Add  
2. Wait 30s → "Active" status  

**CLI (Connectors Only – After Extension Install):**  
```bash
az extension add --name security-insights
az securityinsights data-connector create \
  --resource-group rg-phishing-emirates \
  --workspace-name law-phishing-emirates \
  --kind MicrosoftSecurityIncidentCreation \
  --display-name "Phishing Auto-Incident"
