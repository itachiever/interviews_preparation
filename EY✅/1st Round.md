# Questions:
1. Tell me about yourself, your skill set, experience, day-to-day activities, and responsibilities.

2. Apart from AKS, Key Vault, and Azure Monitor, what other Azure services have you worked with?

3. Have you worked only on CI/CD pipeline creation in GitHub Actions, or have you also managed self-hosted agents?

4. How do you integrate Snyk into Jenkins or GitHub Actions CI/CD pipelines?

5. What is the meaning of “code smells” in SonarQube reports?

6. Have you managed SonarQube servers or only integrated SonarQube into pipelines?

7. How would you secure a self-hosted SonarQube server?

8. What do you think about implementing SSO for SonarQube?

9. What is SQL Injection?

10. What is LDAP Injection?

11. How do you securely manage secrets/credentials in Terraform without exposing them in logs or repositories?

12. How does Terraform fetch secrets securely from HashiCorp Vault?

13. If a SAST tool missed a major vulnerability that later caused a production incident, what could be the possible reasons?

14. Do you know about Azure Front Door?

15. How would you secure AKS ingress and RBAC access from a networking and access-control perspective?

16. What Kubernetes security best practices would you implement for RBAC and ingress security?

17. Have you worked with Azure Blob Storage and Storage Accounts?

18. How would you securely connect an AKS application to Azure Blob Storage within the same VNET?

19. Do you know about Azure private endpoints and service endpoints?

20. Which endpoint type would you use to securely connect AKS to Blob Storage?

21. Do you know about VNET peering?

22. What is one important subnet/IP-related condition to keep in mind while configuring VNET peering?

23. How would you secure an AKS cluster in production?

24. Apart from RBAC, what networking and policy controls would you implement in AKS?

25. How would you secure Docker images used in AKS deployments?

26. What security best practices would you follow in a Dockerfile?

27. How would you scan Docker images for vulnerabilities?

28. Do you have any questions for me?

# Answers:


# 1. Tell me about yourself, your skill set, experience, day-to-day activities, and responsibilities.

### Answer

Hi, I'm NAME. I have around 4 years of experience in DevOps and DevSecOps engineering.

Currently, I am working as a DevSecOps Engineer at CURRENT COMPANY, supporting a fintech client in the payment processing domain. Prior to this, I worked as a DevOps Engineer at PREVIOUS COMPANY  for around 2.5 years.

My primary expertise is in CI/CD automation, Kubernetes, Docker, Jenkins, Terraform, GitLab, Azure, AWS, and DevSecOps tooling.

In my current role, I am responsible for:

* Building and maintaining Jenkins CI/CD pipelines
* Integrating security tools such as Fortify, SonarQube, Snyk, Dependency Check, and Trivy
* Managing Kubernetes deployments
* Supporting Azure AKS environments
* Infrastructure automation using Terraform
* Container image security scanning
* Release management and production deployments
* Monitoring using Prometheus, Grafana, ELK, and Azure Monitor

On a day-to-day basis, I work with developers, security teams, and infrastructure teams to ensure secure and reliable software delivery while maintaining compliance requirements.



# 2. Apart from AKS, Key Vault, and Azure Monitor, what other Azure services have you worked with?

### Answer

Apart from AKS, Azure Key Vault, and Azure Monitor, I have worked with:

### Compute

* Azure Virtual Machines
* VM Scale Sets (basic exposure)

### Networking

* Virtual Networks (VNET)
* Subnets
* NSGs
* Load Balancers
* Application Gateway
* Private Endpoints

### Storage

* Azure Storage Accounts
* Azure Blob Storage

### Identity

* Azure AD (Entra ID)
* Managed Identities
* RBAC

### Security

* Microsoft Defender for Cloud
* Azure Policy

### Monitoring

* Log Analytics Workspace
* Application Insights

In my projects, my involvement was primarily from a DevSecOps perspective rather than deep cloud administration.



# 3. Have you worked only on CI/CD pipeline creation in GitHub Actions, or have you also managed self-hosted agents?

### Answer

I have worked on both.

On the CI/CD side, I have created GitHub Actions workflows for:

* Build automation
* Security scanning
* Docker image creation
* Deployment automation

I have also worked with self-hosted runners.

My responsibilities included:

