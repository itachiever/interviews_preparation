# Interview Questions: 1st Round

1. Tell me about your experience, specifically focusing on the security aspects of what you have worked on.

2. All the tools you mentioned-are those tools you personally worked on, or are they just part of the project?

3. Why do you think we need an SBOM?

4. Can you explain the SBOM flow ideally?

5. You generated an SBOM yesterday and today. Since builds happen frequently, what do you do with those SBOMs?

6. Where do you store the SBOM files?

7. How do you decide what action to take based on the SBOM?

8. Think from an audit perspective-if an auditor asks for the last six months of generated SBOMs, how would you provide that information?

9. What tool are you primarily using for generating SBOMs?

10. Is Sonatype open source or licensed?

11. Do you know the pricing of Sonatype?

12. If an organization does not want to spend money, what open-source alternatives would you suggest?

13. Can Trivy generate SBOMs?

14. Can you use Trivy as your auditing solution?

15. What do you think is the difference between Trivy and Dependency-Track?

16. Let's say you have a database password and need to provide datasource details to an application running in a container. What are the ways to secure that password?

17. When we say HashiCorp Vault or another secrets manager, somebody still has to upload the password there. Correct?

18. When that secret is injected into a container, someone with access to the container can still retrieve it. Correct?

19. How do you solve that problem?

20. How do you ensure the person uploading the password never knows the actual password?

21. How do you prevent anyone-including administrators-from seeing the actual password?

22. How do you stop a container from running as the root user?

23. Have you done Infrastructure as Code (IaC) scanning?

24. When I say IaC scanning, what exactly do we do there?

25. Can you list down the things that are scanned during IaC scanning?

26. Apart from passwords, what else do you think IaC scanning looks for?

27. You said you worked in a PCI-DSS environment. Tell me the usual activities that happen daily, monthly, and quarterly.

28. On a daily basis, what activities do you perform? Just list them.

29. Other than SBOM, CBOM, SAST, and related scans, what else do you do regularly?

30. How many requirements are there in PCI-DSS?

31. When we say an application is PCI-DSS compliant, what are the requirements that need to be met?

32. What are the PCI-DSS requirements?

33. Have you worked on those PCI-DSS requirements directly?

34. Any questions for me?

---

# Interview Answers



# 1. Tell me about your experience, specifically focusing on the security aspects of what you have worked on.

### 

> I am currently working as a DevSecOps Engineer at CURRENT COMPANY, supporting a fintech client in the digital payments domain. Since the applications process financial transactions, security and compliance are key requirements.
>
> My primary responsibility is integrating security throughout the Software Development Lifecycle using DevSecOps practices. I work closely with development, infrastructure, and security teams to implement and maintain security controls in CI/CD pipelines.
>
> From a code security perspective, I manage SAST using Fortify and dependency security using Sonatype Lifecycle. I also work on SBOM generation and management using Sonatype SBOM Manager. For container security, I integrate Trivy image scanning and enforce container hardening best practices. Secret scanning is performed using GitLeaks and GitGuardian.
>
> We have both VM-based and Kubernetes-based deployments, so I also support Kubernetes security controls and secure deployment practices. Additionally, I coordinate vulnerability remediation with developers, maintain security reports and audit evidence, onboard new applications into the security pipeline, and support compliance requirements through continuous vulnerability management and security monitoring.



# 2. All the tools you mentioned-are those tools you personally worked on, or are they just part of the project?

### 

> I have personally worked on all the tools that I mentioned.
>
> My responsibilities include onboarding applications into these security tools, configuring integrations within Jenkins pipelines, troubleshooting scan failures, generating reports, coordinating vulnerability remediation, and maintaining the operational health of the tools.
>
> For example:
>
> * Fortify for SAST
> * Sonatype Lifecycle for SCA
> * Sonatype SBOM Manager for SBOM management
> * Trivy for container and IaC scanning
> * GitLeaks and GitGuardian for secret scanning
> * Jenkins for CI/CD orchestration
> * Nexus Repository Manager for artifact management
>
> I am involved not only in consuming reports but also in tool administration, integration, and operational support activities.



# 3. Why do you think we need an SBOM?

### 

> SBOM, or Software Bill of Materials, provides a complete inventory of all software components, libraries, frameworks, and dependencies used within an application.
>
> The primary purpose of an SBOM is visibility and traceability.
>
> If a new vulnerability or zero-day vulnerability is announced, we can quickly identify which applications or microservices are affected by checking the SBOM instead of manually analyzing each application.
>
> SBOM also supports:
>
> * Vulnerability management
> * Supply chain security
> * Compliance and audit requirements
> * Risk assessment
> * Software inventory management
>
> In highly regulated environments such as fintech and PCI-DSS environments, maintaining software component visibility is critical for security and audit readiness.

