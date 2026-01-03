# Preparation Questions:

# Core DevSecOps Concepts
* What does DevSecOps mean to you, and how is it different from traditional DevOps?
* Can you walk me through a real-world example where you integrated security into the CI/CD pipeline?
* What are the key pillars of a mature DevSecOps practice?
* How do you measure the success or effectiveness of DevSecOps implementation?

# CI/CD and Automation
* How have you automated security controls within CI/CD pipelines?
* Which CI/CD tools have you used (Jenkins, Azure DevOps, Tekton, etc.) and how did you integrate SAST/DAST scans into them?
* How do you ensure that a failed security scan (like high vulnerabilities) breaks the build pipeline?
* Explain how you would integrate container image scanning in a pipeline using tools like Trivy, Anchore, or Aqua.
* How do you handle secret management in CI/CD pipelines?

# SAST (Static Application Security Testing)
* What is the main purpose of SAST, and where is it typically integrated in the SDLC?
* What tools have you used for static analysis (e.g., SonarQube, Checkmarx, Fortify, Veracode)?
* How do you deal with false positives from SAST reports?
* What kinds of vulnerabilities can SAST detect that DAST cannot?

# DAST (Dynamic Application Security Testing)
* Explain the difference between SAST and DAST with examples.
* How would you integrate a DAST tool (e.g., OWASP ZAP, Burp Suite, AppScan) into a Jenkins pipeline?
* How do you ensure authenticated scanning in DAST for web applications?
* What key metrics do you track from DAST results?

# Container & Cloud Security
* How do you secure container images during the build process?
* Explain your approach to managing vulnerabilities in base images.
* What is an SBOM, and how does it help in container security?
* Which commercial container security tools have you worked with (e.g., Prisma Cloud, Aqua, StackRox/ACS)?
* How do you enforce image signing and verification in the deployment pipeline?

# Vulnerability Management
* How do you prioritize vulnerabilities discovered during scanning?
* What is your process for remediating vulnerabilities that impact production containers?
* How do you integrate vulnerability management automation (e.g., ticketing, reporting)?
* Can you describe how you track and close vulnerabilities identified in CI or runtime?

# Secure Coding and Application Security
* What are OWASP Top 10 vulnerabilities, and how can they be mitigated?
* How would you perform or assist in secure code review?
* Give an example of a fix for a common vulnerability like SQL injection or XSS.
* How do tools like Veracode or Checkmarx help enforce secure coding practices?

# Infrastructure as Code (IaC) Security
* How do you apply DevSecOps principles to IaC tools like Terraform or Ansible?
* Which scanners or checks do you use for IaC security (e.g., tfsec, Checkov)?
* How would you automate compliance checks for cloud configurations?

# Real-World Scenario Questions
* Suppose a container image fails vulnerability scanning in the CI pipeline. How would you troubleshoot and resolve the issue?
* You find a critical vulnerability in a third-party library used across multiple microservices — what steps would you take?
* A DAST scan flags multiple false positives, but release deadlines are tight. How do you proceed?
* You’re asked to improve the organization’s DevSecOps maturity — what short-term and long-term steps would you propose?

# Behavioral & Ownership Questions
* Describe a time when you identified and fixed a major security gap in a CI/CD process.
* How do you balance security and delivery speed in a fast-moving DevOps environment?
* How do you keep yourself updated with the latest security trends and vulnerabilities?



# Preparation Questions & Answers:

# Core DevSecOps concepts

# 1. What does DevSecOps mean to you, and how is it different from traditional DevOps?
DevSecOps is the practice of embedding security into every phase of the SDLC and CI/CD pipeline instead of treating it as a separate, late-stage gate. In DevOps the focus is mainly on speed, collaboration, and automation between dev and ops, while DevSecOps extends this by making security a shared responsibility with automated checks, policies, and vulnerability management from code to production.

