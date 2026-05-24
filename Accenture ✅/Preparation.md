# Self introduction:

“Hi, thank you for the opportunity.

My name is Yuvaraju Sai Kumar, and currently I’m working as a DevSecOps Engineer at TalaKunchi Networks, where I’m deployed to the client side at ISG, which is a fintech organization providing payment gateway solutions for banking clients.

Overall, I have around 4 years of experience across DevOps and DevSecOps domains.

In my current role, I primarily work on DevSecOps tooling integration, CI/CD security enablement, vulnerability management, and deployment automation support.

Our environment is a hybrid setup where some applications are VM-based and some are Kubernetes-based microservices deployments.

We mainly use Jenkins for CI/CD, GitLab for source code management, Nexus for artifact management, Fortify for SAST and DAST, Sonatype Lifecycle for SCA and SBOM management, and Trivy for container image scanning.

My responsibilities include integrating these security tools into CI/CD pipelines, implementing security gates, onboarding applications, supporting developers in remediation activities, managing vulnerability governance workflows, and working on automation improvements around DevSecOps processes.

I’m also involved in deployment workflows, artifact promotion processes, rollback handling, secrets management integrations using Vault, and monitoring activities using Prometheus and Grafana.

Before this, I worked at TCS, where I was mainly involved in CI/CD support, automation, deployment coordination, monitoring, and operational activities.

Technically, I’m comfortable with Jenkins, GitLab CI, Docker, Kubernetes basics, Terraform fundamentals, security tooling integrations, Linux, scripting, and DevSecOps workflows.

Currently, I’m looking for an opportunity where I can work on larger enterprise DevSecOps environments, improve my cloud and automation exposure further, and contribute more towards secure CI/CD and platform engineering initiatives.”

# Project Archirecture & Day to day activities:
“Currently, I’m working on a fintech client environment called ISG, where they provide payment gateway and financial transaction solutions for banking clients.

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
