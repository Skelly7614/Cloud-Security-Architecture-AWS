# Cloud Security Architecture for Financial Services on AWS

Project Duration: Sep 2025 – Oct 2025

Team Project: 3 members

This repository documents a complete cloud security architecture designed for financial services workloads operating on AWS.  
It integrates identity governance, network protection, and data security to achieve confidentiality, integrity, and availability in compliance with standards such as PCI DSS, GDPR, and APRA CPS 234.
<img width="600" alt="image" src="https://github.com/user-attachments/assets/4e078179-1a0c-4a93-a60e-953915c62acb" />


I was primarily responsible for the Storage & Data Protection component of the architecture.


## 1. Project Overview

This framework provides a resilient, auditable, and secure cloud environment.  
It outlines controls that apply across the data lifecycle, including:

- Identity verification and access control
- Network segmentation and threat prevention
- Secure data storage, retention, and long-term archival
- Compliance alignment and security governance

The design follows AWS Well-Architected best practices and applies multi-layered security to protect financial data.


## 2. Architecture Layers

### Identity & Access Layer
Controls who can access resources.  
Includes IAM policies, MFA, role-based access, CloudTrail auditing, GuardDuty, and Security Hub integration.

### Network & Perimeter Layer
Controls how traffic flows and how attacks are mitigated.  
Includes VPC multi-AZ design, private/public subnet separation, NAT gateways, NACL and security group hardening, WAF, Shield, and VPC endpoints.

### Storage & Data Layer (My Component)
Secures what data is stored and how it is retained.  
Includes S3, RDS, DynamoDB, and Glacier with encryption, lifecycle automation, recovery, and immutability controls.

## 3. My Contribution: Storage & Data Protection

I designed and implemented the full Storage & Data Protection architecture, including:

### S3 Log Archive Storage
- KMS CMK encryption
- Versioning and Object Lock (WORM)
- S3 Lifecycle policy to S3-IA and Glacier
- Cross-Region Replication for resilience

### RDS Transaction Data Storage
- Multi-AZ deployment
- KMS encryption for storage and snapshots
- Automated backups and point-in-time recovery
- Secrets Manager for credential rotation

### DynamoDB High-Concurrency Events
- Point-in-Time Recovery (PITR)
- Auto-scaling RCUs and WCUs
- SSE-KMS encryption
- VPC endpoints for private access

### Glacier Archival Storage
- Vault Lock for immutability
- Long-term data retention (7–10 years)
- Compliance-aligned WORM policies

Detailed documentation is available in `docs/Storage-Data-Protection.md`.


## 4. Cloud Security Lifecycle

This architecture applies security controls across the full data lifecycle:

| Phase | Security Measures |
|-------|-------------------|
| Creation | IAM least privilege, MFA, CMK encryption |
| Use | Private access, VPC endpoint restrictions, continuous monitoring |
| Storage | Multi-AZ redundancy, snapshots, versioning, PITR |
| Disposal | Automated lifecycle deletion and archival policies |


## 5. Compliance Mapping

The architecture addresses requirements from:

- PCI DSS (auditing, encryption, access control)
- GDPR (data lifecycle management and minimization)
- APRA CPS 234 (resilience and traceability)
- AWS Well-Architected Framework (Security and Reliability Pillars)

Compliance details are maintained in `docs/Compliance-Mapping.md`.

## 6. Technologies and Services

- Amazon S3, S3-IA, Glacier  
- Amazon RDS (MySQL/Postgres, Multi-AZ)  
- Amazon DynamoDB  
- IAM, Security Hub, GuardDuty  
- AWS KMS  
- CloudWatch, CloudTrail  
- VPC, WAF, Shield, NAT Gateways, Route 53  
- Secrets Manager  

## 7. Documentation PDF

The complete project report is available in the `pdf/` directory.


## 8. License

This project is released for academic and professional demonstration purposes.

