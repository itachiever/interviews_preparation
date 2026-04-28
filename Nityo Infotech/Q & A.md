# Questions

### Category 1: Strategy, Governance & Compliance
1. How do you explain the "Shift-Left" principle to a development team that views security purely as a roadblock?
2. If an external auditor asks for proof of CIS AWS Benchmark compliance, how do you use your DevSecOps pipeline to provide that evidence automatically?
3. Walk me through how you would map specific OWASP Top 10 vulnerabilities (like Injection or Broken Access Control) to automated checks in a CI/CD pipeline.
4. What DevSecOps metrics would you put on a dashboard for C-level management, and how are they different from the metrics you show to engineering teams?
5. How do you define and enforce a "Security SLA" (e.g., time to fix Critical vs. Low vulnerabilities) within a CI/CD pipeline?

### Category 2: Secure CI/CD Pipeline Architecture
6. Walk me through the end-to-end architecture of a secure CI/CD pipeline on AWS, from a developer's git commit to production deployment.
7. How do you design reusable pipeline templates for multiple teams without creating a rigid system that slows down innovation?
8. At what exact stages of a pipeline should security gates be "hard fails" (blocking deployment) vs. "advisory" (generating a ticket)?
9. How do you handle a situation where a newly introduced security scanning tool increases the pipeline build time from 10 minutes to 45 minutes?
10. What strategies do you use to ensure security scans run in parallel with application builds to optimize pipeline speed?

### Category 3: SAST (Static Code Analysis)
11. What is the difference between SAST and Code Quality tools, and how do you prevent them from overlapping in a pipeline?
12. How do you handle false positives in tools like SonarQube without forcing developers to blindly accept them or shutting down the pipeline?
13. Explain how you would integrate SonarQube into a Pull Request (PR) workflow. What happens if a developer tries to merge code that introduces a new critical bug?
14. When would you choose CodeQL over a traditional SAST tool like SonarQube or Checkmarx? 

### Category 4: SCA (Open-Source Dependency Scanning)
15. Explain the difference between a CVE (Technical vulnerability) and a License Risk in SCA. How do you automate checks for both?
16. A developer adds a new npm package. The SCA tool flags a "transitive dependency" (a dependency of a dependency) with a Critical CVE. The developer says they didn't install it. How do you resolve this?
17. How do you configure an SCA tool to automatically create a Jira ticket for a newly discovered vulnerability in an older, currently deployed microservice?
18. What is an SBOM (Software Bill of Materials), and why is it becoming a critical artifact in secure CI/CD pipelines?

### Category 5: DAST (Dynamic Runtime Testing)
19. Why do we need DAST if we already have SAST and SCA in the pipeline?
20. DAST tools often cause "flaky" pipelines or accidentally bring down staging environments. How do you automate DAST safely?
21. How do you handle authentication in an automated DAST scan? (e.g., How does the tool log in to test authenticated API endpoints?)
22. If a DAST scan finds a vulnerability in production that was missed by SAST in the pipeline, what is your immediate remediation and root-cause analysis process?

### Category 6: Container Security
23. What are the top 3 security misconfigurations you look for when reviewing a developer's Dockerfile?
24. How do you ensure that the container image running in production is the *exact same* image that was scanned and approved in the CI/CD pipeline? (Hint: Image digests vs. tags).
25. A base image (e.g., `node:14`) has a newly announced Critical CVE, but there is no patched version available yet. What is your mitigation strategy?
26. How do you implement runtime security for containers (e.g., preventing a container from spawning a shell or accessing the host filesystem)?

### Category 7: Secrets & Credential Management
27. What are the inherent risks of using native CI/CD secret variables (like GitHub Actions Secrets or Jenkins Credentials) compared to a dedicated vault?
28. Walk me through the workflow of a pipeline securely retrieving a dynamic database credential from HashiCorp Vault or AWS Secrets Manager.
29. How do you prevent developers from accidentally committing secrets (API keys) to Git, and how do you react if a secret is pushed?
30. How do you securely pass secrets to an application running inside a Kubernetes Pod without writing them to disk?

