
## Pipeline Securiy:

In Jenkins, we secured the pipeline by implementing RBAC, integrating Vault for secret management, enabling MFA through SSO, restricting production deployment permissions, securing build agents, enabling audit logs, and enforcing pull-request-based pipeline changes with approval workflows.

Securing the pipeline itself involves protecting CI/CD infrastructure, runners, credentials, pipeline definitions, and deployment permissions using RBAC, MFA, secrets management, least privilege access, branch protection, audit logging, secure runners, and approval gates.


## CSPM

CSPM(Cloud Security Posture Management) focuses on identifying cloud misconfigurations and compliance violations such as public exposure, weak IAM permissions, disabled encryption, and insecure networking.

## CNAPP

CNAPP(Clouud Native Application Protection Platform) is a broader cloud-native security platform that combines CSPM, container security, IaC scanning, vulnerability management, Kubernetes security, and runtime protection into a unified solution.

## PCI-DSS

PCI-DSS is a compliance framework focused on protecting cardholder data. In DevSecOps, we support PCI compliance by implementing secure CI/CD pipelines, enforcing least privilege access, enabling encryption, integrating IaC/container security scans, monitoring logs, and automatically blocking deployments if compliance violations are detected.

## IaC scan for PCI DSS:
n DevSecOps pipelines, we integrated IaC scanning tools to validate PCI-DSS compliance before infrastructure deployment. The scans checked for public exposure, encryption settings, IAM permissions, logging configurations, and secure network access. If critical PCI violations were detected, the pipeline automatically failed to prevent insecure infrastructure deployment.

