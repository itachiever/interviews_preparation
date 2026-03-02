# Job Description: DevSecOps Engineer

## Mandatory Skills

* IAM
* Networking
* CI/CD pipelines in GitLab
* CloudFormation
* OpenTofu
* Docker
* Kubernetes
* EKS
* GitLab security scanning

---

## Requirements

* 2+ years of hands-on experience with cloud platforms (AWS preferred), including IAM, networking, compute, and storage.
* 2+ years of experience designing and maintaining CI/CD pipelines in GitLab, including integrating security scanning and pipeline controls.
* 2+ years of Infrastructure as Code (IaC) experience using CloudFormation, OpenTofu, or similar tools.
* Advanced understanding of cloud security principles, including least privilege, network segmentation, and encryption.
* 1+ year of experience integrating GitLab security scanning (SAST, DAST, SCA, container scanning, secrets detection) into CI/CD pipelines.
* 1+ year of experience with container platforms and tooling (Docker, Kubernetes, EKS).
* 1+ year of experience with identity and access management (AWS IAM, Identity Center, role-based access).
* 1+ year of experience implementing logging, monitoring, and alerting for cloud workloads.
* Understanding of SDLC, DevOps practices, and automated testing strategies.
* Experience implementing reusable pipeline templates and enforcing security guardrails at scale.
* Experience integrating CI/CD pipelines with cloud IAM and secrets management using short-lived credentials.
* Advanced problem-solving and analytical skills.
* Demonstrated ability to collaborate across development, security, and infrastructure teams.
* Demonstrated willingness to take accountability and ownership to solve problems.
* Must be authorized to work in the United States.

---

## Nice to Have

* AWS Certified Solutions Architect, Security – Specialty, or Cloud Practitioner certification.
* Experience with compliance frameworks (SOC 2, ISO 27001, NIST, CIS Benchmarks).
* Experience with policy-as-code tools (OPA, Sentinel, AWS Config rules).
* Experience supporting production incident response and post-incident analysis.

---

## Roles & Responsibilities

This role combines strong cloud engineering, security, and automation skills to support modern application platforms. The DevSecOps Engineer partners closely with Cloud Engineering, Application Development, Security, and Architecture teams to enforce security-by-design principles while enabling developer velocity.

### Responsibilities

* Design, implement, and maintain secure CI/CD pipelines for cloud-native workloads.
* Embed security controls into Infrastructure as Code (IaC) and deployment workflows.
* Integrate security scanning, testing, and policy enforcement into build pipelines.
* Implement and manage cloud security controls across cloud environments.
* Support identity and access management, secrets management, and least-privilege models.
* Automate compliance, monitoring, and vulnerability management processes.
* Partner with engineering teams to remediate security findings and reduce risk.
* Contribute to cloud security standards, patterns, and best practices.
* Support incident response, post-incident reviews, and security improvements.
* Stay current with emerging DevSecOps tools, AWS services, cloud security trends, and threats.
* Identify opportunities to streamline delivery processes and improve cloud adoption strategies.

---
# Questions:


### **Part 1: AWS Cloud, IAM & Security Fundamentals**

1.  What are the core components of an **AWS IAM Policy** (Effect, Action, Resource, Condition), and how do they enforce the **Principle of Least Privilege**?
2.  How does **AWS Identity Center** (formerly SSO) differ from traditional IAM User management for workforce access?
3.  What is the architectural design of a secure **VPC** (Virtual Private Cloud) regarding public and private subnets, and how are **NACLs** different from **Security Groups**?
4.  How are **Short-lived Credentials** generated and managed for CI/CD pipelines using AWS STS (Security Token Service) or OIDC?
5.  What is the difference between **AWS Secrets Manager** and **Parameter Store**, and when should each be used for storing sensitive data?
6.  How does **AWS KMS** (Key Management Service) manage encryption keys, and what is the difference between Customer Managed Keys (CMK) and AWS Managed Keys?
7.  What are the mechanisms to enforce **Network Segmentation** within AWS (VPC Peering, Transit Gateway, PrivateLink)?
8.  How does **AWS S3 Bucket Policy** differ from IAM User Policy in terms of access control?

### **Part 2: GitLab CI/CD & Security Integration (Mandatory)**

