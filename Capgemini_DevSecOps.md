# Complete List of 65 DevSecOps Practice Interview Questions

# 1. CI/CD Pipeline Security (Q1-5)
	1. Walk me through how you would secure a CI/CD pipeline from source code to deployment.
	2. How do you implement secrets management in CI/CD pipelines? What tools have you used?
	3. Explain shift-left security. How have you implemented it in your projects?
	4. What security gates would you implement in a CI/CD pipeline and at what stages?
	5. How do you handle pipeline failures due to security issues? What's your threshold for blocking deployments?
# 2. SAST (Static Application Security Testing) (Q6-10)
	1. Explain the difference between SAST and DAST. When would you use each?
	2. You've integrated SonarQube into your pipeline. How do you handle false positives?
	3. What are the limitations of SAST tools? How do you complement them?
	4. How would you configure Checkmarx or Fortify to scan only critical code paths to reduce scan time?
	5. Explain CWE and OWASP Top 10. How do SAST tools map findings to these?
# 3. DAST (Dynamic Application Security Testing) (Q11-15)
	1. How does OWASP ZAP differ from Burp Suite? Which would you choose for CI/CD integration?
	2. Walk me through setting up automated DAST scanning in a CI/CD pipeline.
	3. How do you handle authentication when performing DAST scans?
	4. What's the difference between active and passive scanning in DAST tools?
	5. How would you scan a single-page application (SPA) or API effectively with DAST?
# 4. Container Security (Q16-22)
	1. Explain the container security lifecycle from image build to runtime.
	2. How do you secure Docker images? What checks do you perform before pushing to a registry?
	3. What is the difference between image scanning and runtime container security?
	4. You discover a critical vulnerability in a base image used across 50 containers. Walk through your remediation process.
	5. Explain how Red Hat Advanced Cluster Security (or Aqua/Twistlock) works.
	6. How do you implement security policies for Kubernetes/OpenShift clusters?
	7. What are the security differences between Docker and Kubernetes/OpenShift?
# 5. Vulnerability Management (Q23-27)
	1. How do you prioritize vulnerabilities for remediation when you have hundreds of findings?
	2. Explain the difference between CVE, CVSS, and CWE.
	3. What's your approach to managing vulnerability SLAs (e.g., Critical: 7 days, High: 30 days)?
	4. How do you handle zero-day vulnerabilities in production?
	5. Describe your experience with vulnerability scanning tools. How do they integrate with your workflow?
# 6. Software Composition Analysis (SCA) (Q28-31)
	1. What is SCA and why is it important? How does Black Duck or Snyk work?
	2. How do you manage vulnerable dependencies in a project?
	3. Explain the difference between direct and transitive dependencies. How do you secure both?
	4. A critical vulnerability is found in a library 4 levels deep in your dependency tree. How do you fix it?
# 7. Secure Code Review (Q32-35)
	1. What do you look for when performing a security-focused code review?
	2. How do you identify SQL injection vulnerabilities in code? What about in compiled code?
	3. Explain OWASP Top 10. Pick 3 and describe how you'd detect and prevent them.
	4. What are the common security issues in API implementations?
# 8. Cloud & Infrastructure Security (Q36-39)
	1. How do you secure Infrastructure as Code (Terraform)? What tools would you use?
	2. What security considerations are unique to cloud environments (AWS/Azure/GCP)?
	3. How would you implement security scanning for Terraform/CloudFormation templates in CI/CD?
	4. Explain the shared responsibility model in cloud security.
# 9. Automation & Integration (Q40-44)
	1. You need to integrate 5 different security tools into a Jenkins pipeline. How do you approach this?
	2. How do you aggregate and normalize findings from multiple security tools?
	3. Write a simple script/pseudo-code to break a build if SAST finds high-severity issues.
	4. How do you handle API rate limits when integrating security tools?
	5. Describe how you've used APIs to automate security workflows.
# 10. Jenkins & Pipeline-Specific (Q45-47)
	1. How do you secure Jenkins itself as part of DevSecOps?
	2. Explain Jenkinsfile security best practices.
	3. How do you implement security scanning stages in a declarative Jenkins pipeline?
# 11. Kubernetes/OpenShift Security (Q48-52)
	1. What are Pod Security Policies (deprecated) and Pod Security Standards?
	2. How do you implement network segmentation in Kubernetes?
	3. Explain RBAC in Kubernetes. How would you implement least-privilege access?
	4. What is an admission controller? How does it enhance security?
	5. How do you secure secrets in OpenShift/Kubernetes?
# 12. Compliance & Standards (Q53-55)
	1. How do you ensure compliance in automated deployments?
	2. What compliance frameworks have you worked with (SOC2, PCI-DSS, HIPAA)?
	3. How do you implement policy-as-code? What tools have you used?
# 13. Incident Response & Monitoring (Q56-58)
	1. A container in production is exhibiting suspicious behavior. Walk through your investigation.
	2. What security monitoring would you implement for containers in production?
	3. How do you differentiate between a false positive and a real security incident?
# 14. Scenario-Based Questions (Q59-62)
	1. Your SAST tool reports 500 vulnerabilities before a critical release tomorrow. What do you do?
	2. Developers complain security scans slow down their pipeline by 30 minutes. How do you respond?
	3. A third-party library you depend on has a critical RCE vulnerability with no patch available. What's your approach?
	4. You're starting at a new company with no DevSecOps practices. What's your 90-day plan?
# 15. Behavioral & Soft Skills (Q63-65)
	1. Describe a time when you had to convince developers to fix a security issue they deemed low priority.
	2. How do you stay updated with the latest security threats and tools?
	3. Tell me about a security incident you helped resolve. What was your role?

# Total: 65 questions covering all JD requirements
✅ CI/CD Security (5)
✅ SAST/DAST (10)
✅ Container Security (7)
✅ Vulnerability Management (5)
✅ SCA (4)
✅ Secure Code Review (4)
✅ Cloud/IaC (4)
✅ Automation (5)
✅ Jenkins (3)
✅ Kubernetes/OpenShift (5)
✅ Compliance (3)
✅ Incident Response (3)
✅ Scenarios (4)
✅ Behavioral (3)


# ------------------------------------------


# Preparation Questions & Answers:

# 1. CI/CD Pipeline Security

* Q1: Walk me through how you would secure a CI/CD pipeline from source code to deployment.
Answer (story + structure):
“The pipeline security in stages: source control → build → artifacts → deploy → runtime, with strong identity and secrets management across everything.”
	1. Source control (Git, Bitbucket, Azure Repos)
	• Enforce branch protection (no direct push to main, mandatory PRs and reviews).
	• Enable required status checks: SAST, lint, tests must pass before merge.
	• Enable commit signing and prevent force‑push on protected branches.
	• Use pre‑commit hooks or server‑side checks to block secrets and obvious vulnerabilities.
	2. Build stage (Jenkins, Azure DevOps, Tekton)
	• Use a hardened, minimal build agent image (no unnecessary tools, patched OS).
	• Don’t store secrets in pipeline YAML. Only use secure credential stores.
	• Run:
		○ SAST
		○ Dependency/SCA scanning (open‑source vulnerabilities)
		○ Basic unit/integration tests
	• Fail the build on critical/high severity security issues.
	3. Artifact management (Nexus/Artifactory/Registry)
	• Push only artifacts from successful, verified builds.
	• Use a private artifact repository / container registry with RBAC.
	• Enable artifact signing (e.g., Cosign/Notary) and/or checksum verification.
	• Enable vulnerability scanning on artifacts/images in the registry.
	4. Deployment stage (Kubernetes/OpenShift/VMs)
	• Use environment‑specific service accounts with least privilege.
	• Use deployment manifests stored as code (GitOps/IaC) and validate them:
		○ Policy‑as‑code (e.g., OPA, Conftest) to block bad configurations (privileged pods, no resource limits, etc.).
	• Use admission controllers to reject unsigned/vulnerable images.
	5. Secrets & identity across the pipeline
	• Centralized secret manager (Vault/AWS SM/Azure KV), never in code.
	• Rotate secrets regularly, use short‑lived tokens wherever possible.
	• Use fine‑grained identities (e.g., separate service accounts per pipeline or environment).
	6. Post‑deployment / runtime
	• DAST or API security scans on test/QA or staging.
	• Runtime monitoring (logs, IDS/IPS, container runtime policies, alerts).
	• Regular vulnerability scans on running workloads and underlying hosts/nodes.
