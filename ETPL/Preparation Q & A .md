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

1. **How would you design a highly available web application on AWS or Azure, starting from VPC/VNet, subnets, and load balancers?**  
High availability starts with isolating the application in at least two availability zones inside a single VPC/VNet. Public subnets host only entry points like load balancers or API gateways, while application servers and databases stay in private subnets. The load balancer distributes traffic across instances or containers in multiple AZs and performs health checks to route away from unhealthy nodes. Databases use managed multi‑AZ or replica configurations, and stateless app nodes are placed behind autoscaling groups or scale sets so they can be replaced automatically on failure.

2. **What is the difference between high availability and disaster recovery, and how do RPO and RTO influence design choices?**  
High availability focuses on staying up during localized failures (like a single node or AZ going down) by adding redundancy and automatic failover within the primary region. Disaster recovery assumes the primary region or major components are lost and defines how to bring the system back in another location. RPO (how much data loss is acceptable) drives the frequency of backups or replication, while RTO (how fast the system must be restored) influences whether to use warm/active‑active environments or cold standby; tighter RPO/RTO means more automation, more replication, and higher cost.

3. **How would you securely connect an on‑prem CI/CD system to a cloud environment for deployments (for example, via VPN and DMZ)?**  
A secure setup keeps the CI/CD system inside the internal network and exposes only minimal endpoints through a DMZ. A site‑to‑site VPN or private connectivity (like Direct Connect/ExpressRoute) is established between the on‑prem network and cloud VPC/VNet, with routing restricted to only required subnets and ports. Security groups/NSGs and firewall rules allow traffic only from CI/CD IP ranges to specific deployment endpoints such as Kubernetes API servers or bastion hosts. All sensitive traffic uses encrypted channels, and no inbound access from the cloud back into CI/CD is allowed other than what is strictly necessary.

4. **In a multi‑environment setup (DEV/SIT/UAT/PROD), how do you isolate environments at the cloud networking level?**  
Each environment typically has its own VPC/VNet or at least dedicated subnets and security boundaries. Network ACLs, security groups/NSGs, and routing rules are configured so that lower environments cannot directly reach production components. Shared services, such as centralized logging or artifact repositories, are accessed via tightly controlled endpoints or peering, not open flat networks. This separation ensures configuration mistakes or testing in non‑prod cannot accidentally impact production workloads.

5. **What considerations go into choosing between managed DB services (like RDS/Azure SQL) versus self‑hosted databases on VMs?**  
Managed databases handle backups, patching, failover, and some scaling automatically, reducing operational burden and lowering the chance of misconfiguration for critical features like encryption and replication. Self‑hosted databases offer more control over configuration, extensions, and custom clustering models but increase responsibility for monitoring, patching, HA, and DR. The decision depends on compliance requirements, need for advanced features, existing team expertise, and whether the team prefers to invest effort in infra management or focus on application features.

6. **Walk through how you would troubleshoot a Linux server where “application is slow” but there’s no obvious error in the logs.**  
Troubleshooting starts with checking system resource usage: CPU, memory, load average, disk I/O, and network using tools like top/htop, vmstat, iostat, and ss. If resources are constrained, the next step is identifying which processes are consuming them and whether there is contention such as high I/O wait or frequent context switches. If system resources look healthy, attention shifts to external dependencies like database latency, upstream/downstream services, or DNS, often visible through connection counts and response times. Finally, application‑level metrics and profiling help find issues such as thread exhaustion, connection pool limits, or inefficient queries.

7. **How do you investigate high CPU or memory usage on a Linux host, and what tools/commands would you use?**  
High CPU is first checked with tools like top or htop to see which processes and threads are consuming CPU and whether it is user, system, or I/O wait time. For deeper insight, utilities like pidstat, perf, or stack traces can reveal hot paths or tight loops. Memory issues are examined using free, vmstat, and tools such as smem or pmap to identify processes with large RSS or memory leaks. Swap usage, cached memory, and OOM events in system logs indicate whether the system is under real pressure or just aggressively caching.

8. **What are typical hardening steps applied on Linux servers that host production workloads?**  
Typical hardening includes disabling password‑based SSH logins in favor of key‑based access, restricting SSH to specific users or bastion hosts, and turning off unused services. File permissions are tightened, sudo access is minimized, and logs are forwarded to centralized logging for audit. Kernel parameters and firewall rules (iptables/nftables/security groups) are configured to restrict inbound and outbound traffic, while automatic security updates or patching processes are put in place to reduce known vulnerabilities.

9. **How would you design a CI/CD pipeline in Jenkins for a SaaS product that has multiple environments and frequent releases?**  
A typical design includes a single reusable pipeline template that runs build, unit tests, static analysis, security scans, and packaging once, producing versioned artifacts stored in an artifact repository or registry. Promotion to environments (DEV, SIT, UAT, PROD) is done by reusing the same artifact with environment‑specific configuration and approvals, not rebuilding code. Each stage includes automated checks and optionally manual gates for higher environments, with deployment steps automated through scripts, IaC, or Kubernetes manifests. The pipeline is parameterized to support different services and environments while keeping governance and visibility centralized.

10. **What are the key stages you would include in a robust pipeline (build, test, quality, security, deploy), and why?**  
The build stage compiles code and packages artifacts to ensure the codebase is in a deployable state. Test stages (unit, integration, and possibly smoke tests) validate functionality early to catch regressions before they reach higher environments. Quality and coverage checks enforce coding standards, complexity limits, and minimum test coverage, improving long‑term maintainability. Security stages such as SAST, SCA, and container scanning catch vulnerabilities and misconfigurations before deployment. Finally, deployment and post‑deployment verification stages roll out the change, run health checks or smoke tests in the target environment, and provide automatic rollback paths if something fails.

