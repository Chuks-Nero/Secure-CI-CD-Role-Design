# Secure CI/CD Role Design
## Goal

Design a secure IAM role for CI/CD pipeline that:

1. Enable automatic deployment to Development environments.
2. Restrict Production deployments to approved, tagged releases only.
3. Minimize blast radius across environments

## Project Description

This project defines a secure, enterprise-grade IAM role architecture for CI/CD pipelines in AWS. The design follows DevSecOps and Zero Trust principles, ensuring that automated pipelines can deploy safely with minimal privileges, strong identity verification, and strict environment separation.

The architecture eliminates static credentials, enforces identity federation, and introduces tag-based authorization to control production deployments. Development environments deploy automatically, while production deployments are cryptographically gated through tagging and role-based conditions.

This model is suitable for regulated environments and enterprise cloud governance programs.

## Role Architecture Overview

The CI/CD security model uses three roles:

1. CICD-AssumeRole
    
    Entry role assumed by the CI/CD system via OIDC.
    
2. CICD-Dev-DeployRole
    
    Role used for automatic deployments to Development environments.
    
3. CICD-Prod-DeployRole
    
    Role used for Production deployments, gated by release tagging.
    

Role Flow:

CI/CD System

→ CICD-AssumeRole (OIDC Identity Federation)

→ CICD-Dev-DeployRole (Auto Dev Deploy)

→ CICD-Prod-DeployRole (Tag-Gated Prod Deploy)
