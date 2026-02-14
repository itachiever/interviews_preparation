# Role: Azure Devops Engineer

Job highlights

• Repos,Pipelines,Boards,Artifacts . Strong experience with YAML-based CI / CD pipelines .
• Experience creating pipeline templates and reusable components . End-to-end automation of build,test,and deployment workflows .
• Strong experience with Git and version control workflows .

Job Description:

Azure DevOps:

• Hands-on experience with Azure DevOps Services:
Repos, Pipelines, Boards, Artifacts
• Strong experience with YAML-based CI/CD pipelines
• Knowledge of Git branching strategies (Git Flow, Trunk-based development)
• Experience creating pipeline templates and reusable components
• End-to-end automation of build, test, and deployment workflows

Version Control & Automation:

• Strong experience with Git and version control workflows
• Build and release automation
• Repository management and access control
• Scripting and automation using Bash, Python, and PowerShell

Role: DevOps Engineer
Key Skills: Azile, CI/CD, Azure DevOps, SQL


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
# Answers:


---

### **Part 1: Azure DevOps Services (Repos, Boards, Artifacts)**

### **1. What is the purpose of Azure Artifacts, and how does it integrate with CI/CD pipelines for package management?**

**Answer:**
Think of **Azure Artifacts** as your private, secure "storehouse" for packages. It allows teams to host NuGet, npm, Maven, Python, and Universal packages in one place.
**Integration:** In a CI/CD pipeline, when the "Build" stage finishes, we push the compiled code (like a `.zip` or `.nupkg` file) to Azure Artifacts. Later, in the "Deploy" stage, the pipeline pulls that specific package version from Artifacts to deploy it. This ensures that what we test is exactly what we deploy, and it prevents us from using broken or unapproved public libraries.

**2. How does Azure Boards integrate with Azure Repos and Pipelines to support a full development lifecycle?**

**Answer:**
The integration is all about **traceability**. In Azure Boards, we create a Work Item (like a User Story or Bug). When a developer writes code to fix it, they include the Work Item ID in their Git commit message. This automatically links the code to the Board. When the Pipeline runs, it also updates the Work Item to show the status of the build. This creates a full story: from the *Request* (Board) -> to the *Code* (Repos) -> to the *Release* (Pipelines), all visible in one place.

**3. What is the difference between a Pipeline Artifact and a Build Artifact in Azure DevOps?**

**Answer:**
While they sound similar, they have different technical uses.
*   **Build Artifacts** are the older, traditional mechanism. They are essentially just a folder of files published to the server.
*   **Pipeline Artifacts** are the newer, optimized method specifically designed for YAML pipelines. They are faster because they only upload changed files and are optimized for passing data between stages in the same pipeline.
**Best Practice:** For new YAML pipelines, we generally prefer **Pipeline Artifacts** because they integrate better with the multi-stage YAML experience.

**4. How are Branch Policies enforced in Azure Repos to ensure code quality before merging?**

**Answer:**
Branch Policies act as a "gatekeeper" for important branches like `main` or `release`. You can configure several rules:
*   **Require a Pull Request:** You cannot push directly; you must create a PR for review.
*   **Minimum Reviewers:** You require at least one or two people to approve the code.
*   **Build Validation:** The PR cannot be completed until a new build (CI pipeline) runs successfully.
*   **Work Item Linking:** You must link the code to a Task or Bug before merging.
This ensures that no bad code ever enters your main branch.

**5. What is the function of Project Collections versus Projects in Azure DevOps organization hierarchy?**

**Answer:**
Think of it like a file system:
*   **Organization** is the root (your company).
*   **Project Collections** are the top-level containers. Large enterprises might use them to separate different departments (e.g., "HR Collection" vs. "Engineering Collection").
*   **Projects** live inside collections. This is where the actual work happens (Repos, Pipelines, Boards).
Collections allow you to manage administration (like users and permissions) at a higher level, while Projects isolate the data and teams working on specific products.

**6. How do you configure Package Feeds in Azure Artifacts to use upstream sources from NuGet.org or npmjs?**

**Answer:**
An **Upstream Source** allows your private feed to act as a "caching proxy."
When you create a feed in Azure Artifacts, you can enable "Upstream sources" and add public sources like `nuget.org` or `npmjs.com`. When your pipeline requests a package (like `lodash` or `Newtonsoft.Json`), Azure Artifacts checks your private feed first. If it's not there, it fetches it from the public source, saves a copy in your private feed, and then hands it to the pipeline. This saves bandwidth and ensures that even if the public site goes down, your builds still work because you have a cached copy.

**7. What are Test Plans in Azure Test Plans, and how are they integrated into the pipeline execution?**

