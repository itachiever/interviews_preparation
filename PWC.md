# Job Description

### Role: DevSecOps Engineer

---

### Mandatory Skills & Experience

### Experience

* Minimum **4 years** of experience in a DevOps or DevSecOps role.
* Strong focus on:

  * Azure
  * GitHub DevOps practices
  * Terraform
* Experience working from a secure infrastructure mindset.



### Certifications

* Azure certifications such as:

  * **Microsoft Certified: Azure DevOps Engineer Associate**
  * **Microsoft Certified: Azure Administrator Associate**



### Terraform & Azure

* Minimum **2 years** of experience with Terraform in an Azure environment
  **OR**
* Operational support of Azure resources using Terraform.


### Technical Knowledge

* Familiarity with Agile methodologies and practices.
* Strong understanding of:

  * Networking concepts
  * Cloud security best practices
* Knowledge of monitoring and logging tools such as:

  * Azure Monitor
  * Prometheus
  * Grafana
  * ELK Stack

### Scripting & Automation

* Proficiency in scripting languages such as:

  * PowerShell
  * Bash
  * Python
  * Go



### Security & DevSecOps

* Experience with security tools and practices including:

  * Static code analysis
  * Vulnerability scanning
  * Incident response


### DevOps & Cloud Services Expertise

* Strong experience with **GitHub Enterprise**.
* GitHub Actions / Workflows.
* Azure Kubernetes Service (AKS).
* Infrastructure as Code (Terraform in Azure).
* Hands-on experience with Docker and Kubernetes.


### Nice-to-Have Skills

* Excellent problem-solving and troubleshooting abilities.
* Strong communication and cross-functional collaboration skills.
* Detail-oriented with focus on high-quality deliverables.
* Ability to work independently and manage multiple tasks in a fast-paced environment.

---
 # Questions & Answers:


### **GitHub Enterprise & CI/CD**

**1. How does GitHub Enterprise differ from the public GitHub.com?**

**Answer:**
GitHub Enterprise is the self-hosted version that runs on your own servers (or in your own cloud). The main difference is **Control**. You own the data, you control the security policies, and you manage the user access. Public GitHub is managed by GitHub. Enterprise also allows you to enforce specific security rules (like blocking certain commits) across all your organization's repositories automatically.

**2. How are GitHub Actions workflows structured, and how do they automate security?**
**Answer:**
A workflow is a YAML file that defines jobs and steps.
*   **Structure:** Jobs run on runners (servers). Steps are the individual commands (like `npm install` or `docker build`).
*   **Security Automation:** You add "Steps" that run security scanners. For example, a step can run a tool like `Trivy` to scan your Docker image. If the scanner finds a vulnerability, the workflow fails, stopping the deployment automatically.

**3. How are secrets managed securely in GitHub Actions?**
**Answer:**
You never write secrets in the code. You go to the repository settings and add "Secrets" (like an API Key).
When the workflow runs, GitHub makes these secrets available as environment variables. However, in the logs, they are masked (hidden) so no one can see them. GitHub ensures the secret is only available to the workflows that explicitly ask for it.

**4. What are Self-Hosted Runners in GitHub Enterprise, and why are they used?**
**Answer:**
Runners are the servers that execute the code instructions.
*   **Self-Hosted:** You install the runner software on a server inside your private network.
*   **Usage:** You use this when your pipeline needs to access a private database or internal servers that the public internet cannot reach. It is also used for performance if your build process requires very large, powerful hardware.

**5. How does GitHub Advanced Security integrate with the CI/CD pipeline?**
**Answer:**
GitHub Advanced Security provides tools like **Code Scanning (SAST)** and **Secret Scanning**.
*   **Integration:** When you push code, GitHub runs these scans automatically. If a developer opens a "Pull Request" (PR), GitHub displays the security results directly in the conversation. This blocks the merge until the security issue is fixed.

---

### **Terraform & Azure Infrastructure**

**6. How do you structure Terraform Modules for an Azure environment?**
**Answer:**
A Module is a folder containing reusable code.
*   **Structure:** It contains `main.tf` (the resources), `variables.tf` (settings you can change), and `outputs.tf` (information you get back).
*   **Usage:** Instead of writing the code for a Virtual Network every time, you write it once in a module. You then call that module in your main file, just passing in the name of the network. This ensures all networks in your company are built the same way.

**7. How do you manage Terraform State in a team environment at an enterprise scale?**
**Answer:**
The state file tracks your infrastructure. In a team, you cannot keep it on your laptop.
*   **Remote State:** You store the state file in a secure location like **Azure Storage Account**.
*   **Locking:** You enable "State Locking." If one engineer is running Terraform, it locks the file so no one else can run it at the same time. This prevents two people from changing the infrastructure simultaneously and breaking it.

