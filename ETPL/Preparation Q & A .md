# 30 concept‑centric questions

***

### Cloud, HA, and architecture

1. How would you design a highly available web application on AWS or Azure, starting from VPC/VNet, subnets, and load balancers?  
2. What is the difference between high availability and disaster recovery, and how do RPO and RTO influence your design choices?  
3. How would you securely connect an on‑prem CI/CD system to a cloud environment for deployments (for example, via VPN and DMZ)?  
4. In a multi‑environment setup (DEV/SIT/UAT/PROD), how do you isolate environments at the cloud networking level?  
5. What considerations go into choosing between managed DB services (like RDS/Azure SQL) versus self‑hosted databases on VMs?

***

### Linux and system administration

6. Walk through how you would troubleshoot a Linux server where “application is slow” but there’s no obvious error in the logs.  
7. How do you investigate high CPU or memory usage on a Linux host, and what tools/commands would you use?  
8. What are typical hardening steps you apply on Linux servers that host production workloads?

***

### CI/CD and Jenkins

9. How would you design a CI/CD pipeline in Jenkins for a SaaS product that has multiple environments and frequent releases?  
10. What are the key stages you would include in a robust pipeline (build, test, quality, security, deploy), and why?  
11. How do you implement rollbacks in a CI/CD pipeline, and what strategies can be used to minimize downtime during deployments?  
12. How would you architect Jenkins itself for a growing team (controller/agents, folder structure, credentials management)?

***

### Containers and microservices

13. What problem does containerization solve compared to deploying directly on VMs, especially for a microservices‑based platform?  
14. Explain the lifecycle of a container image from code commit to running in production, including registry and scanning.  
15. How would you design the deployment of multiple microservices behind a single public endpoint, and what role do reverse proxies or ingress play?

***

### Kubernetes (even though the JD stresses Docker)

16. Conceptually, how would you explain the relationship between Deployments, Pods, Services, and Ingress in Kubernetes?  
17. In a Kubernetes‑based SaaS platform, how do you handle configuration, secrets, and per‑environment differences?  
18. What strategies can be used in Kubernetes (or even with plain Docker + LB) to achieve zero‑downtime deployments?

***

### IaC, automation, and Ansible

19. Why is infrastructure‑as‑code important for a company scaling a SaaS platform, and what risks does it reduce?  
20. How would you structure Terraform or similar IaC for multiple environments to avoid duplication but still keep isolation?  
21. What types of tasks are best handled by Ansible or similar configuration management tools in a DevOps setup?

***

### Security and DevSecOps

22. What does “baseline security architecture” mean for you at the infrastructure level (network, access, data protection)?  
23. How would you integrate security scanning (SAST, SCA, container scanning, secret scanning) into a CI/CD pipeline without blocking developers unnecessarily?  
24. In a fintech or sensitive domain, what are your main concerns around secrets management in pipelines and runtime environments?  
25. How can messaging/streaming systems like Kafka or RabbitMQ change the threat model or architecture for a microservices platform?

***

### Monitoring, observability, incidents, and backup/DR

26. What are the most important metrics and logs you would monitor for a multi‑service SaaS platform to ensure reliability?  
27. Describe how you would run a root cause analysis (RCA) after a production outage caused by a bad deployment.  
28. How would you design a backup and restore strategy for an application with both relational databases and file/object storage?

***

### Collaboration, ownership, and ways of working

29. As a Senior DevOps engineer, how do you collaborate with development, QA, and security teams to improve delivery speed without compromising stability?  
30. Give an example scenario where you would push back on a risky deployment or design decision, and how you would handle that conversation.

---

# Answers:


1. **Question:** How would you design a highly available web application on AWS or Azure, starting from VPC/VNet, subnets, and load balancers?  
   **Answer:**  
   - Start with a VPC/VNet split into public and private subnets across at least two AZs/regions for redundancy.  
   - Place load balancers in public subnets, and app servers/containers in private subnets so they are not directly exposed to the internet.  
   - Use auto scaling groups or VM scale sets for app nodes so instances can scale and recover automatically.  
   - Keep databases in private subnets with multi‑AZ or replica setups, and connect everything with security groups/NSGs instead of open ports.  

2. **Question:** What is the difference between high availability and disaster recovery, and how do RPO and RTO influence design choices?  
   **Answer:**  
   - High availability focuses on keeping the system running during normal failures (node crash, AZ failure) using redundancy and failover in the same region.  
   - Disaster recovery deals with rare, big failures (region down, data center loss) using backups, replicas, and a secondary site/region.  
   - RPO (Recovery Point Objective) defines how much data loss is acceptable; smaller RPO means more frequent backups/replication.  
   - RTO (Recovery Time Objective) defines how fast the system must be back; smaller RTO means more automation, pre‑provisioned standby resources, and tested runbooks.  

