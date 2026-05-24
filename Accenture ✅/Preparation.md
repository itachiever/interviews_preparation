
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