You can summarize in an interview as:
“Secure code repo, hardened build agents, gated artifacts, policy‑driven deployments, and strong secrets/identity — all glued with automated SAST/DAST/SCA and vulnerability scanning.”

# Q2: How do you implement secrets management in CI/CD pipelines? What tools have you used?
Answer:
“Core rule: no secrets in code, no secrets in pipeline files. I always centralize secrets and fetch them at runtime.”
Typical approach:
	• Use tools like:
		○ HashiCorp Vault
		○ AWS Secrets Manager
		○ Azure Key Vault
		○ Or the CI platform’s encrypted credential store (Jenkins Credentials, GitHub Actions Secrets, Azure DevOps Library).
Example – Jenkins + Vault pattern (pseudo‑script):

groovy
pipeline {
  agent any
  environment {
    // This is NOT the real secret. It's a token that Jenkins uses
    // to talk to Vault (or a Vault approle ID).
    VAULT_TOKEN = credentials('vault-token-id')
  }
  stages {
    stage('Fetch Secrets') {
      steps {
        script {
          // Example: Call Vault API from Jenkins to fetch DB password
          def dbPass = sh(
            script: "vault kv get -field=password secret/prod/db",
            returnStdout: true
          ).trim()
          // Inject the secret into environment only for later steps
          env.DB_PASSWORD = dbPass
        }
      }
    }
    stage('Deploy') {
      steps {
        sh '''
          # Use the secret only here and avoid echoing it in logs
          # Example: pass it to an app config or Helm chart
          deploy_app --db-password "$DB_PASSWORD"
        '''
      }
    }
  }
}
How to prevent secrets from being logged or exposed:
	• Disable echo / set -x for secret commands.
	• Use CI features like Jenkins “mask passwords” or GitHub “secrets masking”.
	• Restrict who can view pipeline logs and configuration.
	• Make sure debug logs don’t print environment variables.

# Q3: Explain shift-left security. How have you implemented it in your projects?
Answer:
“Shift‑left security means moving security checks as early as possible: in developer tools, pre‑commit, and early CI, instead of waiting for a big security review at the end.”
How to implement:
	• Developer IDE level:
		○ Plugins for security (e.g., SAST IDE plugins, secret scanners).
		○ Developers see and fix issues while coding.
	• Git hooks / pre‑commit checks:
		○ pre‑commit hook for:
			§ secret scanning
			§ simple static checks
			§ linting and basic SAST.
	• Early CI stages:
		○ On every PR:
			§ SAST
			§ Dependency scanning
			§ Basic IaC scanning (Terraform/Helm).
	• Education and templates:
		○ Provide secure boilerplates and sample pipelines so devs inherit security by default.
You can phrase it like:
“In my projects, the moment code is pushed, it hits SAST and SCA, and Terraform goes through IaC checks. Developers get fast feedback before the code is merged, which is the essence of shift‑left.”

# Q4: What security gates would you implement in a CI/CD pipeline and at what stages?
Answer:
“I like to define security gates at four levels: pre‑commit, PR/CI, pre‑deploy, and post‑deploy.”
	1. Pre‑commit (optional but ideal)
	• Local linters and formatters.
	• Optional local secret scan or basic static checks.
	2. Pull Request / CI (main gates):
	• SAST gate: fail if any critical/high issues.
	• Dependency/SCA gate: fail on critical CVEs (or known exploited vulnerabilities).
	• IaC gate: block insecure Terraform/K8s manifests (e.g., 0.0.0.0/0, public S3, privileged pods).
	• Unit/integration tests: functional quality.
	3. Pre‑deploy (staging / pre‑prod):
	• Container image scanning before pushing to production registry.
	• Policy‑as‑code for deployment manifests.
	• Optional DAST on staging environment with non‑prod data.
	4. Post‑deploy (prod):
	• Runtime security tools (host and container).
	• Continuous vulnerability scans on running workloads.
	• Alerting for new critical CVEs on existing images.
Thresholds example:
	• Critical: always block.
	• High: block in prod release, might allow in dev with explicit approval.
	• Medium/Low: log and schedule in backlog.

# Q5: How do you handle pipeline failures due to security issues? What’s your threshold for blocking deployments?
Answer:
“First I let automation block by default for high risk, then I have a clear exception process.”
Handling failures:
	• If SAST/SCA/scan returns issues above threshold:
		○ Pipeline fails automatically.
		○ Create a ticket (Jira, Azure Boards) with details and assign to service team.
	• For genuine high‑risk issues, dev team is expected to fix before merge/release.
Threshold example (practical):
	• SAST:
		○ Block: Critical & High.
		○ Warn: Medium & Low (don’t fail build but show report).
	• Dependency/SCA:
		○ Block: Critical CVEs, known exploited vulnerabilities (KEV).
	• Container scans:
		○ Block: Critical, or High in internet‑facing services.
Exception process:
	• If there is a business emergency:
		○ Security + product owner jointly approve a temporary exception.
		○ Document risk, set an expiry date (e.g., 2 weeks) and track it with a ticket.
You can say:
“My default is to block deployments for critical/high security issues, but there is a documented, time‑bound exception workflow for genuine edge cases.”

# 2. SAST (Static Application Security Testing)

# Q6: Explain the difference between SAST and DAST. When would you use each?
Answer:
	• SAST (Static Application Security Testing):
		○ Runs on source code / bytecode without executing the application.
		○ Good for finding:
			§ Unsafe API calls
			§ Potential injection points
			§ Hard‑coded secrets
			§ Insecure crypto usage.
		○ Used early: on commits, PRs, and builds.
	• DAST (Dynamic Application Security Testing):
		○ Tests a running app from the outside (black‑box or gray‑box).
		○ Sends HTTP/HTTPS requests to find:
			§ SQL injection
			§ XSS
			§ Auth/Session issues
			§ Misconfigurations.
		○ Used later: after app is deployed to QA/staging.
When to use:
	• Use SAST early to catch patterns in code before deployment.
	• Use DAST once a build is running in an environment, to test it “like an attacker”.

# Q7: You’ve integrated SonarQube into your pipeline. How do you handle false positives?
Answer:
“I treat SonarQube as a helper, not a judge. The process is: triage → mark correctly → tune rules → keep quality gates realistic.”
Practical handling:
	1. Triage findings:
		○ For each issue, check:
			§ Is the path actually exploitable?
			§ Is this part of dead code or test code?
		○ If it’s a real issue, fix it.
	2. Mark false positives correctly:
		○ In SonarQube UI, mark as:
			§ “False Positive”
			§ or “Won’t Fix” with a clear justification.
		○ This helps future scans ignore the same pattern in that location.
	3. Tune rules & quality profiles:
		○ Disable rules that are too noisy and not relevant to your language/stack.
		○ Introduce stricter rules only once the team is ready, to avoid overwhelming them.
	4. Quality gate strategy:
		○ Start with:
			§ “No new critical/high vulnerabilities or code smells on new code”
		○ This prevents new issues while you gradually fix the legacy backlog.
Script line you can use:
“I always prioritize making SonarQube usable for developers by reducing noise; otherwise they start ignoring all findings.”

# Q8: What are the limitations of SAST tools? How do you complement them?
Answer:
Some realistic limitations:
	• High false positives:
		○ Static analysis sometimes flags potential issues that are not reachable or not exploitable.
	• Language and framework coverage:
		○ Some languages or new frameworks are poorly supported or have immature rules.
	• No runtime context:
		○ SAST cannot see real data, runtime configs, or environment‑specific behavior.
	• Limited understanding of complex flows:
		○ Multi‑service, event‑driven, or heavily dynamic code (reflection, meta‑programming) is hard for SAST.
