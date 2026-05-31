# Questions:

1. Introduce yourself, your experience, technologies, domains, daily activities, recent challenges, and achievements.

2. Which cloud platforms are you comfortable with?

3. Explain how you would design and deploy a PCI-DSS compliant three-tier web application on AWS, including AWS services, Well-Architected Framework considerations, CI/CD approach, infrastructure setup, deployment, and monitoring.

4. What application and infrastructure requirements would you gather before planning and deploying the infrastructure?

5. How would you deploy the infrastructure using Terraform?

6. Have you worked on Terraform provisioners? What are the types of provisioners, and in what scenarios would you use file provisioners?

7. How would you copy files from a local machine to a newly provisioned EC2 instance using Terraform?

8. How would you establish communication between two VPCs in different AWS accounts within the same region?

9. What could cause a VPC peering request to fail?

10. If two VPCs have overlapping CIDR ranges and cannot be modified, what alternative solution would you use instead of VPC peering?

11. Why do we use Transit Gateway, what challenges does it solve compared to VPC peering, and can VPC peering be transitive?

12. How would you establish communication between VPCs when direct transitive communication is not possible?

13. How would you provide secure outbound internet access from workloads running in a private subnet?

14. Where would you provision a NAT Gateway, what route table changes are required, and which route tables must be modified?

15. Have you worked on Terraform modules?

16. What is the purpose of a null_resource in Terraform?

17. If you have petabytes of data in S3 with unpredictable access patterns, which S3 storage tier would you choose and why? Have you implemented it in production?

18. How would you deploy changes only to odd-numbered VMs using Terraform?

19. How would you configure Terraform remote state storage in AWS?

20. Do we still need DynamoDB for Terraform state locking, and what recent changes have been introduced regarding state locking?

21. Which AWS native service would you use to scan AMIs, installed packages, and libraries for vulnerabilities?

22. How did you implement sensitive data masking, scrubbing, and secret management in your PCI-DSS CI/CD pipelines?

23. If an EC2 instance in an Auto Scaling Group is unhealthy, how would you remove it from service, troubleshoot it, and add it back?

24. What happens when an instance is placed in Standby mode in an Auto Scaling Group?

25. What are Auto Scaling lifecycle hooks and what are they used for?

26. In Terraform, how would you ensure a new instance is created before the old instance is destroyed?

27. What types of VPN connectivity have you worked on?

28. What AWS services must be provisioned to establish a Site-to-Site VPN connection?

29. Have you worked with Virtual Private Gateway (VGW) and Customer Gateway (CGW)? What is a Customer Gateway in AWS?

30. Have you personally deployed VPN connectivity, or was it managed by a separate networking team?



# Answers:


## 1. Introduce yourself, your experience, technologies, domains, daily activities, recent challenges, and achievements.

**Answer:**

My name is Yuvaraju Sai Kumar Dasari, and I have around 4+ years of experience in DevOps and DevSecOps engineering.

I started my career at TCS as a DevOps Engineer, where I worked for around 2.5 years supporting the NSWS project. My responsibilities included CI/CD automation, Kubernetes deployments, AWS infrastructure provisioning using Terraform, monitoring, and release management.

Currently, I am working as a DevSecOps & Cloud Infrastructure Engineer at TalaKunchi Networks, supporting a fintech client that operates in a PCI-DSS compliant environment. My primary focus is integrating security into the SDLC and CI/CD pipelines while managing cloud and on-prem infrastructure.

My key technical expertise includes:

* CI/CD: Jenkins, GitLab CI, GitHub Actions
* Containers: Docker, Kubernetes, Helm
* Cloud: AWS, Azure AKS
* Infrastructure as Code: Terraform, Ansible
* Security: Fortify, SonarQube, Snyk, Trivy, GitLeaks, OWASP Dependency Check
* Monitoring: Prometheus, Grafana, ELK Stack
* Scripting: Python, Bash, Shell

My day-to-day activities include:

* Managing CI/CD pipelines
* Security tool integration and onboarding
* Kubernetes deployments
* Infrastructure provisioning using Terraform
* Vulnerability management and remediation tracking
* Supporting releases and production deployments
* Collaborating with developers, security teams, and infrastructure teams

One of the recent challenges was implementing a secure DevSecOps platform for a PCI-DSS compliant fintech environment. We integrated SAST, DAST, SCA, SBOM generation, secret scanning, RBAC, SSO, and secure deployment workflows across multiple environments.

