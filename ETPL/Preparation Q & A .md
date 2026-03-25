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

