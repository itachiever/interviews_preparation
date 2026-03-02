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


---

### **Part 1: AWS Cloud, IAM & Security Fundamentals**

**1. What are the core components of an AWS IAM Policy (Effect, Action, Resource, Condition), and how do they enforce the Principle of Least Privilege?**

**Answer:**
An IAM Policy is a JSON document that defines permissions. It consists of:
*   **Effect:** Whether the statement allows (`Allow`) or denies (`Deny`) access.
*   **Action:** The specific AWS operation (e.g., `s3:GetObject`, `ec2:DescribeInstances`).
*   **Resource:** The specific AWS object the action applies to (e.g., `arn:aws:s3:::my-bucket/*`).
*   **Condition:** Optional constraints (e.g., IP address, time of day, or MFA presence).
**Least Privilege Enforcement:** By defining `Resource` strictly (using ARNs) rather than wildcards (`*`), and listing only specific `Action`s required, the policy ensures the identity has permission to perform only the tasks necessary for its function, nothing more.

**2. How does AWS Identity Center (formerly SSO) differ from traditional IAM User management for workforce access?**

**Answer:**
**IAM Users** are long-term credentials created within AWS. They typically involve username/password combinations or Access Keys that must be manually managed and rotated.
**AWS Identity Center** is a centralized identity management service that allows workforce users to sign in using their existing corporate credentials (via SAML 2.0 or OIDC). It provides temporary, short-lived session credentials via AWS STS, rather than long-term keys. This centralizes access management and removes the need to create individual IAM users for every employee.

**3. What is the architectural design of a secure VPC (Virtual Private Cloud) regarding public and private subnets, and how are NACLs different from Security Groups?**

**Answer:**
A secure VPC separates traffic using **Public Subnets** (with a route to an Internet Gateway) and **Private Subnets** (with no direct route to the internet, typically using a NAT Gateway). Databases and application servers reside in private subnets to prevent direct internet access.
**Differences:**
*   **NACLs (Network Access Control Lists):** Operate at the **Subnet level**. They are **stateless** (rules must be defined for both inbound and outbound traffic) and are evaluated first.
*   **Security Groups:** Operate at the **Instance (ENI) level**. They are **stateful** (return traffic is automatically allowed) and are evaluated after NACLs.

**4. How are Short-lived Credentials generated and managed for CI/CD pipelines using AWS STS (Security Token Service) or OIDC?**

**Answer:**
**OIDC (OpenID Connect):** The CI/CD provider (e.g., GitLab) generates a JSON Web Token (JWT). The pipeline exchanges this JWT with AWS STS using the `AssumeRoleWithWebIdentity` API call.
**STS:** AWS validates the token against the configured OIDC provider and returns temporary credentials (Access Key ID, Secret Access Key, and Session Token). These credentials are valid for a short duration (e.g., 1 hour) and are automatically expired, removing the need to store long-term secrets in the CI/CD configuration.

**5. What is the difference between AWS Secrets Manager and Parameter Store, and when should each be used for storing sensitive data?**

**Answer:**
**AWS Secrets Manager:** Optimized for storing secrets like database credentials and API keys. It includes features for **automatic rotation** of secrets (e.g., rotating a RDS password automatically) at a defined schedule. It is slightly more expensive.
**Parameter Store:** Optimized for configuration data and strings. It has a **Standard** tier (free) and an **Advanced** tier. It can store SecureStrings (encrypted), but it does not natively manage automatic rotation logic without custom Lambda functions.
**Use Case:** Use Secrets Manager for secrets requiring rotation; use Parameter Store for configuration data or secrets where cost is a major constraint and rotation isn't required.

**6. How does AWS KMS (Key Management Service) manage encryption keys, and what is the difference between Customer Managed Keys (CMK) and AWS Managed Keys?**

**Answer:**
**KMS** is a managed service that creates and controls the cryptographic keys used to encrypt data.
*   **Customer Managed Keys (CMK):** Keys created and fully controlled by the user. You define the key policy, enable/disable the key, and manage rotation manually. You pay a monthly fee for these keys.
*   **AWS Managed Keys:** Keys created and managed by AWS services (e.g., `aws/ebs`). You cannot manage the key policy or disable them, but they are free to use. They provide less granular control.

**7. What are the mechanisms to enforce Network Segmentation within AWS (VPC Peering, Transit Gateway, PrivateLink)?**

