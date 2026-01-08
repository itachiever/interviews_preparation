# DevSecOps & Cloud Security Interview Topics

## Multi-Cloud Security Fundamentals (AWS, Azure, OCI)

* How do IAM models differ across AWS, Azure, and OCI?
* What is the principle of least privilege, and how do you apply it across multi-cloud environments?
* How would you design a secure multi-cloud network architecture connecting AWS, Azure, and OCI?
* Explain how you manage secrets and credentials across different clouds securely.
* What tools or methods do you use to implement centralized identity management across multiple clouds?

---

## Infrastructure as Code (Terraform, CloudFormation, Bicep)

* Describe how Terraform manages state and how you secure Terraform state files.
* What are best practices for structuring Terraform modules in a multi-cloud project?
* How do you implement role-based access control in Terraform for large teams?
* Compare CloudFormation vs Terraform — when would you prefer one over the other?
* How do you integrate Terraform execution into a Jenkins or GitHub Actions CI/CD pipeline with security checks?

---

## Policy as Code (OPA, Sentinel, Azure Policy, AWS Config)

* How does Policy as Code differ from Infrastructure as Code?
* Explain how Open Policy Agent (OPA) works and how it can be integrated with CI/CD.
* What is Sentinel in Terraform Cloud, and how can you enforce compliance through it?
* How can AWS Config and Security Hub be used to automate remediation?
* Give a real example of a policy you wrote to enforce security compliance in Terraform.

---

## Cloud Governance and Control

* How do you implement Service Control Policies (SCPs) in AWS Organizations?
* What is an Azure Blueprint, and how can it help enforce governance at scale?
* Describe an OCI compartment strategy that supports least privilege and separation of duties.
* How do you manage exceptions or “break-glass” access securely in production?
* What are key differences between AWS Control Tower, Azure Landing Zone, and OCI Landing Zone?

---

## CI/CD Security Integration

* How do you secure secrets in Jenkins or GitHub Actions pipelines?
* What’s your approach for inserting security scanning tools (SAST, DAST, SCA) into CI/CD flows?
* In what sequence should SAST, DAST, and IaC scans be integrated in a pipeline?
* How can you automate approval gates for high-severity vulnerabilities in a pipeline?
* Describe a pipeline stage you implemented that prevented a misconfigured Terraform deployment.

---

## Serverless Security and Automation (Lambda, Azure Functions, OCI)

* What are some security best practices when developing Lambda functions?
* How do you implement IAM roles and least privilege for serverless functions?
* How do you secure environment variables in AWS Lambda?
* What are common vulnerabilities in serverless environments, and how do you mitigate them?
* Can you describe a use case where you used a serverless function to automate a security check?

---

## Cloud Security Controls and Monitoring

* How do you continuously monitor misconfigurations across AWS, Azure, and OCI?
* What’s your approach to implementing Cloud Security Posture Management (CSPM)?
* Explain how to use AWS Security Hub and Azure Defender together for unified visibility.
* How do you automate tagging policies to maintain compliance across accounts?
* What metrics do you consider key indicators of cloud security health?

---

## Container and Kubernetes Security

* How do you secure container images before deployment?
* Which tools can perform container scanning as part of CI/CD?
* What are key security configurations for Kubernetes cluster hardening?
* How do you implement role-based access control (RBAC) in Kubernetes?
* Explain the concept of a Kubernetes Admission Controller and its role in enforcing security.

---

## Secure Coding and Scanning

* Differentiate between SAST, DAST, and SCA with examples.
* What is the importance of OWASP Top 10 for DevSecOps engineers?
* How do you ensure developers write secure code from the start?
* Describe a time you identified and mitigated a real vulnerability using SCA or static analysis.
* How would you secure APIs or webhooks used in your CI/CD pipelines?

---

## Compliance and Documentation

* How do you prepare for compliance audits like ISO 27001 or SOC 2 in a DevSecOps environment?
* What automated methods can generate evidence for compliance reporting?
* Describe your process for documenting policies, controls, and exceptions.
* How do you map cloud resources and controls to compliance frameworks like PCI-DSS?
* How do you keep documentation and IaC definitions in sync to avoid configuration drift?

---

