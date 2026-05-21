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


---
11. What are the other deployment strategies?

> “Apart from rolling deployments, common deployment strategies are:

Blue-Green Deployment → Two identical environments are maintained. Traffic switches from old version to new version after validation.

Canary Deployment → New version is released to a small percentage of users first before full rollout.

Recreate Deployment → Old version is stopped completely before deploying new version. This can cause downtime.

A/B Deployment → Different versions are exposed to different user groups for testing and analysis.


In our environment, rolling deployment is the primary strategy for Kubernetes workloads.”




---

12. After deployment, how do you roll back failed deployments?

> “If deployment fails, first we identify whether the issue is application-level, configuration-level, or infrastructure-level.

For Kubernetes deployments, we usually perform rollback using the previous stable deployment revision. Kubernetes maintains rollout history, so rollback can be triggered quickly.

For VM-based deployments, we redeploy the last known-good artifact version from Nexus using the deployment pipeline.

Our pipelines also maintain version tracking and deployment approvals, which helps restore stable releases safely.”




---

13. Explain artifact repositories and the tools used.

> “Artifact repositories are centralized platforms used to securely store versioned build artifacts and container images after successful builds and security validations.

Examples of artifacts are:

JAR files

WAR files

Docker images

ZIP packages


In our environment, we use Sonatype Nexus Repository.

Pipeline flow is:

Build application

Run quality and security scans

Push approved artifact to Nexus

Deploy only approved artifact across environments


This ensures artifact consistency, version control, rollback capability, and traceability.

We also use image signing and artifact verification mechanisms before deployments.”




---

14. What are the differences between SAST, DAST, SCA, and IAST?

SAST (Static Application Security Testing)

> “SAST scans application source code, bytecode, or binaries without running the application.

It identifies coding vulnerabilities like SQL injection, hardcoded secrets, insecure functions, etc.

We use Fortify SAST in our pipelines during build stages.”




---

DAST (Dynamic Application Security Testing)

> “DAST scans running applications during runtime by testing APIs, URLs, endpoints, authentication, and application behavior.

It helps identify runtime vulnerabilities like XSS, authentication issues, security misconfigurations, etc.

We use Fortify WebInspect for DAST.”




---

SCA (Software Composition Analysis)

> “SCA identifies vulnerabilities in third-party libraries and open-source dependencies used by the application.

It checks package versions against vulnerability databases like CVE/NVD.

We use Sonatype Lifecycle for SCA.”




---

IAST (Interactive Application Security Testing)

> “IAST combines both runtime monitoring and code-level analysis while the application is running.

It provides more accurate vulnerability detection with lower false positives by observing actual application execution behavior.”




---

15. How do you handle dependency vulnerabilities or repeated vulnerabilities?

> “For dependency vulnerabilities, first we identify:

severity,

affected package,

vulnerable version,

and available fixed version.


Then we coordinate with development teams to upgrade or replace vulnerable dependencies.

For repeated vulnerabilities, we check whether:

remediation was incomplete,

the dependency reappeared through transitive dependencies,

or it is an accepted risk/false positive.


In Fortify and Sonatype, previously reviewed findings can be marked as suppressed, false positive, or risk accepted with proper justification and audit tracking.

We also maintain security gates to prevent repeated high-severity vulnerabilities from reaching production.”




---

16. What is Zero Trust Security?

> “Zero Trust Security follows the principle of ‘never trust, always verify.’

No user, device, application, or service is trusted by default even if it is inside the organization network.

Every access request must be authenticated, authorized, and continuously validated.

Key principles include:

least privilege access,

MFA,

continuous verification,

network segmentation,

and strict identity-based access control.”





---

17. Which containerization platform are you using?

> “We primarily use Docker for containerization.

Applications are packaged into Docker images along with required dependencies, which ensures consistency across environments.

These images are scanned using Trivy and then deployed into Kubernetes environments for orchestration.”




---

18. Difference between Docker containers and VMs?

> “Virtual Machines virtualize the hardware layer and each VM contains its own guest operating system.

Docker containers virtualize at the operating system level and share the host OS kernel.

Because containers share the host kernel, they are lightweight, start faster, consume fewer resources, and are more portable compared to VMs.

VMs provide stronger isolation, while containers are optimized for scalability and microservices deployments.”




---

19. How do you optimize Docker images?

> “Some common Docker image optimization practices are:

Using lightweight base images like Alpine

Using multi-stage builds

Removing unnecessary packages and cache

Reducing image layers

Running containers as non-root users

Excluding unnecessary files using .dockerignore

Scanning images for vulnerabilities using Trivy


These practices reduce image size, improve security, and speed up deployments.”



---

20. Have you worked with cloud technologies?

> “Yes, I have worked mainly with AWS and Azure environments, and I also have basic exposure to GCP concepts.

In AWS, I worked with services like EC2, S3, RDS, IAM, and EKS-related workflows.

In Azure, I have exposure to AKS, Azure Key Vault, Azure Monitor, networking basics, and deployment integrations.

