# Job Description: DevOps Engineer

### Overview

We are seeking a skilled **DevOps Engineer** to join our dynamic team. The ideal candidate will have extensive experience with AWS and Azure cloud services, along with solid experience in CI/CD pipelines and Infrastructure as Code using Terraform.

If you are passionate about automating processes and enhancing our DevSecOps practices, we would love to hear from you!


### Key Responsibilities

* Design, implement, and manage CI/CD pipelines using Azure DevOps and GitHub.
* Deploy and manage applications on:

  * Azure Kubernetes Service (AKS)
  * AWS Kubernetes Service (EKS)
  * Other Azure cloud services
* Collaborate with development teams to enhance the deployment process and implement best practices in cloud architecture.
* Develop Terraform modules for Infrastructure as Code, ensuring consistent and repeatable deployments across environments.
* Implement DevSecOps practices, including:

  * Static Application Security Testing (SAST)
  * Software Composition Analysis (SCA)
* Optimize Docker container images.
* Monitor and optimize cloud environments to ensure high availability and performance.
* Troubleshoot and resolve issues in development, test, and production environments.
* Collaborate with cross-functional teams to define and refine DevOps processes.


### Required Skills & Qualifications

* Minimum **4 years** of DevOps Engineer experience.
* Minimum **4 years** of experience in AWS and Azure.
* Strong expertise in Azure DevOps and GitHub tools.
* Experience with:

  * Azure Pipelines
  * Azure Kubernetes Service (AKS)
* Proficiency in AWS and Azure cloud services.
* Solid understanding of:

  * GitHub
  * API Management
  * GitHub Action Workflows
* Hands-on experience creating and managing Terraform modules.
* Proficiency in HCL (HashiCorp Configuration Language).
* Experience in multistage pipelines and building tools for:

  * .NET
  * Python
  * Angular
  * React
* Familiarity with DevSecOps principles and tools related to SAST and SCA.
* Strong scripting skills (PowerShell, Bash, Python).
* Excellent problem-solving skills with the ability to work in a fast-paced environment.
* Strong communication skills and ability to collaborate effectively within a team.
* Ability to quickly adapt, learn, and implement new DevOps tools.

---

# 30 concept-centric interview Preparation questions

### **Part 1: Hybrid Cloud & Kubernetes (AWS/Azure)**

1.  What are the architectural differences between **AWS EKS** and **Azure AKS** regarding control plane management and node provisioning?
2.  How is networking configured differently between an **AWS VPC** and an **Azure VNet**, particularly regarding subnets and peering?
3.  How do **Azure RBAC** (Role-Based Access Control) and **AWS IAM** differ in managing permissions for Kubernetes clusters?
4.  What is the process for managing secrets in a hybrid environment using **Azure Key Vault** and **AWS Secrets Manager**?
5.  How does container image scanning differ between **Azure Container Registry (ACR)** and **Amazon ECR**?
6.  What are the strategies for configuring high availability for a multi-cloud application spanning AWS and Azure?

### **Part 2: CI/CD Pipelines (Azure DevOps & GitHub)**

7.  What are the key architectural differences between **Azure DevOps (ADO)** and **GitHub Actions** in terms of agents, runners, and pipeline definition?
8.  How is a **Multi-stage Pipeline** structured in GitHub Actions (YAML) to separate build, test, and deploy phases?
9.  How do **Azure Artifacts** and **GitHub Packages** compare in terms of NuGet and npm package management?
10. What is the role of **Azure API Management (APIM)** in a DevOps workflow, and how is it integrated with CI/CD pipelines?
11. How do you manage environment-specific variables and secrets in **Azure DevOps** versus **GitHub**?
12. What is the purpose of **Self-Hosted Runners** in GitHub Actions, and when would you choose them over GitHub-hosted runners?

### **Part 3: Infrastructure as Code (Terraform)**

13. What is the structure of a **Terraform Module**, and how do inputs, outputs, and child modules promote code reusability?
14. How do you manage **Terraform State** when provisioning resources across multiple clouds (AWS and Azure)?
15. What are the advanced features of **HCL (HashiCorp Configuration Language)** such as dynamic blocks, locals, and loops?
16. How do you use **Data Sources** in Terraform to fetch existing resources (like an existing VPC) before creating new infrastructure?
17. What is the strategy for handling **Drift Detection** and remediation in a Terraform-managed multi-cloud environment?

### **Part 4: Containerization & Optimization**

18. What specific techniques are used for **Docker Image Optimization** (e.g., Multi-stage builds, Slim images, Layer caching)?
19. How does the build process differ for **.NET Core** applications compared to **Angular/React** (Single Page Applications) in a Docker environment?
20. How do you configure **Ingress Controllers** in AKS (using Azure Application Gateway Ingress Controller) vs. EKS (using AWS Load Balancer Controller)?
21. What are the resource limit and request strategies for **Pods** to ensure stability in a multi-tenant Kubernetes cluster?