# 2. Real-world example where you integrated security into a CI/CD pipeline
In a typical pipeline, security is added as stages: secret scanning and linting on commit, SAST during build, dependency/SCA and container image scanning before packaging, and DAST plus compliance checks in pre‑prod or post‑deployment. Each security stage has thresholds so that high or critical issues fail the pipeline and automatically create tickets or notifications for the responsible team.

# 3. Key pillars of a mature DevSecOps practice
Key pillars include: security by design (threat modeling, secure requirements), automated testing (SAST, DAST, SCA, container and IaC scanning), strong secrets and access management, and continuous monitoring of vulnerabilities and misconfigurations. There is also a cultural pillar: shared ownership between dev, ops, and security, backed by training and clear remediation workflows.

# 4. How do you measure DevSecOps success?
Success can be measured using metrics like mean time to remediate vulnerabilities, number of security defects found in production vs earlier stages, and percentage of builds failing on security gates. Additional indicators are policy compliance rates (e.g., IaC checks passing), frequency of secure releases, and reduced manual security exceptions.

# CI/CD and automation

# 5. How have you automated security controls in CI/CD pipelines?
Security controls are automated by turning them into pipeline stages, for example: running SAST, SCA, and container scanning as part of CI and triggering DAST scans on deployed test environments. The tools are integrated via plugins or API calls, and their results are parsed into quality gates so that builds fail if severity thresholds are exceeded.

# 6. Which CI/CD tools have you used and how did you integrate SAST/DAST?
Tools like Jenkins, GitLab CI, Azure DevOps, or Bitbucket can run SAST/DAST either through native extensions or simple shell steps that call the scanners’ CLI or REST APIs. Typically, SAST runs right after compilation, while DAST runs after the application is deployed to a test URL, with scan results published as build artifacts or imported into the platform’s security dashboards.

# 7. How do you ensure a failed security scan breaks the build?
Most scanners output standardized formats (JSON, XML, SARIF), so the pipeline parses the results and evaluates conditions like “any critical or high issues”. If the condition is true, the job uses a non‑zero exit code or built‑in quality gate features (e.g., SonarQube quality gate) to mark the pipeline as failed.

# 8. How do you integrate container image scanning in a pipeline?
After building the image with Docker or a similar tool, a container scanner such as Trivy or commercial platforms is invoked against the image tag before pushing to the registry. The pipeline is configured to fail when vulnerabilities above a certain severity are detected, and reports are stored or exported to vulnerability management systems.

# 9. How do you handle secret management in CI/CD pipelines?
Secrets should never be hard‑coded in code or pipeline definitions and are instead stored in dedicated secret managers like Vault, AWS Secrets Manager, or the CI tool’s secure store. During runtime, jobs fetch secrets through secure integrations and inject them as environment variables or temporary files with restricted scope and rotation policies.


# SAST (Static Application Security Testing)

# 10. What is SAST and where is it integrated in SDLC?
SAST statically analyzes source code or binaries to detect security weaknesses such as injection, insecure APIs, and hard‑coded secrets without executing the application. It is typically integrated early in the SDLC, for example as a pre‑commit hook, part of CI builds, or as mandatory checks before merge.

# 11. What tools have you used for SAST?
Common SAST tools include SonarQube, Fortify, Checkmarx, Veracode, and various language‑specific analyzers; many provide plugins for CI tools and IDEs. These tools generate issue lists with severity, location, and remediation guidance that can be exported into issue trackers.

# 12. How do you deal with false positives from SAST reports?
False positives are managed by triaging findings, validating whether the vulnerable path is actually exploitable, and then using the tool’s suppression or marking features to flag them appropriately. Teams also tune rulesets, customize configurations per repository, and periodically review suppressions to avoid hiding real issues.

# 13. What can SAST detect that DAST cannot?
SAST can find issues in code paths that are hard to reach at runtime, such as insecure internal functions, improper cryptography use, or logic flaws that do not surface in typical HTTP flows. It also helps discover issues before the app is runnable, while DAST only operates on a deployed, running application.


# DAST (Dynamic Application Security Testing)

