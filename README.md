# 🔐 Secure Multi-Account AWS Environment (IAM + SCP)

## 📌 Overview
Designed and implemented a secure multi-account AWS environment using AWS Organizations, IAM Identity Center (SSO), and Service Control Policies (SCPs) to enforce least privilege access and centralized identity management.

---

## 🏗️ Architecture Overview
- Centralized management account controlling member accounts  
- Organizational Unit (Prod) for workload isolation  
- SCPs applied at OU level for policy enforcement  
- Cross-account access via IAM roles (STS)  

---

## 🛠️ Implementation Walkthrough

### 1. AWS Organization Created
Established a centralized management account to govern multiple AWS accounts.

Org

---

### 2. Organizational Unit (Prod) Created
Designed an OU structure to isolate production workloads and enforce policies at scale.

OU

---

### 3. Member Account Moved to Prod OU
Organized accounts under the Prod OU to enable centralized governance and policy inheritance.

Move

---

### 4. Service Control Policy (SCP) Created
- Created custom SCP "DenyModifyIAMRole"  
- Restricted IAM role modification across accounts  

---

### 5. SCP Attached to OU
- Attached SCP to Prod OU  
- Enforced centralized governance across member accounts  

SCP

---

## 🔐 Identity & Access Management

### IAM Identity Center (SSO)
- Configured centralized authentication across accounts  
- Assigned permission sets:
  - AdministratorAccess  
  - ViewOnlyAccess  
- Enforced MFA for secure user authentication  

---

### Cross-Account Access (STS)
- Created IAM role for cross-account access  
- Configured trust relationship between accounts  
- Validated access using AssumeRole functionality  

---

### Monitoring & Logging
- Enabled AWS CloudTrail for audit logging  
- Configured EventBridge to detect sensitive actions  
- Verified logs in CloudWatch  

---

## 🔍 SCP Enforcement Validation
- Tested SCP by attempting restricted IAM action  
- Action was explicitly denied due to SCP restrictions  
- Verified centralized governance across AWS accounts  

Deny

---

## 🔒 Security Impact
- Reduced risk by isolating production workloads using OUs  
- Centralized identity and access management using SSO  
- Enforced least privilege using IAM roles and permission sets  
- Improved visibility using CloudTrail and monitoring services  
- Prevented unauthorized privilege escalation using SCPs  
- Eliminated need for shared credentials via secure role assumption  

---

## ✅ Outcome
Successfully built a secure multi-account AWS environment demonstrating:
- Centralized governance  
- Identity management (SSO)  
- Access control (IAM + SCP)  
- Monitoring and auditing (CloudTrail, CloudWatch)  

This project simulates a real-world enterprise cloud security architecture
