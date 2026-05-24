# FINAL PREPARATION PLAN BEFORE INTERVIEW
Revise These 10 Things
- Self introduction
- Project architecture
- Jenkins pipeline flow
- Security integrations
- Kubernetes deployment flow
- Rollback process
- Secrets management flow
- Artifact lifecycle
- Production troubleshooting
- Your exact responsibilities

## Self introduction:

“Hi, thank you for the opportunity.

My name is (NAME), and currently I’m working as a DevSecOps Engineer at (CURRENT COMPANY NAME), where I’m deployed to the client side at (CLIENT NAME), which is a fintech organization providing payment gateway solutions for banking clients.

Overall, I have around 4 years of experience across DevOps and DevSecOps domains.

In my current role, I primarily work on DevSecOps tooling integration, CI/CD security enablement, vulnerability management, and deployment automation support.

Our environment is a hybrid setup where some applications are VM-based and some are Kubernetes-based microservices deployments.

We mainly use Jenkins for CI/CD, GitLab for source code management, Nexus for artifact management, Fortify for SAST and DAST, Sonatype Lifecycle for SCA and SBOM management, and Trivy for container image scanning.

My responsibilities include integrating these security tools into CI/CD pipelines, implementing security gates, onboarding applications, supporting developers in remediation activities, managing vulnerability governance workflows, and working on automation improvements around DevSecOps processes.

I’m also involved in deployment workflows, artifact promotion processes, rollback handling, secrets management integrations using Vault, and monitoring activities using Prometheus and Grafana.

Before this, I worked at (PREVIOUS COMPANY NAME), where I was mainly involved in CI/CD support, automation, deployment coordination, monitoring, and operational activities.

Technically, I’m comfortable with Jenkins, GitLab CI, Docker, Kubernetes basics, Terraform fundamentals, security tooling integrations, Linux, scripting, and DevSecOps workflows.

Currently, I’m looking for an opportunity where I can work on larger enterprise DevSecOps environments, improve my cloud and automation exposure further, and contribute more towards secure CI/CD and platform engineering initiatives.”


## Project Archirecture & Day to day activities:

“Currently, I’m working on a fintech client environment called (CLIENT NAME), where they provide payment gateway and financial transaction solutions for banking clients.

The environment is a hybrid architecture where some applications are traditional VM-based deployments and some are Kubernetes-based microservices applications.

Overall, the organization has around 60 to 80 applications, mostly Java-based services along with Python, Node.js, C/C++, and some mobile applications.

From CI/CD perspective, developers push code into GitLab repositories. Jenkins is used as the central CI/CD orchestration platform.

Once code is committed, Jenkins pipelines trigger automatically.

The pipeline flow generally starts with:

source code checkout,
dependency installation,
application build using Maven/Gradle/npm,
followed by code quality and security validations.

For code quality, we use SonarQube.

For security:

Fortify is used for SAST,
WebInspect for DAST,
Sonatype Lifecycle for SCA/SBOM,
and Trivy for container image scanning.

We implemented security gates in pipelines where builds can fail automatically if critical or high vulnerabilities cross the defined thresholds.

Once scans are successful, artifacts like JARs, WARs, or Docker images are generated and pushed into Nexus Repository.

For containerized applications, Docker images are built and stored in the registry after vulnerability validation and integrity verification.

Deployment-wise:

VM-based applications are deployed using Ansible-driven deployments,
Kubernetes applications are deployed using Kubernetes manifests and rolling update strategy.

Environments mainly include:

DEV,
SIT,
UAT,
and PROD.

Production deployments are approval-based.

Usually deployment approvals happen after:

UAT validation,
security clearance,
and release approvals from respective stakeholders.

Secrets and credentials are managed through Jenkins Credentials Manager and recently through HashiCorp Vault integrations, where pipelines fetch secrets dynamically during runtime instead of hardcoding them.

Monitoring and observability are handled using Prometheus, Grafana, ELK Stack, and some cloud-native monitoring integrations.

For Kubernetes deployments, we mainly use rolling update strategy to minimize downtime, and if deployment issues occur, rollback is done either through Kubernetes rollout undo or by redeploying the previously stable artifact version from Nexus.

My day-to-day activities mainly include:

integrating security tools into pipelines,
onboarding new applications,
troubleshooting pipeline failures,
vulnerability management and remediation coordination,
supporting developers on security findings,
maintaining Jenkins jobs,
handling scan failures,
improving automation workflows,
deployment coordination support,
and working on DevSecOps enhancement POCs.

