# Cybersecurity-Awareness-Threat-Intelligence-Dashboard
A cybersecurity dashboard that combines threat intelligence, vulnerability tracking, IOC enrichment, risk scoring, correlated alerts, and security awareness features. It uses synthetic threat data, automated analysis, validation tests, and interactive insights to help identify, assess, and respond to cyber threats effectively.
# 🛡️ Cybersecurity Awareness & Threat Intelligence Dashboard

> **A defensive cybersecurity platform for threat intelligence analysis, risk assessment, alert correlation, vulnerability prioritization, and security awareness.**

## 📌 Overview

The **Cybersecurity Awareness & Threat Intelligence Dashboard** is an educational and defensive cybersecurity project designed to demonstrate how threat intelligence can be collected, validated, enriched, correlated, prioritized, and presented through a unified dashboard.

The system combines **Threat Intelligence (CTI)** capabilities with a **Cybersecurity Awareness** module, helping analysts understand suspicious indicators and risks while enabling users to improve their security awareness through learning modules and quizzes.

The project runs as a **single Google Colab cell**, automatically generating the required project structure, synthetic database, backend services, frontend dashboard, awareness content, and automated validation tests.

---

## ✨ Key Features

### 🔎 Threat Intelligence

* Synthetic threat intelligence dataset generation
* Support for:

  * IPv4 / IPv6 addresses
  * Domains
  * URLs
  * MD5 / SHA1 / SHA256 hashes
  * Email domains
  * CVE identifiers
* IOC syntax validation and normalization
* Defanged indicator handling
* Threat categorization
* Threat enrichment
* Campaign and indicator correlation
* Source reliability assessment
* Confidence scoring
* Risk scoring from **0–100**
* Threat classification
* MITRE ATT&CK mapping when behavioral evidence supports it

The notebook generates **2,000 synthetic threat records** and **120 synthetic vulnerability records** for demonstration and testing.

---

## 🚨 Alert Detection & Correlation

The dashboard includes a rule-based alert engine that identifies potentially important security events using factors such as:

* Risk score
* Confidence score
* Repeated observations
* Correlated indicators
* Vulnerability priority
* Campaign relationships

Alert events can be correlated within a defined time window to reduce duplicate alerts and provide a more useful analyst view.

Example alert categories include:

* `HIGH_RISK_HIGH_CONFIDENCE`
* `REPEATED_OBSERVATION`
* `CORRELATED_INDICATORS`
* `VULNERABILITY_PRIORITY`

---

## 🧮 Risk & Confidence Scoring

The project separates **risk** from **confidence**.

### Risk Score

Risk considers factors including:

* Severity
* Confidence
* Recency
* Observation frequency
* Source reliability
* Related alerts
* Context

### Confidence Score

Confidence considers:

* Source reliability
* Corroborating sources
* Number of observations
* Intelligence freshness
* Available contextual evidence

This distinction helps prevent the common mistake of treating a high-risk indicator as automatically representing a confirmed compromise.

---

## 🐛 Vulnerability Prioritization

The system includes context-aware vulnerability prioritization rather than relying only on CVSS.

Priority calculations consider:

* CVSS score
* Asset criticality
* Internet exposure
* Exploitation status
* Business impact

Vulnerabilities are categorized into:

| Priority | Meaning   |
| -------- | --------- |
| **P1**   | Immediate |
| **P2**   | This week |
| **P3**   | Planned   |
| **P4**   | Routine   |

The demonstration dataset contains **120 synthetic vulnerabilities**.

---

## 🎓 Cybersecurity Awareness Module

The project includes **15 cybersecurity awareness modules** covering topics such as:

* Phishing
* Password Security
* Multi-Factor Authentication
* Social Engineering
* Safe Browsing
* Secure Wi-Fi
* Software Updates
* Ransomware
* USB & Removable Media
* Data Privacy
* Mobile Security
* Remote Work Security
* Cloud Account Security
* Incident Reporting
* AI-enabled Scams

Each module provides:

* What the threat is
* Why it matters
* Warning signs
* Safe practices
* Recommended actions if an incident occurs

The automated tests verify retrieval of all **15 awareness modules**.

