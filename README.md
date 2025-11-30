# Secure Storage Architecture on AWS

This repository documents a secure, resilient, and compliance-aligned **Storage and Data Protection Architecture** for financial workloads running on AWS.  
The design focuses on protecting log data, transactional records, audit trails, and long-term archival data with strong encryption, immutability, redundancy, and automated recovery strategies.

This project represents the **Storage Layer** portion of a larger cloud security architecture.

## 1. Overview

Financial data requires strict guarantees of confidentiality, integrity, availability, and long-term auditability.  
This storage architecture provides:

- End-to-end encryption at rest and in transit  
- Multi-AZ and multi-region resilience  
- Immutability for audit logs  
- Automated backup and recovery  
- Lifecycle and compliance retention enforcement  
- Service selection based on data category and workload requirements  

Core AWS services include **Amazon S3, DynamoDB, RDS, and S3 Glacier**.


## 2. Architecture Summary

The following diagram summarizes the data categories, AWS services, key security measures, and redundancy strategies:

<img width="1440" height="480" alt="image" src="https://github.com/user-attachments/assets/9979c919-2853-4f2a-91e4-f083df38489e" />

## 3. Architecture Components

### 3.1 Logs and Audit Records – Amazon S3

**Security Controls**
- Versioning  
- Object Lock (WORM)  
- SSE-KMS server-side encryption  
- Restricted bucket policies  
- VPC Endpoint access  
- Lifecycle transitions to S3-IA, expiration of old versions  

**Resilience**
- Cross-Region Replication (CRR)  
- Immutable audit record storage  


### 3.2 High-Concurrency Events – Amazon DynamoDB

**Security Controls**
- SSE-KMS encryption  
- VPC Endpoint restriction  
- Fine-grained IAM access policies  
- DynamoDB Streams for log forwarding  

**Resilience**
- Point-in-Time Recovery (PITR) up to 35 days  
- On-demand scaling for high activity workloads  


### 3.3 Transaction Data – Amazon RDS

**Security Controls**
- SSE-KMS encryption  
- TLS in-transit encryption  
- Secrets Manager for automatic credential rotation  
- Automated backups and retention policies  

**Resilience**
- Multi-AZ deployment with synchronous replication  
- Snapshot-based recovery for DR  


### 3.4 Long-Term Archives – Amazon S3 Glacier

**Security Controls**
- Vault Lock (immutability)  
- Compliance retention enforcement  
- SSE-KMS encryption  

**Resilience**
- Multi-region replication options  
- Long-term archival storage (7–10+ years)  


## 4. Data Governance and Compliance Mapping

This storage design supports major financial security requirements:

- Immutable audit logs  
- Multi-year regulatory retention  
- Data confidentiality through encryption  
- Integrity protection with Object Lock  
- Rapid recovery for time-critical systems  
- Geographic redundancy for operational resilience  


## 5. My Contribution

This repository reflects the portion of the cloud security architecture that I designed:  
**the Storage and Data Protection Layer**.

My responsibilities included:

- Data classification and service selection  
- Security controls for S3, RDS, DynamoDB, Glacier  
- KMS encryption architecture (SSE-KMS)  
- IAM, bucket policies, and VPC endpoint access design  
- PITR, backups, snapshots, archival lifecycle design  
- Compliance-oriented retention and immutability policies  
- Disaster recovery and cross-region replication planning  

## 6. Technologies

- Amazon S3  
- Amazon S3 Glacier  
- Amazon DynamoDB  
- Amazon RDS  
- AWS KMS  
- IAM  
- VPC Endpoints  
- Backup and recovery services  

