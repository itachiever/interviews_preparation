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


11. **Question:** How do you implement rollbacks in a CI/CD pipeline, and what strategies can be used to minimize downtime during deployments?  
    **Answer:**  
    - Keep every artifact and deployment versioned so any version can be re‑deployed quickly.  
    - Use deployment strategies like blue‑green, rolling, or canary releases so a previous version stays available while the new one is tested.  
    - Automate health checks and use them as gates; if checks fail, the pipeline should automatically switch traffic back to the last good version.  
    - Store database migrations carefully and, where possible, support backward‑compatible changes to avoid data issues during rollback.  

12. **Question:** How should Jenkins itself be architected for a growing team (controller/agents, folder structure, credentials management)?  
    **Answer:**  
    - Use a dedicated controller (master) mainly for orchestration, and run builds on separate agents (static or auto‑scaling) to improve performance and isolation.  
    - Organize jobs into folders by product/team/environment so access and configuration are easy to manage.  
    - Store credentials centrally in Jenkins credentials store or an external vault, and inject them into jobs only when needed.  
    - Apply role‑based access control so teams can manage their own jobs without touching global configuration.  

13. **Question:** What problem does containerization solve compared to deploying directly on VMs, especially for a microservices‑based platform?  
    **Answer:**  
    - Containers bundle application and dependencies into a consistent unit, avoiding “works on my machine” issues across environments.  
    - They start and stop much faster than full VMs, which helps with scaling and recovery.  
    - For microservices, containers make it easier to run many small, isolated services on shared infrastructure.  
    - Images provide an immutable, versioned artifact that fits well with CI/CD and security scanning.  

14. **Question:** Explain the lifecycle of a container image from code commit to running in production, including registry and scanning.  
    **Answer:**  
    - A change is committed and triggers the CI pipeline, which builds a container image from a Dockerfile.  
    - The image is tagged with a version or commit ID, scanned for vulnerabilities, and then pushed to a container registry.  
    - Deployment tools (Kubernetes, compose, or scripts) pull the image from the registry and start containers in target environments.  
    - Monitoring and logging track the running containers, and new versions repeat the same flow while old images can be rolled back if needed.  

15. **Question:** How can deployment of multiple microservices behind a single public endpoint be designed, and what role do reverse proxies or ingress play?  
    **Answer:**  
    - A single public endpoint (like a load balancer) forwards traffic to a reverse proxy or ingress layer.  
    - The reverse proxy/ingress inspects the request (host name or path) and routes it to the correct microservice.  
    - This allows one external entry point while keeping internal services separate and hidden.  
    - It also centralizes features like TLS termination, rate limiting, and authentication at the gateway layer.  

16. **Question:** Conceptually, how can the relationship between Deployments, Pods, Services, and Ingress in Kubernetes be explained?  
    **Answer:**  
    - A Deployment defines the desired state for application instances (how many replicas, which image, update strategy).  
    - Pods are the actual running instances of the containers that the Deployment manages.  
    - A Service provides a stable virtual IP and DNS name to access a group of Pods, handling basic load balancing.  
    - Ingress exposes HTTP/HTTPS routes from outside the cluster to Services, acting like an application‑level gateway.  

17. **Question:** In a Kubernetes‑based SaaS platform, how are configuration, secrets, and per‑environment differences handled?  
    **Answer:**  
    - Non‑sensitive configuration is stored in ConfigMaps, and sensitive values (passwords, keys) are stored in Secrets.  
    - Different environments (DEV, UAT, PROD) use separate namespaces or clusters with their own ConfigMaps and Secrets.  
    - Helm charts or Kustomize overlays can be used to keep a common base and only override environment‑specific values.  
    - Access to Secrets is restricted by RBAC so only authorized Pods and users can read them.  

18. **Question:** What strategies can be used in Kubernetes (or even with plain Docker + load balancer) to achieve zero‑downtime deployments?  
    **Answer:**  
    - Rolling updates gradually replace old instances with new ones while keeping enough healthy replicas serving traffic.  
    - Blue‑green deployments run old and new versions side by side, then switch traffic in one step when the new one is validated.  
    - Canary releases send a small percentage of traffic to the new version first, then increase gradually if metrics look good.  
    - Health checks and readiness probes ensure traffic only goes to containers that are fully initialized and ready.  

19. **Question:** Why is infrastructure‑as‑code important for a company scaling a SaaS platform, and what risks does it reduce?  
    **Answer:**  
    - IaC keeps infrastructure definitions in version control, making changes reviewable, auditable, and reproducible.  
    - It reduces configuration drift between environments because the same code is applied everywhere.  
    - It enables faster, consistent environment creation for new regions, tenants, or test setups.  
    - It reduces the risk of manual errors and undocumented “snowflake servers” that no one knows how to rebuild.  

20. **Question:** How can Terraform or similar IaC be structured for multiple environments to avoid duplication but still keep isolation?  
    **Answer:**  
    - Common pieces (like VPC, database, app stack) are written as reusable modules.  
    - Each environment has its own configuration files that call these modules with different variables (names, sizes, CIDRs).  
    - Separate state files or backends per environment keep resources isolated and safer to manage.  
    - Naming conventions and tagging help distinguish resources while keeping most of the code shared.  

