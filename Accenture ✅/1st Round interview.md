Questions:

1. Tell me about yourself.


2. What is your current role/project?


3. What is DevSecOps and how is it different from traditional DevOps?


4. How do you integrate security into the CI/CD pipeline?


5. Explain shift-left security approach.


6. How do you secure secrets and credentials in pipelines?


7. What is immutable infrastructure?


8. What are the common security risks in CI/CD systems?


9. Which CI/CD tools have you worked with?


10. What deployment strategy are you using?


11. What are the other deployment strategies?


12. After deployment, how do you roll back failed deployments?


13. Explain artifact repositories and the tools used.


14. What are the differences between:



• SAST

• DAST

• SCA

• IAST

15. How do you handle dependency vulnerabilities or repeated vulnerabilities?


16. What is Zero Trust Security?


17. Which containerization platform are you using?


18. Difference between Docker containers and VMs?


19. How do you optimize Docker images?


20. Have you worked with cloud technologies?


21. Difference between Azure DevOps and GitHub Actions?


22. What is Azure Key Vault?


23. Can you explain GCP IAM roles?


24. How do you manage Terraform remote state securely?


25. What is centralized logging?


26. If deployment fails in production, how would you troubleshoot it?


27. If your CI pipeline becomes very slow, how would you optimize it?


28. Which project management tool are you using? Jira or Azure DevOps?


29. Is there any portal where tasks are assigned/tracked?


30. Which organization are you currently working with?


31. You worked with TCS also, right?


32. Are you currently in Bangalore or Mumbai?


33. Do you have any questions for me?


# Answers 


1. Tell me about yourself

> “My name is (NAME). Currently I’m working as a DevSecOps Engineer at (COMPANY) and deployed to a fintech client called (CLIENT NAME), which provides payment gateway solutions for banking clients.

My primary responsibility is integrating security into CI/CD pipelines and managing DevSecOps tooling. I work mainly with Jenkins, GitLab, Nexus, Fortify for SAST/DAST, Sonatype Lifecycle for SCA/SBOM, and Trivy for container image scanning.

I’m also involved in pipeline automation, vulnerability management, developer coordination, and security remediation activities. Along with this, I worked on integrating tools into Jenkins pipelines, handling approvals, scan gates, reporting, and deployment workflows.

Before this, I worked at (PREVIOUS COMPANY NAME) where I was mainly involved in CI/CD automation, Jenkins pipelines, scripting, and deployment support activities.

Overall, I have around 4 years of experience focused mainly on DevOps and DevSecOps practices, especially secure CI/CD and security automation.”




---

2. What is your current role/project?

> “Currently I’m working as a DevSecOps Engineer for a fintech client environment. The organization follows PCI-DSS-oriented security practices and supports payment gateway applications.

My role is mainly focused on integrating and managing DevSecOps security tooling across CI/CD pipelines. We use Jenkins for CI/CD, GitLab as SCM, Nexus for artifact storage, Fortify for SAST/DAST, Sonatype Lifecycle for SCA and SBOM, and Trivy for image scanning.

I’m responsible for tool onboarding, configuration, pipeline integration, scan automation, vulnerability reporting, and supporting development teams for remediation activities.

The environment has both VM-based and Kubernetes-based deployments, and deployments are handled through automated Jenkins pipelines with approvals and rollback mechanisms.”




---

3. What is DevSecOps and how is it different from traditional DevOps?

> “DevSecOps is the practice of integrating security into every stage of the software development lifecycle instead of treating security as a separate final phase.

Traditional DevOps mainly focuses on faster development, automation, and continuous delivery. DevSecOps extends that by embedding security controls into CI/CD pipelines and development workflows.

In DevSecOps, activities like SAST, DAST, SCA, secret scanning, image scanning, and compliance checks are integrated early into the pipeline using a shift-left approach.

The goal is to achieve both speed and security together.”




---

4. How do you integrate security into the CI/CD pipeline?

> “We integrate security into the CI/CD pipeline by adding automated security stages into Jenkins pipelines.

Typically the flow is:

Code checkout from GitLab

Build using Maven/Gradle/npm

SonarQube quality analysis

Fortify SAST scanning

Sonatype SCA/SBOM scan

Docker image build

Trivy image scan

Artifact upload to Nexus

Deployment approval and deployment


Based on severity thresholds, the pipeline can fail automatically if critical or high vulnerabilities are detected.

We use both plugin-based integrations and API/CLI-based integrations depending on tool capability.”




---

5. Explain shift-left security approach

> “Shift-left security means moving security checks earlier into the software development lifecycle instead of performing them only before production release.

For example, developers can trigger SAST or dependency scans during the build stage itself or even from IDE integrations.

This helps identify vulnerabilities earlier, reduces remediation cost, improves developer awareness, and prevents vulnerable code from reaching later environments.

In our pipelines, security scans are integrated directly into CI stages so vulnerabilities are caught before deployment.”




---

6. How do you secure secrets and credentials in pipelines?

> “We avoid hardcoding secrets inside pipelines or repositories.

Secrets are managed using Jenkins Credentials Manager and HashiCorp Vault.

Sensitive information like API keys, database passwords, tokens, and certificates are securely stored in Vault or Jenkins credential stores, and fetched dynamically during pipeline runtime.

Access is controlled using RBAC and least privilege principles. We also restrict credential visibility and rotate sensitive credentials periodically.”




---

7. What is immutable infrastructure?

> “Immutable infrastructure means infrastructure components are not modified after deployment. Instead of updating existing servers manually, we replace them with newly provisioned versions whenever changes are required.

This helps reduce configuration drift, improves consistency, and makes deployments more predictable and reproducible.

Tools like Terraform and container-based deployments support immutable infrastructure practices.”




---

8. What are the common security risks in CI/CD systems?

> “Some common security risks in CI/CD systems are:

Hardcoded secrets in pipelines

Excessive user permissions

Vulnerable plugins or outdated tools

Insecure artifact repositories

Unsigned or unverified artifacts/images

Pipeline bypass without approvals

Vulnerable third-party dependencies

Insecure container images

Lack of RBAC and audit logging


To mitigate these, we implement RBAC, security scanning, signed artifacts, approval gates, centralized logging, and secure secret management.”




---

9. Which CI/CD tools have you worked with?

> “Primarily I worked with Jenkins for CI/CD automation and pipeline orchestration.

I also have exposure to GitLab CI and basic exposure to GitHub Actions.

In Jenkins, I worked on:

Pipeline development

Security integrations

Shared libraries

Deployment workflows

Multi-environment deployments

Approval gates

Rollback handling

Artifact promotions


Jenkins is the primary CI/CD platform in my current environment.”




---

10. What deployment strategy are you using?

> “Primarily we use rolling deployment strategy for Kubernetes-based applications.

In rolling updates, pods are replaced gradually with the new version without complete downtime. Kubernetes ensures application availability while updating instances incrementally.

For VM-based deployments, deployments are handled through controlled Ansible-based rollout workflows with approvals and rollback support.

We also have rollback mechanisms to restore the previous stable version if deployment validation fails.” 