### One-Line Version

> SBOM gives complete visibility of software components, enabling faster vulnerability identification, compliance, and software supply chain security.



# 4. Can you explain the SBOM flow ideally?

### 

> The typical SBOM flow starts during the CI/CD pipeline.
>
> 1. Developer commits code.
> 2. Application build is triggered.
> 3. During the build process, the SBOM generation tool analyzes all dependencies and components.
> 4. An SBOM document is generated in formats such as CycloneDX or SPDX.
> 5. The generated SBOM is stored in a centralized repository or SBOM management platform.
> 6. The SBOM is then used for vulnerability correlation by matching components against vulnerability databases.
> 7. Security teams review findings and coordinate remediation where necessary.
> 8. Historical SBOMs are retained for audit, compliance, and future incident investigations.
>
> This creates a complete software inventory for every application release.



# 5. You generated an SBOM yesterday and today. Since builds happen frequently, what do you do with those SBOMs?

### 

A stronger answer:

> Every generated SBOM should be treated as a versioned artifact associated with a specific application release.
>
> We do not overwrite previous SBOMs because each release may contain different dependencies and security risks.
>
> Each generated SBOM is stored with:
>
> * Application name
> * Version number
> * Build number
> * Timestamp
>
> This allows us to trace the exact software composition of any historical release.
>
> If a vulnerability is discovered later, we can identify which application versions were affected by reviewing the corresponding SBOM.



# 6. Where do you store the SBOM files?

### 

> SBOMs should be stored in a centralized and version-controlled location.
>
> Depending on the organization, this may be:
>
> * Sonatype SBOM Manager
> * Dependency-Track
> * Artifact repositories such as Nexus
> * Dedicated compliance repositories
>
> In my project, SBOMs are maintained through Sonatype SBOM Manager, which provides centralized storage, tracking, and reporting capabilities.
>
> Historical records are retained to support audits, vulnerability investigations, and compliance requirements.



# 7. How do you decide what action to take based on the SBOM?

### 

> The SBOM itself is an inventory document.
>
> The actual action is determined after correlating the SBOM components with vulnerability intelligence databases such as NVD or vendor advisories.
>
> Based on the findings:
>
> * Critical vulnerabilities require immediate remediation.
> * High vulnerabilities are prioritized according to SLA.
> * Medium and low vulnerabilities are scheduled based on business risk.
>
> We also assess:
>
> * Exploitability
> * Business impact
> * Exposure level
> * Availability of fixes
>
> This helps prioritize remediation activities effectively.



# 8. Think from an audit perspective-if an auditor asks for the last six months of generated SBOMs, how would you provide that information?

### 

> Since every SBOM is retained and versioned, we can retrieve historical SBOM records directly from the centralized repository or SBOM management platform.
>
> Each record is associated with:
>
> * Application name
> * Release version
> * Build timestamp
> * Scan results
>
> For an audit request, we can generate reports covering the required period and provide evidence showing:
>
> * Software inventory history
> * Dependency tracking
> * Vulnerability status
> * Remediation records
>
> Maintaining historical SBOMs is important because auditors often require evidence demonstrating software supply chain visibility over time.



# 9. What tool are you primarily using for generating SBOMs?

### 

> In my current project, we primarily use Sonatype SBOM Manager for managing and maintaining SBOMs.
>
> For evaluation and proof-of-concept activities, I have also worked with open-source tools such as:
>
> * Trivy
> * Syft
> * CycloneDX generators
>
> However, our production environment primarily relies on Sonatype due to centralized management, reporting capabilities, vulnerability correlation, and audit support.



# 10. Is Sonatype open source or licensed?

### 

> Sonatype Lifecycle and Sonatype SBOM Manager are enterprise licensed products.
>
> They provide advanced features such as:
>
> * Policy enforcement
> * Vulnerability intelligence
> * License compliance
> * SBOM management
> * Audit reporting
> * CI/CD integrations
>
> Unlike open-source tools that mainly focus on scanning, Sonatype provides a complete governance and software supply chain security platform suitable for enterprise and compliance-driven environments.



# 11. Do you know the pricing of Sonatype?

### 

> I do not handle procurement directly, so I am not involved in contract negotiations or exact licensing discussions.
>
> However, I am aware that Sonatype Lifecycle and Sonatype SBOM Manager are enterprise licensed products, and the pricing generally depends on factors such as:
>
> * Number of applications
> * Number of users
> * Deployment model (SaaS or On-Premises)
> * Additional modules such as SBOM management
>
> In our environment, the solution was procured as an enterprise package because of compliance, governance, auditability, and centralized vulnerability management requirements.

