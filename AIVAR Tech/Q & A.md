# Questions:

### **Category 1: AWS Security & Identity (Deep, not checkbox-level)**
1. **GuardDuty in EKS:** GuardDuty triggers a finding for "Unusual API Activity" from an EKS worker node node profile. Walk me through your exact triage process using CloudTrail and EKS audit logs.
2. **KMS & Data Sovereignty:** For HIPAA compliance on Velogent deployments, how do you design envelope encryption in AWS KMS for EKS secrets, and what is the exact blast radius if a single data key is compromised?
3. **IRSA Edge Case:** You have a GPU workload pod that needs to write to S3. It works with IRSA, but fails intermittently when scaling up via HPA. What AWS IAM or K8s misconfiguration would you investigate first?
4. **Security Hub Aggregation:** Security Hub is noisy. How do you use AWS Config Rules (custom or managed) to automatically suppress findings for accepted risks in dev environments while enforcing strict SLAs in prod?

### **Category 2: Kubernetes & Container Security**
5. **Falco in GPU Clusters:** Falco throws a high-severity alert for a "Node Exec" or unexpected "Kernel Module Load" on an EKS GPU node. How do you differentiate between a legitimate Nvidia device plugin activity and a container escape attempt?
6. **OPA/Gatekeeper Architecture:** Write the logic for an OPA Gatekeeper constraint template that rejects any pod in the `healthcare` namespace attempting to mount the Docker socket or run with `privileged: true`.
7. **Supply Chain Security:** You scan an image with Trivy in CI/CD and it’s clean (no CRITICAL CVEs). How do you ensure an attacker hasn't replaced the image in the registry before deployment? Explain the Sigstore/Cosign workflow.
8. **PSP to PSA Migration:** A legacy Velogent microservice requires `hostPID: true`. How do you handle this in a modern K8s cluster utilizing Pod Security Admission (PSA) without violating SOC2 baseline controls?
9. **K8s Audit Logging:** By default, K8s audit logs are incredibly verbose. How do you configure the audit policy to log `exec` into pods and secret accesses, but ignore `get` requests for configmaps, to prevent SIEM costs from exploding?
10. **EKS Multi-Tenancy:** You have two regulated customers (one HIPAA, one Basel III) sharing a single hardened EKS cluster. How do you enforce namespace-level network and compute isolation to prevent cross-tenant data leakage?

### **Category 3: CI/CD Security & Supply Chain**
11. **Pipeline Sequencing:** In a GitHub Actions workflow, at exactly which stages do you inject SAST (e.g., Semgrep), SCA (Snyk), and Container Scanning (Trivy)? More importantly, how do you prevent a developer from bypassing the SCA step using a PR label?
12. **SCA False Positives:** Snyk flags a critical transitive dependency CVE in your Python app, but the vulnerable function isn't called. SOC2 auditors want it fixed. How do you use automation (like Reachability analysis) to formally document and dismiss this risk?
13. **Security-as-Code:** A developer writes a Terraform module that creates an EKS cluster with public endpoint access enabled. How do you use `tfsec` or `Checkov` in pre-commit hooks to block this commit and generate a Jira ticket?
14. **GitHub Actions Poisoning:** A supply chain attack occurs because a third-party GitHub Action was compromised. How do you mitigate this using Action Pinning (SHA vs. Tag) and OIDC trust policies?

### **Category 4: Secrets Management**
15. **ESO Architecture:** Why use the External Secrets Operator (ESO) instead of native K8s secrets? Explain the synchronization loop and how you prevent a K8s admin from decrypting an AWS Secrets Manager secret just because they have K8s cluster admin rights.
16. **Zero-Downtime Rotation:** A database credential used by a Velogent microservice needs rotating per HITRUST requirements. Walk me through how AWS Secrets Manager triggers a rotation without dropping active HIPAA transactions.
17. **etcd Encryption:** You enable encryption at rest for K8s secrets using the KMS plugin. A developer accidentally deletes the KMS key. What exactly happens to the running cluster and the workloads?
18. **CI/CD Secret Leakage:** A developer hardcodes an AWS key in a GitHub Action script. GitHub scans and deletes it, but it was live for 5 minutes. Walk me through your automated incident response (revoke key, scan code, block merge).