I also interact regularly with developers, infrastructure teams, security teams, and release stakeholders for deployment planning, vulnerability discussions, and production support activities.”


## Jenkins  pipeline flow:

“Currently in our project Jenkins is the primary CI/CD orchestration tool. We use mostly declarative pipelines along with shared libraries for standardization across applications.

The overall pipeline flow starts when developer pushes code into GitLab repository or manually triggers build for release branches.

The stages are generally like this:

1. **Code Checkout**
   Jenkins pulls source code from GitLab using secured credentials.

2. **Build Stage**
   Based on application type:

   * Maven/Gradle for Java
   * npm for NodeJS
   * gcc/g++ for C/C++
   * Python packaging for Python apps

3. **Code Quality & Security Scans**
   Here we integrated:

   * SonarQube for code quality
   * Fortify SAST for source code vulnerabilities
   * Sonatype Lifecycle for SCA/SBOM
   * GitLeaks for secret detection
   * Trivy for container image scanning

   We configured quality gates and policy thresholds.
   If critical vulnerabilities exceed threshold, pipeline fails automatically.

4. **Artifact Creation**
   After successful scans:

   * JAR/WAR/binaries are generated
   * Docker image is built if containerized app

5. **Artifact Signing & Storage**
   Artifacts/images are pushed into Nexus repository.
   We also use Cosign for image signing to ensure integrity verification before deployment.

6. **Deployment Stage**
   Depending on application:

   * VM deployments happen through Ansible playbooks
   * Kubernetes deployments use kubectl/Helm-based rollout

7. **Environment Promotion Flow**
   Usually:
   DEV → SIT → UAT → PROD

   Lower environments are mostly automated.
   For PROD, manual approval gates are enabled in Jenkins.

8. **Secrets Handling**
   Secrets are never hardcoded.
   Jenkins credentials and HashiCorp Vault are used for runtime secret retrieval.

9. **Monitoring & Notifications**
   After deployment:

   * Prometheus/Grafana monitor application health
   * Logs go to ELK
   * Notifications sent through mail/Teams.

10. **Rollback Strategy**
    If deployment fails:

* Kubernetes rollout undo or previous image deployment
* For VM deployments, previous stable artifact redeployed through Ansible.

My role was mainly:

* integrating security tools into pipelines,
* maintaining pipeline workflows,
* configuring security gates,
* onboarding applications,
* troubleshooting failures,
* and coordinating with developers/security teams during remediation.”

## Security integrations

“In our project, security integrations were one of the major responsibilities handled by me as part of DevSecOps implementation.

We followed a shift-left security approach where security checks were integrated directly into Jenkins CI/CD pipelines instead of performing scans only before production release.

The major security integrations we implemented were:

1. **Fortify SAST**
   Integrated during build stage.
   Source code gets scanned for vulnerabilities like SQL injection, XSS, hardcoded secrets, insecure APIs, etc.

2. **Fortify DAST / WebInspect**
   Used mainly for runtime and API security testing in SIT/UAT environments after deployment.

3. **Sonatype Lifecycle (SCA/SBOM)**
   Used for third-party dependency analysis.
   It checks vulnerable open-source packages, CVEs, license risks, and generates SBOM reports.

4. **Trivy Image Scanning**
   Docker images were scanned before pushing into registry.
   It detects OS-level vulnerabilities and package-level issues.

5. **SonarQube**
   Used for code quality, code smells, bugs, and security hotspot analysis.

6. **GitLeaks**
   Used for secret detection to identify accidentally committed passwords, tokens, or keys.

We implemented policy-based quality gates:

* If critical/high vulnerabilities exceed threshold,
* pipeline automatically fails,
* artifact promotion gets blocked.

All reports were centralized into dashboards like:

* Fortify SSC,
* Sonatype IQ,
* SonarQube dashboards.

We also worked with developers for:

* remediation guidance,
* false positive handling,
* suppression management,
* and secure coding awareness sessions.

My responsibility was mainly:

* tool setup/configuration,
* Jenkins integration,
* plugin/API integration,
* scan automation,
* troubleshooting scan failures,
* and coordinating remediation workflows with development teams.”


## Kubernetes deployment flow

“In our project, Kubernetes deployments were mainly used for containerized microservices-based applications.

The deployment flow starts after successful CI stages in Jenkins.

1. **Docker Image Build**
   Jenkins builds the Docker image using application Dockerfile.

2. **Image Security Scan**
   Before deployment, Trivy scans the image for OS and package vulnerabilities.
   If critical vulnerabilities exceed threshold, deployment gets blocked.