### Category 8: Infrastructure-as-Code (IaC) & AWS
31. What are the security risks of writing IaC (Terraform/Bicep), and how do you scan IaC templates *before* they provision infrastructure?
32. How do you securely manage and protect the Terraform State file in an AWS environment? (Focus on encryption and access control).
33. Explain how you would use Terraform to enforce the principle of least privilege for an AWS IAM role used by a microservice.
34. How do you automate the rotation of infrastructure secrets (like database passwords) using IaC without causing downtime?

### Category 9: Policy-as-Code (OPA, Sentinel)
35. Explain Policy-as-Code in simple terms. Why is it considered a mature step up from traditional security gates?
36. Give me a practical example of a policy you would write in OPA (Rego) or Terraform Sentinel for an AWS environment.
37. How does Policy-as-Code integrate with a GitOps workflow? (e.g., evaluating policies before a Terraform Plan is applied).

### Category 10: Real-Time Troubleshooting Scenarios
38. **Scenario:** A SAST tool flags a critical SQL injection in a legacy monolith. Devs say it’s a false positive but can't fix it before the end-of-quarter release. As an L2 DevSecOps engineer, how do you handle this without compromising security or halting the business?

---

# Answers


**1. How do you explain the "Shift-Left" principle to a development team that views security purely as a roadblock?**

**Answer:** I explain it as a developer experience improvement, not a police checkpoint. Instead of security finding 100 bugs right before a release—which requires tearing apart weeks-old code—shift-left acts like a "spell-checker for security" right in their IDE. It catches issues when the code is fresh in their mind, making it significantly faster, cheaper, and less frustrating to fix. 

**2. If an external auditor asks for proof of CIS AWS Benchmark compliance, how do you use your DevSecOps pipeline to provide that evidence automatically?**

**Answer:** I integrate an AWS compliance scanner (like Prowler or AWS Security Hub) into the deployment pipeline. Every time infrastructure is deployed, this tool runs and automatically generates a time-stamped compliance report (JSON/HTML). This report is archived in a secure S3 bucket. I simply give the auditor read-only access to that S3 bucket so they can view continuous, historical proof of compliance without interrupting the team.

**3. Walk me through how you would map specific OWASP Top 10 vulnerabilities (like Injection or Broken Access Control) to automated checks in a CI/CD pipeline.**

**Answer:** It’s about matching the right tool to the right risk. For "Injection" (like SQL injection), I map it to SAST (SonarQube) to scan the raw source code, and SCA to check for vulnerable libraries. For "Broken Access Control," SAST cannot see how the server routes traffic at runtime, so I map that to DAST (like OWASP ZAP) to automatically test the running API and verify that User A cannot access User B's data.

**4. What DevSecOps metrics would you put on a dashboard for C-level management, and how are they different from the metrics you show to engineering teams?**

**Answer:** C-levels care about business risk, not tooling. I show them "Mean Time to Remediate (MTTR)" for critical vulnerabilities, overall "Security Debt," and compliance status percentage. For engineering teams, I show actionable data: "False Positive Rates" per tool, "Pipeline Build Failures due to Security," and exactly which microservices have the most open issues so they know where to focus their work.

**5. How do you define and enforce a "Security SLA" (e.g., time to fix Critical vs. Low vulnerabilities) within a CI/CD pipeline?**

**Answer:** We automate the enforcement through pipeline rules. A "Critical" CVE is a hard stop—the pipeline will not allow deployment to production until it is fixed. For "Low" vulnerabilities, the pipeline passes, but an automated Jira ticket is created with a 30-day SLA timer. If that ticket isn't closed in 30 days, an automated script blocks the *next* scheduled release until the backlog is cleared.

**6. Walk me through the end-to-end architecture of a secure CI/CD pipeline on AWS, from a developer's git commit to production deployment.**

**Answer:** 
1. **Commit:** Developer pushes code to GitHub/GitLab.
2. **Build (CI):** Pipeline triggers. SAST and SCA scan the raw code. If they pass, the code is compiled.
3. **Package:** A Docker image is built. A container scanner (like Trivy) scans the image for OS-level vulnerabilities.
4. **Store:** The approved image is pushed to AWS ECR (Elastic Container Registry).
5. **Deploy (CD):** AWS CodePipeline or ArgoCD deploys the image to ECS/EKS. 
6. **Verify:** DAST runs against the staging environment before final production traffic is routed.