### **Part 5: DevSecOps (SAST, SCA, Scanning)**

22. What is the technical difference between **SAST (Static Application Security Testing)** and **SCA (Software Composition Analysis)** in the context of a CI/CD pipeline?
23. How are security scans (SAST/SCA) integrated into a **Multistage Pipeline** in Azure DevOps without slowing down the build?
24. How do you implement **Image Scanning** for vulnerabilities in Docker images pushed to Azure Container Registry?
25. What is the process for creating **Policy as Code** to enforce compliance (e.g., no public S3 buckets) across both AWS and Azure?

### **Part 6: Scripting & Automation**

26. What are the key differences between **PowerShell** (for Azure) and **Bash** (for AWS) when automating cloud infrastructure tasks?
27. How do you use **Python** (e.g., Boto3, Azure SDK) to automate repetitive tasks such as bulk resource provisioning or log analysis?
28. What are the best practices for writing **Error Handling and Logging** in shell scripts used for Cron jobs or maintenance tasks?

### **Part 7: Architecture, Troubleshooting & Strategy**

29. How do you approach **Troubleshooting** a failed deployment in a Kubernetes environment across both AKS and EKS?
30. What is your strategy for **Adopting New Tools** (e.g., moving from on-premise to cloud, or introducing a new SAST tool) to ensure minimal disruption to the team?

---

# Answers:

### **Part 1: Hybrid Cloud & Kubernetes (AWS/Azure)**

**1. What are the architectural differences between AWS EKS and Azure AKS?**

**Answer:**
Both services manage Kubernetes, but the setup is different.
*   **AWS EKS (Elastic Kubernetes Service):** You must manage the "Worker Nodes" (the servers) yourself using EC2 instances. AWS manages the "Control Plane" (the brain) for you, but you control the underlying servers.
*   **Azure AKS (Azure Kubernetes Service):** Azure offers a feature called "Serverless" nodes. You can choose to let Azure manage the underlying servers completely. You just define the resources you need (CPU/Memory), and Azure handles the hardware updates and management automatically.

**2. How is networking configured differently between an AWS VPC and an Azure VNet?**

**Answer:**
Both are private networks in the cloud, but the terms and scope vary.
*   **AWS VPC:** The network is defined per "Region." To connect two VPCs, you use "VPC Peering."
*   **Azure VNet:** The network spans across an entire "Region" by default. To connect two VNets, you use "VNet Peering."
*   **Subnets:** In both, you divide the network into smaller subnets. However, in Azure, subnets are always regional. In AWS, subnets are mapped to specific "Availability Zones" (data centers).

**3. How do Azure RBAC and AWS IAM differ in managing Kubernetes?**

**Answer:**
*   **AWS IAM:** Permissions are strictly tied to the account. You define who can access the EKS API server.
*   **Azure RBAC:** Permissions are more integrated with Azure Active Directory (Entra ID). In AKS, you can grant users access directly using their corporate login credentials without needing separate cloud keys. It connects the company's identity system directly to the cluster.

**4. How do you manage secrets in a hybrid environment?**

**Answer:**
You store secrets separately for each cloud to avoid latency and compliance issues.
*   For **AWS resources**, you use **AWS Secrets Manager** or **Parameter Store**.
*   For **Azure resources**, you use **Azure Key Vault**.
*   The application code is written to look for the secret in the specific cloud provider it is currently running on.

**5. How does container image scanning differ between Azure Container Registry (ACR) and Amazon ECR?**

**Answer:**
*   **Azure ACR:** Scanning is often integrated directly into the registry service. You can see the security scan results right in the Azure portal after pushing an image.
*   **Amazon ECR:** Scanning is usually a feature called "Enhanced Scanning" that you enable. It uses a separate engine (like Inspector) to analyze the image layers for vulnerabilities.

**6. What are the strategies for high availability across AWS and Azure?**

**Answer:**
You cannot rely on a single cloud provider.
*   **Data Replication:** You replicate critical data (like databases) to both clouds.
*   **Traffic Management:** You use a Global DNS service. If the primary cloud (e.g., AWS) goes down, the DNS automatically routes traffic to the backup cloud (e.g., Azure).
*   **Container Orchestration:** You run the same Kubernetes application in both AKS and EKS, ensuring the application environment is identical in both places.

---

### **Part 2: CI/CD Pipelines (Azure DevOps & GitHub)**

**7. What are the key differences between Azure DevOps and GitHub Actions?**