**Answer:**
*   **VPC Peering:** Connects two VPCs via a direct network route. They must have non-overlapping CIDR blocks. Traffic flows privately between them.
*   **Transit Gateway:** Acts as a cloud router. It connects thousands of VPCs and on-premises networks through a central hub, simplifying network topology.
*   **AWS PrivateLink:** Exposes specific services (like an API or a load balancer) privately via private IPs within your VPC. It allows services to be accessed without traversing the public internet or using NAT gateways.

**8. How does AWS S3 Bucket Policy differ from IAM User Policy in terms of access control?**

**Answer:**
**IAM User Policy:** An **Identity-based policy** attached to a user or role. It defines what *that identity* can do (e.g., "User X can list objects").
**S3 Bucket Policy:** A **Resource-based policy** attached to the S3 bucket itself. It defines *who* can access *this specific bucket* (e.g., "This bucket allows User X to list objects").
The key difference is that the Bucket Policy travels with the resource. Even if the user has no IAM policy, if the Bucket Policy allows the user's account ID, access is granted.

---

### **Part 2: GitLab CI/CD & Security Integration (Mandatory)**

**9. What is the structure of a GitLab CI/CD Pipeline (`.gitlab-ci.yml`), and how do stages, jobs, and scripts relate to each other?**

**Answer:**
The pipeline is defined in a YAML file.
*   **Stages:** Define the execution order (e.g., `build`, `test`, `deploy`). Jobs in the `build` stage must finish before `test` starts.
*   **Jobs:** Define specific tasks to run. Each job runs on a **Runner** (an execution agent). Jobs within the same stage run in parallel.
*   **Scripts:** The shell commands executed by the job (e.g., `npm install`, `make test`).

**10. How is GitLab SAST (Static Application Security Testing) configured and integrated into a pipeline workflow?**

**Answer:**
GitLab provides a predefined template. You include it in your `.gitlab-ci.yml` file:
```yaml
include:
  - template: Security/SAST.gitlab-ci.yml
```
When the pipeline runs, GitLab uses default analyzers (like Semgrep or Bandit) to scan the source code for security flaws (SQL injection, XSS). The results appear as a **Security Report** in the Merge Request.

**11. What is the difference between GitLab Container Scanning and Dependency Scanning (SCA)?**

**Answer:**
*   **Container Scanning:** Scans the **container image** (e.g., Docker image) for operating system package vulnerabilities (like vulnerabilities in the Alpine or Debian OS layers).
*   **Dependency Scanning (SCA):** Scans the **application dependencies** defined in manifest files (like `package-lock.json`, `Gemfile.lock`, `pom.xml`) for known vulnerabilities in the libraries (like a vulnerable version of `lodash`).

**12. How does GitLab Secrets Detection work within a pipeline, and where does it scan for credentials?**

**Answer:**
GitLab Secrets Detection uses tools like Gitleaks. It is included via the `Secrets-Detection` template. It scans the **repository files** in the pipeline, including the commit history, looking for patterns that match secrets (e.g., AWS Access Keys, API tokens, private keys). It attempts to detect secrets even if they were committed to the repo in the past.

**13. How is DAST (Dynamic Application Security Testing) integrated into a GitLab pipeline, and what are the infrastructure requirements?**

**Answer:**
DAST requires a **running application** to scan. It is included via the `DAST` template.
**Infrastructure Requirements:** You must deploy your application to a dynamic environment (like a Review App or Staging) and provide the `DAST_WEBSITE` variable (the URL to scan). The DAST analyzer (usually ZAProxy) sends HTTP requests to that URL to find vulnerabilities like XSS or SQL injection.

**14. What are GitLab CI/CD Variables, and how are they masked to prevent secret leakage in logs?**

**Answer:**
Variables are key-value pairs configured in the GitLab UI or `.gitlab-ci.yml` (for non-secret data). They act as environment variables in the job.
**Masking:** In the GitLab UI, you can check the "Mask variable" box. GitLab then replaces the variable value with `[masked]` in the job logs. Note that masking works best if the value is a single line and matches the output exactly.

**15. How do GitLab Rules (e.g., `only`, `except`, `when`) control pipeline execution flow?**