---

## 🧠 Security Awareness Quiz

The dashboard also provides an interactive cybersecurity quiz covering topics including:

* Phishing
* Passwords
* MFA
* Social Engineering
* Safe Browsing
* Ransomware
* Privacy
* Wi-Fi
* Mobile Security
* Incident Reporting

Quiz responses are scored and accompanied by explanations and learning recommendations.

---

## 🗂️ Threat Categories

The system supports multiple threat categories:

```text
PHISHING
MALWARE
RANSOMWARE
CREDENTIAL THREATS
WEB THREATS
NETWORK THREATS
VULNERABILITY EXPOSURE
SOCIAL ENGINEERING
DATA EXPOSURE
ACCOUNT SECURITY
```

These categories are also connected to defensive recommendations and awareness content.

---

## 🧩 MITRE ATT&CK Integration

The project includes MITRE ATT&CK terminology and mappings for supported threat behaviors.

Mappings are applied only when behavioral evidence and confidence requirements are satisfied rather than automatically assigning a technique to every indicator.

Example:

```text
Phishing → Initial Access → Phishing → T1566
```

This approach helps distinguish **observed behavior** from simple indicator presence.

---

## 🔐 Defensive Security Design

This project is intentionally designed for **defensive and educational use**.

The system:

* Uses synthetic data
* Does not contact submitted indicators
* Does not execute files
* Does not scan systems
* Performs indicator validation locally
* Uses documentation/reserved domains and IP ranges for demonstrations
* Sanitizes analyst notes before storage
* Provides viewer and analyst roles
* Validates API inputs and permissions

The notebook explicitly states that indicators are analyzed as data and are never contacted.

---

## 🏗️ Project Architecture

```text
                 ┌─────────────────────────────┐
                 │     Synthetic Threat Data   │
                 └──────────────┬──────────────┘
                                │
                                ▼
                 ┌─────────────────────────────┐
                 │   IOC Validation Engine     │
                 │ IP • Domain • URL • Hash    │
                 │ Email • CVE                 │
                 └──────────────┬──────────────┘
                                │
                                ▼
              ┌──────────────────────────────────┐
              │ Threat Intelligence Processing   │
              │ Enrichment • Risk • Confidence   │
              │ Correlation • ATT&CK Mapping     │
              └───────────────┬──────────────────┘
                              │
                ┌─────────────┴──────────────┐
                ▼                            ▼
      ┌──────────────────┐         ┌──────────────────┐
      │ Alert Engine     │         │ Vulnerability    │
      │ Detection &      │         │ Prioritization   │
      │ Correlation      │         │ CVSS + Context   │
      └────────┬─────────┘         └────────┬─────────┘
               │                            │
               └──────────────┬─────────────┘
                              ▼
                 ┌─────────────────────────────┐
                 │       Security Dashboard    │
                 └──────────────┬──────────────┘
                                │
                 ┌──────────────┴──────────────┐
                 ▼                             ▼
        ┌──────────────────┐          ┌──────────────────┐
        │ Threat Analysis │          │ Awareness & Quiz │
        └──────────────────┘          └──────────────────┘
```

---

## 🛠️ Technology Stack

| Technology                     | Purpose                               |
| ------------------------------ | ------------------------------------- |
| **Python**                     | Core application logic                |
| **Flask**                      | Backend/API server                    |
| **Pandas**                     | Data generation and analysis          |
| **SQLite**                     | Persistent local database             |
| **HTML/CSS/JavaScript**        | Dashboard interface                   |
| **Google Colab**               | Development and execution environment |
| **MITRE ATT&CK**               | Threat behavior classification        |
| **Regex / ipaddress / urllib** | IOC validation and normalization      |

The project automatically creates directories for backend services, frontend assets, awareness content, data, tests, screenshots, reports, and documentation.

---

## 📁 Project Structure

```text
Cybersecurity-Threat-Intelligence-Dashboard/
│
├── backend/
│   └── services/
│
├── frontend/
│
├── awareness/
│
├── data/
│   └── ti_dashboard.db
│
├── tests/
│
├── screenshots/
│
├── reports/
│
└── docs/
```