**Answer:**
*   **Azure DevOps:** It is a complete suite for large enterprises. It has a specific section for "Boards" (project tracking) and "Repos" (code). It uses "Agents" to run jobs.
*   **GitHub Actions:** It is built directly into the code repository. It is simpler and more modular. It uses "Runners" to execute jobs. It is very popular for open-source and modern startups because everything happens in one place.

**8. How is a Multi-stage Pipeline structured in GitHub Actions?**

**Answer:**
A pipeline is divided into distinct steps called "Stages."
*   **Stage 1 (Build):** The code is compiled into an executable.
*   **Stage 2 (Test):** Automated tests are run.
*   **Stage 3 (Deploy):** The application is pushed to the server.
In the YAML file, you define these stages in order. GitHub Actions will not start the "Deploy" stage until the "Test" stage finishes successfully.

**9. How do Azure Artifacts and GitHub Packages compare?**

**Answer:**
Both are libraries for storing application packages (like libraries, installers, or container images).
*   **Azure Artifacts:** Integrates tightly with other Microsoft tools like NuGet and .NET.
*   **GitHub Packages:** Integrates tightly with the code repository.
Functionally, they do the same thing: they store files and version them so you can download them during the build process.

**10. What is the role of Azure API Management (APIM)?**

**Answer:**
APIM acts as a secure front door for your APIs (Application Programming Interfaces).
*   It exposes a single URL to the outside world, even if you have multiple microservices behind it.
*   It handles security (checking who is calling) and traffic limits (stopping people from calling the API too many times).
*   In CI/CD, you update the configuration in APIM when you deploy a new version of your API.

**11. How do you manage variables in Azure DevOps vs. GitHub?**

**Answer:**
Both allow you to store data to be used in pipelines.
*   **Azure DevOps:** You use "Library" groups to define variables and mark them as "Secret" to hide them.
*   **GitHub:** You use "Repository Secrets" or "Organization Secrets." You reference them in the YAML file using a specific syntax (like `${{ secrets.VAR_NAME }}`).

**12. What are Self-Hosted Runners in GitHub Actions?**

**Answer:**
A "Runner" is the server that executes the code instructions.
*   **GitHub-Hosted:** GitHub provides the server for you. It is fast and easy.
*   **Self-Hosted:** You install the runner software on your own server. You use this when you need access to a private network, have specific hardware requirements, or need to use large files that are too big for GitHub's standard servers.

---

### **Part 3: Infrastructure as Code (Terraform)**

**13. What is the structure of a Terraform Module?**

**Answer:**
A module is a folder of code that creates a specific piece of infrastructure.
*   **Inputs:** These are the settings you change (like the server size or the region).
*   **Resources:** The actual code that defines what to create (like a database or a network).
*   **Outputs:** The information that the module produces after creation (like the IP address of the server).
Instead of writing the code 10 times, you write a module once and just change the inputs.

**14. How do you manage State across multiple clouds?**

**Answer:**
The "State" file is the record of what exists.
*   You cannot use one state file for two different clouds (AWS and Azure) because they don't understand each other's resources.
*   You create a separate "Backend" (a storage location) for each cloud provider. One state file lives in an AWS S3 bucket, and another lives in Azure Blob Storage.

**15. What are advanced features of HCL (Terraform language)?**

**Answer:**
*   **Dynamic Blocks:** Instead of writing the same code 50 times for 50 servers, you write a "dynamic block" that loops 50 times to create all 50 servers automatically.
*   **Locals:** These are variables that exist only while Terraform is running. They help you simplify complex calculations.
*   **Loops:** Using `for_each` to create multiple versions of a resource based on a list of names.

**16. How do you use Data Sources in Terraform?**

**Answer:**
Usually, Terraform *creates* new things. "Data Sources" allow Terraform to *read* things that already exist.
For example, if you already have a network set up, you use a Data Source to read the ID of that network. Then, you use that ID to create a new database inside that existing network.

**17. What is Drift Detection?**

**Answer:**
Drift happens when someone manually changes a server in the cloud console instead of using Terraform.
*   **Detection:** When you run Terraform, it compares the "State" file (what Terraform thinks exists) with the "Actual Cloud" (what really exists).
*   **Remediation:** If they don't match, Terraform shows a "Drift." To fix it, you run the apply command again, and Terraform changes the cloud back to match your code.

---

### **Part 4: Containerization & Optimization**

**18. What are the techniques for Docker Image Optimization?**

**Answer:**
*   **Multi-stage Builds:** You use one image to compile the code (heavy), and then copy only the final executable to a tiny, empty image for running. This removes all the build tools and reduces file size.
*   **Layer Caching:** You order the Dockerfile commands to copy the code only at the very end. This ensures that if you change one line of code, Docker doesn't have to re-download all your library dependencies again.
*   **Slim Images:** You use "Alpine Linux" or "Distroless" images which have no extra tools, just the bare minimum needed to run the application.