**Answer:**
*   **`only` and `except`:** Define when a job is added to the pipeline based on branch names, tags, or variables (e.g., `only: [main]`).
*   **`when`:** Controls the execution condition of the job.
    *   `on_success`: (Default) Runs if the previous stage succeeded.
    *   `on_failure`: Runs if the previous stage failed.
    *   `manual`: Requires manual intervention in the UI to start (often used for production deployments).
    *   `always`: Runs regardless of the previous stage's status.

**16. How is OIDC (OpenID Connect) configured between GitLab and AWS to allow secure pipeline authentication without long-lived credentials?**

**Answer:**
1.  **AWS:** Create an **OIDC Identity Provider** in IAM (using the GitLab URL). Create an IAM Role with a Trust Policy allowing the GitLab provider to assume it.
2.  **GitLab:** Configure CI/CD variables: `AWS_ROLE_ARN` (the ARN of the IAM role) and `AWS_WEB_IDENTITY_TOKEN_FILE`.
3.  **Pipeline:** GitLab generates a JWT. The AWS SDK in the job uses this token to call `sts:AssumeRoleWithWebIdentity` and retrieves temporary AWS credentials.

**17. What are GitLab Pipeline Templates, and how do they promote reusability and standardization across projects?**

**Answer:**
Templates are reusable YAML snippets stored in the `.gitlab-ci.yml` file (using `include` or `extends`) or in a separate repository.
**Promoting Reusability:** Instead of writing the build steps for a Java app 50 times, you write it once in a template. All Java projects simply `include` that template. If you need to update the Java version or add a security scan, you update the template file, and all projects inherit the change automatically.

**18. How do Protected Branches and Status Checks enforce security guardrails before merging code?**

**Answer:**
**Protected Branches:** restrict who can push changes or merge Merge Requests to specific branches (like `main` or `production`).
**Status Checks:** When a pipeline runs, it generates status checks. You can configure a Protected Branch to require all checks to "Pass" before the "Merge" button is enabled. This ensures no code can be merged into `main` unless tests and security scans have passed.

**19. What is the function of GitLab Runners (Shared vs. Specific), and how are they secured?**

**Answer:**
**Runners** are the servers that execute the jobs.
*   **Shared Runners:** Provided by GitLab. They execute jobs for any public project (or private projects with minutes). They are shared across users.
*   **Specific (Project) Runners:** Registered to a specific project. Only that project can use them.
**Security:**
*   Runners should run in a **containerized environment** (using Docker executor) to isolate jobs.
*   For self-hosted runners, run them in a private network and use **tags** to ensure sensitive deployment jobs only run on trusted, secure runners, not public shared ones.

  

---

### **Part 3: Infrastructure as Code (CloudFormation & OpenTofu)**

**20. What are the architectural and syntax differences between AWS CloudFormation and OpenTofu (the open-source fork of Terraform)?**

**Answer:**
**Syntax:**
*   **CloudFormation** uses **JSON** or **YAML** templates.
*   **OpenTofu** (and Terraform) uses **HCL** (HashiCorp Configuration Language), which is designed specifically for infrastructure and is often considered more readable and modular.
**Architecture:**
*   **CloudFormation** is **AWS-specific**. It is a managed AWS service where AWS manages the state and provisioning engine.
*   **OpenTofu** is **cloud-agnostic**. It uses providers to interact with AWS, Azure, or GCP. You must manage the backend state yourself (e.g., in S3) and install the OpenTofu binary to run it.

**21. How is State Management handled in OpenTofu, and why is Remote State with Locking essential for teams?**

**Answer:**
**State Management:** OpenTofu records the mapping between your code and the real-world resources in a **State File** (`.tfstate`).
**Remote State & Locking:**
*   In a team, storing this file locally is impossible. **Remote State** stores the file in a shared backend (like AWS S3 or Consul).
*   **Locking:** When a user runs `tofu apply`, a lock is placed on the state file. This prevents other users from running `tofu apply` at the same time, which could corrupt the file or cause race conditions. It ensures the state remains consistent and valid.

**22. What are CloudFormation Stacks, and how does StackSets enable deployment across multiple accounts/regions?**

**Answer:**
**Stacks:** A Stack is a collection of AWS resources that are managed as a single unit. All resources in a stack are created, updated, and deleted together.
**StackSets:** A StackSet extends the concept of a stack to enable deployments across multiple AWS accounts and regions with a single operation. You define the stack template once, and the StackSet pushes it to target accounts/regions automatically. It handles the orchestration of creating stacks in those different targets.

**23. How are Modules used in OpenTofu to organize and reuse infrastructure code?**