### If pressed further

> I am familiar with the licensing model at a high level, but I would not want to quote exact numbers because pricing varies significantly between organizations and contracts.



# 12. If an organization does not want to spend money, what open-source alternatives would you suggest?

### 

> If cost is a major factor, there are several open-source alternatives available depending on the requirement.
>
> For SCA and SBOM:
>
> * Trivy
> * Syft
> * Grype
> * Dependency-Track
>
> For container scanning:
>
> * Trivy
>
> For secret scanning:
>
> * GitLeaks
>
> For IaC scanning:
>
> * Checkov
> * Trivy
> * tfsec
>
> For SBOM generation:
>
> * Syft
> * Trivy
> * CycloneDX generators
>
> While these tools provide strong technical capabilities, enterprise solutions often offer better governance, reporting, audit readiness, policy enforcement, and centralized management.



# 13. Can Trivy generate SBOMs?

### 

> Yes.
>
> Trivy can generate SBOMs in industry-standard formats such as:
>
> * CycloneDX
> * SPDX
>
> Trivy analyzes:
>
> * Container images
> * File systems
> * Repositories
>
> and produces an inventory of software components and dependencies.
>
> The generated SBOM can then be used for vulnerability correlation, compliance, and software supply chain security.

### One-Line Answer

> Yes, Trivy supports SBOM generation in SPDX and CycloneDX formats.



# 14. Can you use Trivy as your auditing solution?

### 

> Trivy can support audit activities, but I would not consider it a complete auditing solution.
>
> Trivy is primarily a scanning and SBOM generation tool.
>
> It can generate reports and vulnerability findings, but audit programs typically require:
>
> * Historical evidence retention
> * Version tracking
> * Compliance reporting
> * Policy management
> * Approval workflows
> * Long-term record maintenance
>
> For enterprise audits, organizations usually complement Trivy with platforms such as:
>
> * Dependency-Track
> * Sonatype Lifecycle
> * Sonatype SBOM Manager
> * Artifact repositories
>
> which provide centralized evidence management.

### Strong One-Liner

> Trivy is an excellent scanner, but not a complete audit management platform.



# 15. What do you think is the difference between Trivy and Dependency-Track?

### 


> Trivy and Dependency-Track serve different purposes.
>
> Trivy is primarily a scanning engine.
>
> It scans:
>
> * Container images
> * Source code repositories
> * File systems
> * Infrastructure-as-Code
>
> and identifies vulnerabilities.
>
> Dependency-Track is a software composition analysis and SBOM management platform.
>
> It focuses on:
>
> * SBOM ingestion
> * Vulnerability correlation
> * Risk tracking
> * Historical analysis
> * Continuous monitoring
>
> A common architecture is:
>
> * Trivy generates the SBOM.
> * Dependency-Track consumes the SBOM.
> * Dependency-Track continuously monitors vulnerabilities over time.
>
> So Trivy is a scanner, while Dependency-Track is a vulnerability and SBOM management platform.



# 16. Let's say you have a database password and need to provide datasource details to an application. What are the ways to secure that password?

### 

> Database passwords should never be hardcoded in source code, Docker images, Terraform files, or configuration repositories.
>
> Common secure approaches include:
>
> * HashiCorp Vault
> * AWS Secrets Manager
> * Azure Key Vault
> * Kubernetes Secrets integrated with external secret stores
>
> The application retrieves the secret securely during runtime through authentication mechanisms such as IAM roles, service accounts, or Vault policies.
>
> Additionally:
>
> * Secrets should be encrypted at rest.
> * Secrets should be encrypted in transit.
> * Access should follow least privilege.
> * Secrets should be rotated regularly.



# 17. When we say HashiCorp Vault or another secrets manager, somebody still has to upload the password there. Correct?

### 

> Yes, initially a secret must be created or provisioned.
>
> However, modern secret management solutions reduce human involvement by supporting:
>
> * Dynamic secrets
> * Automated credential generation
> * Automated secret rotation
>
> In mature environments, administrators often do not manually create long-term passwords. Instead, the vault system generates short-lived credentials dynamically.

This answer shows maturity.



# 18. When that secret is injected into a container, someone with access to the container can still retrieve it. Correct?

### 

> Potentially yes.
>
> If a user gains privileged access to the container or host, there is a possibility of accessing secrets that are loaded into application memory.
>
> To reduce this risk, organizations implement:
>
> * Least privilege access
> * Non-root containers
> * Runtime security monitoring
> * Secret rotation
> * Short-lived credentials
> * Workload identity mechanisms
>
> The objective is to minimize exposure and limit the impact if a container is compromised.