**Answer:**
**Test Plans** are a formal way to organize and track manual or automated test cases.
**Integration:** We can link "Automated Tests" (unit tests or Selenium tests) from our code to specific Test Cases in Azure Test Plans. When the CI pipeline runs, it publishes the test results back to Azure DevOps. The Test Plan then automatically updates to show which test cases passed and which failed, giving the QA team a live dashboard of the application's health without manual entry.

---

### **Part 2: YAML Pipelines & Automation**

**8. What is the standard structure of a multi-stage YAML pipeline in Azure DevOps?**

**Answer:**
A YAML pipeline is hierarchical. The standard structure is:
1.  **Triggers:** Defines when the pipeline runs (e.g., `main` branch).
2.  **Variables:** Values to reuse (like `buildConfiguration`).
3.  **Stages:** The major phases (e.g., `Build`, `Dev_Deploy`, `Prod_Deploy`).
4.  **Jobs:** Each stage contains jobs. A job runs on an agent (a server).
5.  **Steps:** Each job contains steps (the actual commands like `dotnet build` or `npm install`).

**9. How do variables differ from parameters in a YAML pipeline, and when should you use each?**

**Answer:**
Think of them like function arguments versus local variables.
*   **Parameters** are inputs you pass *into* a template or pipeline at compile time. They are great for things that change between different runs or projects (e.g., `environmentName`).
*   **Variables** are defined inside the pipeline and are set at runtime. They are used for configuration values that shouldn't be exposed (like secrets) or for values computed during the run.
**Simple rule:** If you need to pass data *into* a reusable template, use **Parameters**. If you just need to store a value for that specific run, use **Variables**.

**10. What are pipeline templates, and how do they promote reusability across multiple projects?**

**Answer:**
**Templates** are separate YAML files that contain a set of predefined steps or stages.
Instead of writing the same "Build, Test, and Push" code in 20 different microservice repositories, we write it once in a file called `build-template.yml`. Then, in every project's pipeline, we just reference that template. If we need to update the build process (e.g., change the version of the Node.js runner), we update the *one* template file, and all 20 projects automatically get the fix. It enforces consistency and saves time.

**11. How can you implement conditional logic (e.g., `condition: succeeded()`) to control stage or job execution?**

**Answer:**
Conditions act like "If-Then" statements in your pipeline.
By default, a job runs only if the previous job succeeded. But we can change this:
*   `condition: succeeded()`: Runs only if the previous stage worked (default).
*   `condition: failed()`: Runs only if the previous stage failed (useful for running cleanup scripts or notifying devs).
*   `condition: always()`: Runs no matter what happened before (essential for releasing resources or logging final status).
*   Custom conditions: You can even write logic like `and(succeeded(), eq(variables['build.sourceBranch'], 'refs/heads/main'))` to only run a deploy job if it's the main branch.

**12. What is the purpose of the `resources` section in a YAML pipeline file?**

**Answer:**
The `resources` section tells the pipeline about external things it depends on. It supports:
*   **Pipelines:** Triggers this pipeline when another pipeline finishes (useful for dependencies).
*   **Repositories:** Allows you to checkout code from multiple Git repositories in a single pipeline.
*   **Containers:** Allows you to specify a Docker image to use as the environment for your job.
It essentially expands the context of your pipeline beyond just its own code.

**13. How do you handle environment-specific configurations (Dev, Test, Prod) within a single YAML pipeline?**

**Answer:**
We follow the **"Build Once, Deploy Many"** principle. We build the artifact *once*, and then we deploy it to multiple environments.
To handle configs, we use **Pipeline Variables** scoped to stages. For example, we define a variable called `connectionString`.
*   For the **Dev** stage, the value is the Dev DB string.
*   For the **Prod** stage, the value is the Prod DB string.
We also use tasks like **File Transform** or **Variable Substitution** to swap these values inside the configuration files (like `appsettings.json`) during the deployment step automatically.

**14. What is the syntax for defining matrices in YAML, and how does it help in running jobs against multiple configurations simultaneously?**

**Answer:**
A **Matrix** lets you generate multiple copies of a job with different variable combinations dynamically.
**Syntax:** You define a strategy with a matrix.
```yaml
strategy:
  matrix:
    linux:
      imageName: 'ubuntu-latest'
    windows:
      imageName: 'windows-latest'
```
This will automatically create **two jobs** in parallel: one running on Linux and one on Windows. It is incredibly useful for testing your code against multiple operating systems or multiple Python/Node versions simultaneously without writing the job code twice.

**15. How do you implement self-hosted agents versus Microsoft-hosted agents in a YAML pipeline?**