**8. How do you implement Infrastructure as Code (IaC) scanning for security?**
**Answer:**
IaC scanning tools (like Checkov or TfSec) read your Terraform code before you deploy it.
*   **Process:** You run the tool as a step in your GitHub Action. It looks for misconfigurations, like an Azure SQL Database that has the firewall set to "Allow All Traffic." If it finds an error, it breaks the build, ensuring you never deploy insecure infrastructure.

**9. How do you handle secrets in Terraform when deploying to Azure?**
**Answer:**
You do not hardcode passwords in the `.tf` file.
*   **Method:** You define a variable (e.g., `db_password`). When you run Terraform, you don't type the password. You use a script or a tool to fetch the password from **Azure Key Vault** (the secure store) and pass it to Terraform. The password exists only in memory for a split second and is never saved in the code or the state file.

**10. What is the strategy for rolling out updates to Azure resources using Terraform?**
**Answer:**
You use the "Immutable Infrastructure" strategy.
*   **Strategy:** You never update the existing server in place. Instead, you deploy a *new* server with the new configuration. Once the new server is healthy, you switch the traffic to it and destroy the old one. Terraform handles this by looking at the code, seeing the changes, and orchestrating the swap automatically.

---

### **Azure Kubernetes Service (AKS) & Containers**

**11. How does Azure Kubernetes Service (AKS) differ from a standard Kubernetes setup?**
**Answer:**
With standard Kubernetes, you have to manage the "Control Plane" (the master nodes) yourself—patching, updating, and securing them.
With **AKS**, Azure manages the Control Plane for you. You only manage the "Worker Nodes" (where your applications run). This reduces your operational burden significantly. Azure ensures the master is always up-to-date and secure.

**12. How do you secure communication between Pods in AKS?**
**Answer:**
You use **Network Policies**.
*   **Mechanism:** By default, all Pods can talk to all Pods. A Network Policy is a rule that says "Pod A" can talk to "Pod B", but "Pod C" is blocked. This limits how an attacker can move sideways through your system if they compromise one application.

**13. What is the role of the Azure Container Registry (ACR) in a DevOps pipeline?**
**Answer:**
ACR is a private storage place for your Docker images.
*   **Process:** Your GitHub Action builds the Docker image. Instead of saving it on the build server, it pushes it to ACR. AKS (Kubernetes) then pulls the image from ACR to run the application. This keeps your images secure, private, and version-controlled.

**14. How do you optimize Docker images for AKS deployments?**
**Answer:**
Optimization reduces download time and attack surface.
*   **Technique 1:** Use **Multi-stage builds**. Build the app in a heavy image, but copy the final executable to a tiny, stripped-down image.
*   **Technique 2:** Use **Alpine Linux** or **Distroless** images. These have no extra tools, just the minimum required to run the app.
*   **Technique 3:** Combine `RUN` commands to reduce the number of layers in the image.

**15. How do you configure AKS to automatically scale applications?**
**Answer:**
You use the **Horizontal Pod Autoscaler (HPA)**.
*   **Configuration:** You set a target, for example, "Keep CPU usage at 70%." If traffic increases and CPU goes to 90%, the HPA automatically adds more Pods (copies of the application) to handle the load. When traffic drops, it removes the extra Pods to save money.

---

### **DevSecOps & Security Practices**

**16. What is the difference between SAST and SCA in a security pipeline?**
**Answer:**
*   **SAST (Static Application Security Testing):** Scans the **Source Code**. It looks for bad coding practices, like writing passwords in the code or functions that allow hackers to inject commands.
*   **SCA (Software Composition Analysis):** Scans the **Libraries**. It checks if the external code (packages) you downloaded (like `npm` or `pip` packages) have known security flaws.

**17. How do you implement Vulnerability Scanning in a CI/CD pipeline?**
**Answer:**
You make it a "Gate."
*   **Flow:** In the pipeline, after building the Docker image, you run a scanner (like Trivy).
*   **The Gate:** You configure the pipeline to fail if the scanner finds "High" or "Critical" vulnerabilities. The code stops there and cannot be deployed to production until the vulnerability is fixed.

**18. What is the workflow for an Incident Response in a DevOps environment?**
**Answer:**
*   **Detection:** Monitoring tools (like Azure Monitor) send an alert that a system is down or behaving strangely.
*   **Containment:** Stop the damage. This might mean isolating a server or rolling back the software to the previous version.
*   **Eradication:** Find the root cause (e.g., a bad config or a bug) and fix it.
*   **Post-Mortem:** Write a document explaining what happened, why it happened, and how to prevent it next time.

**19. How do you use "Shifting Left" in security?**
**Answer:**
"Shifting Left" means testing security as early as possible.
*   **Implementation:** Instead of waiting for the code to be deployed to test the security, you run the security scan automatically when the developer writes the code (Pre-commit hook) or when they save it to the repository. This ensures they fix security bugs while they are coding, not weeks later.