My primary involvement was around CI/CD integration, DevSecOps tooling, deployments, monitoring, and automation workflows rather than deep cloud architecture design.”


---

21. Difference between Azure DevOps and GitHub Actions?

> “Azure DevOps is a complete DevOps platform that provides Boards, Repos, Pipelines, Test Plans, and Artifacts in a single ecosystem.

GitHub Actions is mainly a CI/CD and workflow automation platform integrated directly with GitHub repositories.

Azure DevOps is commonly used in enterprise environments requiring complete ALM and project management capabilities, while GitHub Actions is lightweight and developer-friendly for repository-based automation workflows.

I primarily worked with Jenkins and GitLab CI, and I have basic exposure to GitHub Actions workflows.”




---

22. What is Azure Key Vault?

> “Azure Key Vault is a secure secret management service provided by Azure.

It is used to securely store and manage:

passwords,

API keys,

certificates,

encryption keys,

and sensitive credentials.


Applications and pipelines can securely retrieve secrets during runtime instead of hardcoding them inside code or pipelines.

It also supports RBAC, audit logging, and secret rotation capabilities.”




---

23. Can you explain GCP IAM roles?

> “GCP IAM stands for Identity and Access Management.

It is used to control who can access which resources and what actions they can perform.

GCP IAM mainly supports:

Basic roles

Predefined roles

Custom roles


Access is assigned to users, groups, or service accounts based on least privilege principles.

IAM helps centrally manage permissions securely across GCP resources.”




---

24. How do you manage Terraform remote state securely?

> “Terraform remote state should be stored centrally and securely to support collaboration and avoid conflicts.

Commonly, we use remote backend storage like AWS S3 along with DynamoDB locking for state locking and concurrency control.

Security best practices include:

encryption at rest,

restricted IAM access,

versioning,

backup,

and avoiding local state sharing.


State locking prevents multiple users from modifying infrastructure simultaneously.”




---

25. What is centralized logging?

> “Centralized logging means collecting logs from multiple servers, applications, containers, and environments into a single centralized platform for monitoring and troubleshooting.

In our environment, ELK Stack is used for centralized logging.

It helps with:

troubleshooting,

root cause analysis,

auditing,

security monitoring,

and faster incident investigation.


Monitoring metrics like CPU, memory, and application health are handled separately using Prometheus and Grafana.”




---

26. If deployment fails in production, how would you troubleshoot it?

> “First, I identify whether the issue is related to:

application code,

deployment configuration,

infrastructure,

or environment dependencies.


For Kubernetes deployments, I check:

pod status,

logs,

events,

rollout status,

readiness/liveness probes,

and resource usage.


For VM-based deployments, I verify:

service status,

deployment logs,

environment variables,

configuration changes,

and connectivity issues.


If production impact is critical, we immediately rollback to the previous stable version and then perform detailed RCA.”




---

27. If your CI pipeline becomes very slow, how would you optimize it?

> “First, I identify which stage is causing the delay by analyzing pipeline execution time.

Common optimization approaches are:

parallelizing independent stages,

dependency caching,

optimizing build steps,

reducing unnecessary scans,

optimizing Docker image builds,

improving agent resources,

and reducing redundant artifact downloads.


I also verify whether recent code changes, large dependencies, or scanner performance issues are increasing execution time.

Pipeline optimization should maintain security checks while improving execution efficiency.”




---

28. Which project management tool are you using? Jira or Azure DevOps?

> “Primarily Jira is used for sprint planning, defect tracking, vulnerability tracking, and task management activities.

Security findings, remediation tasks, and release coordination are tracked through Jira workflows.”




---

29. Is there any portal where tasks are assigned/tracked?

> “Yes, tasks, sprint items, vulnerabilities, change requests, and remediation activities are tracked through Jira.

Teams coordinate through sprint boards, tickets, dashboards, and approval workflows.”




---

30. Which organization are you currently working with?

> “Currently I’m working with CURRENT COMPANY as a DevSecOps Engineer and deployed to a fintech client environment called CLIENT COMPANY.”

(If asked further)

“Client provides payment gateway and financial transaction-related solutions for banking clients.”




---

31. You worked with (PREVIOUS COMPANY NAME) also, right?

> “Yes. Before my current role, I worked at (PREVIOUS COMPANY) for around 2.5 years.

My primary involvement there was around CI/CD support activities, Jenkins automation, scripting, deployment coordination, monitoring, and operational support.”




---

32. Are you currently in Bangalore or Mumbai?

> “Currently I’m in Mumbai because I’m deployed at the client location. Originally I’m from Andhra Pradesh side.”




---

33. Do you have any questions for me?

> “Yes, I would like to understand:

whether the role is more aligned toward DevOps or DevSecOps responsibilities,

what kind of projects or environments the team is currently supporting,

and how the DevSecOps maturity and tooling ecosystem looks within the organization.”


OR

“I’d also like to understand the team structure and the type of cloud/container environments primarily used in the project.” 