**7. How do you design reusable pipeline templates for multiple teams without creating a rigid system that slows down innovation?**

**Answer:** I create a "base template" that handles only the mandatory, non-negotiable security steps (e.g., pushing logs to a central SIEM, basic SCA scanning). For everything else, I use variables. For example, the template allows teams to pass a parameter to choose their own SAST tool (SonarQube vs. CodeQL) or skip DAST if they are deploying a non-web library. This keeps security standardised but gives teams flexibility.

**8. At what exact stages of a pipeline should security gates be "hard fails" (blocking deployment) vs. "advisory" (generating a ticket)?**

**Answer:** Hard fails should only happen when the risk is immediate and severe: a critical CVE, an unencrypted secret found in code, or a failed container image scan. Everything else (medium/low vulnerabilities, code style issues, minor misconfigurations) should be advisory. If you make too many things "hard fails," developers will become frustrated and find ways to bypass the pipeline entirely.

**9. How do you handle a situation where a newly introduced security scanning tool increases the pipeline build time from 10 minutes to 45 minutes?**

**Answer:** First, I check if the tool supports "incremental scanning"—meaning it only scans the code that changed in that specific Pull Request, rather than the whole repository. Second, I move the heavy scanning to run asynchronously in parallel with other build steps. If it's still too slow, I make the deep scan mandatory only on the "main" branch, keeping individual developer feature-branch builds fast.

**10. What strategies do you use to ensure security scans run in parallel with application builds to optimize pipeline speed?**

**Answer:** I decouple the tools from the main build thread. For example, while the application is compiling (which consumes CPU), I run SAST and SCA in separate, independent container agents simultaneously. Instead of a sequential flow (Build -> Scan -> Test), I design a matrix flow where the build artifacts are passed to a scanning stage that runs right alongside the unit testing stage, dramatically reducing total wait time.

**11. What is the difference between SAST and Code Quality tools, and how do you prevent them from overlapping in a pipeline?**

**Answer:** Code quality tools look for technical debt—like messy code, missing comments, or inefficient loops—which makes the app hard to maintain. SAST looks for security flaws—like SQL injection or hardcoded passwords—which makes the app unsafe. To prevent overlap, I carefully configure "Quality Profiles" in tools like SonarQube. I strictly separate the rules: the quality profile only checks for clean code, while the security profile only checks for vulnerabilities. This ensures a messy but safe codebase doesn't trigger a security panic.

**12. How do you handle false positives in tools like SonarQube without forcing developers to blindly accept them or shutting down the pipeline?**

**Answer:** I establish a formal, transparent "Waiver Process." If a developer spots a false positive, they cannot just click "ignore." They must add a comment in the code explaining *why* it is a false positive (e.g., "Variable is already sanitized on line 42"). Then, a designated security champion or L2 engineer reviews and approves the waiver in the SonarQube dashboard. This keeps the pipeline moving while maintaining an audit trail.

**13. Explain how you would integrate SonarQube into a Pull Request (PR) workflow. What happens if a developer tries to merge code that introduces a new critical bug?**

**Answer:** I integrate SonarQube using the "Pull Request Decoration" feature. When a developer opens a PR, SonarQube runs a quick analysis and posts the results directly as comments on the specific lines of code in GitHub/GitLab. If they introduce a new critical vulnerability, SonarQube marks the PR Quality Gate as "Failed." I then configure the Git platform (e.g., GitHub branch protection rules) to physically disable the "Merge" button until the Quality Gate passes.

**14. When would you choose CodeQL over a traditional SAST tool like SonarQube or Checkmarx?**

**Answer:** I choose CodeQL when dealing with massive, highly complex codebases or when deep, semantic analysis is required. Traditional SAST tools often rely on pattern matching (like searching for specific words), which causes high false positives. CodeQL actually compiles the code into a database of how data flows through the application. It is incredibly powerful for finding complex vulnerabilities (like "User input flows from this web form, through three functions, all the way to this database query") that simpler tools miss.

**15. Explain the difference between a CVE (Technical vulnerability) and a License Risk in SCA. How do you automate checks for both?**

