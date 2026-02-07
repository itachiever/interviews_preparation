Devops Engineer

 Key Responsibilities :
 1. Kubernetes Operations 
     ● Manage and operate Kubernetes clusters (EKS/GKE/AKS) for microservices. 
     ● Handle deployments, rollout strategies, scaling, and basic cluster maintenance. 
     ● Configure workloads, ingress, services, ConfigMaps, secrets, and RBAC. 
     ● Troubleshoot pod failures, networking issues, and resource utilization problems. 
 2. Cloud Infrastructure Support
     ● Work on AWS cloud services including EC2, VPC, IAM, Load Balancers, and storage. 
     ● Support infra provisioning using Terraform or Pulumi. 
     ● Assist in implementing security best practices, scaling, HA setups, and networking configurations. 
     ● Take responsibility for day-to-day cloud operations, monitoring, and issue resolution. 
 3. CI/CD Pipeline Maintenance 
     ● Build, maintain, and improve CI/CD pipelines (Jenkins / TeamCity). 
     ● Automate builds, tests, and deployments for microservices. 
     ● Work with developers to troubleshoot pipeline failures. 
     ● Implement reusable templates and enforce pipeline best practices. 
 4. Observability & Monitoring 
     ● Maintain and operate monitoring and logging systems (Prometheus, Grafana, Loki, CloudWatch, etc.). 
     ● Configure dashboards, alerts, and metrics to monitor service health and performance. 
     ● Participate in on-call/incident support (if required in contract). 
 5. Automation & Scripting 
     ● Write scripts (Python/Bash/Go) to automate repetitive tasks. 
     ● Improve deployment processes, infra provisioning, and operational workflows. 
     ● Contribute to internal tools and utilities. 
 6. Security & Compliance Assistance 
     ● Support IAM configurations, secret management, and vulnerability remediation. 
     ● Ensure basic Kubernetes and cloud security hygiene. 
     ● Work with security teams to fix compliance gaps. 

 What You’ll Bring Technical Skills 
 ● 2+ years of solid DevOps experience. 
 ● Practical experience working with Kubernetes in production or staging environments. 
 ● Good understanding of containers, pods, deployments, services, ingress, RBAC. 
 ● Hands-on knowledge of CI/CD tooling. 
 ● Familiarity with cloud platforms (only AWS). 
 ● Experience with IaC tools like Terraform/Pulumi. 
 ● Strong scripting skills (Bash/Python). 
 ● Understanding of monitoring systems and logs. 

 Soft Skills 
 ● Strong sense of ownership and ability to work independently. 
 ● Good communication and team collaboration. 
 ● Problem-solving mindset and willingness to learn advanced DevOps concepts. 

Preferred Qualifications 
 ● Experience with service mesh, advanced CNI, or multi-cluster setups. 
 ● Exposure to distributed systems or high-scale environments. 
 ● Certifications such as CKA/CKAD or cloud associate-level certs.
<img width="1169" height="1476" alt="image" src="https://github.com/user-attachments/assets/a9c41cc4-ddd0-4528-95d5-23094eed21f5" />


**Below are interview-ready answers**

---

### 1. Walk me through your profile — current role, key responsibilities, major projects, and the tech stack you actively work with.

I’m currently working as a **DevSecOps / Platform Engineer** with around **4 years of experience**, supporting cloud-native applications in production. My responsibilities include **designing and maintaining CI/CD pipelines**, managing **Kubernetes clusters**, automating **cloud infrastructure using Terraform**, and ensuring **security is embedded into the SDLC**.

I’ve worked on enterprise-scale projects involving **microservices deployed on Kubernetes**, both on **AWS and Azure**, supporting multiple environments like DEV, UAT, and PROD. My active tech stack includes **AWS (EC2, EKS, VPC, IAM, ALB/NLB)**, **Kubernetes, Docker, Helm**, **Jenkins**, **Terraform**, **Python/Bash scripting**, and **monitoring tools like Prometheus, Grafana, ELK, and CloudWatch**.

