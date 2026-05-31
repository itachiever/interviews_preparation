


---

# 1. Tell me about yourself, your skill set, experience, day-to-day activities, and responsibilities.

### Answer

Hi, I'm NAME. I have around 4 years of experience in DevOps and DevSecOps engineering.

Currently, I am working as a DevSecOps Engineer at COMPANY, supporting a fintech client in the payment processing domain. Prior to this, I worked as a DevOps Engineer at PREVIOUS COMPANY  for around 2.5 years.

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

These answers are at the level expected for an EY/Azure DevSecOps client interview and are aligned with your current experience rather than sounding overly theoretical.