# 19. How do you solve that problem?

### 

> The preferred approach is to avoid long-lived static credentials.
>
> Instead, we use dynamic secrets.
>
> For example:
>
> * Vault dynamically generates database credentials.
> * The application authenticates to Vault.
> * Vault creates temporary credentials.
> * Credentials automatically expire after a defined lease period.
>
> Even if credentials are exposed, they become useless after expiration.
>
> Combined with least privilege access and secret rotation, this significantly reduces risk.

### One-Line Answer

> Use dynamic, short-lived credentials instead of static passwords.



# 20. How do you ensure the person uploading the password never knows the actual password?


### 

> The best approach is to eliminate manual password creation altogether.
>
> Instead of a human creating and uploading a password, the secret management platform generates credentials automatically.
>
> For example:
>
> * Vault Dynamic Database Secrets
> * AWS IAM Database Authentication
> * AWS Secrets Manager Rotation
>
> In these models:
>
> * The system generates credentials.
> * The application retrieves them securely.
> * Credentials rotate automatically.
> * No individual user ever knows the actual password.
>
> This follows the principle of reducing human access to sensitive credentials and significantly improves security.

### Strong One-Line Answer

> We avoid human-created passwords by using dynamic credential generation and automatic rotation, ensuring no individual ever knows the actual secret.



# 21. How do you prevent anyone-including administrators-from seeing the actual password?

### 

> The best approach is to eliminate static passwords and use dynamic credential generation.
>
> For example, with HashiCorp Vault Dynamic Secrets or AWS IAM Database Authentication:
>
> * Credentials are generated automatically.
> * Applications retrieve them during runtime.
> * Credentials expire automatically after a lease period.
> * No administrator, developer, or operator needs to know the actual password.
>
> Additionally, access to the secret management platform itself is controlled using RBAC, MFA, audit logging, and least-privilege policies.
>
> This follows the principle of minimizing human exposure to sensitive credentials.



# 22. How do you stop a container from running as the root user?

### 


> Running containers as root increases security risk because a container compromise can potentially impact the host system.
>
> To prevent this:
>
> * Create a dedicated non-root user inside the Docker image.
> * Use the USER directive in the Dockerfile.
> * Configure Kubernetes SecurityContext with runAsNonRoot: true.
> * Remove unnecessary Linux capabilities.
> * Use read-only root filesystems where possible.
>
> Example:
>
> ```dockerfile
> RUN adduser -D appuser
> USER appuser
> ```
>
> This ensures the application runs with limited privileges.

### One-Line Answer

> Use a dedicated non-root user in the Dockerfile and enforce runAsNonRoot through Kubernetes SecurityContext.



# 23. Have you done Infrastructure as Code (IaC) scanning?

### 

> Yes.
>
> I have worked on scanning Terraform code before deployment to identify security misconfigurations and policy violations.
>
> We used tools such as Trivy and occasionally evaluated other IaC security scanners to validate Terraform configurations before infrastructure provisioning.



# 24. When I say IaC scanning, what exactly do we do there?

### 

> IaC scanning involves analyzing infrastructure code such as Terraform templates before deployment to identify security risks and configuration issues.
>
> Instead of finding issues after resources are deployed, we detect them during the development phase itself.
>
> This follows the shift-left security approach by preventing insecure infrastructure from being provisioned.



# 25. Can you list down the things that are scanned during IaC scanning?

### 

> Common checks performed during IaC scanning include:
>
> * Publicly accessible S3 buckets
> * Open security groups (0.0.0.0/0)
> * Public databases
> * Unencrypted storage
> * Missing logging configurations
> * Excessive IAM permissions
> * Hardcoded credentials
> * Missing backup configurations
> * Insecure network configurations
> * Non-compliant cloud resource settings
>
> These checks help ensure secure cloud deployments before infrastructure is provisioned.



# 26. Apart from passwords, what else do you think IaC scanning looks for?

### 

> Apart from detecting hardcoded secrets, IaC scanning validates security best practices across infrastructure resources.
>
> Examples include:
>
> * Security group misconfigurations
> * Publicly exposed resources
> * Missing encryption
> * Excessive IAM permissions
> * Missing monitoring and logging
> * Public storage buckets
> * Network segmentation issues
> * Compliance policy violations
>
> The objective is to detect security weaknesses before deployment.



# 27. You said you worked in a PCI-DSS environment. Tell me the usual activities that happen daily, monthly, and quarterly.