How to complement:
	• DAST: to validate runtime behavior and externally exposed vulnerabilities.
	• SCA / dependency scanning: to catch vulnerabilities in third‑party libs.
	• IaC scanning: to catch misconfigurations in cloud/Kubernetes/Terraform.
	• Manual secure code review: for high‑risk modules like auth, payments, crypto.
You can say:
“SAST is great but not enough; I always combine it with DAST, SCA, IaC scans, and targeted manual review for critical components.”

# Q9: How would you configure Checkmarx or Fortify to scan only critical code paths to reduce scan time?
Answer:
Idea: scope down the scan rather than scanning the entire monolith every time.
Practical techniques:
	• Incremental/partial scanning:
		○ Configure the tool to scan only files changed in the last commit/PR.
		○ Many enterprise tools support “incremental scan” modes to base on the last full scan.
	• Scope by directories / modules:
		○ Create different projects/profiles per module or service.
		○ Example: Scan only auth-service/ or payment-service/ more frequently than others.
	• Exclude non‑critical or generated code:
		○ Exclude folders like tests/, vendor/, node_modules/, auto‑generated code.
		○ This reduces noise and speed.
	• Schedule full scans separately:
		○ Daily/weekly full scan on main branch.
		○ Lightweight incremental scans on each PR.
Interview line:
“I usually run fast incremental scans on PRs and a scheduled full scan at night. That keeps developer feedback quick without losing full coverage.”

# Q10: Explain CWE and OWASP Top 10. How do SAST tools map findings to these?
Answer:
	• CWE (Common Weakness Enumeration):
		○ A standardized catalog of software weakness types, like “CWE‑79: Cross‑Site Scripting” or “CWE‑89: SQL Injection”.
		○ It’s about classes of weaknesses in code.
	• OWASP Top 10:
		○ A prioritized list of the most critical web application security risks (e.g., Broken Access Control, Cryptographic Failures, Injection).
		○ It’s more high‑level and risk‑oriented.
How SAST tools map to these:
	• Each rule in a SAST tool is usually labeled with:
		○ One or more CWE IDs.
		○ Often an OWASP Top 10 category.
Example explanation you can give:
“If SonarQube flags an SQL injection issue, it might mark it as CWE‑89 and map it under OWASP Top 10 ‘Injection’. That helps teams report and track compliance and coverage against standard frameworks.”



# 3. DAST (Dynamic Application Security Testing)

# Q11: How does OWASP ZAP differ from Burp Suite? Which would you choose for CI/CD integration?
Answer:
OWASP ZAP is open‑source and very automation‑friendly, with good CLI, Docker images, and APIs that fit nicely into CI/CD pipelines. Burp Suite is extremely powerful for manual, interactive testing but the full automation capabilities (Burp Enterprise) are commercial and more complex to integrate. For pure CI/CD integration, ZAP is usually the first choice because you can run it headless in Docker, script scans, and parse reports easily; for deep manual testing and complex logic, Burp is still my go‑to tool.