**Answer:**
*   **Microsoft-hosted agents** are "Rental Cars." Microsoft provides them, they are fresh every time, and you don't need to maintain them. You specify them with `vmImage: 'ubuntu-latest'`.
*   **Self-hosted agents** are "Your Own Car." You install the agent software on your own server (on-prem or in a custom cloud VM). You specify them with `pool: 'MyPrivatePool'`.
We use **self-hosted agents** when we need access to private corporate networks (behind a firewall), need specific software pre-installed (like a huge SDK), or want to save money for high-volume builds. We use **Microsoft-hosted** for speed and simplicity for open-source or standard projects.


Here are the detailed, senior-level answers for **Questions 16 to 30**. These are designed to be read clearly on camera and used as a high-quality reference guide.

---

### **Part 3: Build, Release & Deployment Strategies**

**16. What is the difference between a Classic Release Pipeline and a YAML Multi-stage Pipeline?**

**Answer:**
The main difference is **"Configuration as Code"** versus **"GUI Configuration."**
*   **Classic Release Pipelines** are designed using a graphical user interface with drag-and-drop tasks. The configuration is stored in the database, not in your Git repo.
*   **YAML Multi-stage Pipelines** define the entire process (Build, Test, and Deploy) in a text file (YAML) that lives in your Git repository.
**Why YAML wins:** Because the pipeline definition is code, you can version it, review it via Pull Requests, and roll it back just like application code. It is the modern standard for DevOps.

**17. How does the "Build Once, Deploy Anywhere" principle apply to Azure DevOps artifacts and deployments?**

**Answer:**
This principle treats the build artifact as an immutable "golden master."
Once the code is compiled and packaged into an artifact (like a `.zip` or `.dll`), we **never rebuild it** for different environments. We take that exact same artifact and deploy it to Dev, then Test, then Prod.
**Why?** If you rebuild for Production, you risk introducing a new bug or a slightly different binary. By building once and promoting the same package, you guarantee that what you tested in Dev is *identical* to what runs in Production.

**18. What are the key phases in an end-to-end automation workflow for a typical application?**

**Answer:**
Think of this as an assembly line with four main phases:
1.  **Build:** We fetch the code, install dependencies, and compile it into an executable or package.
2.  **Test:** We run automated tests (Unit, Integration, and UI tests) to ensure the code works.
3.  **Package:** We publish the successful build as an Artifact in Azure Artifacts.
4.  **Deploy:** We take that artifact and push it to an environment (App Service, VM, or Kubernetes).

**19. How do you implement approval gates (e.g., manual intervention) before deploying to a Production environment?**

**Answer:**
In a YAML pipeline, we use **Environments** with specific **Checks**.
We define a stage that targets a "Production" environment. In the Azure DevOps UI, we go to that environment and add a "Pre-deployment approval" check. We assign it to a specific person or group (like the Release Managers).
Now, when the pipeline reaches the Production stage, it automatically **pauses**. It sends an email to the approver. The pipeline will not proceed until that person clicks the "Approve" button in the portal.

**20. What are deployment jobs, and how do they support strategies like Blue-Green or Canary deployments in YAML?**

**Answer:**
A **Deployment Job** is a special type of job in YAML (`deployment: jobName`) designed specifically for deploying apps. It includes lifecycle hooks like `preDeploy`, `deploy`, `routeTraffic`, and `postDeploy`.
**Strategies:**
*   **RunOnce:** Standard deployment (stop old, start new).
*   **Rolling:** Replaces instances incrementally (e.g., one by one).
*   **Canary:** Deploys the change to a small subset of servers first. The `routeTraffic` hook allows you to shift a small percentage of traffic to that new version to test it before a full rollout.

**21. How do you configure rollback strategies in a release pipeline if a deployment fails?**

**Answer:**
A rollback is essentially "undoing" the change.
In Azure DevOps, there are two main ways:
1.  **Redeploy Previous Release:** If you are using Classic Releases, you can simply click "Redeploy" on the previous successful release.
2.  **Code Rollback:** If you are using YAML, the safest way is to revert the code commit that caused the issue. The pipeline will trigger a new build that restores the previous state.
**Advanced:** We can also use **Feature Flags** (like Azure App Configuration). If a release fails, we simply turn off the new feature in the configuration without rolling back the actual code.

**22. What is the role of Infrastructure as Code (IaC) tasks (like Azure CLI or PowerShell) within a deployment pipeline?**