**Answer:** A CVE is a technical security hole; it means a hacker could exploit your system. A License Risk is a legal issue; it means you are using an open-source library with a restrictive license (like GPL) that might legally force your company to make its proprietary, confidential code public. I automate both by configuring the SCA tool with a strict "Policy File." The policy is set to block the pipeline automatically if a critical CVE is found, AND block it if a restricted license is detected.

**16. A developer adds a new npm package. The SCA tool flags a "transitive dependency" (a dependency of a dependency) with a Critical CVE. The developer says they didn't install it. How do you resolve this?**

**Answer:** I explain to the developer that while they didn't install it directly, they *did* choose a package that requires it. The fix is usually simple: we run an update command (like `npm audit fix`) which tells the package manager to update the direct package to a newer version that relies on a safe version of the transitive package. If a safe version doesn't exist yet, we either find an alternative library or use the SCA tool to generate a "pull request patch" that temporarily fixes the vulnerable file until the library author updates it.

**17. How do you configure an SCA tool to automatically create a Jira ticket for a newly discovered vulnerability in an older, currently deployed microservice?**

**Answer:** I use the SCA tool's webhook integration feature. I configure it to monitor our production environments. If the tool detects a newly announced zero-day vulnerability in a dependency we are actively using, it triggers a webhook. I set up a middle automation script (or use native integrations) that takes that webhook data, maps the affected microservice to the correct Jira project/team, and automatically creates a high-priority ticket with all the technical details and fix instructions included.

**18. What is an SBOM (Software Bill of Materials), and why is it becoming a critical artifact in secure CI/CD pipelines?**

**Answer:** An SBOM is essentially an "ingredients list" for software. It is a machine-readable file listing every single open-source library and version used to build your application. It is becoming critical because of new government regulations (like the US Executive Order on Cybersecurity) and because of attacks like Log4j. When a new zero-day is announced, instead of scanning millions of lines of code for days, you simply search your SBOMs to instantly see if you are using the vulnerable ingredient.

**19. Why do we need DAST if we already have SAST and SCA in the pipeline?**

**Answer:** SAST looks at the *source code recipe*, and SCA looks at the *ingredients*. However, neither can see how the application actually behaves once it is running on a server. DAST looks at the *baked cake*. It is the only tool that can find runtime vulnerabilities, such as missing security HTTP headers, misconfigured web servers, or authentication flaws that only appear when the frontend, backend, and database are actually talking to each other.

**20. DAST tools often cause "flaky" pipelines or accidentally bring down staging environments. How do you automate DAST safely?**

**Answer:** First, I never point a heavy DAST tool at a shared staging environment used by QA. Instead, I spin up a dedicated, temporary "DAST environment" that is an exact clone of staging. Second, I configure "rate limiting" on the DAST tool so it doesn't bombard the application with thousands of requests per second and trigger false alarms. Finally, I ensure the DAST environment uses dummy test data so that if the tool does break something, it doesn't corrupt real testing data.

**21. How do you handle authentication in an automated DAST scan? (e.g., How does the tool log in to test authenticated API endpoints?)**

**Answer:** I never hardcode usernames and passwords into the DAST configuration. Instead, I use a "Scripted Login" approach. I write a small script that tells the DAST tool to send a POST request to the login endpoint with test credentials. The script captures the authentication token (like a JWT or session cookie) that the server returns, and the DAST tool automatically attaches that token to all of its subsequent test requests.

**22. If a DAST scan finds a vulnerability in production that was missed by SAST in the pipeline, what is your immediate remediation and root-cause analysis process?**

**Answer:** **Immediate:** Coordinate with the team to patch the code or, if that takes time, put a Web Application Firewall (WAF) rule in place to virtually block the attack pattern in production immediately. **Root-Cause:** Investigate *why* SAST missed it. Was the SAST tool misconfigured? Was the vulnerability caused by a server setting SAST can't see (like a missing HTTP header)? Once I find the gap, I configure a new automated check in the pipeline to ensure that specific type of vulnerability is caught next time.


**23. What are the top 3 security misconfigurations you look for when reviewing a developer's Dockerfile?**