Q12: Walk me through setting up automated DAST scanning in a CI/CD pipeline.
Answer:
“I typically use ZAP in Docker as a stage after deploying to a test environment.”
Basic flow:
	1. Pre‑req: App is deployed to a QA/stage URL (e.g., https://qa.myapp.com).
	2. Pipeline stage: Add a “DAST Scan” stage after deployment.
Example (pseudo Jenkinsfile):

groovy
stage('DAST Scan') {
  steps {
    script {
      // Run ZAP baseline scan in Docker
      sh '''
        docker run --rm \
          -v $PWD/reports:/zap/wrk \
          owasp/zap2docker-stable zap-baseline.py \
          -t https://qa.myapp.com \
          -r zap-report.html \
          -J zap-report.json \
          -m 5  # max 5 mins spider
      '''
      // Parse report for high/critical issues
      // In practice you would write a small script to read JSON and exit !=0 if threshold exceeded
    }
  }
}
	1. Result handling:
	• Archive the HTML/JSON report as artifacts.
	• Small script parses JSON and fails the build if high/critical issues are found.
	2. Optional: Schedule a nightly full scan job (more aggressive than the baseline) against staging.

# Q13: How do you handle authentication when performing DAST scans?
Answer:
“Authentication is usually the tricky part; my approach depends on whether it’s session‑based or token‑based.”
Typical patterns:
	• Form‑based login (session cookie):
		○ Configure ZAP/Burp with login URL, username, password.
		○ Create an authentication script or context in ZAP that:
			§ Logs in.
			§ Extracts the session cookie.
			§ Reuses it for all scan requests.
	• Token‑based (JWT/API key):
		○ Use a pre‑step to obtain a token (e.g., login API call, OAuth client credentials).
		○ Configure the DAST tool to add Authorization: Bearer <token> header for all requests.
		○ Keep token in secret store and inject at runtime.
	• Recorded sessions / scripts:
		○ For complex SSO flows, record the login sequence using ZAP/Burp or Selenium.
		○ Use that script as part of the scan to establish an authenticated session.
Key point to mention: “I always ensure credentials/tokens are handled via secret management, not hard‑coded in scan configs.”

# Q14: What’s the difference between active and passive scanning in DAST tools?
Answer:
	• Passive scanning:
		○ The tool only observes traffic (requests and responses), for example while you or a crawler browse the site.
		○ It looks for issues in headers, cookies, responses (e.g., missing security headers, info leakage).
		○ Low risk because it doesn’t send malicious payloads.
	• Active scanning:
		○ The tool actively injects payloads and manipulates parameters (e.g., SQLi, XSS probes).
		○ Higher coverage but also higher risk: may trigger errors, timeouts, or modify data.
In practice:
“I usually start with passive or a baseline scan in shared environments and run more aggressive active scans only against non‑production or dedicated test environments.”

Q15: How would you scan a single‑page application (SPA) or API effectively with DAST?
Answer:
SPAs and APIs need a bit more configuration:
	• SPAs:
		○ Use a crawler/spider that supports AJAX and JS (like ZAP’s AJAX Spider or headless browser).
		○ Make sure the DAST tool can execute JavaScript to discover routes (e.g., React/Angular/Vue).
		○ Provide a list of important URLs manually if auto‑discovery is weak.
	• APIs:
		○ Import OpenAPI/Swagger/Postman collections into ZAP/Burp.
		○ Define the base URL and authentication headers (e.g., JWT).
		○ Let the tool generate requests from the spec and then actively scan those endpoints.
You can say: “For SPAs I rely on JS‑aware crawling, and for APIs I always try to feed an OpenAPI spec or collection so the scanner doesn’t miss endpoints.”

# 4. Container Security

# Q16: Explain the container security lifecycle from image build to runtime.
Answer:
“I think of it as four phases: build → store → deploy → run.”
	1. Build:
		○ Use minimal, trusted base images.
		○ Bake in only what is needed; no compilers, shells in final images if possible.
		○ Run:
			§ Dependency/SCA scanning.
			§ Container image scanning during CI.
	2. Store (registry):
		○ Use a private, authenticated registry (e.g., ECR, ACR, Harbor).
		○ Enable:
			§ Image vulnerability scanning.
			§ Image signing (Cosign/Notary).
		○ Apply RBAC so only CI has push access.
	3. Deploy:
		○ Use Kubernetes/OpenShift with:
			§ Admission controllers to enforce policies (no :latest, no privileged, signed‑image‑only).
		○ Validate manifests/IaC with policy‑as‑code before applying.
	4. Runtime:
		○ Use runtime security tooling:
			§ Detect suspicious syscalls, network anomalies, container escapes.
		○ Enforce network policies and least‑privileged RBAC.
		○ Continuously scan nodes and running containers for new CVEs and drift.
Interview phrase: “Secure build, secure registry, policy‑driven deployment, and runtime monitoring together form the full container security lifecycle.”

# Q17: How do you secure Docker images? What checks do you perform before pushing to a registry?
Answer:
“Most of the security is decided in the Dockerfile and CI pipeline.”
Key practices:
	• Base image:
		○ Choose official or trusted images (e.g., alpine, ubi, distro official images).
		○ Keep them updated regularly.
	• Dockerfile hygiene:
		○ Use multi‑stage builds so final image is small and doesn’t contain compilers or build tools.
		○ Run the app as a non‑root user (USER directive).
		○ Avoid copying .git, test data, or secrets into the image.
		○ Set proper file permissions and reduce attack surface.
	• Checks before pushing:
		○ SCA on dependencies (e.g., npm audit, pip-audit, mvn plugins).
		○ Image vulnerability scan (Trivy, Grype, commercial scanner) in CI:
			§ Fail build on critical/high issues.
		○ Secret detection on image layers (ensure no keys/certs baked in).
Example snippet:

text
#Stage 1: build
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
#Stage 2: runtime
FROM node:20-alpine
RUN addgroup -S app && adduser -S app -G app
USER app
WORKDIR /app
COPY --from=build /app/dist ./dist
COPY --from=build /app/node_modules ./node_modules
CMD ["node", "dist/server.js"]

# Q18: What is the difference between image scanning and runtime container security?
Answer:
	• Image scanning:
		○ Looks at the container image (packages, OS layers, libraries) before it runs.
		○ Detects known vulnerabilities (CVEs), outdated components, sometimes misconfigurations.
		○ It’s static and usually part of CI or registry scanning.
	• Runtime container security:
		○ Monitors containers while they’re running:
			§ Unexpected processes
			§ Suspicious syscalls (e.g., attempts at ptrace, kernel tampering)
			§ Network anomalies
			§ File system modifications.
		○ Detects attacks, exploitation, and drift (container behavior different from what image suggests).
Analogy you can use: “Image scanning checks what you plan to run; runtime security checks what is actually happening.”

# Q19: You discover a critical vulnerability in a base image used across 50 containers. Walk through your remediation process.
Answer:
“My priority is to understand impact, patch centrally, and roll out in a controlled but quick way.”
Steps:
	1. Assess impact:
		○ Identify all images built on that base (via tags, SBOM, or registry search).
		○ Check if they’re internet‑facing, dealing with sensitive data, or internal only.
		○ Look at exploitability details: is there a known exploit or active exploitation?
	2. Patch & rebuild:
		○ Update the base image to the latest patched tag.
		○ Rebuild all dependent images in CI:
			§ Run full SCA/image scans.
			§ Run regression tests.
	3. Rollout strategy:
		○ Prioritize:
			§ External and high‑risk services first.
		○ Deploy to staging, validate, then roll out to production with canary or phased deployment.
	4. Communication & tracking:
		○ Create a central incident ticket referencing the CVE.
		○ Track which services are patched and which are pending.
		○ Document timeline and any risk acceptance.
	5. Prevent recurrence:
		○ Ensure base images are regularly updated (e.g., weekly scheduled rebuilds).
		○ Use policies to avoid very old base images.

# Q20: Explain how Red Hat Advanced Cluster Security (or Aqua/Twistlock) works.
Answer (generic commercial container security platform):
“These platforms provide full lifecycle security: build, deploy, and runtime.”
Core capabilities:
	• Build time:
		○ Scan container images and IaC for vulnerabilities and misconfigurations.
		○ Enforce policies like “no critical CVEs”, “no root user”, “no latest tag”.
	• Deploy time / admission control:
		○ Integrate with Kubernetes/OpenShift API as admission controllers.
		○ Reject workloads that violate policies (e.g., privileged pods, unsigned images).
	• Runtime protection:
		○ Deploy agents/daemons on nodes to:
			§ Monitor container processes, file access, and network flows.
			§ Detect anomalies, policy violations, or known attack patterns.
	• Compliance and visibility:
		○ Provide dashboards with compliance checks (CIS, PCI, etc.).
		○ Show cluster topology, risky components, and prioritized remediation actions.
You can summarize: “They connect to the cluster, watch images and running workloads, and enforce security policies at every step from CI to runtime.”

# Q21: How do you implement security policies for Kubernetes/OpenShift clusters?
Answer:
“I use a combination of built‑in mechanisms and policy‑as‑code.”
Key controls:
	• Pod Security (Pod Security Standards / Admission):
		○ Enforce:
			§ No privileged containers.
			§ No hostPath mounts unless explicitly allowed.
			§ Non‑root user, read‑only root filesystem where possible.
	• RBAC (Role‑Based Access Control):
		○ Grant least privilege:
			§ Developers may manage resources in their namespaces, not cluster‑wide.
			§ Service accounts have only the permissions they need (no cluster-admin by default).
	• Network Policies:
		○ Default‑deny east‑west traffic where possible.
		○ Allow only necessary service‑to‑service communication.
	• Resource quotas & limits:
		○ Set CPU/memory limits and requests to prevent abuse and DoS by noisy pods.
	• Policy‑as‑code (OPA Gatekeeper / Kyverno):
		○ Write policies like:
			§ Disallow images from untrusted registries.
			§ Require labels/annotations, owner references.
			§ Enforce TLS, mandatory probes, etc.
For OpenShift specifically, mention Security Context Constraints (SCCs) as an extra control.

# Q22: What are the security differences between Docker and Kubernetes/OpenShift?
Answer:
“At a high level: Docker is about running containers on a single host; Kubernetes/OpenShift is about orchestrating them across a cluster with extra security layers.”
Key differences:
	• Scope:
		○ Docker Engine secures containers on one host (namespaces, cgroups, local networking).
		○ Kubernetes/OpenShift adds multi‑tenant concerns: multiple teams, namespaces, and shared infrastructure.
	• Identity & access:
		○ Docker has local users and group controls on the host.
		○ Kubernetes/OpenShift add:
			§ API server with authentication/authorization (RBAC).
			§ Service accounts for workloads, with fine‑grained permissions.
	• Network & isolation:
		○ Docker by itself has basic networks and iptables rules.
		○ Kubernetes/OpenShift use CNI plugins, NetworkPolicies, and often service mesh for granular traffic control.
	• Policy & governance:
		○ Docker alone has no cluster‑level policies.
		○ Kubernetes/OpenShift provide:
			§ Admission controllers, PodSecurity, SCCs (OpenShift), and policy‑as‑code tools to enforce security standards.
You can phrase it: “Docker gives container‑level isolation; Kubernetes/OpenShift add the security layers needed to safely run many teams and apps on shared clusters (RBAC, policies, network controls, admission).”


# 5. Vulnerability management

# Q23: How do you prioritize vulnerabilities for remediation when you have hundreds of findings?
Answer:
“I don’t treat all findings equally; I prioritize by severity, exploitability, and business impact.”
	• Start with severity (CVSS): focus on Critical and High first, then Medium, then Low.
	• Consider exploitability & context: public‑facing apps, internet‑exposed ports, sensitive data, known exploited CVEs get higher priority than internal, low‑impact systems.
	• Factor asset criticality: production payment API > internal reporting tool, even with same CVSS.
	• Use your VM tool’s risk score (severity + exposure + asset info) to drive a clear queue for each product team.

Q24: Explain the difference between CVE, CVSS, and CWE.
Answer:
	• CVE (Common Vulnerabilities and Exposures):
		○ A unique ID for a specific vulnerability, like “CVE‑2024‑12345”.
		○ Think of it as a catalog entry describing “this particular bug in this product”.
	• CVSS (Common Vulnerability Scoring System):
		○ A standardized way to score how severe a vulnerability is (0.0–10.0), considering impact and exploitability.
		○ Often mapped to Critical/High/Medium/Low for prioritization.
	• CWE (Common Weakness Enumeration):
		○ A list of generic weakness types in software, e.g., CWE‑79 (XSS), CWE‑89 (SQL injection).
		○ SAST tools usually map findings to CWEs because they describe “what kind of coding weakness” it is.

Q25: What’s your approach to managing vulnerability SLAs (e.g., Critical: 7 days, High: 30 days)?
Answer:
“I turn SLAs into something the tools can enforce and the teams can see.”
	• Define a clear SLA policy like: Critical 7 days, High 30 days, Medium 60 days, Low 90 days (or similar).
	• In the VM platform, configure due dates based on discovery date + SLA and sync issues into Jira/Azure Boards with those due dates.
	• Dashboards show SLA breaches per team/service; regularly review them in security/engineering syncs.
	• For exceptions (legacy system, blocked by vendor), raise a formal risk acceptance with expiry and track it separately so it’s visible.

Q26: How do you handle zero‑day vulnerabilities in production?
Answer:
“For zero‑days, I treat it like an incident: assess fast, add compensating controls, then patch when possible.”
	• Assessment: Quickly check if your stack/versions are affected and where (which apps, images, or components).
	• Compensating controls:
		○ Add or tighten WAF rules, block specific payloads, or restrict endpoints.
		○ Disable or limit risky features if possible.
	• Emergency patch plan:
		○ If vendor or community patch/workaround exists, prioritize a hotfix release for critical systems, test minimally, roll out gradually.
	• Monitoring and comms:
		○ Increase logging/alerting around suspected paths and keep stakeholders informed until permanent fixes are deployed.

Q27: Describe your experience with vulnerability scanning tools. How do they integrate with your workflow?
Answer:
“Modern tools are wired into code, containers, and cloud, and then into our ticketing system.”
	• Use scanners for:
		○ Code/open‑source (SCA like Snyk, Black Duck, etc.).
		○ Infrastructure/hosts (Nessus, Qualys, etc.).
		○ Containers/registry and cloud (container/IaC scanners).
	• Integrate with CI/CD so scans run automatically on PRs, builds, and image pushes and fail on defined thresholds.
	• Connect scanners to issue trackers (Jira, Azure Boards) so each finding creates or updates tickets with owners, due dates, and status.
	• Use reporting dashboards to track trends, SLA adherence, and top risky apps so leadership sees progress, not just raw findings.

6. Software Composition Analysis (SCA)

Q28: What is SCA and why is it important? How does Black Duck or Snyk work?
Answer:
	• SCA (Software Composition Analysis):
		○ Scans your codebase or images to detect open‑source libraries, their versions, known vulnerabilities, and license/compliance issues.
		○ Important because most modern apps are 60–90% open‑source, and many vulnerabilities live in those dependencies, not your custom code.
	• How tools like Black Duck / Snyk work:
		○ Analyze manifests (e.g., package.json, pom.xml, requirements.txt) and SBOMs to build a dependency graph.
		○ Cross‑reference components with their vulnerability databases and show CVEs, severity, and fixed versions.
		○ Integrate with IDEs, repos, CI/CD, and registries, continuously monitoring for new CVEs and raising alerts or tickets when something becomes vulnerable.

Q29: How do you manage vulnerable dependencies in a project?
Answer:
“Mainly: update smartly, pin versions, and avoid blind upgrades.”
	• Regular updates:
		○ Use tooling (npm audit fix, pip-tools, Dependabot, Renovate, etc.) to propose upgrades.
		○ Prefer upgrading to the smallest safe version that fixes the CVE (e.g., 1.2.3 → 1.2.5 instead of 2.x if possible).
	• Version pinning and lockfiles:
		○ Use lockfiles (package-lock.json, poetry.lock, Gemfile.lock) to keep environments reproducible.
		○ After updating, regenerate lockfiles and run tests.
	• Alternative libraries:
		○ If a dependency is abandoned or repeatedly vulnerable, consider replacing it with a better‑maintained library.
	• Process:
		○ Treat upgrades like normal changes: PR, code review, tests, then deploy; don’t silently patch in production.

Q30: Explain the difference between direct and transitive dependencies. How do you secure both?
Answer:
	• Direct dependencies:
		○ Libraries your project explicitly declares and imports, like entries in package.json or pom.xml.
		○ You choose and control their versions.
	• Transitive dependencies:
		○ Libraries required by your direct dependencies (and by their dependencies, and so on).
		○ They are not explicitly listed in your main manifest but are pulled in automatically.
Securing both:
	• Use SCA tools that scan the full dependency tree, not just top‑level packages.
	• Keep lockfiles under version control so you know exactly which transitive versions are installed.
	• When a transitive dependency is vulnerable, you might:
		○ Update the direct dependency that brings it in.
		○ Override the transitive version via dependency management features (Maven/Gradle/npm resolutions) if supported.

Q31: A critical vulnerability is found in a library 4 levels deep in your dependency tree. How do you fix it?
Answer:
“I first find which direct dependency pulls it in, then fix that chain with minimal breakage.”
Steps:
	1. Identify the chain:
		○ Use SCA tooling or npm ls, mvn dependency:tree, gradle dependencies to see which top‑level package brings that transitive library.
		○ Example: your-app → A → B → C → vulnerable-lib.
	2. Find a fixed version path:
		○ Check if your direct dependency (A) has a newer version that uses a patched version of the vulnerable library.
		○ If yes, update A, regenerate lockfile, run tests.
	3. Override if necessary:
		○ If the direct dependency is not updated yet, use dependency overrides (Maven dependencyManagement, npm/yarn resolutions, Gradle constraints) to force the safe version of the vulnerable library.
	4. Validate and roll out:
		○ Run unit/integration tests to catch compatibility issues.
		○ Deploy through normal CI/CD; don’t hot‑patch in prod manually.
You can phrase it: “I avoid hacking the vendor code; I instead update or override the dependency chain so the vulnerable library gets a fixed version, and then I validate it with tests before rollout.”


7. Secure code review

Q32: What do you look for when performing a security‑focused code review?
Answer:
“For security reviews, I don’t read every line; I focus on high‑risk areas.”
Key focus areas:
	• Input validation & output encoding:
		○ Is all external input validated on server side for type, length, format, and range?
		○ Is output properly encoded to prevent XSS and injection?
	• Authentication & session:
		○ Is login done over HTTPS, are passwords handled securely, and are tokens/cookies marked secure/HttpOnly?
	• Authorization:
		○ Are there centralized checks (e.g., middleware) instead of scattered if checks?
		○ Is role/permission verified on every sensitive action or resource?
	• Cryptography & secrets:
		○ Is strong crypto used (no MD5/SHA‑1 for passwords, keys not hard‑coded, proper key rotation)?
	• Injection & external calls:
		○ Are queries parameterized, and are external API responses validated before use?
	• Logging & error handling:
		○ Do logs avoid printing secrets/PII, and do error messages avoid leaking stack traces or internal details?

Q33: How do you identify SQL injection vulnerabilities in code? What about in compiled code?
Answer:
“In source code, I look for string‑built queries; in compiled code or binaries, I lean on tools and taint analysis.”
	• In source code:
		○ Red flag: string concatenation using user input in SQL, e.g. "... WHERE id = " + userInput.
		○ Safe pattern: parameterized queries or prepared statements:
			§ Java: PreparedStatement with ? placeholders.
			§ Python: parameter tuples, not f‑strings.
			§ ORMs (Hibernate, JPA, Django ORM) used correctly with parameters.
	• In compiled/closed‑source code:
		○ Use SAST/IAST tools that do taint analysis: track untrusted input flowing into SQL sinks.
		○ Combine with DAST (e.g., ZAP/Burp) to see if crafted inputs cause SQL errors, time delays, or data leakage.
You can phrase it: “If I see string concatenation or building SQL from raw request parameters, that’s an immediate candidate for SQL injection.”

Q34: Explain OWASP Top 10. Pick 3 and describe how you’d detect and prevent them.
Answer:
“The OWASP Top 10 is a list of the most critical web app risks. I’ll pick Injection, Broken Authentication, and XSS.”
	1. Injection (e.g., SQL injection):
		○ Detect:
			§ SAST rules looking for unsafe SQL building.
			§ DAST tests that send ' OR '1'='1 style payloads and look for anomalies.
		○ Prevent:
			§ Parameterized queries / prepared statements, ORMs, and strict input validation.
	2. Broken Authentication:
		○ Detect:
			§ Review code for weak password rules, no account lockout, missing MFA, insecure session handling.
			§ DAST checks for session fixation, weak cookies, or predictable tokens.
		○ Prevent:
			§ Strong password storage (bcrypt/Argon2), secure cookies, short‑lived tokens, MFA, proper logout and session invalidation.
	3. Cross‑Site Scripting (XSS):
		○ Detect:
			§ Secure code review focusing on user‑supplied data being reflected without encoding.
			§ DAST using XSS payloads to see if scripts execute.
		○ Prevent:
			§ Output encoding, templating frameworks with auto‑escaping, input validation, CSP headers where possible.

Q35: What are the common security issues in API implementations?
Answer:
“For APIs, the big issues are auth, authorization, input, and data exposure.”
Typical problems:
	• Authentication & authorization:
		○ Missing or weak auth (no tokens, shared API keys).
		○ No per‑user/per‑tenant authorization checks (IDOR/Broken Object Level Authorization).
	• Input validation & output filtering:
		○ No schema validation on JSON/XML; APIs trusting client‑side validation.
		○ Returning entire objects instead of only required fields, leading to excessive data exposure.
	• Rate limiting & abuse:
		○ No throttling, allowing brute force or scraping.
	• Transport & secrets:
		○ No HTTPS, credentials in URLs, tokens not rotated.
In a review, you’d mention: “I always check if each endpoint has proper auth/authorization, input validation, and reasonable data minimization.”


8. Cloud & infrastructure security

Q36: How do you secure Infrastructure as Code (Terraform)? What tools would you use?
Answer:
“I treat Terraform like app code: scan it, review it, and enforce policy‑as‑code.”
Key practices:
	• Static analysis tools:
		○ Use Checkov, tfsec, or Terrascan to catch misconfigurations: open security groups, public buckets, missing encryption, weak IAM.
	• Policy as code:
		○ Enforce org rules with custom policies (Rego/OPA, Checkov/Terrascan policies), e.g., “no 0.0.0.0/0 on SSH.”
	• Process:
		○ Store Terraform in Git, require PR reviews, and run scans on every change.
		○ Ignore .terraform or vendor modules to avoid noise, focus on what your team controls.

Q37: What security considerations are unique to cloud environments (AWS/Azure/GCP)?
Answer:
“In cloud, misconfig and IAM mistakes hurt the most.”
Unique concerns:
	• IAM & permissions:
		○ Overly broad roles (*:*) instead of least privilege.
		○ Misconfigured cross‑account roles and trust relationships.
	• Network security:
		○ Publicly exposed services due to open security groups or wide firewall rules.
		○ No network segmentation between tiers.
	• Data protection & configuration:
		○ Unencrypted storage (S3, EBS, RDS), missing logging (CloudTrail), and insecure defaults.
	• Shared responsibility & services:
		○ Different responsibilities for IaaS vs PaaS vs SaaS (provider secures infra; you secure configs, keys, apps).

Q38: How would you implement security scanning for Terraform/CloudFormation templates in CI/CD?
Answer:
“I put IaC scans as early gates, just like SAST.”
Implementation:
	• Pre‑commit hooks:
		○ Run tfsec/Checkov locally before commit to catch obvious issues.
	• CI pipeline stage:
		○ Add a “IaC Security Scan” stage that runs:
			§ checkov -d . or
			§ tfsec . or
			§ terrascan scan -d .
		○ Fail pipeline if critical/high issues or policy violations are found.
Example pseudo step:

bash
# CI stage: Terraform security scan
checkov -d . --quiet --framework terraform --soft-fail false
# or
tfsec --minimum-severity HIGH
	• Plan scanning:
		○ For extra safety, also scan terraform plan output to see the actual changes being applied.youtube​

Q39: Explain the shared responsibility model in cloud security.
Answer:
“The cloud provider secures the cloud; you secure what you run in the cloud.”
Concept:
	• Provider responsibilities (e.g., AWS/Azure/GCP):
		○ Physical data centers, hardware, networking, hypervisors, and managed service infrastructure.
	• Customer responsibilities:
		○ Identity & access (IAM), network configuration, OS patching (for IaaS), app code, data protection, and overall configuration.
	• Depends on service type:
		○ IaaS: you manage OS, apps, data.
		○ PaaS: provider manages OS/runtime; you manage app, data, config.
		○ SaaS: provider manages most; you still manage identities, usage, and data classifications.


9. Automation & integration

Q40: You need to integrate 5 different security tools into a Jenkins pipeline. How do you approach this?
Answer:
“I design a modular pipeline with one ‘security stage’ per tool and a small layer to normalize results.”
Approach:
	• Tool selection:
		○ Use Jenkins plugins where stable (e.g., SonarQube, DefectDojo) and CLI/API for others.
	• Pipeline structure:
		○ Separate stages: SAST, SCA, container scan, IaC scan, DAST.
		○ Each stage:
			§ Runs the tool (CLI/Docker).
			§ Produces a report (JSON/XML/HTML).
	• Failure strategy:
		○ Parse each report, apply thresholds, and mark build failed if critical/high issues.
	• Aggregation:
		○ Optionally, send all reports to a central system (DefectDojo, custom service) for deduplication and dashboards.

Q41: How do you aggregate and normalize findings from multiple security tools?
Answer:
“With many tools, you get duplicate noise; I push everything into a central platform.”
Options:
	• Use a dedicated platform:
		○ Tools like DefectDojo ingest reports from 100+ scanners, normalize by CWE/CVE, and deduplicate findings.
		○ They provide a single pane to track status, SLAs, and ownership.
	• Custom aggregation:
		○ Build a small service that:
			§ Accepts tool reports (JSON/XML).
			§ Normalizes fields: severity, CWE, component, location.
			§ Deduplicates based on “same file + line + rule + service” and pushes final items into Jira or a database.
Mention: “Aggregation helps teams see ‘one SQL injection issue’ instead of five copies from SAST, DAST, and SCA.”

Q42: Write a simple script/pseudo‑code to break a build if SAST finds high‑severity issues.
Answer (pseudo in shell):

bash
#!/usr/bin/env bash
# Example: Break build if SAST JSON report contains any HIGH or CRITICAL issues
REPORT="sast-report.json"
# Parse with jq (commonly available in CI images)
HIGH_COUNT=$(jq '[.issues[] | select(.severity=="HIGH" or .severity=="CRITICAL")] | length' "$REPORT")
echo "Found $HIGH_COUNT HIGH/CRITICAL SAST issues"
if [ "$HIGH_COUNT" -gt 0 ]; then
  echo "Failing build due to SAST high-severity findings"
  exit 1  # non-zero exit code makes the CI job fail
fi
echo "No blocking SAST issues, continuing..."
You can explain: “In a real pipeline, I adapt field names to that tool’s JSON schema, but the logic is always: parse → count high issues → exit 1 or 0.”

Q43: How do you handle API rate limits when integrating security tools?
Answer:
“In production pipelines, rate limits are real; I handle them with respectful timing and retry logic.”
Practical steps:
	• Batch and schedule:
		○ Avoid hitting APIs for every tiny event; batch uploads and run heavy jobs on schedules (nightly) where possible.
	• Backoff & retry:
		○ Implement exponential backoff on 429/5xx responses instead of hammering again immediately.
	• Caching:
		○ Cache results like tool metadata, rules, or large static lookups so you don’t call the API unnecessarily.
	• Rate limit aware design:
		○ For org‑wide scans or bulk uploads, use asynchronous jobs and queues rather than synchronous CI steps.
You can say: “I design integrations as good API citizens—respecting limits, batching where sensible, and failing gracefully if the security backend is temporarily overloaded.”

Q44: Describe how you’ve used APIs to automate security workflows.
Answer:
“APIs are how I glue tools and processes together.”
Common examples:
	• Scan orchestration:
		○ CI pipeline calls security tool APIs (SAST/DAST/SCA) to trigger scans and later fetch results instead of relying only on CLI.
	• Ticket creation & updates:
		○ Automation that reads scan results and creates Jira/Azure Boards tickets via their REST APIs, filling fields like severity, CWE/CVE, component, and SLA due date.
	• Reporting & dashboards:
		○ Nightly jobs query security platforms (DefectDojo, Snyk, etc.) and push summaries into dashboards or Slack/Teams notifications.
	• Workflow hooks:
		○ When a critical vulnerability is found, an API‑driven workflow can auto‑tag images, block promotion in CD, or notify on‑call channels.
You can phrase it as: “Whenever I see a repetitive manual step in security, I look for that tool’s API and convert it into a script or pipeline stage.”


10. Jenkins & pipeline‑specific

Q45: How do you secure Jenkins itself as part of DevSecOps?
Answer:
“I treat Jenkins like a critical production app: harden it, lock it down, and keep it clean.”
	• Access control & auth:
		○ Integrate with LDAP/SSO if possible, enforce strong auth, and use matrix‑based security so only admins can manage system config.
		○ Disable anonymous job execution and restrict who can create/modify pipelines and credentials.
	• Credentials & hardening:
		○ Store secrets only in Jenkins Credentials, never in Jenkinsfile or job parameters; restrict who can view credentials.
		○ Keep Jenkins and plugins updated, remove unused plugins, run Jenkins on a hardened VM/container with least privilege and regular backups.

Q46: Explain Jenkinsfile security best practices.
Answer:
“In Jenkinsfiles, the key is to avoid leaking secrets and limit what the pipeline can do.”
Best practices:
	• Secrets handling:
		○ Use credentials() and withCredentials blocks; never hard‑code passwords, tokens, or keys.
		○ Avoid printing env vars or secrets to logs; use masking and avoid set -x.
	• Least privilege & safety:
		○ Use dedicated service accounts/credentials per pipeline or project, not one global admin token.
		○ Avoid arbitrary user‑supplied Groovy code; prefer shared libraries reviewed and version‑controlled for reusable functions.
	• Integrity:
		○ Keep Jenkinsfiles in the same repo as the app, protected by PR review, so pipeline changes go through the same controls as code.

Q47: How do you implement security scanning stages in a declarative Jenkins pipeline?
Answer:
“I create separate stages per scan and sometimes run them in parallel.”
Example structure:

groovy
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean package'
      }
    }
    stage('Security Scans') {
      parallel {
        stage('SAST') {
          steps {
            sh 'run-sast-tool --project my-service --out sast-report.json'
          }
        }
        stage('SCA') {
          steps {
            sh 'run-sca-tool --out sca-report.json'
          }
        }
        stage('Container Scan') {
          steps {
            sh '''
              docker build -t my-service:${BUILD_NUMBER} .
              trivy image --exit-code 1 --severity HIGH,CRITICAL my-service:${BUILD_NUMBER} || exit 1
            '''
          }
        }
      }
    }
  }
  post {
    always {
      archiveArtifacts artifacts: '**/*report*.json', fingerprint: true
    }
    failure {
      mail to: 'team@example.com', subject: "Build failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}"
    }
  }
}