# 14. Explain SAST vs DAST with examples.
SAST is white‑box analysis of source or compiled code, catching issues like unsafe input handling or insecure function calls before runtime. DAST is black‑box testing of a running application, sending crafted requests to detect vulnerabilities like SQL injection, XSS, and misconfigurations exposed over HTTP.

# 15. How would you integrate a DAST tool into a Jenkins pipeline?
In Jenkins, a DAST stage is added after deployment to a test environment; the stage runs ZAP, Burp, or another scanner via CLI or Docker, targeting the app URL. The job then collects the report, evaluates severity thresholds, and fails the build or publishes the report as an artifact or HTML report.

# 16. How do you ensure authenticated DAST scanning?
Authenticated scans require configuring login flows, session management, or tokens within the DAST tool, often using scripts, authentication profiles, or API tokens. Credentials are managed securely via secret stores, and the scanner is configured to maintain sessions so it can crawl authorized areas of the application.

# 17. What key metrics do you track from DAST results?
Important metrics include number of vulnerabilities by severity, trend of unresolved findings over time, and average remediation time for DAST‑identified issues. Coverage metrics such as percentage of critical paths scanned or number of authenticated endpoints reached are also useful.


# Container and cloud security

# 18. How do you secure container images during the build process?
Security starts with minimal, trusted base images, avoiding unnecessary packages, and applying regular updates and patches. The Dockerfile should follow best practices such as non‑root users, read‑only filesystems where possible, and multi‑stage builds to remove build‑time tools from the final image.

# 19. How do you manage vulnerabilities in base images?
Base images are scanned regularly with container scanners and updated to newer patched versions as part of a scheduled maintenance process. Applications are rebuilt against these updated bases, and the registry or platform may enforce policies that block outdated or vulnerable images.

# 20. What is an SBOM and how does it help container security?
A Software Bill of Materials (SBOM) is a machine‑readable inventory of all components, libraries, and dependencies bundled into an application or image. For containers, SBOMs make it easier to identify which images are affected when a new CVE is announced and to prove compliance or supply‑chain transparency.

# 21. Which commercial container security tools have you worked with?
Commercial tools such as Prisma Cloud, Aqua Security, and Red Hat Advanced Cluster Security provide image scanning, runtime protection, and policy enforcement across registries and clusters. They integrate with CI/CD, Kubernetes/OpenShift, and cloud platforms to implement admission control, compliance checks, and vulnerability dashboards.

# 22. How do you enforce image signing and verification?
Image signing can be done with tools like Notary, Cosign, or built‑in registry features, generating cryptographic signatures for trusted images. Kubernetes admission controllers or registry policies then verify signatures before allowing images to run in clusters.


# Vulnerability management

# 23. How do you prioritize vulnerabilities from scanning?
Prioritization uses severity (CVSS), exploitability, exposure, and business context, focusing first on internet‑exposed workloads, critical data paths, and runtime‑reachable components. Policies may define SLA targets, such as fixing critical issues within days and medium issues within sprints.

# 24. How do you remediate vulnerabilities affecting production containers?
The usual approach is to patch or upgrade affected dependencies or base images, rebuild and scan the images, and then roll out the updated containers through the deployment pipeline. Emergency patches might require out‑of‑band releases, but always with testing and rollback strategies.

# 25. How do you integrate vulnerability management automation?
Automation includes pushing scanner findings into ticketing systems like Jira, tagging them by service and owner team, and updating status based on rescans. Dashboards and alerts highlight SLA breaches or rising risk so teams can adjust priorities.

# 26. How do you track and close vulnerabilities identified in CI or runtime?
Tracking typically combines scanner reports, central vulnerability databases, and issue trackers, linking each finding to a remediation task and owner. Closure is validated by reruns of the relevant scans and by ensuring no remaining occurrences in the latest builds or runtime inventory.


# Secure coding and application security

