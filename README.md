
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

<img src="https://github.com/user-attachments/assets/0d9b3516-a16a-49ad-9885-8078f71fec5b" width="800" />

---

### 2. Organizational Unit (Prod) Created
Designed an OU structure to isolate production workloads and enforce policies at scale.

<img src="https://github.com/user-attachments/assets/3d36be7e-e578-43b6-b5a9-2295bd13cafc" width="800" />

### 3. Member Account Moved to Prod OU
Organized accounts under the Prod OU to enable centralized governance and policy inheritance.

<img src="https://github.com/user-attachments/assets/d1db4d2e-9b2c-49da-9991-07737ccca222" width="800" />

---

### 4. Service Control Policy (SCP) Created
- Created custom SCP "DenyModifyIAMRole"  
- Restricted IAM role modification across accounts  
<img src="https://github.com/user-attachments/assets/53628e72-1fab-41d5-84b7-9d8942a54059" width="800" />

### 5. SCP Attached to OU
- Attached SCP to Prod OU  
- Enforced centralized governance across member accounts  
<img src="https://github.com/user-attachments/assets/43b4dc80-34f3-4756-856b-7a79c71926e4" width="800" />

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

- Created IAM role to allow secure access from management account to member account
- Configured trust relationship for cross-account role assumption
- Attached S3 permissions to demonstrate controlled resource access
- Used AssumeRole to access resources without sharing credentials
- Verified role assumption by switching roles and accessing S3 resources in the target account

<img src="https://github.com/user-attachments/assets/425548ec-2c4c-4aa6-8487-7e5b502ca7e3" width="900" />
<img src="https://github.com/user-attachments/assets/ee5c97cc-ba1b-4664-8a1d-f8ce7f728096" width="900" />

### Cross-Account S3 Access

- Configured S3 bucket policy to allow access from a specific IAM role in another account
- Restricted access using role-based permissions instead of public access
- Enabled secure cross-account data sharing using least privilege principles and STS AssumeRole
- Successfully validated access by assuming role and accessing S3 bucket in target account

<img src="https://github.com/user-attachments/assets/f9676217-58ac-4542-81da-409be4d165f8" width="900" />


<img src="https://github.com/user-attachments/assets/fcbd05da-ba5a-41b9-8fc0-a67ad1c907fb" width="800" />

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