11. Kubernetes / OpenShift security

Q48: What are Pod Security Policies (deprecated) and Pod Security Standards?
Answer:
“Pod Security Policy (PSP) was the old way to control pod privileges; Pod Security Standards (PSS) is the newer, simpler model.”
	• Pod Security Policies (PSP):
		○ Cluster‑level objects that controlled things like privileged mode, hostPath, host networking, and allowed capabilities.
		○ Powerful but complex, now deprecated and removed in newer Kubernetes versions.
	• Pod Security Standards (PSS):
		○ Built‑in “profiles” (Privileged, Baseline, Restricted) that define what is allowed in a namespace.
		○ Enforced via the PodSecurity admission plugin or via tools like Kyverno/Gatekeeper; easier to apply per namespace.
You can say: “Now we use Pod Security Standards or admission policies instead of PSP to enforce privilege levels.”

Q49: How do you implement network segmentation in Kubernetes?
Answer:
“I use NetworkPolicies and sometimes a service mesh to control which pods can talk to which.”
	• NetworkPolicies:
		○ With a CNI that supports them, define rules that allow or deny traffic between pods/namespaces.
		○ Typical pattern: default deny all, then allow specific app‑to‑app or app‑to‑DB traffic only.
	• Ingress & egress:
		○ Use Ingress controllers with TLS, WAF rules, and IP whitelisting where needed.
		○ Use egress policies or firewalls to restrict outbound traffic to specific services.
	• Service mesh (e.g., Istio/Linkerd):
		○ Adds mTLS and fine‑grained traffic policies between services for extra protection.