**Answer:**
Modern DevOps isn't just about deploying code; it's also about deploying the *infrastructure* (databases, VMs, networking).
We add tasks in our pipeline—such as **Azure PowerShell** or **Azure CLI**—to run scripts that create or update these resources. For example, before deploying our app, a script might run to ensure a SQL Database exists or to create a Storage Account. This automates the entire environment setup, ensuring that the infrastructure matches the application's needs every time.

---

### **Part 4: Git & Version Control Strategies**

**23. What is the Git Flow branching strategy, and what are the roles of `master`, `develop`, and `feature` branches?**

**Answer:**
**Git Flow** is a strict branching model designed for project management around releases.
*   **Master:** This branch always contains production-ready code. It only gets updated when we release a version.
*   **Develop:** This is the integration branch where all features come together. It represents "the next release."
*   **Feature:** Developers create a branch off `develop` to work on a specific task. When done, they merge it back into `develop`.
There are also `release` and `hotfix` branches to handle final production preparations and emergency fixes.

**24. How does Trunk-Based Development differ from Git Flow, and why is it often preferred for CI/CD?**

**Answer:**
**Trunk-Based Development** is much simpler. There is essentially one main branch (often called `main` or `master`).
Developers commit small changes frequently to this branch, often using short-lived branches that live for less than a day.
**Why it's preferred:** It encourages **Continuous Integration**. Because there are no long-lived "develop" branches, code is integrated and tested daily. It avoids "merge hell" where features conflict after being isolated for weeks. It is perfect for teams practicing true CI/CD.

**25. What is the purpose of Pull Request (PR) workflows, and what policies can be enforced?**

**Answer:**
A **Pull Request** is a request to merge code from one branch into another. It is the primary mechanism for **Code Review**.
**Policies we can enforce:**
*   **Minimum Reviewers:** Require at least 1 or 2 people to approve the code.
*   **Build Validation:** A new build must pass before the PR can be completed.
*   **Comment Resolution:** All comments from reviewers must be resolved.
*   **Work Item Linking:** A bug or task ID must be linked to the PR.

**26. How do you resolve merge conflicts in Git using Visual Studio or the web portal?**

**Answer:**
A merge conflict happens when two people change the same line of code differently.
**In the Web Portal:** Azure DevOps shows you a "Resolve Conflicts" screen. It highlights the conflicting lines side-by-side. You can click "Accept Yours," "Accept Theirs," or manually edit the code to pick the best parts of both.
**In Visual Studio:** It provides a similar visual merge tool. Once you manually fix the code to look correct, you mark the conflict as "resolved" and commit the merge.

**27. What are Git Tags, and how are they utilized in the build process for versioning releases?**

**Answer:**
A **Tag** is a marker (like a bookmark) that points to a specific commit in history. It is usually used for **Version Numbers** (e.g., `v1.0.2`).
**In the Build Process:** We configure the CI pipeline to read the Git Tag. If the build is triggered by a tag, we use that tag name as the version number for our artifact (e.g., naming the file `myapp-v1.0.2.zip`). This creates a permanent link between a specific version of the code and the binary artifact.

**28. How do you manage branch permissions and access control within an Azure Repos Git repository?**

**Answer:**
We use **Branch Policies** and **Security settings** in Azure DevOps.
We can lock down specific branches (like `main`) so that only certain people can push directly to them (often no one). We can also define who can "Contribute," "Create Branches," or "Force Push."
For example, we might set a rule that only "Project Administrators" can delete branches, or that "Testers" can only read the code but not push changes.

---

### **Part 5: Scripting & SQL Integration**

**29. How do you invoke a PowerShell or Bash script from a YAML pipeline, and how do you handle script failures?**

**Answer:**
We use the **`PowerShell`** or **`Bash`** task in the YAML file.
```yaml
- task: PowerShell@2
  inputs:
    filePath: 'scripts/deploy.ps1'
```
**Handling Failures:** By default, if the script returns a non-zero exit code (an error), the pipeline fails immediately.
To control this, we can use properties like `failOnStdErr: true` (fail if text is written to the error stream) or `continueOnError: true` (to let the pipeline continue even if the script fails, which is useful for "best effort" cleanup scripts).

**30. How can you integrate SQL script execution (e.g., schema updates or stored procedures) into an automated CI/CD pipeline?**

**Answer:**
We treat the database as part of the application code.
**Method 1: DACPAC (Recommended)**
We use the **SqlAzureDacpacDeployment** task. We compile our database project into a `.dacpac` file during the build. The deployment task then compares the `.dacpac` to the target database and automatically generates and executes the SQL script to update the schema (update/add columns) without losing data.
**Method 2: Raw SQL Scripts**
We use the **Azure CLI** or **SQLCMD** task to run `.sql` files stored in our repo against the database. This is often used for static data updates or simple stored procedure changes.