* Installing runners on Linux servers
* Registering runners with GitHub repositories or organizations
* Managing runner updates
* Troubleshooting runner failures
* Configuring network access and firewall rules
* Managing secrets required by the runners

In my primary project Jenkins was the main orchestration platform, but I also gained hands-on exposure to GitHub Actions and self-hosted runners.



# 4. How do you integrate Snyk into Jenkins or GitHub Actions CI/CD pipelines?

### Answer

The integration process is straightforward.

### Step 1: Create Snyk Account

Generate a Snyk API token.

### Step 2: Store Token Securely

Store the token in:

* Jenkins Credentials Store
* GitHub Secrets

### Step 3: Install Snyk CLI

```bash
npm install -g snyk
```

or use the Snyk Jenkins Plugin.

### Jenkins Example

```groovy
stage('Snyk Scan') {
  steps {
    withCredentials([string(credentialsId: 'snyk-token', variable: 'SNYK_TOKEN')]) {
      sh '''
      snyk auth $SNYK_TOKEN
      snyk test
      '''
    }
  }
}
```

### GitHub Actions Example

```yaml
- name: Snyk Scan
  run: snyk test
  env:
    SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
```

### What We Scan

* Open-source dependencies (SCA)
* Containers
* Infrastructure as Code
* Source code security

### Pipeline Gate

We can configure the pipeline to fail when:

* Critical vulnerabilities exist
* High vulnerabilities exceed threshold

This supports shift-left security practices.



# 5. What is the meaning of “Code Smells” in SonarQube reports?

### Answer

Code Smells are not security vulnerabilities.

They are indicators of poor coding practices that may impact:

* Maintainability
* Readability
* Scalability
* Reliability

Examples:

### Duplicate Code

Same logic repeated in multiple places.

### Long Methods

Large methods performing multiple responsibilities.

### Unused Variables

Variables declared but never used.

### Hardcoded Values

Configuration values directly written into code.

### Complex Conditions

Very large nested if-else statements.

Code smells help developers improve code quality before the application becomes difficult to maintain.



# 6. Have you managed SonarQube servers or only integrated SonarQube into pipelines?

### Answer

I have experience with both.

### Pipeline Integration

* Sonar Scanner integration
* Quality Gate validation
* Pull Request analysis
* Jenkins integration

### SonarQube Administration

I have supported:

* SonarQube upgrades
* Plugin management
* User and role management
* LDAP/SSO integration support
* Database connectivity validation
* Backup and maintenance activities

Although I was not a dedicated SonarQube administrator, I was involved in operational support and troubleshooting of the platform.



# 7. How would you secure a self-hosted SonarQube server?

### Answer

I would follow multiple security layers.

### Secure Communication

Enable HTTPS using TLS certificates.

### Strong Authentication

* Integrate with Azure AD or LDAP
* Disable anonymous access

### RBAC

Provide least-privilege access.

### Patch Management

Keep:

* SonarQube
* OS
* Plugins

updated regularly.

### Network Security

Restrict access using:

* Firewalls
* NSGs
* Internal networks

### Database Security

* Secure database credentials
* Encrypt communication

### Monitoring

Track:

* Login failures
* Audit logs
* Security events

### Backups

Perform regular backups for:

* Database
* Configuration
* Plugins



# 8. What do you think about implementing SSO for SonarQube?

### Answer

Implementing SSO is a security and operational best practice.

Benefits include:

### Centralized Authentication

Users log in through Azure AD or corporate identity providers.

### Improved User Experience

No separate credentials.

### Stronger Security

Supports:

* MFA
* Conditional Access
* Password Policies

### Easier User Management

When employees leave the organization, access is automatically revoked.

### Compliance

Provides centralized auditability and governance.

In enterprise environments, SonarQube should ideally be integrated with Azure AD or LDAP through SAML or OAuth-based SSO.



# 9. What is SQL Injection?

### Answer

SQL Injection is a web application attack where malicious SQL statements are inserted into application inputs and executed by the database.

### Example

Application query:

```sql
SELECT * FROM users
WHERE username='admin'
AND password='password'
```

Attacker enters:

```sql
' OR '1'='1
```

Result:

```sql
SELECT * FROM users
WHERE username='' OR '1'='1'
```

This may bypass authentication.

### Risks

* Unauthorized access
* Data theft
* Data modification
* Database compromise