Q50: Explain RBAC in Kubernetes. How would you implement least‑privilege access?
Answer:
“RBAC controls who can do what; I keep roles narrow and bind them only where needed.”
	• RBAC basics:
		○ Role / ClusterRole: define allowed verbs on resources (e.g., get/list/watch pods).
		○ RoleBinding / ClusterRoleBinding: bind those roles to users/groups/service accounts.
	• Least privilege approach:
		○ Create namespace‑scoped Roles for app teams (e.g., can manage Deployments/Services in their own namespace, not cluster‑wide).
		○ Use separate service accounts per application and bind only the permissions they truly need (e.g., read ConfigMaps in their namespace, nothing else).
		○ Avoid using cluster-admin except for cluster operators.

Q51: What is an admission controller? How does it enhance security?
Answer:
“Admission controllers are hooks that can validate or mutate requests before objects are stored in etcd.”
	• Definition:
		○ Components that intercept requests to the API server after authentication/authorization and before persistence.
		○ Types: built‑in controllers (NamespaceLifecycle, ResourceQuota) and webhook‑based (Validating/MutatingAdmissionWebhook).
	• Security benefits:
		○ Enforce security policies such as disallowing privileged pods, requiring certain labels/annotations, or blocking images from untrusted registries.
		○ Tools like OPA Gatekeeper or Kyverno use admission webhooks to evaluate policies and reject non‑compliant resources.