21. **Question:** What does “baseline security architecture” mean at the infrastructure level (network, access, data protection)?  
    **Answer:**  
    - A baseline security architecture is the minimum set of security controls that every environment must follow.  
    - At network level, it means private subnets, restricted inbound rules, only necessary ports open, and segmentation between tiers.  
    - For access, it means strong authentication, least‑privilege roles, and separation of duties.  
    - For data, it means encryption in transit and at rest, proper key management, and secure backups.

22. **Question:** How can security scanning (SAST, SCA, container scanning, secret scanning) be integrated into a CI/CD pipeline without blocking developers unnecessarily?  
    **Answer:**  
    - Run fast checks (SCA, secret scanning, lightweight SAST rules) on every commit or merge request to give quick feedback.  
    - Run deeper scans (full SAST, container scans) on main branches or nightly pipelines.  
    - Use severity thresholds and allow low‑risk issues to pass while failing builds only for critical/high issues.  
    - Provide clear reports and links so developers can fix problems quickly instead of just seeing a “failed” status.

23. **Question:** In a fintech or sensitive domain, what are the main concerns around secrets management in pipelines and runtime environments?  
    **Answer:**  
    - Secrets must never be stored in plain text in code, config files, or logs.  
    - Pipelines should fetch secrets from a secure vault or secret store, and only when needed.  
    - Access to secrets must be audited and limited to specific services and users.  
    - Rotation policies and emergency revocation must be in place in case a secret is exposed.

24. **Question:** How can messaging/streaming systems like Kafka or RabbitMQ change the threat model or architecture for a microservices platform?  
    **Answer:**  
    - They introduce central components (brokers) that, if compromised, can expose a lot of data or allow message tampering.  
    - Access control on topics/queues becomes important so services only see what they should.  
    - Encryption in transit and sometimes at rest is needed, because messages can contain sensitive business events.  
    - From an architecture view, they decouple services, which improves resilience but also adds new places to monitor and secure.

25. **Question:** What are the most important metrics and logs to monitor for a multi‑service SaaS platform to ensure reliability?  
    **Answer:**  
    - At application level: request rate, error rate, and latency (the classic “RED” metrics).  
    - At infrastructure level: CPU, memory, disk I/O, network usage, and node/pod health.  
    - At business level: key flows like login success rate or payment success rate.  
    - Centralized logs for all services, with correlation IDs, help trace a single request across multiple microservices.

26. **Question:** How is a root cause analysis (RCA) run after a production outage caused by a bad deployment?  
    **Answer:**  
    - First stabilize the system (rollback or hotfix), then capture timelines, logs, and metrics around the incident.  
    - Identify what changed (code, config, infra) and how that change led to the failure.  
    - Document technical root cause, contributing factors (testing gaps, missing alerts), and the user impact.  
    - Define corrective actions (tests, checks, process changes) and track them until completed to prevent repeat incidents.

27. **Question:** How can a backup and restore strategy be designed for an application with both relational databases and file/object storage?  
    **Answer:**  
    - For relational databases, use automated backups and snapshots with a retention policy aligned to RPO/RTO.  
    - For object/file storage, use versioning and lifecycle rules to keep past versions and protect against accidental deletion.  
    - Regularly test restore procedures in a non‑production environment to validate that backups are usable.  
    - Document clear runbooks so restoration steps are known and not invented during an emergency.

28. **Question:** As a Senior DevOps engineer, how is collaboration with development, QA, and security teams handled to improve delivery speed without losing stability?  
    **Answer:**  
    - Work with development to define standards for branching, testing, and deployment so pipelines are predictable.  
    - Partner with QA to automate as many tests as possible and place them early in the pipeline.  
    - Integrate security checks into the pipeline and review results with the security team instead of treating them as a separate gate at the end.  
    - Share observability dashboards and incident learnings so all teams see the same reality and improve together.

29. **Question:** In what scenario should a Senior DevOps engineer push back on a risky deployment or design decision, and how should that conversation be handled?  
    **Answer:**  
    - Push back when a change violates basic safety, such as skipping tests, ignoring critical security findings, or deploying without rollback options.  
    - Explain the risk in simple terms: what can break, who will be affected, and how hard it will be to fix.  
    - Offer safer alternatives, like doing a canary release, enabling feature flags, or adding specific tests first.  
    - Keep the discussion focused on system reliability and user impact, not on blame.

30. **Question:** Why is role‑based access control (RBAC) important in tools like Jenkins, Kubernetes, and cloud platforms for a scaling company?  
    **Answer:**  
    - RBAC ensures people and services get only the permissions they actually need.  
    - It reduces the blast radius if a user account, API token, or service is compromised.  
    - It makes audits and compliance easier because access can be reviewed and justified per role.  
    - As teams grow, RBAC avoids “everyone is admin” situations that lead to mistakes and security issues.