**Answer:**
**Modules** are containers for multiple resources that are used together. Instead of writing the same VPC configuration (subnets, route tables, IGW) for every project, you write it once in a module directory.
The module accepts **Input Variables** (like CIDR blocks) and outputs **Output Values** (like VPC ID). In your root configuration, you simply call the module with specific variables. This promotes standardization and reduces code duplication across projects.

**24. What is Drift Detection, and how is it handled in both CloudFormation and OpenTofu?**

**Answer:**
**Drift Detection** is the process of detecting changes made to infrastructure outside of the IaC tool (e.g., a manual change in the Console).
*   **CloudFormation:** You can enable "Drift Detection" on a stack. CloudFormation compares the actual configuration of the resources against the template and reports any drift.
*   **OpenTofu:** You run the command `tofu plan -refresh-only`. This updates the state file with the real-world values without making changes, highlighting in the plan what has drifted. To fix drift, you re-apply the configuration to bring resources back to the desired state.

**25. How can Security Scanning (e.g., Checkov, TFSec) be integrated into the IaC development lifecycle?**

**Answer:**
Scanning is integrated into the **CI/CD Pipeline** and the **Pre-commit Hook**.
*   **Pre-commit:** Developers run a local scan (e.g., `checkov -d .`) before pushing code.
*   **CI/CD:** The pipeline runs the scanner against the CloudFormation template or OpenTofu files. If the scanner finds security issues (e.g., an open security group or unencrypted S3 bucket), the pipeline fails immediately. This enforces security *before* the infrastructure is ever deployed.

**26. What are Change Sets in CloudFormation, and how do they assist in safe infrastructure updates?**

**Answer:**
A **Change Set** is a summary of the changes that CloudFormation will make to a stack if you execute it.
Instead of executing a template directly, you create a Change Set first. CloudFormation compares the new template with the current stack and lists exactly what will be added, modified, or deleted. You can review this list to ensure the changes are expected and safe. Once approved, you execute the Change Set to apply the updates.

---

### **Part 4: Policy-as-Code & Compliance (Nice to Have)**

**27. What is the concept of Policy-as-Code, and how does it differ from traditional compliance auditing?**

**Answer:**
**Policy-as-Code** involves defining security and compliance policies as machine-readable code (like Rego or Sentinel) and automatically enforcing them via automation tools.
**Difference:**
*   **Traditional Auditing:** Usually manual and periodic (e.g., a quarterly review). It finds violations after they have occurred.
*   **Policy-as-Code:** Is continuous and preventative. The automation checks the infrastructure configuration *before* it is provisioned or *during* the deployment, automatically blocking non-compliant resources.

**28. How does OPA (Open Policy Agent) work, and what is the purpose of the Rego language?**

**Answer:**
**OPA** is a general-purpose policy engine. It decouples policy from the service.
**Workflow:**
1.  A system (like Kubernetes or Terraform) sends a JSON input to OPA (e.g., "User X wants to create a Pod").
2.  OPA evaluates the input against policies written in **Rego**.
3.  OPA returns a decision: "Allow" or "Deny".
**Rego:** The declarative query language used to write the policy logic in OPA.

**29. What is the role of Sentinel (specifically in the Terraform/Enterprise context) compared to OPA?**

**Answer:**
**Sentinel** is HashiCorp's Policy-as-Code framework, primarily used within **Terraform Cloud/Enterprise**.
**Comparison:**
*   **OPA:** Open source, language-agnostic, widely used in Kubernetes and cloud-native environments.
*   **Sentinel:** Proprietary to HashiCorp, integrated deeply into Terraform workflows. It uses a similar logic (Sentinel language) but is designed specifically to govern Terraform plans and state.

**30. How do AWS Config Rules evaluate resource configurations for compliance (e.g., SOC 2, NIST controls)?**
**Answer:**

**AWS Config** continuously monitors and records the configuration of AWS resources.
**Config Rules:** You define a rule (or use a managed rule) based on compliance standards like SOC 2 or NIST.
**Process:** When a resource configuration changes, AWS Config triggers the associated rule. The rule evaluates the resource properties against the defined logic (e.g., "Is encryption enabled?"). The resource is tagged as **Compliant** or **Non-Compliant**, and remediation actions can be triggered automatically.

**31. How are CIS Benchmarks automated and enforced using cloud-native tools or open-source scanners?**