### Prevention

* Parameterized queries
* Prepared statements
* Input validation
* Least privilege database accounts



# 10. What is LDAP Injection?

### Answer

LDAP Injection is similar to SQL Injection, but it targets LDAP directories such as Active Directory.

An attacker manipulates LDAP queries through application inputs.

### Example

Normal query:

```text
(uid=john)
```

Attacker input:

```text
*)(|(uid=*))
```

Modified query may return unauthorized records.

### Risks

* Authentication bypass
* User enumeration
* Unauthorized directory access
* Privilege escalation

### Prevention

* Input validation
* Escaping special LDAP characters
* Parameterized LDAP queries
* Least privilege access

### Real-world Context

Since many enterprise applications integrate with Active Directory, LDAP Injection can become a serious authentication and authorization risk if inputs are not properly sanitized.



# 11. How do you securely manage secrets/credentials in Terraform without exposing them in logs or repositories?

### Answer

In Terraform, secrets should never be hardcoded in `.tf` files, variables files, or source code repositories.

I typically follow these practices:

### 1. Use External Secret Managers

Store secrets in:

* Azure Key Vault
* HashiCorp Vault
* AWS Secrets Manager

instead of storing them inside Terraform code.



### 2. Use Environment Variables

Example:

```bash
export ARM_CLIENT_ID=xxxxx
export ARM_CLIENT_SECRET=xxxxx
```

Terraform automatically consumes them.



### 3. Use Sensitive Variables

```hcl
variable "db_password" {
  sensitive = true
}
```

This prevents accidental display in Terraform output.



### 4. Secure State Files

Terraform state files can contain secrets.

Store state remotely in:

* Azure Storage Account
* Terraform Cloud

Enable:

* Encryption at rest
* RBAC access
* Versioning



### 5. Restrict Logging

Avoid:

```bash
terraform plan -out=plan.out
```

being shared publicly.

Mask sensitive outputs in CI/CD pipelines.



### Real Project Example

In our project, we used HashiCorp Vault and Azure Key Vault for storing credentials. Jenkins pipelines fetched secrets dynamically during execution and passed them to Terraform without storing them in Git repositories.



# 12. How does Terraform fetch secrets securely from HashiCorp Vault?

### Answer

Terraform integrates directly with Vault through the Vault Provider.

### Step 1: Authenticate with Vault

Terraform first authenticates using:

* Token
* AppRole
* Kubernetes Authentication
* Azure Authentication

Example:

```hcl
provider "vault" {
  address = "https://vault.company.com"
}
```



### Step 2: Read Secret

```hcl
data "vault_kv_secret_v2" "db" {
  mount = "secret"
  name  = "database"
}
```



### Step 3: Consume Secret

```hcl
resource "azurerm_sql_server" "sql" {
  administrator_login_password =
    data.vault_kv_secret_v2.db.data["password"]
}
```



### Security Benefits

* No hardcoded passwords
* Dynamic secret retrieval
* Centralized secret rotation
* Audit trail available in Vault



### Real Project Example

In my current project, Vault stores application credentials, API tokens, and deployment secrets. Jenkins authenticates to Vault and retrieves secrets dynamically during pipeline execution.



# 13. If a SAST tool missed a major vulnerability that later caused a production incident, what could be the possible reasons?

### Answer

If a SAST tool misses a vulnerability, I would investigate several areas.



### 1. Incorrect Scan Configuration

The vulnerable code path may not have been included in the scan scope.

Example:

* Certain folders excluded
* Misconfigured rules



### 2. Policy Misconfiguration

The rule detecting that vulnerability may have been disabled.

Example:

* Severity threshold changed
* Custom policy applied



### 3. False Negative

No security scanner detects 100% of vulnerabilities.

The vulnerability may not have been covered by the scanning engine.



### 4. Suppression or Waiver

The vulnerability was detected but:

* Suppressed
* Marked as accepted risk
* Ignored during triage



### 5. New Vulnerability Introduced Later

Code may have changed after the scan.

Example:

```text
Scan → Code Change → Deployment
```

The vulnerability entered after the scan was completed.



### 6. Incomplete SDLC Coverage

Relying only on SAST is risky.

We should combine:

* SAST
* DAST
* SCA
* Container Scanning
* Manual Security Reviews