You can say: “Admission controllers are the ‘last gate’ to enforce security rules on every Kubernetes object creation or update.”

Q52: How do you secure secrets in OpenShift/Kubernetes?
Answer:
“I avoid storing raw secrets in manifests and use encryption plus external managers where possible.”
Practices:
	• Kubernetes Secrets + encryption at rest:
		○ Enable secret encryption at the API server so secrets in etcd are encrypted, not plain base64.
	• External secret managers:
		○ Use tools like External Secrets Operator or CSI Secrets Store to sync from Vault/AWS SM/Azure KV into Kubernetes.
		○ App reads them as regular Secrets, but source‑of‑truth and rotation are managed externally.
	• Sealed secrets / GitOps:
		○ With Sealed Secrets (e.g., Bitnami), store only encrypted secrets in Git; controller decrypts them inside the cluster.
	• Access control:
		○ Limit which service accounts and users can read secrets in each namespace via RBAC.


12. Compliance & standards

Q53: How do you ensure compliance in automated deployments?
Answer:
“I bake compliance checks into pipelines and keep evidence automatically.”
	• Policy as code:
		○ Use tools (OPA, Checkov, tfsec, Terrascan, Kyverno) to enforce cloud/IaC/K8s standards (e.g., encryption required, no public S3, no 0.0.0.0/0).
	• Automated controls:
		○ CI/CD gates for SAST, SCA, IaC, container scans that align with compliance requirements (e.g., PCI’s secure coding and vulnerability management controls).
	• Audit & evidence:
		○ Log all deployments, approvals, and scan reports; store artifacts (reports, logs) in a central location for audits.
		○ Use change management tickets linked to builds/releases so auditors can trace “who deployed what, when, and with which checks”.

Q54: What compliance frameworks have you worked with (SOC 2, PCI‑DSS, HIPAA)?
Answer (template – customize to your reality):
“I’ve mostly aligned practices with SOC 2 type controls and PCI‑DSS‑style requirements.”
Examples you can mention generically:
	• SOC 2: focus on access control, change management, logging, and incident response; DevSecOps helps by enforcing code reviews, CI/CD checks, and centralized logging.
	• PCI‑DSS: requires secure coding practices, vulnerability management, segmentation of cardholder data environments, and regular scans; security gates and IaC policies support these technically.
	• HIPAA: focus on protecting PHI, strong access controls, encryption, and audit logging; DevSecOps pipelines ensure that only compliant configurations and images reach environments handling PHI.
If you haven’t worked directly with audits, say you’ve implemented technical controls that map to those frameworks.

