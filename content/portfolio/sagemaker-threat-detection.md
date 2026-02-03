---
title: "Cybersecurity Threat Detection (Amazon SageMaker)"
date: 2026-02-02
draft: false
summary: "Built a near real-time threat detection system using SageMaker and XGBoost to flag anomalous network activity, with secure IAM access, automated ML workflow, and CloudWatch monitoring."
tags: ["AWS", "SageMaker", "XGBoost", "Security", "ML", "IAM", "CloudWatch"]
---

## Overview
This project implements a **near real-time cybersecurity threat detection system** using Amazon SageMaker. It uses machine learning to identify anomalous or malicious network behavior—such as DDoS patterns, unauthorized access attempts, and phishing-related traffic—by learning behavioral patterns from network traffic data.

The design mirrors **production-style ML security architectures**, emphasizing secure access control, reproducibility, automation, and monitoring.

## Objectives
- Detect abnormal network behavior using machine learning
- Automate the ML lifecycle from preprocessing to deployment
- Implement least-privilege, auditable access using AWS IAM
- Deliver near real-time inference with minimal operational overhead
- Produce a portfolio-ready, production-style cloud security project

## High-level architecture
**Data flow**
1. Raw network traffic data is stored in Amazon S3  
2. AWS Lambda performs preprocessing and feature engineering  
3. Processed data is saved back to S3  
4. SageMaker trains an XGBoost model  
5. The model is deployed as a SageMaker endpoint  
6. New traffic is scored for anomalies via near real-time inference  
7. Logs and metrics are captured in CloudWatch

## AWS services used
- **Amazon SageMaker** — training, deployment, inference, and pipelines  
- **Amazon S3** — raw/processed data + model artifacts  
- **AWS Lambda** — serverless preprocessing + feature extraction  
- **Amazon CloudWatch** — logging, metrics, monitoring  
- **AWS IAM** — role-based access control and least privilege

## Security & access control
A dedicated **SageMaker execution role** is used for notebooks, training jobs, and endpoints.

**Key characteristics**
- Temporary credentials (no hard-coded secrets)
- Least-privilege access to only required resources (S3, CloudWatch, ECR)
- Auditable actions via CloudTrail

## Data ingestion & preprocessing
**Dataset**
A public intrusion detection dataset (e.g., CICIDS, NSL-KDD, or UNSW-NB15) is used to simulate real-world traffic and attack behavior.

**Preprocessing steps**
- Remove duplicates and irrelevant features
- Handle missing/malformed values
- Encode categorical features
- Normalize numeric fields
- Engineer behavioral features (examples):
  - Connection frequency
  - Packet size statistics
  - Session duration metrics

Processed datasets are stored in S3 and versioned for reproducibility.

## Model training & evaluation
**Algorithm: XGBoost**
Chosen for strong performance on tabular data, speed, and ability to capture nonlinear relationships.

**Training workflow**
- SageMaker pulls processed data from S3
- Training runs in a managed container
- Model artifacts are saved to S3
- Logs and metrics are emitted to CloudWatch

## Deployment & inference
The trained model is deployed as a **SageMaker endpoint**, enabling:
- Managed, scalable inference
- Secure API-based predictions
- Near real-time threat detection (~30-second delay)

Incoming network data is evaluated and labeled as **normal** or **potentially malicious**.

## Automation with SageMaker Pipelines
SageMaker Pipelines automate:
- preprocessing
- training
- evaluation
- conditional deployment

This supports repeatability, versioning, and audit-friendly ML operations.

## Monitoring & observability
CloudWatch is used to:
- capture logs for training jobs and endpoints
- monitor prediction volume and error rates
- support future drift monitoring

## Cost & performance considerations
- Estimated runtime: **2–3 hours**
- Estimated cost: **~$1–$2**
- Managed/serverless services minimize idle overhead

## Limitations & future enhancements
**Current limitations**
- Near real-time (not fully streaming)
- Single-model architecture

**Planned enhancements**
- Add Amazon Kinesis for real-time streaming
- Add drift detection and automated retraining triggers
- Expand to multi-model/ensemble detection
- Integrate alerting via SNS and/or Security Hub

## Resume-ready summary
Designed and implemented a secure, automated ML pipeline on AWS using SageMaker and XGBoost to detect anomalous network activity with near real-time inference, leveraging IAM-based access control, serverless preprocessing, and CloudWatch monitoring.