### RCA Approach

I would review:

* Scan configuration
* Scan logs
* Policies
* Suppression records
* Code changes
* Security exceptions

to identify why the vulnerability was missed.



# 14. Do you know about Azure Front Door?

### Answer

Yes.

Azure Front Door is Microsoft's global Layer-7 application delivery and web application protection service.

It sits at the edge and provides:

### Global Load Balancing

Routes users to the nearest healthy backend.



### Web Application Firewall (WAF)

Protects against:

* SQL Injection
* XSS
* OWASP Top 10 attacks



### SSL Offloading

Handles HTTPS termination.



### High Availability

Automatically redirects traffic if one region fails.



### Typical Flow

```text
User
 ↓
Azure Front Door
 ↓
Application Gateway / AKS
 ↓
Backend Application
```



### Banking Use Case

For internet-facing banking applications, Azure Front Door is commonly used for:

* Global traffic routing
* DDoS resilience
* WAF protection
* Disaster recovery



# 15. How would you secure AKS ingress and RBAC access from a networking and access-control perspective?

### Answer

AKS security requires both network controls and access controls.



### Network Security

#### Ingress Controller

Use:

* NGINX Ingress
* AGIC (Application Gateway Ingress Controller)

instead of exposing services directly.



#### TLS Encryption

All traffic must use HTTPS.



#### Network Policies

Control pod-to-pod communication.

Example:

```text
Frontend → Backend
Backend → Database

Allowed

Frontend → Database

Denied
```



#### Private Cluster

Use Private AKS whenever possible.

API Server remains inaccessible from public internet.



#### NSGs

Restrict inbound and outbound traffic.



### Access Security

#### RBAC

Grant minimum permissions.

Example:

```text
Developer
→ Read Pods

Platform Admin
→ Cluster Admin
```



#### Azure AD Integration

Authenticate users through Azure AD.



#### Managed Identities

Avoid storing service account secrets.



### Real Project Example

In our AKS deployments, we used ingress controllers, RBAC, TLS certificates, private networking, and restricted service communication using Kubernetes network policies.



# 16. What Kubernetes security best practices would you implement for RBAC and ingress security?

### Answer

### RBAC Best Practices

#### Least Privilege

Never grant cluster-admin unnecessarily.



#### Role-Based Access

Create dedicated:

* Roles
* ClusterRoles
* RoleBindings



#### Separate Service Accounts

Every application should have its own service account.



#### Audit Permissions

Review permissions regularly.



### Ingress Security

#### HTTPS Everywhere

Enable TLS certificates.



#### WAF Integration

Use:

* Azure Application Gateway WAF
* Azure Front Door WAF



#### Restrict Public Exposure

Expose only required services.



#### Rate Limiting

Protect against abuse and DoS attacks.



#### Network Policies

Restrict east-west traffic inside the cluster.



# 17. Have you worked with Azure Blob Storage and Storage Accounts?

### Answer

Yes.

I have worked with Azure Storage Accounts and Blob Storage mainly for:

### Artifact Storage

Storing:

* Build artifacts
* Backup files
* Logs



### Application Storage

Applications storing:

* Documents
* Reports
* Media files



### Terraform State Backend

Using Azure Storage Account as Terraform backend.



### Security Features Used

* Private Endpoints
* RBAC
* Storage Account Access Control
* Encryption at Rest



### Definition

Storage Account is the Azure resource.

Blob Storage is a service inside the Storage Account used for unstructured data.



# 18. How would you securely connect an AKS application to Azure Blob Storage within the same VNET?

### Answer

The recommended approach is:

### Step 1

Create a Storage Account.



### Step 2

Create a Private Endpoint.

This gives the Storage Account a private IP inside the VNET.



### Step 3

Disable Public Access.

Only private network traffic is allowed.



### Step 4

Use Managed Identity.

Avoid:

```text
Storage Keys
Connection Strings
```



### Step 5

Grant RBAC Permissions

Example:

```text
Storage Blob Data Contributor
```



### Flow

```text
AKS Pod
 ↓
Managed Identity
 ↓
Private Endpoint
 ↓
Blob Storage
```

No internet exposure.

No hardcoded credentials.



### Banking Environment

This is the preferred architecture because it satisfies security and compliance requirements.



# 19. Do you know about Azure Private Endpoints and Service Endpoints?