**19. How does the build process differ for .NET vs. Angular?**

**Answer:**
*   **.NET (Backend):** You compile the code into a binary (DLL/EXE). You then run this binary using the .NET runtime.
*   **Angular (Frontend):** You don't compile into a binary. You run a "build" command which generates "Static Files" (HTML, CSS, JavaScript). These files are then served by a web server like Nginx.

**20. How do you configure Ingress Controllers in AKS vs. EKS?**

**Answer:**
An Ingress Controller directs traffic from the internet to the correct service.
*   **AKS:** You often use "Azure Application Gateway Ingress Controller." It connects directly to Azure's Load Balancer.
*   **EKS:** You often use "AWS Load Balancer Controller." It creates an AWS Load Balancer specifically for the Kubernetes services you create.

**21. What are the resource limit strategies?**

**Answer:**
*   **Requests:** You tell the cluster, "This application needs 1GB of RAM." The cluster finds a server that has at least 1GB free and puts the application there.
*   **Limits:** You tell the cluster, "This application should never use more than 2GB of RAM." If it tries to use more, the operating system will stop it. This prevents one application from crashing the whole server.

---

### **Part 5: DevSecOps (SAST, SCA, Scanning)**

**22. What is the difference between SAST and SCA?**

**Answer:**
*   **SAST (Static Application Security Testing):** It scans the **source code** you wrote. It looks for bad coding practices, like writing passwords in the code or using unsafe functions.
*   **SCA (Software Composition Analysis):** It scans the **libraries** you downloaded. It looks for known security flaws in code that other people wrote (like the `log4j` vulnerability).

**23. How are security scans integrated into a Multi-stage Pipeline?**

**Answer:**
You add a specific "Scan Stage" between the "Test" and "Deploy" stages.
*   If the scan finds a "High" severity vulnerability, the pipeline stops (fails) immediately.
*   This prevents bad code from being deployed. It happens automatically every time a developer saves code.

**24. How do you implement Image Scanning in ACR?**

**Answer:**
When you push a Docker image to **Azure Container Registry**, you can enable "Trivy" or Microsoft's built-in scanner.
*   The scan runs automatically.
*   In the Azure portal, you see a list of vulnerabilities (like "OS Kernel needs update").
*   You can set a rule that does not allow deployment if the image has a "Critical" vulnerability.

**25. What is Policy as Code?**

**Answer:**
Instead of writing rules in a document, you write the rules in a programming language.
*   You create a policy (e.g., "All S3 buckets must be private").
*   You apply this policy to your Cloud or Kubernetes.
*   If a developer tries to create a public bucket, the system rejects it automatically using the policy code.

---

### **Part 6: Scripting & Automation**

**26. What are the differences between PowerShell and Bash?**

**Answer:**
*   **PowerShell:** It is designed for **Windows** and **Azure**. It is object-based, meaning it outputs data as "Objects" which are easy to manipulate. It uses "Cmdlets" (commands) like `Get-AzVM`.
*   **Bash:** It is designed for **Linux** and **AWS**. It is text-based, meaning it outputs text strings. It uses standard commands like `ls` or `grep`.

**27. How do you use Python for automation?**

**Answer:**
Python uses "SDKs" (Software Development Kits) to talk to the cloud APIs.
*   **AWS:** You import the library called `Boto3`.
*   **Azure:** You import `Azure SDK`.
*   **Usage:** You write a script to loop through 100 servers. Instead of clicking in the console 100 times, you run the script, and Python sends 100 commands to the cloud API in seconds.

**28. What are best practices for Error Handling in scripts?**

**Answer:**
*   **Exit Codes:** Always check if the previous command worked. If a command fails, stop the script immediately so you don't continue making mistakes.
*   **Logging:** Print messages to the screen or a log file (e.g., "Connecting to Database..."). If the script crashes, you can look at the logs to see exactly where it stopped.

---

### **Part 7: Architecture, Troubleshooting & Strategy**

**29. How do you troubleshoot a failed deployment in Kubernetes?**

**Answer:**
*   **Step 1:** Check the "Pod Status." Is it "CrashLoopBackOff"? (It's restarting).
*   **Step 2:** Check the "Logs." Run a command to see what the application wrote inside the pod. It usually prints an error message.
*   **Step 3:** Check the "Events." This tells you if the problem is with the image (ImagePullBackOff) or if there is not enough memory.

**30. What is the strategy for Adopting New Tools?**

**Answer:**
*   **Pilot Phase:** Start by using the new tool for just one small project. Do not change everything at once.
*   **Documentation:** Create a guide for the team on how to use the new tool.
*   **Feedback:** Ask the team what is difficult about the new tool and fix those issues.
*   **Rollout:** Once it works for the pilot team, slowly roll it out to the rest of the organization.