---

### 2. Describe the kind of environments you have supported — production, staging, scale, uptime expectations.

I have primarily supported **production and pre-production environments** where uptime and stability are critical. These environments typically host **business-critical microservices** with **24/7 availability expectations**.

Production clusters are designed with **high availability**, multiple node groups, autoscaling, monitoring, alerting, and strict access controls. Lower environments like DEV and UAT are used for testing and validation but still follow the same architecture to avoid surprises in production. We follow **SLAs and SLOs**, and production issues are handled through **incident response and on-call rotations**.

---

### 3. Explain Kubernetes architecture from a platform engineer’s perspective.

From a platform perspective, Kubernetes consists of a **control plane** and **worker nodes**. The control plane manages the desired state of the cluster, while worker nodes run the actual workloads.

The control plane exposes APIs, maintains cluster state, schedules pods, and ensures reconciliation. Worker nodes run **kubelet**, **container runtime**, and **kube-proxy**, which together ensure containers are started, networked, and monitored. As a platform engineer, my focus is on **cluster stability, security, networking, scaling, and observability**, not just deploying applications.

---

### 4. How do control plane components interact with worker nodes internally?

All interactions happen **through the kube-apiserver**. Worker node components like **kubelet** continuously communicate with the API server to fetch pod specs and report node status.

The **scheduler** assigns pods to nodes by updating the API server. The **controller manager** monitors cluster state and triggers corrective actions if the actual state differs from the desired state. The **etcd** stores all cluster metadata. Worker nodes never talk directly to etcd; everything is mediated via the API server.

---

### 5. What happens end-to-end when you run `kubectl apply` for a deployment?

When `kubectl apply` is executed, the request is sent to the **kube-apiserver**, which validates and stores the desired state in **etcd**.

The **deployment controller** detects the new deployment and creates a ReplicaSet. The **scheduler** then selects appropriate nodes for the pods. Once scheduled, **kubelet** on each node pulls the container image, creates the pod, and starts containers. Controllers continuously monitor and reconcile to ensure the desired number of replicas is always running.

---

### 6. How does the scheduler evaluate nodes before placing a pod?

The scheduler follows two main phases: **filtering** and **scoring**.

In filtering, it eliminates nodes that don’t meet requirements such as CPU/memory availability, taints, node selectors, or affinity rules. In scoring, it ranks remaining nodes based on factors like resource utilization and spread. The pod is finally placed on the node with the highest score.

---

### 7. What scheduling constraints have you implemented in real projects and why?

I have implemented **node selectors**, **node affinity**, **taints and tolerations**, and **pod anti-affinity**.

These are used to **isolate workloads**, ensure **high availability**, avoid noisy neighbors, and place critical services on stable nodes. For example, pod anti-affinity ensures replicas don’t run on the same node, improving fault tolerance.

---

### 8. How do you ensure specific workloads run on dedicated or special-purpose nodes?

We label dedicated nodes and use **node affinity or node selectors** in pod specs.

For stricter enforcement, we apply **taints** on those nodes and add **tolerations** only to workloads that are allowed to run there. This approach is commonly used for **GPU workloads, monitoring agents, security tools, or stateful applications**.

---

### 9. How do you isolate workloads across teams or applications inside a cluster?

Isolation is achieved using **namespaces**, **RBAC**, **resource quotas**, and **network policies**.

Each team or application gets its own namespace with restricted permissions. Resource quotas prevent one team from exhausting cluster resources, and network policies control pod-to-pod communication, ensuring strong multi-tenancy within the same cluster.

---

### 10. How do Services enable pod communication, and what service patterns have you used in production?

Kubernetes Services provide a **stable virtual IP and DNS name** for a set of dynamic pods. They decouple pod lifecycle from networking.

In production, I’ve used **ClusterIP** for internal communication, **NodePort** mainly for testing, **LoadBalancer** for exposing services externally, and **Ingress** for HTTP/HTTPS routing. This ensures reliable service discovery and scalable traffic management.

---

