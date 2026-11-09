# Cryptographic Key Lifecycle & Rotation Auditor

<p align="center">
  <img src="https://img.shields.io/badge/Security-Defensive_Auditor-blue?style=flat" alt="Type">
  <img src="https://img.shields.io/badge/Status-Architectural_Showcase-success?style=flat" alt="Status">
  <img src="https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white" alt="Python">
</p>

> 🔒 **Technical Showcase & Architecture Specification**  
> *This repository provides public architectural documentation, system specifications, and implementation summaries. Full production source code, internal test suites, and proprietary algorithms are maintained in a secure private repository.*

---

## 📌 Executive Summary

**Category**: Cryptography & Key Management  
**Tech Stack**: `Python 3.10+ · Cryptography · Key Management (KMS) · Lifecycle Governance`  

Enterprise key governance tool evaluating cryptographic key age, rotation policies, ownership separation, and expiration schedules across KMS and HSMs.

---

## 🎯 The Problem It Solves

Stale or unrotated cryptographic keys violate regulatory requirements and multiply the impact of potential key compromises. Key lifecycles must be continuously audited.

---

## ⚙️ How the Engine Works

1. **Key Metadata Ingestion**: Ingests key inventories from AWS KMS, HashiCorp Vault, or local keystores (creation date, key type, algorithm, rotation status).
2. **Lifecycle Age Analysis**: Computes key age against maximum organizational thresholds (e.g., mandatory 90-day or 365-day rotation).
3. **Automated Rotation Check**: Verifies whether annual automatic key rotation is enabled for Customer Managed Keys (CMKs).
4. **Key Material & Algorithm Verification**: Confirms symmetric key strength (AES-256) and asymmetric RSA key length ($\ge 2048$ bits).
5. **Retirement & Deletion Alerting**: Identifies keys pending deletion or unutilized keys that create unmonitored risk.

---

## 🚀 Key Capabilities

- Flags cryptographic keys exceeding authorized age thresholds
- Identifies disabled automatic rotation policies on KMS CMKs
- Verifies key usage policies and separation of administrative duties
- Generates key lifecycle audit matrices for compliance reviews

---

## 🏗️ System Data Flow & Architecture

```
+-----------------------------------+
|  Target Input / Configuration    |
|  (JSON Snapshots / Policies)      |
+-----------------+-----------------+
                  |
                  v
+-----------------------------------+
|  1. Schema Normalization Engine   |
|  Validates types & formats        |
+-----------------+-----------------+
                  |
                  v
+-----------------------------------+
|  2. Core Analytical Pipeline      |
|  Heuristic rule evaluation,       |
|  invariant checks & drift diffs   |
+-----------------+-----------------+
                  |
                  v
+-----------------------------------+
|  3. Risk Classification           |
|  Assigns severity: INFO / HIGH    |
+-----------------+-----------------+
                  |
                  v
+-----------------------------------+
|  4. Structured Findings & Report  |
|  Root cause, evidence &           |
|  actionable remediation steps     |
+-----------------------------------+
```

---

## 📄 Findings Output Structure

The engine generates structured, machine-parsable JSON reports adhering to this standard audit schema:

```json
{
  "results": [
    {
      "resource": "resource-identifier",
      "severity": "HIGH",
      "check": "CHECK_IDENTIFIER",
      "detail": "Descriptive analysis of the identified security posture issue.",
      "remediation": "Actionable step-by-step guidance to restore compliant state.",
      "evidence": {
        "observed_field": "value",
        "required_policy": "enforced_policy"
      }
    }
  ],
  "count": 1,
  "scope": "Comprehensive defensive security audit"
}
```

---

## 🔒 Source Code & Enterprise Inquiries

To protect proprietary intellectual property and client operational security:
* **Public Repository**: Contains comprehensive architecture specifications, schemas, and design overviews.
* **Private Repository**: Contains the complete production implementation, continuous integration pipelines, and full regression test suites.

For architectural questions or enterprise inquiries, connect via [LinkedIn](https://www.linkedin.com/in/karthikeyansubramaniam04/) or visit the [Portfolio Site](https://karthikeyansubramaniyam.github.io).