One of my achievements was successfully strengthening the organization's DevSecOps posture and helping meet compliance requirements, for which I received client appreciation and internal recognition.

---

# 2. Which cloud platforms are you comfortable with?

**Answer:**

My primary cloud expertise is in AWS, where I have hands-on experience with services such as:

* EC2
* VPC
* EKS
* RDS
* S3
* IAM
* CloudWatch
* Route 53
* Load Balancers
* Auto Scaling Groups
* Secrets Manager

I also have hands-on experience with Azure, particularly:

* AKS
* Azure Key Vault
* Azure Monitor
* Virtual Networks
* Blob Storage

In my current project, we operate in a hybrid setup where on-prem infrastructure communicates securely with Azure AKS through Site-to-Site VPN connectivity.

I also have basic exposure to GCP.

---

# 3. Explain how you would design and deploy a PCI-DSS compliant three-tier web application on AWS, including AWS services, Well-Architected Framework considerations, CI/CD approach, infrastructure setup, deployment, and monitoring.

**Answer:**

For a PCI-DSS compliant three-tier application, I would divide the architecture into:

### Web Layer

* Route 53 for DNS
* CloudFront for content delivery
* AWS WAF for web security
* Application Load Balancer

### Application Layer

* EC2 Auto Scaling Group or EKS
* Private subnets
* IAM Roles
* Security Groups

### Database Layer

* Amazon RDS Multi-AZ deployment
* Encryption at rest using KMS
* Automated backups

### Network Design

* VPC with public and private subnets
* NAT Gateway
* Internet Gateway
* VPC Endpoints wherever possible

### Security Controls

* Least privilege IAM access
* Secrets Manager for credentials
* Encryption in transit and at rest
* WAF protection
* Security Groups and NACLs
* Vulnerability scanning

### DevSecOps Pipeline

Developer Commit → GitLab → Jenkins

Pipeline stages:

1. Source Checkout
2. Build
3. Unit Testing
4. SAST (Fortify/SonarQube)
5. Secret Scanning (GitLeaks)
6. SCA (Dependency Check/Snyk)
7. SBOM Generation
8. Container Build
9. Image Scanning (Trivy)
10. Artifact Storage (Nexus)
11. Deployment to Kubernetes/EKS
12. Post-deployment Validation

### Monitoring

* CloudWatch
* Prometheus
* Grafana
* ELK Stack

### Well-Architected Framework

I would focus on:

* Security
* Reliability
* Operational Excellence
* Performance Efficiency
* Cost Optimization

This design ensures security, scalability, compliance, and operational stability.

---

# 4. What application and infrastructure requirements would you gather before planning and deploying the infrastructure?

**Answer:**

Before designing the infrastructure, I gather the following information:

### Application Details

* Monolithic or Microservices architecture
* Application technology stack (Java, Node.js, Python, .NET)
* Build tools (Maven, Gradle, npm)
* Runtime dependencies
* Containerized or VM-based deployment

### Traffic Requirements

* Expected user load
* Peak traffic patterns
* Auto-scaling requirements

### Environment Requirements

* DEV
* SIT
* UAT
* PROD

### Database Requirements

* Database type
* Storage requirements
* Backup and retention requirements

### Security Requirements

* Compliance requirements (PCI-DSS)
* Encryption requirements
* IAM access controls
* Secret management

### Availability Requirements

* RTO
* RPO
* Disaster Recovery requirements

### Monitoring Requirements

* Logging requirements
* Alerting requirements
* Dashboard requirements

After collecting these details, I design the infrastructure accordingly.

---

# 5. How would you deploy the infrastructure using Terraform?

**Answer:**

I follow an Infrastructure as Code approach using Terraform.

### Step 1: Create Reusable Modules

* VPC Module
* Security Group Module
* EC2/EKS Module
* RDS Module
* Load Balancer Module

### Step 2: Configure Remote Backend

Store Terraform state in:

* S3 Bucket
* State locking using S3 native lockfile or DynamoDB (depending on Terraform version)

### Step 3: Define Infrastructure

Create Terraform files:

* main.tf
* variables.tf
* outputs.tf
* provider.tf

### Step 4: Execute Deployment

```bash
terraform init
terraform validate
terraform plan
terraform apply
```

### Step 5: CI/CD Integration