### 

> Daily Activities:
>
> * SAST scanning
> * SCA scanning
> * Secret scanning
> * Container image scanning
> * Vulnerability triage
> * Developer remediation support
> * Security report reviews
> * Security dashboard monitoring
>
> Monthly Activities:
>
> * Vulnerability review meetings
> * Patch verification
> * Compliance evidence collection
> * Security metrics reporting
> * Access review activities
>
> Quarterly Activities:
>
> * Audit preparation
> * Compliance assessments
> * Security control validation
> * Risk reviews
> * Vulnerability trend analysis
> * Security policy reviews
>
> My primary involvement was in the application security and DevSecOps activities supporting PCI-DSS compliance.



# 28. On a daily basis, what activities do you perform? Just list them.

### 

> Daily activities include:
>
> * SAST scans
> * SCA scans
> * SBOM generation and review
> * Secret scanning
> * Container image scanning
> * Vulnerability validation
> * Developer coordination
> * CI/CD onboarding activities
> * Security report generation
> * Tool administration and troubleshooting
> * Security dashboard monitoring
> * Compliance evidence maintenance



# 29. Other than SBOM, CBOM, SAST, and related scans, what else do you do regularly?

### 

> Apart from security scanning activities, I also:
>
> * Support vulnerability remediation
> * Conduct scan result reviews
> * Maintain compliance evidence
> * Onboard applications into security pipelines
> * Troubleshoot tool issues
> * Fine-tune security policies
> * Support audit requests
> * Coordinate with developers and infrastructure teams
> * Maintain security dashboards and reports
>
> A significant portion of my work involves ensuring security findings are actually remediated rather than just reported.



# 30. How many requirements are there in PCI-DSS?

### 


> PCI-DSS version 4.0 contains 12 primary security requirements organized under six major control objectives.
>
> These requirements cover areas such as:
>
> * Network security
> * Secure system configuration
> * Protection of cardholder data
> * Access control
> * Security monitoring
> * Security testing
>
> As a DevSecOps engineer, my work primarily supports several of these requirements through secure development practices, vulnerability management, access controls, logging, and security testing.

### One-Line Answer

> PCI-DSS 4.0 contains 12 major security requirements.



# 31. When we say an application is PCI-DSS compliant, what are the requirements that need to be met?

### 

> PCI-DSS compliance means the application, infrastructure, processes, and security controls satisfy the PCI-DSS security requirements for protecting cardholder data.
>
> This includes:
>
> * Secure network architecture
> * Secure software development
> * Encryption of sensitive data
> * Access control
> * Logging and monitoring
> * Vulnerability management
> * Security testing
> * Incident response
>
> Compliance is achieved through both technical controls and operational processes.



# 32. What are the PCI-DSS requirements?

### 

1. Install and maintain network security controls.
2. Apply secure configurations to systems.
3. Protect stored account data.
4. Protect data during transmission.
5. Protect systems from malware.
6. Develop and maintain secure systems and software.
7. Restrict access by business need-to-know.
8. Identify and authenticate users.
9. Restrict physical access.
10. Log and monitor access.
11. Test security controls regularly.
12. Maintain information security policies.

### One-Line Answer

> PCI-DSS consists of 12 requirements focused on securing cardholder data through access control, encryption, monitoring, testing, and secure development practices.



# 33. Have you worked on those PCI-DSS requirements directly?

### 

> I have not worked as a PCI-DSS auditor or compliance owner.
>
> However, I have worked on several technical controls that support PCI-DSS compliance.
>
> Examples include:
>
> * SAST implementation
> * SCA implementation
> * SBOM generation
> * Secret scanning
> * Container security scanning
> * Vulnerability management
> * Security reporting
> * Compliance evidence collection
>
> While I may not own the entire PCI-DSS program, my DevSecOps responsibilities directly contribute to multiple PCI-DSS requirements, particularly secure software development, vulnerability management, and security testing.

This is much better than claiming broad PCI-DSS expertise.



# 34. Any questions for me?

### Good Questions

#### Option 1

> How is DevSecOps currently structured within your organization, and what would be the primary expectations from this role during the first six months?


#### Option 2

> What are the biggest security challenges the team is currently trying to solve?


#### Option 3

> Which areas would you recommend I strengthen further to be successful in the next stages of the process and in this role?



# Most Important Learning from This Interview

The interviewer repeatedly tested whether you understood:

1. **Why** security controls exist.
2. **How** security controls support compliance.
3. **Architecture thinking** rather than tool names.
4. **Secrets management maturity**.
5. **PCI-DSS fundamentals**.