Q55: How do you implement policy‑as‑code? What tools have you used?
Answer:
“Policy‑as‑code means writing compliance and security rules as code and letting automation enforce them.”
Typical tools:
	• OPA / Gatekeeper:
		○ Define Rego policies like “no pods with hostNetwork true” or “all resources must have owner labels”.
		○ Gatekeeper runs as an admission controller to reject resources violating policies.
	• Kyverno:
		○ Kubernetes‑native policies written in YAML (easier for many teams), enforcing rules, mutating configs, or generating resources.
	• Terraform policies (Sentinel / Checkov / tfsec):
		○ Use Sentinel (Terraform Cloud/Enterprise) or Checkov/tfsec policies to enforce cloud/IaC rules during plan or in CI.
Process you can describe:
	• Start by codifying a small set of high‑impact rules.
	• Test in “audit mode” first to see impact, then move to “enforce mode” (deny).
	• Store policies in Git, reviewed like normal code, with CI tests for policy logic.
	

13. Incident Response & Monitoring

Q56: A container in production is exhibiting suspicious behavior. Walk through your investigation.
Answer:
“I follow a structured IR process: detect → isolate → analyze → remediate → learn.”
Step-by-step:
	1. Detection & isolation:
		○ Check runtime security tool alerts (Falco, Sysdig, Aqua) for the specific pod/node.
		○ Scale down replicas or cordon the node to limit blast radius without downtime.
	2. Analysis:
		○ kubectl logs, kubectl exec to inspect processes, network connections (netstat, ss), open files.
		○ Check container runtime security for suspicious syscalls, file changes, or network anomalies.
	3. Root cause:
		○ Compare against baseline: is this expected behavior or drift?
		○ Check image history, recent deployments, and if any new vulnerabilities match the behavior.
	4. Remediation:
		○ Roll back to known-good image/config if applicable.
		○ Restart affected pods or recreate namespace if compromised.
	5. Post-mortem:
		○ Document indicators, update detection rules, patch root cause, and conduct a blameless review.

Q57: What security monitoring would you implement for containers in production?
Answer:
“I layer monitoring across logs, metrics, runtime behavior, and network.”
Stack:
	• Runtime security: Falco, Sysdig, or commercial CSPM (Aqua, Prisma Cloud) for syscall monitoring, container escapes, and runtime policy violations.
	• Vulnerability management: Continuous scanning of running images and hosts for new CVEs.
	• Network monitoring: CNI metrics + service mesh telemetry for unexpected connections.
	• Audit logging: Kubernetes audit logs + app logs forwarded to central SIEM (Splunk, ELK).
	• Anomaly detection: ML-based behavioral analysis on CPU, memory, file access patterns.
Alerting: Focus on high-signal events like privilege escalation attempts, outbound connections to C2 domains, or crypto-mining patterns.

Q58: How do you differentiate between a false positive and a real security incident?
Answer:
“I validate with context, evidence, and cross-correlation instead of trusting a single alert.”
Process:
	• Context check: Is this expected behavior for that workload? (e.g., database doing lots of disk I/O is normal).
	• Evidence validation: Look at actual process trees, network flows, file changes — not just the alert summary.
	• Correlation: Does this align with other signals? (multiple alerts from same pod, threat intel match, unusual user agent).
	• Threat intelligence: Check if IOCs match known campaigns or if the CVE has active exploits.
	• Reproduce: Try to trigger the same behavior legitimately to understand false positive patterns.
You can say: “A single alert is a hypothesis; I always validate with multiple data sources before declaring an incident.”


14. Scenario‑based questions

Q59: Your SAST tool reports 500 vulnerabilities before a critical release tomorrow. What do you do?
Answer:
“I triage ruthlessly and focus on real risk, not raw numbers.”
Immediate actions:
	1. Prioritize: Filter for Critical/High only, new issues (not legacy), and exploitable paths.
	2. Quick triage: 80% are likely low/medium or false positives; focus on the actual 5-10 criticals.
	3. Release decision:
		○ If no criticals block release, proceed with risk acceptance for known issues.
		○ Document: “Release X contains Y known high vulns, mitigation Z, owner W.”
	4. Hotfix plan: Schedule fixes for top 10 within 1 week, full cleanup in next sprint.
Phrase it: “500 sounds scary, but after triage it's usually 5 real blockers and 495 items for the backlog.”

Q60: Developers complain security scans slow down their pipeline by 30 minutes. How do you respond?
Answer:
“I optimize without compromising coverage and show them the value.”
Solutions:
	• Incremental scanning: Scan only changed files/code paths instead of full repo.
	• Parallel execution: Run SAST, SCA, IaC scans simultaneously instead of sequentially.
	• Async/offload: Move heavy DAST scans to post-deploy or scheduled jobs, not blocking CI.
	• Caching: Cache clean scan results; only re-scan if dependencies or rules changed.
	• Feedback loop: Show metrics: “Security gates caught 3 criticals this month, preventing X hours of incident response.”
Compromise: “Let’s get PR feedback under 5 minutes, full security validation before prod deploy.”

Q61: A third‑party library you depend on has a critical RCE vulnerability with no patch available. What's your approach?
Answer:
“No patch means workarounds + timeline to replace.”
Immediate:
	1. Assess: Confirm exploitability (requires auth? network access? specific config?).
	2. Compensating controls:
		○ WAF rules to block known exploit payloads.
		○ Network policies/firewalls to limit exposure.
		○ Disable vulnerable feature if possible.
Longer term:
	• Find alternative library with similar functionality.
	• Fork and patch if critical and no alternatives exist.
	• Vendor engagement: request timeline publicly/escalate.
Communication: Document risk, mitigations, and replacement plan with dates.

Q62: You're starting at a new company with no DevSecOps practices. What's your 90‑day plan?
Answer:
Days 1-30: Assess & quick wins
	• Map current pipelines, tools, and pain points.
	• Add basic secret scanning + SAST to main pipelines.
	• Container scanning before prod deploys.
Days 31-60: Build foundation
	• Standardize pipeline templates with security stages.
	• Central vulnerability dashboard (DefectDojo or similar).
	• Basic IaC scanning + K8s admission policies.
Days 61-90: Scale & culture
	• Developer training + IDE plugins.
	• Runtime security POC.
	• Metrics dashboard showing security debt reduction.
Goal: “From zero to blocking critical issues in 90 days, with developer buy-in.”


15. Behavioral & soft skills

Q63: Describe a time when you had to convince developers to fix a security issue they deemed low priority.
Answer (STAR format):
Situation: Hard-coded AWS keys in a config repo used by 3 services.
Task: Get them removed before audit.
Action:
	• Showed them the keys worked (proof of compromise risk).
	• Quantified impact: “One leak = all 3 services compromised.”
	• Proposed fix: Vault integration with 2 lines of code change.
	• Offered to pair program the migration.
Result: Fixed same day, plus team adopted Vault standard.
Key: “I spoke business risk + gave them an easy fix path instead of just saying 'security says no.'”

Q64: How do you stay updated with the latest security threats and tools?
Answer:
“Daily habits + structured learning.”
Daily:
	• CVE feeds (GitHub Advisories, NVD) filtered by my stack.
	• Threat intel summaries (Recorded Future, Mandiant).
	• Twitter/X security accounts + Hacker News.
Weekly:
	• Security blogs (Snyk, Aqua, OWASP).
	• Tool release notes (Trivy, Falco, etc.).
Quarterly:
	• Conferences (Black Hat, Defcon recordings).
	• Certifications/courses (new OSCP, cloud security).
	• Internal security office hours + bug bounties.
Team: Run monthly “security share-out” meetings.

Q65: Tell me about a security incident you helped resolve. What was your role?
Answer (STAR format):
Situation: Log4Shell (CVE-2024-21338) — critical RCE in Log4j across 200+ services.
Task: Coordinate response across 5 teams in 48 hours.
Action:
	• Identified affected services via SCA scans + container image analysis.
	• Prioritized internet-facing services for emergency patching.
	• Coordinated WAF rules as interim protection.
	• Documented mitigations and rollout plan.
Result: 100% patching in 36 hours, no exploitation, plus automated CVE monitoring added to pipelines.
Role: Technical coordinator between security, dev, and ops teams.