**Answer:** 
1. Running the application as the `root` user (I look for a missing `USER` instruction).
2. Using the `latest` tag for base images, which is unpredictable and makes vulnerability tracking impossible.
3. Installing unnecessary software packages (like `curl`, `vim`, or `wget`) that increase the attack surface and should be removed in the final production image using multi-stage builds.

**24. How do you ensure that the container image running in production is the *exact same* image that was scanned and approved in the CI/CD pipeline?**

**Answer:** By strictly using image "Digests" instead of "Tags" in my Kubernetes or ECS deployment manifests. A tag like `app:v1.2` is mutable—someone could overwrite it with a new, unscanned image. A digest (e.g., `app@sha256:abc123...`) is an immutable fingerprint. The CI/CD pipeline scans the image, gets the digest, and injects that exact digest string into the deployment file. Production will only accept that exact cryptographic match.

**25. A base image (e.g., `node:14`) has a newly announced Critical CVE, but there is no patched version available yet. What is your mitigation strategy?**

**Answer:** If the CVE is in a tool inside the image that my application doesn't actually use (like `curl` or `bash`), I rewrite the Dockerfile to remove that tool entirely. If it's in a core library, I look for an alternative base OS (like switching from Ubuntu to Alpine Linux, which has a smaller attack surface). If neither works, I implement a "virtual patch" by putting a Web Application Firewall (WAF) rule in front of the application to block the attack pattern until the vendor releases a fix.

**26. How do you implement runtime security for containers (e.g., preventing a container from spawning a shell or accessing the host filesystem)?**

**Answer:** I use Kubernetes Pod Security Standards (PSS) or Open Policy Agent (OPA). In the deployment YAML, I set `allowPrivilegeEscalation` to `false` and `runAsNonRoot` to `true`. I also set `readOnlyRootFilesystem: true` so the application can't write to unexpected places. This ensures that even if a hacker breaks into the container, they are trapped in a read-only environment and cannot escalate their attack to the underlying AWS server.

**27. What are the inherent risks of using native CI/CD secret variables (like GitHub Actions Secrets or Jenkins Credentials) compared to a dedicated vault?**

**Answer:** Native secrets are often "static" (they don't expire unless manually rotated), lack detailed audit logs (you can't easily see exactly which pipeline accessed a secret), and can sometimes be leaked into pipeline logs if a script fails and dumps environment variables. A dedicated vault (like HashiCorp Vault) provides dynamic secrets (temporary passwords that auto-destroy), strict audit trails of every access, and centralized enterprise management.

**28. Walk me through the workflow of a pipeline securely retrieving a dynamic database credential from HashiCorp Vault or AWS Secrets Manager.**

**Answer:** The CI/CD runner authenticates to Vault using its own identity (like an AWS IAM role or a JWT token). Vault verifies the identity and checks if that specific pipeline is allowed to request a database password. Vault then generates a brand-new, temporary database password (valid for only 1 hour). The pipeline injects this temporary password into the application at runtime. When the hour is up, Vault automatically revokes the password, ensuring no stale credentials exist.

**29. How do you prevent developers from accidentally committing secrets (API keys) to Git, and how do you react if a secret is pushed?**

**Answer:** **Prevention:** I install pre-commit hooks (like GitGuardian or TruffleHog) locally on developer machines that scan code the moment they type `git commit`. **Reaction:** If a secret still gets pushed, the immediate response is not just deleting the code. Because Git retains history, the secret is still compromised. I immediately revoke/rotate that API key in the external system, rewrite the Git history using tools like `git-filter-repo` to remove the secret completely, and enforce branch protection rules to prevent direct pushes to the main branch.


**30. How do you securely pass secrets to an application running inside a Kubernetes Pod without writing them to disk?**

**Answer:** Instead of mounting K8s Secrets as files inside the container (which writes them to the virtual disk), I use the concept of "Inline Secrets" or integrate a Vault Agent sidecar. The Vault sidecar container runs alongside the application, fetches the secret into memory, and exposes it to the application as a temporary environment variable. The secret lives only in the container's RAM and never touches the underlying server's disk storage.

**31. What are the security risks of writing IaC (Terraform/Bicep), and how do you scan IaC templates *before* they provision infrastructure?**

