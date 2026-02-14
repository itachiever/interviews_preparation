#Job Description:

# Questions:
### **Part 1: Azure DevOps Services (Repos, Boards, Artifacts)**

1.  What is the purpose of **Azure Artifacts**, and how does it integrate with CI/CD pipelines for package management?
2.  How does **Azure Boards** integrate with **Azure Repos** and **Pipelines** to support a full development lifecycle (e.g., linking work items to commits)?
3.  What is the difference between a **Pipeline Artifact** and a **Build Artifact** in Azure DevOps?
4.  How are **Branch Policies** enforced in Azure Repos to ensure code quality before merging?
5.  What is the function of **Project Collections** versus **Projects** in Azure DevOps organization hierarchy?
6.  How do you configure **Package Feeds** in Azure Artifacts to use upstream sources from NuGet.org or npmjs?
7.  What are **Test Plans** in Azure Test Plans, and how are they integrated into the pipeline execution?

### **Part 2: YAML Pipelines & Automation**

8.  What is the standard structure of a **multi-stage YAML pipeline** in Azure DevOps?
9.  How do **variables** differ from **parameters** in a YAML pipeline, and when should you use each?
10. What are **pipeline templates**, and how do they promote reusability across multiple projects?
11. How can you implement **conditional logic** (e.g., `condition: succeeded()`) to control stage or job execution?
12. What is the purpose of the **`resources`** section in a YAML pipeline file (e.g., referencing pipelines, builds, or repositories)?
13. How do you handle **environment-specific configurations** (Dev, Test, Prod) within a single YAML pipeline?
14. What is the syntax for defining **matrices** in YAML, and how does it help in running jobs against multiple configurations simultaneously?
15. How do you implement **self-hosted agents** versus **Microsoft-hosted agents** in a YAML pipeline?

### **Part 3: Build, Release & Deployment Strategies**

16. What is the difference between a **Classic Release Pipeline** and a **YAML Multi-stage Pipeline**?
17. How does the **"Build Once, Deploy Anywhere"** principle apply to Azure DevOps artifacts and deployments?
18. What are the key phases in an **end-to-end automation workflow** for a typical application (Build, Test, Deploy)?
19. How do you implement **approval gates** (e.g., manual intervention) before deploying to a Production environment?
20. What are **deployment jobs**, and how do they support strategies like **Blue-Green** or **Canary** deployments in YAML?
21. How do you configure **rollback strategies** in a release pipeline if a deployment fails?
22. What is the role of **Infrastructure as Code (IaC)** tasks (like Azure CLI or PowerShell) within a deployment pipeline?

### **Part 4: Git & Version Control Strategies**

23. What is the **Git Flow** branching strategy, and what are the roles of `master`, `develop`, and `feature` branches?
24. How does **Trunk-Based Development** differ from Git Flow, and why is it often preferred for CI/CD?
25. What is the purpose of **Pull Request (PR) workflows**, and what policies can be enforced (e.g., reviewers, build validation)?
26. How do you resolve **merge conflicts** in Git using Visual Studio or the web portal?
27. What are **Git Tags**, and how are they utilized in the build process for versioning releases?
28. How do you manage **branch permissions** and access control within an Azure Repos Git repository?

### **Part 5: Scripting & SQL Integration**

29. How do you invoke a **PowerShell** or **Bash** script from a YAML pipeline, and how do you handle script failures?
30. How can you integrate **SQL script execution** (e.g., schema updates or stored procedures) into an automated CI/CD pipeline?

***