### Answer

Yes.

Both are used to securely connect Azure services.

However, they work differently.



### Service Endpoint

Extends VNET identity to Azure services.

Traffic remains on Microsoft's backbone network.

Service still has a public endpoint.

```text
VNET
 ↓
Service Endpoint
 ↓
Storage Account
```



### Private Endpoint

Creates a private IP inside the VNET.

Service becomes accessible privately.

```text
VNET
 ↓
Private IP
 ↓
Storage Account
```

No public access required.



### Security Comparison

Private Endpoint is more secure because:

* No public exposure
* Private IP communication
* Better compliance posture



# 20. Which endpoint type would you use to securely connect AKS to Blob Storage?

### Answer

I would use **Private Endpoint**.

### Why?

Because:

* Traffic stays completely private
* Storage account can disable public access
* Communication occurs through private IP
* Better security and compliance
* Preferred architecture for banking and financial workloads

### Architecture

```text
AKS Pod
 ↓
Private Endpoint
 ↓
Azure Blob Storage
```

### Additional Controls

Along with Private Endpoint, I would also use:

* Managed Identity
* RBAC
* NSGs
* Private DNS Zone

to achieve a fully secure connectivity model.




## 21. Do you know about VNET Peering?

### Answer:

Yes. **VNET Peering** is an Azure networking feature that allows two or more Virtual Networks to communicate with each other over Microsoft's private backbone network without traversing the public internet.

### Why do we use it?

* Connect applications hosted in different VNets.
* Enable communication between AKS, databases, storage, and shared services.
* Reduce latency.
* Improve security by avoiding internet exposure.

### Example:

In a banking project:

* AKS Cluster → VNET-A
* Azure SQL Database → VNET-B
* Shared Services → VNET-C

Using VNET Peering, AKS can securely communicate with databases and internal services.

### Interview One-Liner:

> "VNET Peering allows private communication between Azure Virtual Networks using Microsoft's backbone network without requiring VPNs or public internet connectivity."



# 22. What is one important subnet/IP-related condition to keep in mind while configuring VNET Peering?

### Answer:

The most important condition is:

### IP Address Ranges Must Not Overlap

Example:

✅ Valid

VNET-1 → 10.0.0.0/16

VNET-2 → 10.1.0.0/16

❌ Invalid

VNET-1 → 10.0.0.0/16

VNET-2 → 10.0.0.0/24

Because Azure cannot determine routing properly when address spaces overlap.

### Interview One-Liner:

> "The primary requirement for VNET Peering is that the CIDR ranges of both VNets must not overlap."



# 23. How would you secure an AKS cluster in production?

### Answer:

AKS security is implemented in multiple layers.

### 1. Identity & Access Security

* Azure AD Integration
* Kubernetes RBAC
* Least Privilege Access
* Separate Admin and Developer Roles

Example:

Developers → Read-only

DevOps Team → Deploy permissions

Cluster Admin → Full control



### 2. Network Security

* Private AKS Cluster
* NSGs
* Network Policies
* Private Endpoints
* Restricted API Server Access



### 3. Container Security

* Scan Images before deployment
* Use trusted ACR registry
* Block vulnerable images
* Use signed images

Tools:

* Trivy
* Snyk
* Microsoft Defender



### 4. Secrets Security

* Azure Key Vault
* CSI Driver Integration
* Avoid hardcoded credentials



### 5. Pod Security

* Run as non-root
* Read-only filesystem
* Drop Linux capabilities
* Resource limits



### 6. Monitoring & Auditing

* Azure Monitor
* Log Analytics
* Defender for Cloud
* Kubernetes Audit Logs



### Real Project Mapping

At TalaKunchi:

* AKS RBAC implemented
* Azure Key Vault integration
* Trivy image scanning
* Kong Ingress
* Azure Monitor logging
* Terraform-based cluster deployment

### Interview One-Liner

> "To secure AKS in production I focus on RBAC, network policies, private endpoints, image scanning, Key Vault integration, pod security standards, and continuous monitoring through Azure Monitor and Defender for Cloud."



# 24. Apart from RBAC, what networking and policy controls would you implement in AKS?

### Answer:

### Network Policies

Control pod-to-pod communication.

Example:

Frontend Pod → Backend Pod

Backend Pod → Database Pod