**Answer:** The biggest risk is "Infrastructure Misconfiguration"—a developer might write a Terraform script that accidentally opens an AWS S3 bucket to the entire internet, or creates a database without encryption. I prevent this by integrating tools like Checkov or tfsec into the CI/CD pipeline. These tools read the Terraform code *before* the `terraform apply` command runs, look for violations against CIS benchmarks, and fail the pipeline if a misconfiguration is found.

**32. How do you securely manage and protect the Terraform State file in an AWS environment?**

**Answer:** The Terraform state file contains all the plain-text details of your infrastructure, including passwords and private IPs. I secure it by storing it in an AWS S3 bucket that has Server-Side Encryption (SSE) enabled. I enable S3 Versioning so if someone accidentally deletes the state, we can restore it. Finally, I enable DynamoDB State Locking so that if two developers run Terraform at the same time, the second one is blocked, preventing corrupted state files.

**33. Explain how you would use Terraform to enforce the principle of least privilege for an AWS IAM role used by a microservice.**

**Answer:** Instead of using an overly permissive AWS managed policy (like `AmazonS3FullAccess`), I write a custom Terraform IAM policy document. I explicitly list only the exact actions the app needs (e.g., `s3:GetObject` and `s3:PutObject`) and restrict the `resources` array to only the ARN (Amazon Resource Name) of the specific S3 bucket that microservice owns. If the microservice tries to access any other bucket, AWS will block it.

**34. How do you automate the rotation of infrastructure secrets (like database passwords) using IaC without causing downtime?**

**Answer:** IaC shouldn't directly rotate passwords; it manages the *permissions* to get them. I use AWS Secrets Manager (or Vault) to handle the actual rotation via a Lambda function that updates the DB password on a schedule. In my Terraform code, I simply ensure the application's IAM role has permission to read that secret. When the password rotates in the background, the application fetches the new password from Secrets Manager on its next startup or request, requiring zero infrastructure changes and zero downtime.

**35. Explain Policy-as-Code in simple terms. Why is it considered a mature step up from traditional security gates?**

**Answer:** Traditional security gates rely on a human checking a manual checklist before approving a deployment. Policy-as-Code replaces the human with a software rule (like OPA or Sentinel). If a developer writes code to create a public database, the policy code automatically rejects it before it ever reaches AWS. It is mature because software doesn't get tired, doesn't have biases, scales instantly across 100 teams, and provides 100% consistent enforcement.

**36. Give me a practical example of a policy you would write in OPA (Rego) or Terraform Sentinel for an AWS environment.**

**Answer:** *"Deny any AWS EC2 instance creation if the `associate_public_ip_address` is set to true, UNLESS the instance has a specific tag indicating it is a public load balancer."* This single piece of code ensures that no developer can accidentally spin up a server with a public IP address, completely eliminating a massive attack vector across the entire organization.

**37. How does Policy-as-Code integrate with a GitOps workflow?**

**Answer:** In GitOps, the Git repository is the single source of truth. When a developer submits a Pull Request to modify infrastructure, a pre-submit webhook triggers the Policy-as-Code engine (like OPA). The engine evaluates the proposed changes. If the policy fails, the PR is blocked and a comment is posted explaining the violation. The infrastructure is never deployed, and the Git repository remains in a secure, compliant state.

**38. Scenario: A SAST tool flags a critical SQL injection in a legacy monolith. Devs say it’s a false positive but can't fix it before the end-of-quarter release. As an L2 DevSecOps engineer, how do you handle this without compromising security or halting the business?**

**Answer:** This requires a risk-based, compensating control approach. 
1. **Verify:** I quickly review the code with the security team to confirm if it is truly a false positive.
2. **Mitigate:** If it's a real risk but can't be coded out, I implement a Web Application Firewall (WAF) rule specifically designed to block SQL injection patterns targeting that specific endpoint. 
3. **Monitor:** I ensure enhanced logging is turned on for that endpoint to detect any active exploitation attempts.
4. **Approve with SLA:** I approve an official security exception for this release *only* because the WAF neutralizes the threat, but I create a mandatory, high-priority Jira ticket that must be fixed in the very first sprint of the next quarter.