Terraform execution is automated through Jenkins pipelines with approval gates for higher environments.

This ensures repeatable, version-controlled, and auditable infrastructure deployments.

---

# 6. Have you worked on Terraform provisioners? What are the types of provisioners, and in what scenarios would you use file provisioners?

**Answer:**

Yes, I am familiar with Terraform provisioners, although in most enterprise environments we prefer configuration management tools like Ansible over heavy usage of provisioners.

The common Terraform provisioners are:

### File Provisioner

Used to copy files from the local machine to a remote server.

Example:

* Copy application package
* Copy configuration files
* Copy certificates

### Remote-Exec Provisioner

Executes commands on a remote server.

Example:

* Install packages
* Configure services
* Run bootstrap scripts

### Local-Exec Provisioner

Executes commands on the machine running Terraform.

Example:

* Trigger external scripts
* Send notifications
* Call APIs

File provisioners are typically used when newly created instances require configuration files immediately after provisioning.

---

# 7. How would you copy files from a local machine to a newly provisioned EC2 instance using Terraform?

**Answer:**

I would use the Terraform File Provisioner.

Example:

```hcl
resource "aws_instance" "server" {

  ami           = "ami-xxxxx"
  instance_type = "t3.micro"

  provisioner "file" {
    source      = "app.jar"
    destination = "/tmp/app.jar"
  }

  connection {
    type        = "ssh"
    user        = "ec2-user"
    private_key = file("key.pem")
    host        = self.public_ip
  }
}
```

This copies the file from the machine executing Terraform to the target EC2 instance.

In enterprise environments, we generally prefer:

* S3
* Ansible
* Artifact repositories

for large-scale deployments.

---

# 8. How would you establish communication between two VPCs in different AWS accounts within the same region?

**Answer:**

For direct communication between two VPCs in different AWS accounts, I would use VPC Peering.

### Steps:

1. Create VPC Peering Request from Account A.
2. Accept Peering Request from Account B.
3. Update Route Tables on both VPCs.
4. Update Security Groups if required.
5. Validate connectivity.

Requirements:

* Non-overlapping CIDR ranges
* Proper route table configuration
* Appropriate IAM permissions

This enables private communication over AWS backbone networks without traversing the internet.

---

# 9. What could cause a VPC peering request to fail?

**Answer:**

Common reasons include:

### Overlapping CIDR Blocks

Most common reason.

Example:

```text
VPC-A : 10.0.0.0/16
VPC-B : 10.0.0.0/16
```

Peering will fail.

### Permission Issues

* Missing IAM permissions
* Request not accepted

### Incorrect Account Details

* Wrong VPC ID
* Wrong AWS Account ID

### Region Restrictions

Depending on architecture and configuration.

### Route Table Misconfiguration

Routes not properly updated after peering creation.

The first thing I would check is CIDR overlap.

---

# 10. If two VPCs have overlapping CIDR ranges and cannot be modified, what alternative solution would you use instead of VPC peering?

**Answer:**

If CIDR ranges overlap, VPC Peering will not work.

In such situations, I would consider:

### AWS PrivateLink (Preferred)

Allows private service-to-service communication without requiring network-level connectivity.

Benefits:

* Works even with overlapping CIDRs
* Secure private connectivity
* No routing conflicts

### Alternative Approaches

* Reverse Proxy Architecture
* API Gateway-based Integration
* NAT Translation Solutions

A common misconception is that Transit Gateway solves overlapping CIDR problems.

It does not.

Transit Gateway still requires non-overlapping CIDR ranges for routing.

For overlapping CIDRs, AWS PrivateLink is typically the preferred enterprise solution.


---

# 11. Why do we use Transit Gateway, what challenges does it solve compared to VPC peering, and can VPC peering be transitive?

**Answer:**

AWS Transit Gateway acts as a centralized networking hub that connects multiple VPCs, VPNs, and on-premises networks.

### Challenges with VPC Peering

As the number of VPCs increases, VPC peering becomes difficult to manage because:

* Large number of peering connections
* Complex route table management
* High operational overhead
* No transitive routing support

For example:

```text
VPC-A <-> VPC-B
VPC-B <-> VPC-C
```

Even though A can communicate with B and B can communicate with C:

```text
VPC-A ❌ VPC-C
```

VPC peering is **not transitive**.

### How Transit Gateway Helps