Frontend → Database ❌ Blocked



### NSGs

Control traffic entering cluster subnets.

Example:

Allow HTTPS

Block unwanted ports



### Private Cluster

Disable public API access.



### Ingress Restrictions

Allow only approved traffic through:

* NGINX Ingress
* Application Gateway
* Kong Ingress



### Pod Security Standards

Prevent:

* Privileged containers
* Host network access
* Host path mounts



### Azure Policies

Enforce governance automatically.

Example:

* Only approved images
* No public services
* Resource tagging mandatory

### Interview One-Liner

> "Beyond RBAC, I implement network policies, NSGs, private clusters, pod security standards, Azure Policies, and ingress restrictions to achieve defense-in-depth security."



# 25. How would you secure Docker images used in AKS deployments?

### Answer:

Security starts during image creation.

### Step 1: Use Trusted Base Images

Good:

```dockerfile
FROM python:3.12-alpine
```

Avoid:

```dockerfile
FROM ubuntu:latest
```



### Step 2: Keep Images Minimal

Use:

* Alpine
* Distroless

Reduce attack surface.



### Step 3: Scan Images

Tools:

* Trivy
* Snyk
* Defender for Containers

Pipeline Stage:

```bash
trivy image myapp:v1
```



### Step 4: Remove Secrets

Never include:

* Passwords
* Tokens
* Certificates

Inside images.



### Step 5: Sign Images

Use:

* Cosign
* Notary

Verify authenticity.



### Step 6: Store in Secure Registry

Example:

Azure Container Registry (ACR)

With:

* RBAC
* Private Endpoints
* Image Scanning

### Interview One-Liner

> "I secure Docker images using trusted minimal base images, image scanning, secret-free builds, signed images, and secure storage in ACR."



# 26. What security best practices would you follow in a Dockerfile?

### Answer:

### Run as Non-Root User

```dockerfile
RUN adduser appuser
USER appuser
```



### Use Multi-Stage Builds

```dockerfile
FROM maven AS build

FROM openjdk:17-jre
```

Final image contains only runtime artifacts.



### Use Lightweight Images

Examples:

* Alpine
* Distroless



### Avoid Hardcoded Secrets

Bad:

```dockerfile
ENV DB_PASSWORD=admin123
```

Good:

Inject through:

* Kubernetes Secret
* Key Vault



### Minimize Packages

Install only required dependencies.



### Pin Versions

Bad:

```dockerfile
FROM node:latest
```

Good:

```dockerfile
FROM node:20.10
```

### Interview One-Liner

> "I follow Docker hardening practices such as multi-stage builds, non-root users, minimal base images, version pinning, and externalized secrets."



# 27. How would you scan Docker images for vulnerabilities?

### Answer:

Scanning should happen inside CI/CD before deployment.

### Using Trivy

```bash
trivy image myapp:v1
```

Checks:

* OS vulnerabilities
* Package vulnerabilities
* Misconfigurations



### Using Snyk

```bash
snyk container test myapp:v1
```

Provides:

* CVEs
* Severity
* Fix recommendations



### Azure Native

Microsoft Defender for Containers

Scans:

* AKS
* ACR Images

Continuously.



### Jenkins Example

```groovy
stage('Image Scan') {
    steps {
        sh 'trivy image myapp:v1'
    }
}
```

Fail build if:

* Critical vulnerabilities > 0

### Real Project Mapping

At TalaKunchi:

* Trivy integrated into Jenkins
* Reports generated automatically
* Critical findings blocked deployments

### Interview One-Liner

> "I integrate Trivy or Snyk into Jenkins pipelines to scan images before deployment and fail the build when critical vulnerabilities are detected."



# 28. Do you have any questions for me?

Always ask 2-3 professional questions.

### Option 1

> "Can you please share more about the project architecture and how the DevSecOps team is currently structured?"



### Option 2

> "Which Azure services are heavily used in the project apart from AKS?"



### Option 3

> "What are the key challenges the team is trying to solve currently from a DevSecOps or security perspective?"



### Option 4

> "How mature is the CI/CD and DevSecOps adoption in the project today?"



### Option 5

> "What would success look like for this role in the first 6 months?"

These are strong client-round answers and align well with your actual DevSecOps + AKS + Jenkins + Security experience without sounding exaggerated.

