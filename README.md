AWS Real-Time Security Monitoring & Automated Response
This project demonstrates a real-time cloud security monitoring system built using native AWS services.

The system detects access to sensitive data (Honeytoken_credentials) and automatically disables the offending IAM user’s access key using AWS Lambda.
ARCHITECTURE 

CloudTrail → EventBridge → SNS → Lambda → IAM Remediation
Key Features
	•	Multi-region CloudTrail logging
	•	CloudWatch Metric Filter detection
	•	Event-driven alerting with EventBridge
	•	Automated containment via Lambda
	•	IAM access key revocation
	•	Forensic logging
Technologies Used
	•	AWS CloudTrail
	•	Amazon CloudWatch
	•	Amazon EventBridge
	•	AWS Lambda
	•	IAM
	•	AWS Secrets Manager
	•	SNS
Security Outcome
	•	Real-time detection of sensitive API activity
	•	Automated credential revocation
	•	Reduced attacker dwell time
	•	Continuous monitoring aligned with NIST controls