Transit Gateway provides a hub-and-spoke architecture:

```text
          TGW
         / | \
        /  |  \
     VPC1 VPC2 VPC3
```

Benefits:

* Centralized routing
* Scalable architecture
* Reduced number of connections
* Supports transitive routing
* Easier cross-account connectivity
* Simplified network management

Transit Gateway is commonly used in enterprise environments with multiple AWS accounts and VPCs.

---

# 12. How would you establish communication between VPCs when direct transitive communication is not possible?

**Answer:**

If direct transitive communication is required, VPC peering alone cannot achieve it because peering is not transitive.

In such cases, I would use:

### AWS Transit Gateway

It acts as a central routing hub.

Example:

```text
VPC-A → TGW ← VPC-B
          ↑
          |
        VPC-C
```

Now:

* VPC-A can communicate with VPC-B
* VPC-A can communicate with VPC-C
* VPC-B can communicate with VPC-C

through Transit Gateway routing.

For large-scale multi-account environments, Transit Gateway is the recommended solution.

---

# 13. How would you provide secure outbound internet access from workloads running in a private subnet?

**Answer:**

For workloads running inside private subnets, I would use:

### NAT Gateway

The instances remain private and do not receive public IP addresses.

Traffic flow:

```text
Private EC2
     ↓
NAT Gateway
     ↓
Internet Gateway
     ↓
Internet
```

Benefits:

* No direct public exposure
* Secure outbound internet access
* Common enterprise architecture

### Additional Security Enhancements

For AWS service access, I would use:

* VPC Endpoints
* AWS PrivateLink

This avoids internet traversal altogether when accessing AWS services.

---

# 14. Where would you provision a NAT Gateway, what route table changes are required, and which route tables must be modified?

**Answer:**

### NAT Gateway Placement

A NAT Gateway must be provisioned in a **public subnet**.

Reason:

* NAT Gateway requires internet access.
* It must have an Elastic IP.
* It communicates through an Internet Gateway.

### Public Route Table

```text
Destination      Target
0.0.0.0/0        Internet Gateway
```

### Private Route Table

```text
Destination      Target
0.0.0.0/0        NAT Gateway
```

### Route Tables Modified

Both route tables need configuration:

#### Public Subnet Route Table

Allows NAT Gateway to reach the internet.

#### Private Subnet Route Table

Allows private instances to send outbound traffic through the NAT Gateway.

This is the standard AWS architecture for secure outbound connectivity.

---

# 15. Have you worked on Terraform modules?

**Answer:**

Yes.

I have extensively used Terraform modules to create reusable and standardized infrastructure components.

Typical modules I have worked with include:

* VPC Module
* Security Group Module
* EC2 Module
* EKS Module
* RDS Module
* Load Balancer Module

### Benefits of Modules

* Code reusability
* Reduced duplication
* Easier maintenance
* Consistent deployments
* Environment standardization

Example:

Instead of writing VPC code repeatedly for DEV, SIT, UAT, and PROD, we create one reusable VPC module and pass different variables.

This improves maintainability and scalability.

---

# 16. What is the purpose of a null_resource in Terraform?

**Answer:**

A `null_resource` is used when we need Terraform to perform an action that is not directly associated with creating or managing infrastructure resources.

Common use cases:

* Running shell scripts
* Executing custom commands
* Triggering automation workflows
* Running post-deployment tasks
* Calling APIs

Example:

```hcl
resource "null_resource" "deploy" {

  provisioner "local-exec" {
    command = "python deploy.py"
  }
}
```

In real projects, I have mainly used it for:

* Triggering scripts
* Running validations
* Executing deployment-related activities

where no actual AWS resource is being created.

---

# 17. If you have petabytes of data in S3 with unpredictable access patterns, which S3 storage tier would you choose and why? Have you implemented it in production?

**Answer:**

I would choose **S3 Intelligent-Tiering**.

### Reason

The access pattern is unpredictable.

With Intelligent-Tiering:

* AWS automatically monitors access patterns.
* Frequently accessed data remains in frequent-access tiers.
* Less frequently accessed data moves to lower-cost tiers.
* Cost is optimized automatically.

Benefits:

* No performance impact
* No retrieval delays
* No manual lifecycle management

### Production Experience

In my projects, I have worked with lifecycle policies and S3 storage management, but I have not personally implemented Intelligent-Tiering in a production environment. My understanding comes from AWS best practices and technical evaluation of storage optimization strategies.

