Key Responsibilities:
Security here is treated as a continuous, shared responsibility — not a late-stage gate. Your job is to make "shift-left" real and measurable.
What You'll Do
Pipeline & SDLC integration
	• Embed automated security controls across the SDLC, from local developer environments through production runtime.
	• Configure pre-commit hooks and IDE plugins (e.g., Snyk security rules) for real-time developer feedback, plus regex/entropy-based secret detection.
	• Integrate SAST and SCA into pull-request workflows; stand up server-side secret scanning across new and historical commits.
	• Build automated security gates into CI/CD (Jenkins, GitHub Actions, GitLab CI) — SAST, SCA, secret scanning, and policy checks running on every build.
	• Harden Dockerfiles and base images, implement image signing and SBOM generation, and set up versioned, traceable artifact repositories.
	• Implement IaC security scanning for Terraform, Docker, and Kubernetes manifests, plus admission-controller and runtime detection policies for K8s workloads.
	• Stand up vault-based secrets management (e.g., HashiCorp Vault, AWS Secrets Manager) with RBAC, rotation, audit trails, and secure runtime injection.
API & application security assessment
	• Run continuous API security assessments across REST, GraphQL, SOAP, JSON/XML, mobile backend, and authorized third-party APIs 
	• Test authentication/session management, authorization and access control, BOLA/IDOR, injection (SQLi, NoSQLi, command injection, XXE), mass assignment, JWT/token security, rate limiting, and security misconfigurations.
	• Perform manual web application and API penetration testing focused on business logic, authentication, and authorization flaws that automated tooling misses.
	• Conduct DAST in staging, endpoint enumeration/fuzzing, and continuous re-testing of remediated findings.
	• Classify findings by severity (Critical/High/Medium/Low) based on exploitability and business impact, with clear reproduction steps, evidence, and remediation guidance.
Visibility, compliance & monitoring
	• Build and maintain a centralized security dashboard normalizing findings from SAST, DAST, SCA, IaC, and runtime tools.
	• Integrate remediation workflows with issue trackers (JIRA, GitHub Issues), including SLA tracking and assignment.
	• Codify compliance-as-code against OWASP Top 10, PCI DSS, and client internal policies into automated, testable controls.
	• Configure CSPM coverage, WAF rule baselines, and real-time alerting for high-severity findings and anomalous build activity.
Enablement & client delivery
	• Develop threat models for in-scope features and architectural changes.
	• Run DevSecOps maturity baselines and periodic maturity reviews.
	• Deliver developer training workshops, stand up and facilitate a Security Champions network, and run application-layer incident tabletop exercises.
	• Produce clear documentation, runbooks, and implementation guides, and lead handover sessions so client teams can independently operate and extend the capability.
What You'll Bring
Required
	• 4+ years in DevSecOps, application security, or offensive security, with hands-on delivery (not just advisory).
	• Practical experience with SAST, SCA, DAST, and secret-scanning tooling (e.g., Snyk, )
	• Demonstrated CI/CD pipeline security work in at least one of Jenkins, GitHub Actions, or GitLab CI.
	• Strong API and web application penetration testing skills, including the OWASP Top 10 and OWASP API Security Top 10 (BOLA/IDOR, injection, auth/authz flaws, business logic abuse).
	• Working knowledge of container and Kubernetes security (image scanning/signing, admission controllers, SBOMs) and IaC scanning (Terraform).
	• Experience with vault-based secrets management and secure credential handling.
	• Scripting/automation proficiency (Python, Bash) for tooling integration.
	• Clear written and verbal communication — able to write findings reports for both engineers and executives.
Preferred
	• Relevant certifications: OSCP, OSWE, GWAPT, GWEB, CKS, or equivalent.
	• Cloud security depth (AWS/Azure/GCP), CSPM, and WAF tuning.
	• Exposure to compliance frameworks and compliance-as-code approaches.
Prior consulting or client-facing delivery experience.