**20. How do you manage Access Control (IAM) for Azure Resources securely?**
**Answer:**
You use the principle of **Least Privilege**.
*   **Concept:** A developer should only have the permission to "Read" the data, not "Delete" it. You assign permissions based on the specific job role, not just giving everyone "Admin" access. You review these permissions regularly to remove access that is no longer needed.

---

### **Monitoring, Logging & Scripting**

**21. How do you integrate Azure Monitor with Prometheus and Grafana?**
**Answer:**
*   **Azure Monitor:** Collects data (metrics and logs) from Azure services.
*   **Prometheus:** Can also collect metrics, often from Kubernetes.
*   **Grafana:** Is the visualizer. You connect Grafana to both Azure Monitor and Prometheus as "Data Sources." You then build a dashboard in Grafana that displays a graph showing Azure SQL metrics next to Kubernetes Pod metrics in one single view.

**22. How does the ELK Stack (Elasticsearch, Logstash, Kibana) work?**
**Answer:**
*   **Elasticsearch:** The database that stores the log data.
*   **Logstash:** The processor. It collects logs from servers, filters them, and sends them to Elasticsearch.
*   **Kibana:** The visualization tool. You open Kibana in a browser, type a search query, and it searches the Elasticsearch database to show you the specific logs you need.

**23. Why use PowerShell over Bash for Azure Automation?**
**Answer:**
PowerShell is native to the Microsoft ecosystem.
*   **Advantage:** It has built-in modules (called `Az` modules) that connect directly to Azure APIs. The commands are very readable (e.g., `New-AzVM` to create a VM). While Bash can work with Azure via CLI, PowerShell is often preferred in Windows-heavy enterprise environments like PwC.

**24. Why is the "Go" language mentioned in a DevOps context?**
**Answer:**
**Go** is used to build custom tools and plugins.
*   **Usage:** Many DevOps tools you use today (like Docker, Terraform, and Kubernetes) are actually written in Go. As a DevSecOps engineer, you might use Go to write a small custom command-line tool that integrates with the GitHub API to automate a very specific security check for your company.

**25. How do you handle Logging in Kubernetes?**
**Answer:**
You don't log to the disk of the container because the disk disappears if the container dies.
*   **Solution:** You configure a "Logging Agent" (like Fluentd or Filebeat) as a sidecar next to your application. This agent reads the logs your app writes to the screen (stdout) and sends them to a central place like Azure Monitor or ELK Stack.

---

### **General Architecture & Troubleshooting**

**26. How do you ensure High Availability for an AKS Cluster?**
**Answer:**
*   **Multi-Zone:** You create the AKS cluster across multiple "Availability Zones" (different data centers). If one data center fails, the other zones keep running.
*   **Pod Anti-Affinity:** You tell Kubernetes to put copies of the application on different servers. If one server fails, the other servers still have copies of the app running.

**27. What is the difference between Azure Monitor and Application Insights?**
**Answer:**
*   **Azure Monitor:** The main platform that collects data from the infrastructure (CPU, Memory) and logs.
*   **Application Insights:** A specific feature inside Azure Monitor designed strictly for **Application Performance Monitoring (APM)**. It tracks how fast your code runs, how many users visit, and if there are any exceptions in the code.

**28. How do you troubleshoot a "CrashLoopBackOff" in Kubernetes?**
**Answer:**
This means the application keeps starting and crashing repeatedly.
*   **Step 1:** Run `kubectl logs <pod-name>` to see the error message. (Did the app fail to connect to the database?)
*   **Step 2:** If the logs are empty (because it crashed too fast), use `kubectl logs <pod-name> --previous` to see the logs from the *last* time it ran.
*   **Step 3:** Check if the health check (Liveness Probe) is configured correctly.

**29. How do you manage configuration changes across multiple environments (Dev, Test, Prod)?**
**Answer:**
You use **GitOps** and **Helm**.
*   **Helm Values:** You create one Helm chart (the template). You create separate value files for Dev, Test, and Prod.
*   **GitOps:** You store these configuration files in GitHub. When you want to change the config for Prod, you commit the change to GitHub, and the pipeline applies the change automatically. This ensures you have a history of who changed what and when.

**30. What is your approach to learning a new DevOps tool in a fast-paced environment?**
**Answer:**
*   **Concept First:** I focus on understanding the core problem the tool solves (e.g., "This tool helps me visualize data").
*   **Hands-On:** I install it in a test environment and build a small "Hello World" project.
*   **Documentation:** I use the official documentation to understand the key features, rather than trying to learn everything at once.
*   **Sharing:** Once I understand it, I document it for the team so everyone can learn from my research.
 