### **Category 5: Network Security & Zero Trust**
19. **mTLS Implementation:** How do you implement mTLS between microservices in EKS? If a service's certificate expires, how does the mutual authentication failover work without taking down the payment pipeline?
20. **Egress Control:** HIPAA requires preventing data exfiltration. How do you restrict a specific pod in EKS from initiating outbound connections to the internet while still allowing it to pull images from a private ECR?
21. **WAF Tuning:** AWS WAF blocks a legitimate JSON payload from a customer hitting the Velogent API (False Positive). How do you tune the rule without opening up a SQL injection vulnerability?
22. **Zero Trust Networking:** Explain how you combine AWS Security Groups, K8s Network Policies (Cilium/Calico), and Service Mesh to achieve a true Zero Trust architecture for an EKS GPU workload.

### **Category 6: Compliance Automation (SOC 2, HIPAA, HITRUST, GxP)**
23. **Drata/Vanta Integration:** Vanta flags an EKS cluster as "Non-Compliant" because it can't verify that Container Insights logs are being sent to CloudWatch. How do you automate the evidence collection for this specific control?
24. **Automated Evidence for GxP:** GxP requires immutable records. How do you prove to an auditor that no one SSH'd into an EKS node or executed a shell inside a production pod in the last 6 months?
25. **HIPAA PHI Access:** How do you set up an automated alert via Prometheus/Grafana or CloudWatch that triggers when an IAM role not belonging to the `healthcare-group` queries the RDS instance containing PHI?
26. **Continuous Control Validation:** HITRUST requires quarterly vulnerability scans. How do you integrate Inspector/Trivy scans with a CMDB to ensure 100% of the asset inventory is scanned, including transient EKS nodes?

### **Category 7: Vulnerability Management & Observability**
27. **Risk Prioritization:** You have 500 Trivy vulnerabilities across Velogent. One is CVSS 9.8 but in an internal library not exposed to the network; another is CVSS 7.5 in the public-facing NGINX ingress. How do you automate this risk prioritization using EPSS or context-aware tools?
28. **Correlating Alerts:** GuardDuty alerts on an IAM anomaly, Falco alerts on a reverse shell in a container, and Prometheus shows a CPU spike—all within 2 minutes. How do you correlate these three distinct data sources in your SIEM to confirm a breach?
29. **Patch SLA Automation:** A critical zero-day drops affecting the Nvidia GPU driver in your EKS nodes. Your SLA is 24 hours. Walk me through the automated Terraform/node-drain workflow to patch this without human intervention.
30. **Shift-Left vs. Runtime:** If you had to choose between investing budget in shift-left CI/CD scanning (SAST/DAST) or runtime security (Falco/SIEM) for a brand new accelerator, how would you justify your choice to the CTO based on the regulated nature of AIVAR's clients?

---

# Answers:

**1. GuardDuty in EKS:** GuardDuty triggers a finding for "Unusual API Activity" from an EKS worker node node profile. Walk me through your exact triage process using CloudTrail and EKS audit logs.

**Answer:** 
When an alert pops up, the first step is to look at AWS CloudTrail. Think of CloudTrail as a security camera for the AWS account—it shows exactly who did what and when. Next, check the Kubernetes (EKS) audit logs. This shows if someone inside a pod tried to run unauthorized commands. The goal is to match the AWS action with the Kubernetes action to see if a hacker is trying to jump from a container into the main AWS account.

**2. KMS & Data Sovereignty:** For HIPAA compliance on Velogent deployments, how do you design envelope encryption in AWS KMS for EKS secrets, and what is the exact blast radius if a single data key is compromised?

**Answer:** 
Envelope encryption means using a master key to lock smaller data keys, and those smaller keys actually lock the secret passwords. If a hacker steals one small data key, the damage (blast radius) is very small. They can only read that one specific secret. They absolutely cannot use the small key to reverse-engineer the master key or steal other secrets.

**3. IRSA Edge Case:** You have a GPU workload pod that needs to write to S3. It works with IRSA, but fails intermittently when scaling up via HPA. What AWS IAM or K8s misconfiguration would you investigate first?

