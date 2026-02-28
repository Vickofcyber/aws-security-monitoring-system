# AWS Real-Time Security Monitoring & Automated Response

## 📌 Overview

This project demonstrates a real-time cloud security monitoring and automated incident response system built using native AWS services.

The system detects access to a sensitive honeytoken secret (`Honeytoken_credentials`) and automatically disables the offending IAM user's access key using AWS Lambda.

---

## 🏗 Architecture

CloudTrail → EventBridge → SNS → Lambda → IAM Remediation

---

## 🔍 Detection Logic

### Flow 1 – Metric-Based Detection
CloudTrail → CloudWatch Logs → Metric Filter → CloudWatch Alarm → SNS

- Detects `GetSecretValue` API calls
- Triggers if access occurs ≥ 1 time within 1 minute
- Sends email notification via SNS

### Flow 2 – Event-Driven Detection (Primary Flow)
CloudTrail → EventBridge → SNS → Lambda

- Listens for `GetSecretValue` events in real-time
- Sends detailed SNS notification
- Triggers automated containment via Lambda

---

## 🛑 Automated Containment (Kill-Switch)

When the honeytoken is accessed:

1. CloudTrail logs the event
2. EventBridge matches the pattern
3. SNS sends alert notification
4. Lambda disables the IAM user's access key

Result:
Any subsequent AWS CLI command returns:
---

## 🛠 Technologies Used

- AWS CloudTrail
- Amazon CloudWatch
- Amazon EventBridge
- AWS Lambda
- IAM
- AWS Secrets Manager
- Amazon SNS
- AWS CLI

---

## 🔐 Security Outcomes

- Real-time detection of sensitive API activity
- Automated credential revocation
- Reduced attacker dwell time
- Forensic visibility (user identity, source IP, event time)
- Continuous monitoring aligned with NIST principles

---

## 🎯 Key Takeaways

- Event-driven security provides faster detection than metric-based alarms
- Automated containment significantly reduces risk
- CloudTrail logs are critical for forensic investigation
- Lambda enables scalable defensive automation