3. **Question:** How would a secure connection be built between an on‑prem CI/CD system and a cloud environment for deployments (for example, via VPN and DMZ)?  
   **Answer:**  
   - Set up a site‑to‑site VPN or private connectivity (like ExpressRoute/Direct Connect) between on‑prem and cloud VPC/VNet so traffic flows over encrypted tunnels.  
   - Place a DMZ or gateway layer that exposes only the minimal endpoints needed (for example, an ingress/API or a limited Jenkins agent endpoint).  
   - Restrict traffic with firewall rules and security groups/NSGs so only specific ports and IPs are allowed between CI/CD and target subnets.  
   - Use strong identity and secrets management for deployment credentials, avoiding hard‑coded keys in jobs.  

4. **Question:** In a multi‑environment setup (DEV/SIT/UAT/PROD), how can environments be isolated at the cloud networking level?  
   **Answer:**  
   - Use separate VPCs/VNets or separate subnets and route tables per environment so traffic is logically segmented.  
   - Apply different security groups/NSGs per environment so only allowed paths exist (for example, UAT can access shared services, DEV cannot reach PROD).  
   - Use separate peering or VPN connections if needed, and avoid sharing databases between environments.  
   - Tag and manage resources by environment for easier policy enforcement and cost tracking.  

5. **Question:** What considerations go into choosing between managed database services (like RDS/Azure SQL) versus self‑hosted databases on VMs?  
   **Answer:**  
   - Managed services handle backups, patching, failover, and monitoring, which reduces operational effort and improves reliability.  
   - Self‑hosted databases give more control over configuration and versioning but require full responsibility for HA, backups, and tuning.  
   - Compliance, licensing, and cost models might push toward one or the other.  
   - For most SaaS use cases, managed DBs are preferred unless there are very specific customization or regulatory needs.  

6. **Question:** How can a slow Linux server be troubleshooted when the application shows no clear errors in logs?  
   **Answer:**  
   - First check system health: CPU, memory, load average, disk I/O, and network usage using tools like `top`, `htop`, `vmstat`, `iostat`, and `ss`.  
   - Look for resource bottlenecks such as high CPU on a specific process, memory pressure causing swapping, or high disk wait times.  
   - Check OS logs (`/var/log/*`) and specific service logs for warnings like OOM kills, restarts, or file system errors.  
   - Confirm external dependencies (DB, cache, network) are reachable and performing well, since slowness can come from downstream systems.  

7. **Question:** How can high CPU or memory usage on a Linux host be investigated, and which tools are useful?  
   **Answer:**  
   - Use `top` or `htop` to identify which processes consume the most CPU or memory.  
   - Use `ps` with filters to inspect suspicious processes and check how long they have been running and with what arguments.  
   - For memory issues, look at swap usage, cache, and potential memory leaks; for CPU, check if it is user CPU, system CPU, or wait time.  
   - Combine this with logs and application metrics to see whether the load is legitimate (traffic spike) or due to a bug (infinite loops, leaks).  

8. **Question:** What common hardening steps are applied on Linux servers that host production workloads?  
   **Answer:**  
   - Disable password logins and use key‑based SSH with limited allowed users and IPs.  
   - Close unused ports and services, and use a firewall and security groups/NSGs to restrict network access.  
   - Keep packages updated, remove unnecessary software, and enforce least‑privilege for system and application users.  
   - Enable logging and auditing, and protect sensitive files with proper permissions and, where needed, disk or directory encryption.  

9. **Question:** How can a CI/CD pipeline in Jenkins be designed for a SaaS product that has multiple environments and frequent releases?  
   **Answer:**  
   - Use a single pipeline per service that moves artifacts through DEV → SIT → UAT → PROD using stages and environment‑specific configurations.  
   - Trigger builds on commit or merge, run tests and quality checks, then publish versioned artifacts to a registry or repository.  
   - Use manual approvals or checks before higher environments (UAT/PROD) while keeping lower env deployments fully automated.  
   - Store environment settings and secrets outside the code (credentials store, parameterized jobs, config files) so the same artifact is promoted across environments.  

10. **Question:** What key stages should exist in a robust Jenkins pipeline (build, test, quality, security, deploy), and why are they important?  
    **Answer:**  
    - Build: compile/package and produce a consistent artifact or image so the same build is used everywhere.  
    - Test: run unit/integration tests to catch functional issues early.  
    - Quality: run code quality and style checks to keep the codebase maintainable and reduce long‑term technical debt.  
    - Security: run SAST/SCA/container/secret scans to catch vulnerabilities before production.  
    - Deploy: perform automated, repeatable deployments with proper checks and rollback options, reducing human error and downtime.  