---

# 18. How would you deploy changes only to odd-numbered VMs using Terraform?

**Answer:**

This can be achieved using:

* `count`
* `for_each`
* conditional expressions

Example approach:

```hcl
count = 5
```

Terraform creates:

```text
Instance[0]
Instance[1]
Instance[2]
Instance[3]
Instance[4]
```

Then we can apply logic:

```hcl
count.index % 2 != 0
```

This targets:

```text
1
3
5
```

(odd-numbered instances)

Another approach is using `for_each` with filtered maps or lists.

For enterprise environments, `for_each` is generally preferred because resource addressing remains stable.

---

# 19. How would you configure Terraform remote state storage in AWS?

**Answer:**

For enterprise Terraform deployments, I always prefer remote state storage.

### Components

* Amazon S3 Bucket
* State Locking Mechanism
* Encryption Enabled
* Versioning Enabled

### Backend Configuration

```hcl
terraform {
  backend "s3" {
    bucket = "terraform-state-bucket"
    key    = "prod/terraform.tfstate"
    region = "ap-south-1"
  }
}
```

### Deployment Steps

1. Create S3 bucket.
2. Enable versioning.
3. Enable encryption.
4. Configure backend block.
5. Run:

```bash
terraform init
```

Terraform migrates local state to the remote backend.

### Benefits

* Centralized state management
* Team collaboration
* State recovery
* Auditability
* Improved security

---

# 20. Do we still need DynamoDB for Terraform state locking, and what recent changes have been introduced regarding state locking?

**Answer:**

Historically, Terraform remote state on AWS used:

* S3 → State Storage
* DynamoDB → State Locking

Example:

```text
S3 Bucket
    +
DynamoDB Table
```

The DynamoDB table prevented multiple users or pipelines from modifying the same state simultaneously.

### Recent Change

Recent Terraform versions introduced:

```hcl
use_lockfile = true
```

for S3 backends.

This allows Terraform to manage locking directly using lock files in S3.

As a result:

* DynamoDB is no longer mandatory for new deployments.
* Existing environments may still use DynamoDB.
* Many organizations continue using DynamoDB until they fully adopt the newer locking mechanism.

So today:

### Traditional Approach

```text
S3 + DynamoDB
```

### New Approach

```text
S3 + Lockfile
```

Both may still be found in enterprise environments depending on the Terraform version and organizational standards.

---

# 21. Which AWS service can be used to scan AMIs and installed packages for vulnerabilities?

**Answer:**

For AMI and package vulnerability scanning, I would use **Amazon Inspector**.

### What Amazon Inspector Does

* Scans EC2 instances and AMIs
* Identifies CVEs and vulnerabilities
* Checks installed packages and libraries
* Provides severity ratings
* Integrates with Security Hub and EventBridge

### DevSecOps Usage

In a CI/CD process, AMIs can be scanned before deployment to ensure no critical vulnerabilities are present.

Example Flow:

```text
AMI Build
    ↓
Amazon Inspector Scan
    ↓
Security Review
    ↓
Deployment Approval
```

---

# 22. How do you implement sensitive data scrubbing and masking in a CI/CD pipeline?

**Answer:**

For PCI-DSS compliant environments, sensitive data should never be hardcoded or exposed in logs.

### Approach

#### Secrets Management

* HashiCorp Vault
* AWS Secrets Manager
* Azure Key Vault

Secrets are fetched at runtime.

#### Secret Scanning

I integrate tools such as:

* GitLeaks
* Snyk Secrets
* GitHub Secret Scanning

#### Log Masking

Sensitive values are masked inside Jenkins/GitLab pipelines.

Example:

```text
Password = ********
API Key = ********
```

#### RBAC

Only authorized users can access secrets.

### Pipeline Flow

```text
Code Commit
    ↓
Secret Scan
    ↓
Vault Secret Retrieval
    ↓
Build & Deploy
    ↓
Masked Logging
```

---

# 23. How do you troubleshoot an EC2 instance that belongs to an Auto Scaling Group without terminating it?

**Answer:**

I would place the instance into **Standby Mode**.

### Process

1. Select EC2 instance.
2. Move instance to Standby.
3. Instance is removed from load balancing.
4. Traffic stops reaching that instance.
5. SSH/RDP into instance.
6. Troubleshoot and fix issue.
7. Return instance to service.