3. **Image Push to Registry**
   After validation, image is tagged with build version and pushed into Nexus/GitLab Registry.

4. **Image Signing**
   We also implemented Cosign-based image signing for integrity validation.

5. **Deployment Trigger**
   Jenkins triggers Kubernetes deployment using:

   * kubectl commands
   * or Helm charts depending on application.

6. **Manifest/Helm Update**
   Deployment YAML or Helm values are updated with latest image tag.

7. **Deployment into Cluster**
   Application gets deployed into corresponding namespace:

   * DEV
   * SIT
   * UAT
   * PROD

8. **Rolling Update Strategy**
   We mainly use rolling deployment strategy:

   * new pods come up gradually,
   * old pods terminate slowly,
   * ensuring minimum downtime.

9. **Health Checks**
   Kubernetes readiness/liveness probes validate pod health before traffic routing.

10. **Ingress & Service Exposure**
    Applications are exposed internally through ClusterIP and externally through Ingress/load balancer based on requirement.

11. **Monitoring & Validation**
    After deployment:

* kubectl get pods/logs checked,
* Prometheus/Grafana monitor health,
* ELK used for logs.

12. **Rollback Handling**
    If deployment fails:

* kubectl rollout undo
* or redeploy previous stable image version.

My involvement was mainly:

* pipeline integration,
* deployment automation,
* security scanning integration,
* troubleshooting failed deployments,
* coordinating with developers,
* and validating deployment health after release.”


## Rollback process


“In our project rollback process was designed to quickly restore the last stable version if deployment failed or application health degraded.

For Kubernetes-based deployments:

1. Jenkins deploys new image using rolling update strategy.
2. Kubernetes gradually replaces old pods with new pods.
3. During deployment we monitor:

   * pod health,
   * readiness/liveness probes,
   * application logs,
   * and monitoring dashboards.

If issues occur like:

* pod crash,
* application errors,
* failed health checks,
* or performance degradation,

then rollback is triggered.

We mainly use:

```bash
kubectl rollout undo deployment/<deployment-name> -n <namespace>
```

This automatically restores previous stable ReplicaSet and image version.

In some cases Jenkins pipeline itself supports rollback parameter where previous stable image tag from Nexus is redeployed automatically.

For VM-based deployments:

* artifacts are versioned in Nexus,
* Ansible playbooks redeploy previous stable artifact version,
* configuration backup and previous release references are maintained.

In our multi-DC deployments:

* deployment happens sequentially,
* if DC2 fails after DC1 success,
* rollback automatically reverts updated sites to last known-good version.

Before rollback completion we validate:

* application accessibility,
* logs,
* health endpoints,
* and monitoring metrics.

My role was mainly:

* validating deployment health,
* troubleshooting failures,
* triggering rollback if needed,
* coordinating with application teams,
* and performing RCA after stabilization.”


## Secrets management flow

“In our project, secrets management was handled securely to avoid hardcoding credentials inside pipelines, scripts, or deployment files.

Initially we were using Jenkins Credentials Manager for storing:

* GitLab tokens,
* Nexus credentials,
* SSH keys,
* API tokens,
* and deployment passwords.

Later we started adopting HashiCorp Vault for centralized secrets management.

The overall flow was like this:

1. Secrets are securely stored inside Vault under specific paths and policies.
   Example:

```bash id="8ct2qb"
secret/dev/db-password
secret/prod/api-key
```

2. Access policies and RBAC are configured so only authorized pipelines or users can access required secrets.

3. Jenkins authenticates with Vault using:

* token authentication,
* AppRole,
* or Vault plugin integration.

4. During pipeline runtime, Jenkins dynamically fetches secrets from Vault.

Example flow:

```groovy id="iqvbce"
withVault(...) {
   env.DB_PASSWORD
}
```

5. Secrets are injected temporarily as environment variables during execution.
   They are never stored permanently in logs or source code.

6. For Kubernetes deployments:

* secrets are passed securely into Kubernetes Secrets,
* mounted as environment variables or volumes inside pods.

7. Rotation and updates become easier because credentials are centrally managed in Vault instead of modifying pipelines everywhere.

8. Audit logging in Vault helps track:

* who accessed secrets,
* when accessed,
* and from which system.

My role was mainly:

* integrating Vault with Jenkins pipelines,
* configuring secret retrieval flow,
* migrating hardcoded/static credentials,
* troubleshooting authentication/access issues,
* and coordinating secure access management with teams.”

## Artifact lifecycle

“In our project, artifact lifecycle starts from code commit and continues till production deployment and rollback management.