**Answer:**
**CIS Benchmarks** are prescriptive security configuration guidelines.
**Automation:**
*   **AWS Security Hub:** Integrates with AWS Config to check resources against CIS AWS Foundations Benchmarks and generates compliance scores.
*   **Open Source Scanners:** Tools like **Scout Suite** or **Inspec** can be run periodically. They query the cloud API, check the configuration against the CIS checklist, and generate a report of failed controls.

---

### **Part 5: Containerization & Orchestration (Docker, Kubernetes, EKS)**

**32. What are the security benefits of using Multi-stage Builds in Docker?**

**Answer:**
**Multi-stage Builds** use multiple `FROM` instructions in a single Dockerfile.
**Security Benefit:**
*   The **Build Stage** can use a heavy image containing compilers (GCC, Maven) and build tools.
*   The **Final Stage** copies only the compiled binary/artifact into a minimal, stripped-down base image (like Alpine or Distroless).
This removes the compilers, debug tools, and unnecessary system libraries from the final image, significantly reducing the attack surface and potential vulnerabilities in the production container.

**33. How does EKS (Elastic Kubernetes Service) differ from self-managed Kubernetes in terms of control plane responsibility?**

**Answer:**
**Self-Managed:** You are responsible for provisioning the Master Nodes (API Server, etcd, Scheduler) and managing upgrades, patching, and high availability.
**EKS:** AWS manages the **Control Plane** across multiple Availability Zones. AWS handles the upgrades, patching, and high availability of the master nodes. The user is only responsible for the **Worker Nodes** and the applications running on them.

**34. What are Kubernetes Network Policies, and how do they enforce micro-segmentation between pods?**

**Answer:**
**Network Policies** are rules that control how pods communicate with each other and other network endpoints.
**Enforcement:** By default, pods can communicate with all other pods. A Network Policy allows you to define **Whitelist** rules. For example, you can specify that "Pod A (Database)" can only accept traffic from "Pod B (Application)" and reject everything else. This creates micro-segmentation, limiting the lateral movement of attackers if a pod is compromised.

**35. How does Kubernetes RBAC (Role-Based Access Control) work, and what is the difference between a Role and a ClusterRole?**

**Answer:**
**RBAC** regulates who can do what on the cluster using Roles and RoleBindings.
*   **Role:** Defines permissions (like list pods) within a **specific Namespace**. It is namespaced.
*   **ClusterRole:** Defines permissions at the **cluster level** (across all namespaces), often used for cluster-wide resources like Nodes or Persistent Volumes.

**36. What is an Admission Controller in Kubernetes (e.g., OPA Gatekeeper), and how does it enforce security policies?**

**Answer:**
**Admission Controllers** are plugins that intercept requests to the Kubernetes API Server before the object is persisted (created/updated).
**OPA Gatekeeper:** It uses OPA policies as Admission Controllers. When a developer tries to create a Pod (e.g., with `privileged: true`), Gatekeeper intercepts the request. It evaluates the Pod definition against the loaded OPA policies. If the Pod violates the policy, Gatekeeper rejects the request immediately.

**37. How are Docker Image Scans integrated into the CI/CD pipeline before deployment to EKS?**

**Answer:**
Integration typically happens after the Docker build step in the pipeline.
1.  **Scan:** A scanner (like Trivy or Aqua) scans the newly built image for OS-level vulnerabilities (CVEs).
2.  **Fail-Gate:** The pipeline script checks the exit code of the scanner. If vulnerabilities above a certain severity (e.g., Critical/High) are found, the script exits with an error.
3.  **Block:** The pipeline stops, preventing the vulnerable image from being pushed to ECR or deployed to the cluster.

**38. What is the purpose of Helm charts in managing Kubernetes deployments, and how are Helm values secured?**

**Answer:**
**Purpose:** Helm is a package manager for Kubernetes. A **Chart** is a collection of pre-configured Kubernetes resource templates (Deployments, Services, ConfigMaps). It simplifies complex deployments.
**Securing Values:**
The `values.yaml` file contains configuration data. To secure sensitive data:
*   **Do not** hardcode secrets in `values.yaml`.
*   Use **Helm Secrets** plugins or **External Secrets Operator**.
*   Reference Kubernetes Secrets directly in the templates (e.g., `valueFrom: secretKeyRef`). This ensures sensitive data is stored in the encrypted Kubernetes Secret store, not in the Helm chart files.

  