# 27. What are the OWASP Top 10, and how can they be mitigated?
The OWASP Top 10 is a prioritized list of common web application risks such as injection, broken access control, cryptographic failures, and insecure design. Mitigation combines secure coding practices, frameworks enforcing safe defaults, input validation, proper authentication/authorization, and security testing like SAST/DAST.

# 28. How would you perform or assist in secure code review?
Secure code review focuses on security‑critical areas like authentication, authorization, input validation, crypto, and error handling rather than line‑by‑line reading. It combines manual review with automated SAST and checklists, and findings are discussed with developers to align on fixes and patterns.

# 29. Example fix for SQL injection or XSS
For SQL injection, parameterized queries or ORM methods are used instead of concatenating user input directly into SQL statements. For XSS, output encoding, input validation, and using built‑in templating helpers or CSP headers help prevent untrusted data from being interpreted as script.

# 30. How do tools like Veracode or Checkmarx help enforce secure coding?
These platforms integrate into CI/CD and IDEs, providing real‑time feedback on insecure patterns and centralized policies for what must be fixed before release. They also offer training materials and remediation guidance linked to each finding, helping teams continuously improve code quality.


# IaC security

# 31. How do you apply DevSecOps principles to IaC tools like Terraform?
IaC code is treated like application code: stored in version control, peer‑reviewed, and scanned with security tools to catch misconfigurations before deployment. Pipelines run IaC scanners as gates to prevent insecure cloud resources such as open security groups or public storage buckets.

# 32. Which scanners/checks do you use for IaC security?
Popular tools include Checkov, tfsec, and Terrascan, which have rulesets for major cloud providers and common misconfigurations. They integrate with CI tools to provide pass/fail signals and detailed findings mapped to compliance standards.

# 33. How would you automate compliance checks for cloud configurations?
Compliance checks can be automated by running IaC and cloud‑config scanners on every change and periodically against live environments. Findings are then aggregated into compliance dashboards and linked to frameworks like CIS or ISO to track adherence over time.


# Real-world scenarios

# 34. Container image fails vulnerability scanning in CI - what do you do?
First, inspect the report to understand the vulnerabilities, their severities, and which layers or packages they come from. Then decide whether to upgrade or replace packages, switch to a more up‑to‑date base image, or apply configuration mitigations, followed by a rebuild and rescan.

# 35. Critical vulnerability in a shared third‑party library - what steps do you take?
Identify all services and images that use the library (via dependency graphs or SBOMs) and assess exposure and impact. Coordinate a prioritized patch rollout by updating the dependency version, testing, and redeploying, while possibly adding WAF rules or configuration mitigations as temporary defenses.

# 36. DAST scan flags multiple false positives under tight deadlines - what do you do?
Triage the findings quickly to separate clear false positives from potential high‑risk issues that truly need attention. For genuine false positives, document evidence and suppress them in the tool, while focusing remediation efforts on confirmed critical and high vulnerabilities before release.

# 37. Asked to improve DevSecOps maturity - what short‑ and long‑term steps do you propose?
Short term, introduce basic gates like SAST, dependency and container scanning, and secret scanning in CI, plus minimal DAST in pre‑prod. Long term, build out threat modeling, IaC security, policy‑as‑code, runtime monitoring, and continuous training and metrics for teams.


# Behavioral and ownership

# 38. Describe a time you fixed a major security gap in CI/CD.
A strong example is discovering credentials in code or logs and then implementing automated secret scanning and centralized secret management to prevent recurrence. Follow‑up includes rotating exposed secrets, updating documentation, and making secret handling part of the standard pipeline template.

# 39. How do you balance security and delivery speed?
The balance is achieved by shifting security left with automation so most checks run fast and early, leaving fewer surprises before release. Risk‑based policies and severity thresholds ensure that only genuinely dangerous issues block releases, while lower‑risk items are scheduled into future sprints.

# 40. How do you keep yourself updated with security trends and vulnerabilities?
Continuous learning involves following CVE feeds, vendor advisories, security blogs, and attending webinars or community meetups. Many teams also participate in internal knowledge‑sharing sessions and track updates from their main tooling and cloud providers.