**Answer:** 
IRSA gives a pod an ID card to talk to AWS safely. When scaling up creates new pods quickly, failures usually happen for two reasons. First, the IAM role's "trust policy" might have a strict typo in the Kubernetes service account name. Second, the cluster might simply be running out of IP addresses, so the new pod cannot get a network connection to reach AWS to show its ID card.

**4. Security Hub Aggregation:** Security Hub is noisy. How do you use AWS Config Rules (custom or managed) to automatically suppress findings for accepted risks in dev environments while enforcing strict SLAs in prod?

**Answer:** 
Security tools can send too many warning emails. To fix this, use "Tags" on AWS resources. A tag is just a label, like "Environment: Dev". Then, write a rule that says: "If a resource has the Dev tag, ignore low-level warnings." But if the tag says "Environment: Prod", the rule strictly enforces all security laws and creates urgent repair tickets.

**5. Falco in GPU Clusters:** Falco throws a high-severity alert for a "Node Exec" or unexpected "Kernel Module Load" on an EKS GPU node. How do you differentiate between a legitimate Nvidia device plugin activity and a container escape attempt?

**Answer:** 
Falco watches what programs do inside containers. Sometimes, good programs (like Nvidia graphics drivers) need to do special system tasks that look exactly like hacker behavior. To stop fake alerts, Falco allows creating "exception lists." If the alert comes specifically from the official Nvidia program, Falco ignores it. If it comes from an unknown program, it triggers a real hacker alert.

**6. OPA/Gatekeeper Architecture:** Write the logic for an OPA Gatekeeper constraint template that rejects any pod in the `healthcare` namespace attempting to mount the Docker socket or run with `privileged: true`.

**Answer:** 
OPA Gatekeeper acts like a security guard at the door of Kubernetes. Before a pod is allowed to start, the guard checks its rulebook. The logic simply says: "Look at the request. If the pod is trying to enter the 'healthcare' room, AND it asks for 'privileged: true' (full admin power) or asks to use the 'Docker socket' (control over the whole computer), reject it immediately."

**7. Supply Chain Security:** You scan an image with Trivy in CI/CD and it’s clean (no CRITICAL CVEs). How do you ensure an attacker hasn't replaced the image in the registry before deployment? Explain the Sigstore/Cosign workflow.

**Answer:** 
Scanning only checks for software bugs, not tampering. To prove an image was not swapped by a hacker, a digital signature is used. When the developer builds the image, a tool called Cosign locks it with a secret key. When Kubernetes pulls the image to run it, it checks the lock. If the lock is broken or missing, Kubernetes refuses to run the image.

**8. PSP to PSA Migration:** A legacy Velogent microservice requires `hostPID: true`. How do you handle this in a modern K8s cluster utilizing Pod Security Admission (PSA) without violating SOC2 baseline controls?

**Answer:** 
`hostPID: true` means the pod can see everything running on the underlying computer, which is a big security risk. To handle this safely, move that specific pod to a dedicated, isolated computer (node). Then, apply a "warning" security label to that specific area, while applying a "strict" security label to the rest of the cluster. This keeps the old, badly behaved app in a sandbox.

**9. K8s Audit Logging:** By default, K8s audit logs are incredibly verbose. How do you configure the audit policy to log `exec` into pods and secret accesses, but ignore `get` requests for configmaps, to prevent SIEM costs from exploding?

**Answer:** 
Audit logs record every single action, which costs a lot of money to store. To save money, write a filter policy. Tell the system: "Only save logs if someone runs a command inside a pod (`exec`) or reads a password (`secret`). Ignore everything else, like reading normal settings (`configmaps`)." This keeps the log storage small and cheap.

**10. EKS Multi-Tenancy:** You have two regulated customers (one HIPAA, one Basel III) sharing a single hardened EKS cluster. How do you enforce namespace-level network and compute isolation to prevent cross-tenant data leakage?

**Answer:** 
Sharing a cluster is like sharing an apartment building. To keep tenants safe, use Network Policies. This acts like an invisible wall between apartments (namespaces), so Customer A absolutely cannot send data to Customer B. For compute limits, use "Resource Quotas" to ensure Customer A cannot use up all the memory and crash Customer B's apps.


