# AWS-Secret-Monitor

## 📌 Overview
**aws-secret-monitor** is a cloud-native security monitoring solution that detects and responds to unauthorized access to **AWS Secrets Manager** in near real-time.  
It leverages **AWS CloudTrail, CloudWatch, and Amazon SNS** to provide rapid detection, automated alerting, and actionable insights — reducing Mean Time to Detect (MTTD) and strengthening your cloud security posture.

---

## 🎯 Why It Matters
Organizations need to continuously monitor secret access to:
- Prevent credential leakage and data breaches  
- Meet compliance requirements (SOC 2, ISO 27001)  
- Reduce risk exposure through rapid detection & response  

This project demonstrates **event-driven detection, real-time alerting, and actionable incident response workflows** — all aligned with cloud security best practices.

---

## 🏗️ Architecture

**Figure 1: End-to-End Architecture**  
<img width="2048" height="767" alt="Arhcitetcure for cloud monitroing" src="https://github.com/user-attachments/assets/1a4c2027-35cf-437c-921f-3656ca694035" />




**How It Works:**
1. **AWS Secrets Manager** securely stores credentials and API keys.  
2. **AWS CloudTrail** logs every `GetSecretValue` API call.  
3. Logs stream into **CloudWatch Log Groups**.  
4. **Metric Filters** detect secret access events.  
5. **CloudWatch Alarms** fire when events exceed defined thresholds.  
6. **Amazon SNS** publishes notifications to subscribers.  
7. **Email Alerts** are sent to the security team for immediate investigation.

---

## ⚙️ Implementation Details

### 1️⃣ Logging & Tracking
- Enabled **AWS CloudTrail** to capture `GetSecretValue` calls across all regions.
- Configured log aggregation and retention in **CloudWatch Log Groups**.
- Archived logs in **Amazon S3** for long-term retention and audit compliance.

---

### 2️⃣ Real-Time Monitoring
- Created a **CloudWatch Metric Filter** for `eventName = GetSecretValue`.
- Configured **CloudWatch Alarm** with 1-minute evaluation window.  

**Figure 2: Metric Filter & Alarm Configuration**  
<img width="800" height="254" alt="cloud monitor 1" src="https://github.com/user-attachments/assets/6f7cfe54-6dc8-4213-b7a4-2922c557964c" />


| Setting         | Value            |
|-----------------|-----------------|
| **Namespace**   | `SecurityMetrics` |
| **Metric Name** | `Secret is accessed` |
| **Threshold**   | ≥ 1 event per minute |
| **Statistic**   | Sum |

---

### 3️⃣ Incident Response Automation
- Integrated **Amazon SNS** to publish notifications on alarm state changes.
- Subscribed security team email distribution list for immediate alerts.

**Figure 3: Real-Time Email Alert**  
<img width="800" height="404" alt="cloud monitor 2" src="https://github.com/user-attachments/assets/82d1405e-7a30-4433-8601-cb93c1ca9206" />


Includes:
- Alarm name and state
- Triggering metric and threshold
- Timestamp of event
- Direct CloudWatch console link for investigation

---

### 4️⃣ Visualization & Analysis
**Figure 4: CloudWatch Alarm History**  
<img width="800" height="347" alt="cloud monitor 3" src="https://github.com/user-attachments/assets/1f9d09dd-2a90-41bb-942c-ba89f773f85f" />


This dashboard provides:
- A timeline view of secret access events
- Correlation with alarm state changes
- Verification that monitoring is functioning correctly

---

## 🏆 Outcomes
- 📉 **MTTD Reduction:** From hours to < 60 seconds  
- 🛡️ **Improved SOC Capabilities:** Real-time triage and investigation  
- 📜 **Audit-Ready Evidence:** Long-term log retention in encrypted S3 buckets  
- 🚀 **Operational Efficiency:** Fully automated, no manual log inspection required  

---

## 🛠️ Tech Stack
**Amazon KMS · AWS CloudTrail · AWS CloudWatch (Log Groups, Metric Filters, Alarms) · Amazon SNS · Amazon S3**

---

## 💡 Why This Matters
Unlike basic logging setups, **aws-secret-monitor** is a **full event-driven detection pipeline** that demonstrates:
- **Cloud Security Architecture Expertise** – End-to-end system design
- **Operational Maturity** – Automated detection & alerting, ready for production
- **Employer-Relevant Skills** – Hands-on AWS security engineering experience

---

## 📄 License & Use
This project is designed for **educational and portfolio purposes**, but can be adapted for real-world production environments with minimal changes.

---