9.  What is the structure of a **GitLab CI/CD Pipeline** (`.gitlab-ci.yml`), and how do `stages`, `jobs`, and `scripts` relate to each other?
10. How is **GitLab SAST** (Static Application Security Testing) configured and integrated into a pipeline workflow?
11. What is the difference between **GitLab Container Scanning** and **Dependency Scanning** (SCA)?
12. How does **GitLab Secrets Detection** work within a pipeline, and where does it scan for credentials?
13. How is **DAST** (Dynamic Application Security Testing) integrated into a GitLab pipeline, and what are the infrastructure requirements?
14. What are **GitLab CI/CD Variables**, and how are they masked to prevent secret leakage in logs?
15. How do **GitLab Rules** (e.g., `only`, `except`, `when`) control pipeline execution flow?
16. How is **OIDC (OpenID Connect)** configured between GitLab and AWS to allow secure pipeline authentication without long-lived credentials?
17. What are **GitLab Pipeline Templates**, and how do they promote reusability and standardization across projects?
18. How do **Protected Branches** and **Status Checks** enforce security guardrails before merging code?
19. What is the function of **GitLab Runners** (Shared vs. Specific), and how are they secured?

### **Part 3: Infrastructure as Code (CloudFormation & OpenTofu)**

20. What are the architectural and syntax differences between **AWS CloudFormation** and **OpenTofu** (the open-source fork of Terraform)?
21. How is **State Management** handled in OpenTofu, and why is **Remote State** with **Locking** essential for teams?
22. What are **CloudFormation Stacks**, and how does **StackSets** enable deployment across multiple accounts/regions?
23. How are **Modules** used in OpenTofu to organize and reuse infrastructure code?
24. What is **Drift Detection**, and how is it handled in both CloudFormation and OpenTofu?
25. How can **Security Scanning** (e.g., Checkov, TFSec) be integrated into the IaC development lifecycle?
26. What are **Change Sets** in CloudFormation, and how do they assist in safe infrastructure updates?

### **Part 4: Policy-as-Code & Compliance (Nice to Have)**

27. What is the concept of **Policy-as-Code**, and how does it differ from traditional compliance auditing?
28. How does **OPA (Open Policy Agent)** work, and what is the purpose of the **Rego** language?
29. What is the role of **Sentinel** (specifically in the Terraform/Enterprise context) compared to OPA?
30. How do **AWS Config Rules** evaluate resource configurations for compliance (e.g., SOC 2, NIST controls)?
31. How are **CIS Benchmarks** automated and enforced using cloud-native tools or open-source scanners?

### **Part 5: Containerization & Orchestration (Docker, Kubernetes, EKS)**

32. What are the security benefits of using **Multi-stage Builds** in Docker?
33. How does **EKS (Elastic Kubernetes Service)** differ from self-managed Kubernetes in terms of control plane responsibility?
34. What are **Kubernetes Network Policies**, and how do they enforce micro-segmentation between pods?
35. How does **Kubernetes RBAC** (Role-Based Access Control) work, and what is the difference between a `Role` and a `ClusterRole`?
36. What is an **Admission Controller** in Kubernetes (e.g., OPA Gatekeeper), and how does it enforce security policies?
37. How are **Docker Image Scans** integrated into the CI/CD pipeline before deployment to EKS?
38. What is the purpose of **Helm** charts in managing Kubernetes deployments, and how are Helm values secured?

### **Part 6: Monitoring, Logging & Incident Response**

39. What is the difference between **Metrics**, **Logs**, and **Traces** in the context of observability?
40. How are **CloudWatch Logs Insights** or **ELK Stack** used to troubleshoot security incidents?
41. What is the standard workflow for **Incident Response** in a DevSecOps context (Detection, Containment, Eradication)?
42. How are **Alerts** configured for critical security events (e.g., Crypto-mining detected, IAM policy change)?
43. What is the purpose of a **Post-Incident Review (PIR)**, and how does it improve the security posture?

### **Part 7: Advanced DevSecOps Strategies & Automation**

44. How is **Shifting Left** implemented in a software development lifecycle to detect vulnerabilities earlier?
45. What are the strategies for implementing **Guardrails** in CI/CD pipelines to prevent insecure deployments?
46. How does **Dependency Proxying** in GitLab improve security and speed for package downloads?
47. What are the challenges of **Automated Compliance** (SOC 2, ISO 27001) in a rapid deployment environment?
48. How do **Infrastructure Guardrails** prevent developers from creating non-compliant resources (e.g., public S3 buckets)?
49. What is the role of **Service Mesh** (like Istio) in securing microservices communication (mTLS)?
50. How do **Chaos Engineering** practices contribute to improving system reliability and security?

# Answers:
