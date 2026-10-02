
# finovo-iso27001-gap-assessment
Comprehensive ISO/IEC 27001:2022 Annex A ISMS Gap Assessment &amp; Governance Framework for Finovo (Fintech Platform).
# Finovo Technologies — ISO/IEC 27001:2022 ISMS Gap Assessment & Audit Framework

![ISO 27001:2022](https://img.shields.io/badge/Standard-ISO%2FIEC%2027001%3A2022-blue)
![Framework](https://img.shields.io/badge/Framework-Annex%20A%20Controls-green)
![Status](https://img.shields.io/badge/Audit%20Stage-Readiness%20%26%20Baseline-orange)
![Total Controls](https://img.shields.io/badge/Evaluated%20Controls-93-purple)

---

## 📌 Executive Summary & Project Context

> **Note:** This project is a comprehensive **simulated case study** developed to evaluate the information security and governance posture of a hypothetical cloud-native fintech payment provider (Finovo) against the ISO/IEC 27001:2022 standard.

Finovo is modelled as an emerging payment service provider (PSP / EMI) managing high-concurrency transaction processing for 100,000 active customer wallets, with a 
**75-member operational footprint**. (45 Finance & Operations, 15 Core Engineering & DevOps, and 15 Executive, GRC, and Customer Support staff).

This repository contains the end-to-end **Baseline ISMS Gap Assessment & Audit Working Papers** conducted against the **ISO/IEC 27001:2022 Annex A** control framework. The objective of this assessment was to establish the organization's information security baseline posture, identify control non-conformities, capture ground-reality operational evidence, and deliver an actionable remediation roadmap prior to formal ISO/IEC 27001 Stage 1 certification and PCI-DSS compliance audits.

---

## 📊 High-Level Audit Findings & Metric Breakdown

Across the **93 Annex A controls**, the readiness review established the following distribution:

| Compliance Status | Control Count | Percentage (%) | Operational Definition |
| :--- | :---: | :---: | :--- |
| **Compliant** | **0** | 0.0% | Control fully documented, enforced, and backed by verifiable historical audit trails. |
| **Partially Compliant** | **71** | 76.3% | Operational controls exist informally or in draft state; gaps in formal management sign-off, logging, or enforcement. |
| **Non-Compliant** | **22** | 23.7% | No formal control, policy, or technical implementation identified; high non-conformity exposure. |
| **Not Applicable** | **0** | 0.0% | All 93 Annex A controls reside within the Finovo fintech payment processing perimeter. |
| **Total** | **93** | **100%** | Comprehensive baseline coverage across all 4 control themes. |

---

## 🏛️ Annex A Domain Breakdown (2022 Structure)

### 1. A.5 Organizational Controls (37 Controls)
* **Scope:** Policies for information security, role segregation, asset management, supplier risk, and business continuity.
* **Key Observations:** Draft policies exist across Google Drive repositories, but policy lifecycles lack formal review frequencies, annual employee acknowledgment tracking, and C-level sign-offs.
* **Critical Non-Conformities:**
  * `5.5 Contact with authorities` & `5.6 Contact with special interest groups`: Missing formal regulator/law enforcement escalation matrices.
  * `5.7 Threat intelligence`: Lack of formal TI ingestion workflows, feeds, or contextual threat categorization.
  * `5.11 Return of assets`: Absence of offboarding asset reconciliation logs.
  * `5.28 Collection of evidence`: No documented forensic chain of custody for security incidents.

### 2. A.6 People Controls (8 Controls)
* **Scope:** Employee onboarding, background screening, terms of employment, security awareness, and disciplinary procedures.
* **Key Observations:** Hybrid/remote work policies exist informally without conditional access enforcement. Security awareness is communicated informally without structured phishing simulations.
* **Critical Non-Conformities:**
  * `6.1 Screening`: Lack of verified, standardized background verification processes for operational and contract personnel.
  * `6.2 Terms and conditions of employment`: Employment agreements omit mandatory security compliance clauses and post-employment covenants.
  * `6.4 Disciplinary process`: Missing formal governance actions for information security violations.

### 3. A.7 Physical Controls (14 Controls)
* **Scope:** Physical perimeters, facility entry, equipment security, cable shielding, and secure disposal.
* **Key Observations:** Cloud-hosted architecture reduces physical server exposure; however, the corporate office perimeter requires perimeter boundary formalization.
* **Critical Non-Conformities:**
  * `7.1 Physical security perimeters` & `7.3 Securing offices, rooms, and facilities`: Entry badge logs are not audited; visitor escort procedures are informal.
  * `7.5 Protecting against physical and environmental threats`: Server rooms and comms racks lack dedicated environmental and water/fire suppression logs.
  * `7.7 Clear desk and clear screen`: No enforcement of screen locks or physical desk security for finance personnel handling merchant payouts.

### 4. A.8 Technological Controls (34 Controls)
* **Scope:** Identity and access management, cryptography, network security, SSDLC, application testing, and logging.
* **Key Observations:** Core ledger and web applications utilize basic security groups and TLS encryption, but developer access controls and automated deployment pipelines lack security gates.
* **Critical Non-Conformities:**
  * `8.4 Access to source code`: Source code repositories lack strict write-access restrictions and developer tamper logging.
  * `8.11 Data masking`: Non-production and staging databases utilize cloned production customer datasets without dynamic data masking (DDM).
  * `8.15 Logging`: Centralized immutable SIEM logging with automated log tamper-protection is absent.
  * `8.18 Use of privileged utility programs`: Production database administrative utilities lack multi-party authorization or query recording.
  * `8.25 Secure development life cycle (SSDLC)` & `8.28 Secure coding`: Absence of mandatory SAST/DAST pipeline gates and pre-commit secret scanners.
  * `8.33 Test information`: Production customer KYC records and wallet balances used directly during staging regression tests.
  * `8.34 Protection of information systems during audit testing`: Internal testing on production microservices performed without formal change approval.

---

## 🛠️ Remediation Roadmap & Corrective Action Plan (CAP)

The gap assessment defines prioritized remediation actions across three implementation horizons:

1. **Phase 1: Immediate High-Priority Remediation (0 – 30 Days)**
   * Deploy dynamic data masking (DDM) across all staging/testing environments (`A.8.11`, `A.8.33`).
   * Implement automated pre-commit secret scanning (TruffleHog / GitGuardian) and branch protection (`A.8.4`, `A.8.28`).
   * Formalize employee screening workflows and information security disciplinary guidelines with HR (`A.6.1`, `A.6.4`).

2. **Phase 2: Technical Governance & Identity Hardening (30 – 60 Days)**
   * Deploy centralized Privileged Access Management (PAM) with Just-In-Time session recording for production database access (`A.8.2`, `A.8.18`).
   * Establish centralized SIEM log collection with automated forwarding to write-once (WORM) storage (`A.8.15`, `A.8.16`).
   * Integrate automated SAST, DAST, and software bill-of-materials (SBOM) scanning into GitLab/GitHub CI/CD pipelines (`A.8.25`, `A.8.29`).

3. **Phase 3: Formal Policy Lifecycle & Institutional Governance (60 – 90 Days)**
   * Execute formal C-level and Management sign-off across all 18 core ISMS policies (`A.5.1`).
   * Conduct mandatory annual policy acknowledgment and security awareness tracking across all 75 employees (`A.6.3`).
   * Develop and test the Third-Party Vendor Risk Management (TPRM) framework with critical payment partner banks (`A.5.19`, `A.5.21`).

---

## 📂 Repository File Index

* **`Finovo_ISMS_Gap_Assessment_Completed.xlsx`**: The primary audit workbook featuring:
  * **Sheet 1 (`Cover Page`):** Metadata, document control, audit scope, classification, and dynamic `=COUNTIF` compliance counters.
  * **Sheet 2 (`ISMS Gap Assessment`):** Granular assessment across all 93 controls documenting *Current Status*, *Identified Gaps*, *Status*, *Observed Evidence*, *Actionable Recommendations*, and *Management Responses*.
* **`README.md`**: Executive project overview, methodology, statistical summary, and remediation strategy.

---

## 📥 Download Assessment File

👉 **[Click Here to Download Complete Audit Workbook (Excel .XLSX)](https://github.com/user-attachments/files/32953584/Finovo_ISMS_Gap_Assessment_Completed.xlsx)**

---

## 👤 Project Information & Author

* **Project:** Finovo Technologies ISMS Readiness Assessment
* **Standard:** ISO/IEC 27001:2022 Annex A
* **Role:** Information Security & GRC Analyst (Lead Assessor)
* **Author:** Muhammad Hamza
* **Date:** September 2026