---

## 🧪 Automated Testing

The project contains an automated validation suite covering:

* IPv4 validation
* IPv6 validation
* Domain validation
* URL validation
* Hash validation
* CVE validation
* Threat creation
* Risk calculation
* Confidence calculation
* Source reliability
* IOC enrichment
* Threat correlation
* Duplicate observation handling
* Alert generation
* Alert correlation
* Alert status updates
* Analyst notes
* MITRE ATT&CK mapping
* Vulnerability scoring
* Dashboard statistics
* Filtering and sorting
* Awareness module retrieval
* Quiz scoring
* Learning recommendations
* Empty dataset handling
* API validation
* Database persistence
* Defanged indicator handling

The current notebook reports **36/36 automated tests passed**.

---

## 🚀 Getting Started

### 1. Open Google Colab

Create a new Google Colab notebook.

### 2. Copy the Project Cell

Paste the complete project cell from the notebook into Colab.

### 3. Run the Cell

Execute the cell. The project automatically:

1. Creates the project structure
2. Generates synthetic threat and vulnerability data
3. Builds the database
4. Runs automated tests
5. Starts the Flask dashboard
6. Creates dashboard access links

### 4. Access the Dashboard

The notebook generates dashboard links after successful initialization.

> **Important:** The dashboard remains available only while the associated Google Colab runtime is running.

---

## 🔑 Access Roles

The project demonstrates two application roles:

### Analyst

```text
Read + Write
```

Analysts can perform supported investigation and management actions.

### Viewer

```text
Read Only
```

Viewers can inspect dashboard information without write access.

The application defines separate analyst and viewer keys and validates access permissions through the API.

---

## ⚠️ Safety & Responsible Use

This project is intended **strictly for defensive cybersecurity education, demonstrations, and research**.

### Important limitations

* All threat intelligence records are synthetic.
* Indicators are never contacted or queried against external infrastructure.
* No malware is executed.
* No system scanning is performed.
* Demonstration IP addresses and domains use safe/reserved ranges.
* High risk does **not** mean confirmed compromise.
* Indicator validity does **not** mean an indicator is malicious.
* MITRE ATT&CK mappings are only applied where behavioral evidence supports them.

The project should not be interpreted as a production SOC, threat feed, vulnerability scanner, or incident-response platform.

---

## 📊 Demonstration Dataset

The current demonstration environment includes:

```text
2,000  Synthetic Threat Records
120    Synthetic Vulnerability Records
813    Correlated Alerts
11,475 Raw Events
15     Awareness Modules
36     Automated Tests
36/36  Tests Passed
```

These values are generated specifically for the project's demonstration environment.

---

## 🎯 Project Objectives

The project demonstrates how an integrated cybersecurity platform can:

* Centralize threat intelligence
* Validate and normalize indicators
* Quantify risk and confidence
* Enrich threat records with context
* Correlate related indicators and alerts
* Prioritize vulnerabilities using business context
* Map supported behavior to MITRE ATT&CK
* Improve security awareness
* Provide actionable defensive recommendations
* Demonstrate secure API and data-handling practices

---

## 🔮 Future Enhancements

Potential future improvements include:

* Integration with authorized real-world threat feeds
* STIX/TAXII support
* Production-grade authentication
* Role-based access control
* SIEM integration
* Automated IOC ingestion pipelines
* Advanced anomaly detection
* Machine-learning-based threat classification
* Real-time streaming alerts
* Enterprise database support
* Containerized deployment
* Cloud deployment
* Advanced SOC analytics

---

## 📜 Disclaimer

**This project is for defensive, educational, and demonstration purposes only.**

All threat intelligence data is synthetic. The system is designed so that indicators are analyzed locally as data and are not contacted, executed, or used to scan external systems.

---

## 👩‍💻 Project Status

**Status:** ✅ Functional Demonstration

**Environment:** Google Colab

**Testing:** `36/36 Passed`

**Data:** Synthetic / Demo Only

**Security Scope:** Defensive Cybersecurity & Awareness

---

⭐ **If you find this project useful, consider starring the repository and sharing it with other cybersecurity learners.**