### Benefit

* Instance remains running.
* Auto Scaling does not immediately terminate it.
* Safe troubleshooting without impacting users.

---

# 24. What happens when an instance is moved to Standby mode in an Auto Scaling Group?

**Answer:**

When an instance enters Standby:

### What Happens

* Removed from active service.
* Detached from load balancer target group.
* Stops receiving traffic.
* Instance remains running.
* Existing data remains intact.
* Can be accessed for troubleshooting.

### What Does Not Happen

* Instance is not terminated.
* Instance is not stopped.
* Instance is not deleted.

### Use Cases

* Maintenance
* Patching
* Troubleshooting
* Log analysis

---

# 25. What are Lifecycle Hooks in an Auto Scaling Group?

**Answer:**

Lifecycle Hooks allow custom actions during instance launch or termination.

### Types

#### Launch Lifecycle Hook

Triggered when a new instance launches.

Example:

```text
Launch Instance
      ↓
Run Bootstrap Script
      ↓
Install Software
      ↓
Join Service
      ↓
InService
```

#### Terminate Lifecycle Hook

Triggered before instance termination.

Example:

```text
Terminate Request
       ↓
Backup Logs
       ↓
Drain Connections
       ↓
Upload Data
       ↓
Terminate
```

### Benefits

* Better automation
* Graceful startup
* Graceful shutdown

---

# 26. Which Terraform lifecycle policy helps create a replacement instance before destroying the old one?

**Answer:**

Terraform Lifecycle Meta-Argument:

```hcl
lifecycle {
  create_before_destroy = true
}
```

### Purpose

Terraform creates the new resource first and destroys the old one afterward.

### Benefit

* Zero or minimal downtime
* Safe infrastructure replacement
* Useful for production workloads

### Example

```hcl
resource "aws_instance" "web" {

  lifecycle {
    create_before_destroy = true
  }

}
```

This ensures:

```text
New Instance Created
        ↓
Traffic Shifted
        ↓
Old Instance Destroyed
```

---

# 27. What type of VPN connectivity have you worked on?

**Answer:**

In my current project, we established a **Site-to-Site VPN** between:

```text
On-Premises DevSecOps Environment
                ↕
AWS / Azure Cloud Environment
```

### Purpose

* Secure deployment communication
* Cluster management
* Secure access to cloud resources
* Encrypted traffic transmission

### Use Cases

* Jenkins deployments
* Kubernetes administration
* Secure infrastructure access

---

# 28. Which AWS services are required to establish a Site-to-Site VPN connection?

**Answer:**

The primary AWS components are:

### 1. Virtual Private Gateway (VGW)

Attached to the AWS VPC.

### 2. Customer Gateway (CGW)

Represents the on-premises VPN device.

### 3. Site-to-Site VPN Connection

Connects VGW and CGW.

### Architecture

```text
On-Prem Firewall
        │
Customer Gateway
        │
VPN Tunnel
        │
Virtual Private Gateway
        │
AWS VPC
```

Additional components:

* Route Tables
* Security Groups
* Network ACLs

---

# 29. Have you worked on Virtual Private Gateway (VGW) and Customer Gateway (CGW)? What are they?

**Answer:**

### Virtual Private Gateway (VGW)

AWS-side VPN endpoint.

Responsibilities:

* Attached to VPC.
* Receives VPN traffic.
* Terminates VPN tunnels.

### Customer Gateway (CGW)

Represents the customer/on-premises side VPN device.

Contains:

* Public IP of firewall/router
* BGP or static routing information

### Communication Flow

```text
On-Prem Firewall
      ↓
Customer Gateway
      ↓
VPN Tunnel
      ↓
Virtual Private Gateway
      ↓
AWS VPC
```

---

# 30. Have you personally deployed VPN connections?

**Answer:**

My involvement was primarily from the DevSecOps and infrastructure consumption side.

The dedicated network team handled:

* VPN device configuration
* Tunnel establishment
* Routing configuration

My responsibilities included:

* Validating connectivity
* Using VPN for secure deployments
* Accessing Kubernetes clusters
* Managing Jenkins deployment communication
* Troubleshooting connectivity issues

While I understand the architecture and components (VGW, CGW, VPN tunnels, route propagation), the actual VPN provisioning was handled by the networking team in my project.