1. **Code Commit**
   Developer pushes code into GitLab repository.

2. **CI Pipeline Trigger**
   Jenkins pipeline gets triggered automatically.

3. **Build Stage**
   Application is built using:

   * Maven/Gradle,
   * npm,
   * Python packaging,
     depending on tech stack.

4. **Security & Quality Validation**
   Before artifact creation we run:

   * SonarQube,
   * Fortify SAST,
   * Sonatype SCA/SBOM,
   * GitLeaks,
   * Trivy for container images.

   If policy violations exceed threshold, artifact promotion stops.

5. **Artifact Packaging**
   Output artifacts may be:

   * JAR/WAR,
   * binaries,
   * Docker images.

6. **Versioning & Tagging**
   Artifacts are tagged with:

   * build number,
   * release version,
   * Git commit reference.

7. **Artifact Signing**
   We use Cosign for image/artifact signing to ensure integrity and authenticity.

8. **Storage in Nexus**
   Validated artifacts are pushed into Nexus Repository Manager.

9. **Environment Promotion**
   Same approved artifact moves across:
   DEV → SIT → UAT → PROD

   We avoid rebuilding artifact for every environment to maintain consistency.

10. **Deployment**

* VM deployments use Ansible + Nexus artifacts
* Kubernetes deployments use signed Docker images from registry.

11. **Verification Before Deployment**
    Deployment pipelines verify:

* artifact version,
* signature,
* vulnerability compliance,
  before deployment execution.

12. **Retention & Cleanup**
    Old artifacts are maintained based on retention policies for rollback and audit purposes.

13. **Rollback Support**
    Previous stable artifact versions remain available in Nexus for quick rollback during failures.

My role was mainly:

* integrating artifact flow into Jenkins,
* configuring security validation gates,
* managing artifact promotion workflows,
* supporting signing/verification,
* and troubleshooting deployment or repository issues.”


## Production troubleshooting

“In production troubleshooting, first priority is always service restoration and minimizing business impact before deep RCA.

My usual approach is:

1. **Identify the Scope**

* Is issue application-level, infrastructure-level, database-level, or deployment-related?
* Check whether all users are affected or only specific services.

2. **Check Recent Changes**

* Recent deployments,
* configuration changes,
* new image/artifact versions,
* infra modifications,
* or security policy updates.

3. **Validate Deployment Health**
   For Kubernetes:

```bash id="mnv64e"
kubectl get pods -A
kubectl describe pod <pod>
kubectl logs <pod>
```

Check:

* CrashLoopBackOff,
* image pull errors,
* readiness/liveness failures,
* resource issues.

For VM deployments:

* service status,
* process status,
* server logs,
* disk/memory usage.

4. **Check CI/CD & Deployment Logs**

* Jenkins logs,
* deployment stages,
* failed scripts,
* Ansible output,
* rollback status.

5. **Monitoring & Metrics Analysis**
   Using:

* Prometheus,
* Grafana,
* ELK,
* application dashboards.

Check:

* CPU/memory spikes,
* latency,
* error rates,
* failed requests,
* abnormal traffic.

6. **Dependency Validation**
   Verify:

* DB connectivity,
* Vault secret access,
* external APIs,
* DNS/network connectivity,
* load balancer health.

7. **Immediate Mitigation**
   If impact is high:

* rollback to previous stable version,
* scale pods,
* restart failed services,
* disable problematic release.

8. **Root Cause Analysis**
   After stabilization:

* analyze logs,
* identify exact failure point,
* document RCA,
* coordinate with development/security/infra teams.

9. **Preventive Actions**

* improve monitoring,
* add alerts,
* strengthen pipeline validations,
* automate checks,
* update runbooks.

My role was mainly:

* initial deployment validation,
* troubleshooting pipeline/deployment failures,
* coordinating with app teams,
* analyzing logs/monitoring,
* and supporting rollback and RCA activities.”



# Python Scripts

## Python API call:

In DevOps/DevSecOps, we use Python API automation for integrating tools like Jenkins, SonarQube, Jira, Kubernetes, or cloud platforms. This script demonstrates how to send a GET request to an API, validate response status, parse JSON output, and extract required information programmatically.

import requests

# API endpoint
url = "https://jsonplaceholder.typicode.com/posts/1"

# Send GET request
response = requests.get(url)

# Check response status
if response.status_code == 200:

    # Convert response into JSON format
    data = response.json()

    print("API Call Successful")
    print("Title:", data["title"])
    print("Body:", data["body"])

else:
    print("Failed to fetch data")
    print("Status Code:", response.status_code)

    
