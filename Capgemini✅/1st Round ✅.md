# 🧾 Interview Questions Category wise

## 🔹 1. Introduction / Profile

1. Can you tell me about yourself?
2. How many years of experience do you have?
3. Which organization are you currently working in?


## 🔹 2. Jenkins / CI-CD

4. You configured CI/CD pipeline in Jenkins?
5. Did you configure end-to-end pipeline?
6. Can you explain how you configured Jenkins pipeline?
7. What is Jenkins?
8. Which branching strategy are you following in your project?
9. How are releases handled in your project?
10. If a defect occurs in main branch after release, how do you handle it?


## 🔹 3. Python / Shell Scripting

11. Have you worked on Python and Shell scripting?
12. Can you write a Python script for automated file backup?
13. Can you write a Python script to read logs and filter errors?
14. What is the main use case of Python scripting in DevOps?
15. What is the use case of try-except-finally in Python?


## 🔹 4. Jenkins Pipeline Design (Coding)

16. Can you write a basic Jenkins pipeline with:

* parameters
* environment variables
* scheduled jobs
* parallel execution

17. Why do we use parameters in Jenkins pipeline?
18. Why do we use environment variables?
19. Why is the trigger (cron/schedule) section required?


## 🔹 5. Jenkins Execution & Agents

20. How do you configure Jenkins agents?
21. What is the use of `agent any`?
22. What is the use of `agent none`?
23. How does parallel execution work in Jenkins?
24. If one stage already uses an agent, how do you handle parallel execution requiring another agent?


## 🔹 6. Pipeline Troubleshooting

25. How do you handle Jenkins agent CPU/high load or agent down situation?
26. How do you handle Jenkins pipeline failures?
27. How do you debug pipeline failures?


## 🔹 7. Deployment Strategy

28. How do you deploy into different environments (staging/UAT/production) using Jenkinsfile?
29. How do you manage multiple environments in pipeline script?


## 🔹 8. Jenkins Types & Optimization

30. Differentiate declarative vs scripted pipeline
31. How do you optimize pipeline performance? (options only)


## 🔹 9. Docker

32. Can you explain Docker architecture?
33. Can you write a basic Dockerfile?
34. What is the difference between COPY and ADD?
35. What is the difference between CMD and ENTRYPOINT?
36. What is the command to build a Docker image?
37. How do you create/run a Docker container?
38. How do you stop a Docker container?
39. How do you reduce Docker image size?
40. What is the importance of multi-stage Docker builds?
41. Why do we use multi-stage builds?
42. What is the use of ARG instruction in Dockerfile?
43. What is the use of ENV instruction in Dockerfile?


## 🔹 10. Linux / Shell

44. What Linux commands do you use daily?
45. Which command do you use to filter logs in shell (equivalent of Python log filtering)?
46. What is the difference between `find` and `grep`?
47. Write a `find/grep` command example.


## 🔹 11. Terraform / Infrastructure

48. What is Terraform architecture/lifecycle?
49. What is the use of Terraform state files?
50. If state file is missing, how do you recover infrastructure?


## 🔹 12. Data Types / Python Basics

51. What are Python data types?


## 🔹 13. Scenario / Behavioral

52. In case of CTO/lead/agent issue or difficult situation, how do you handle it?
53. If agent suddenly goes down during execution, what will you do?


## 🔹 14. Miscellaneous

54. In which location are you currently working?
55. Are you comfortable with Bangalore location?


# 🎯 Summary Insight

* Total: ~55+ questions
* Focus areas:

  * Jenkins (very heavy)
  * Docker (deep probing)
  * Python scripting (use-case driven)
  * Real-time troubleshooting scenarios



# Actual Questions in order:

	1. Can you tell me about yourself?
	2. How many years of experience do you have?
	3. Which organization are you currently working in?
	4. You configured Jenkins CI/CD pipeline end-to-end?
	5. Can you explain how you configured the Jenkins pipeline?
	6. What is Jenkins?
	7. Which branching strategy are you following in your project?
	8. How do you handle releases?
	9. How do you handle production defects after release?
	10. Have you worked on Python shell scripting?
	11. Can you write a basic Jenkins pipeline?
	12. Can you include parameters, schedules, variables, and parallel execution in the pipeline?
	13. How do you configure Jenkins agents?
	14. What is the meaning/use of agent any in Jenkins?
	15. What is the use of agent none in Jenkins?
	16. How are parallel stages executed in Jenkins?
	17. Why are parameters required in Jenkins pipelines?
	18. Why are environment variables required?
	19. Why is the trigger/cron section required?
	20. How do you debug Jenkins agent issues like CPU spike or agent down?
	21. How do you handle Jenkins pipeline failures?
	22. How do you deploy to different environments like staging/UAT/production?
	23. How do you handle multiple environments in a Jenkinsfile?
	24. Can you differentiate declarative vs scripted pipelines?
	25. Why are you using declarative pipeline instead of Groovy scripted pipeline?
	26. How do you optimize pipeline performance?
	27. Have you worked on Docker?
	28. Can you explain Docker architecture?
	29. Can you write a basic Dockerfile?
	30. What is the difference between CMD and ENTRYPOINT?
	31. What is the difference between COPY and ADD?
	32. What is the command to build a Docker image?
	33. How do you create/run a container?
	34. How do you stop a container?
	35. How do you reduce Docker image size?
	36. What is the importance of multi-stage builds?
	37. What is the use of ARG instruction in Dockerfile?
	38. What is the use of ENV instruction in Dockerfile?
	39. Why are Python and shell scripting required in DevOps?
	40. Can you write a Python script to automate file backup?
	41. Can you write a Python script to read logs and filter errors?
	42. What is the use case of try, except, and finally in Python?
	43. What exactly is the use of except block?
	44. What are Python data types?
	45. What is the difference between list, tuple, dictionary, etc.?
	46. Have you worked on Terraform?
	47. Can you explain Terraform architecture/lifecycle?
	48. What is the use of Terraform state file?
	49. If the Terraform state file is missing, how do you recover infrastructure state?
	50. What Linux commands do you use daily?
	51. Which command is used to filter errors from a log file in Linux?
	52. What is the difference between find and grep?
	53. Can you write a grep command example?
	54. Which location are you currently in?
	55. Are you okay with Bangalore location?
	56. How about the further interview process? (discussion questions i asked)

# Answers:



# 1. Can you tell me about yourself?

### Answer

My name is NAME, and I have over 4 years of experience in DevOps and DevSecOps.

Currently, I am working as a DevSecOps Engineer at CURRENT COMPANY and am deployed to a fintech client called CLIENT NAME, which provides payment gateway solutions and financial transaction platforms.

My primary responsibility is integrating security into the software development lifecycle. I work extensively with Jenkins, GitLab, Fortify SAST/DAST, Sonatype Lifecycle for SCA and SBOM management, SonarQube, Trivy, Nexus Repository, and automation using Python and Shell scripting.

I have been involved in onboarding, installation, configuration, integration, and operational management of security tools, along with integrating them into Jenkins CI/CD pipelines. I also work closely with development teams on vulnerability remediation, secure coding practices, compliance requirements, and security adoption.

Prior to this, I worked at TCS for about 2.5 years, where I gained experience in DevOps tools, automation, CI/CD pipelines, Linux administration, and infrastructure-related activities.

Overall, my expertise lies in DevSecOps automation, Jenkins pipelines, application security, CI/CD implementation, Linux, Docker, Terraform, Python scripting, and security tooling integration.



# 2. How many years of experience do you have?

### Answer

I have over 4 years of total IT experience.

* PREVIOUS COMPANY: Approximately 2.5 years
* CURRENT COMPANY: Approximately 1.5 years

My experience spans DevOps, CI/CD automation, infrastructure automation, and DevSecOps security integration.



# 3. Which organization are you currently working in?

### Answer

Currently, I am working with CURRENT COMPANY as a DevSecOps Engineer.

I am deployed to a fintech client called CLIENT NAME, where I work on DevSecOps initiatives such as SAST, DAST, SCA, SBOM management, Jenkins pipeline integrations, security automation, developer enablement, and compliance-driven security practices.



# 4. You configured CI/CD pipeline in Jenkins?

### Answer

Yes.

I have worked extensively on Jenkins CI pipelines and security integrations.

My responsibilities include:

* Creating and maintaining Jenkins pipelines
* Integrating GitLab repositories
* Configuring build stages
* Integrating security scanners
* Implementing quality gates
* Publishing artifacts to Nexus
* Automating security validations
* Troubleshooting pipeline failures

I have also integrated Fortify, Sonatype Lifecycle, SonarQube, Trivy, and secret scanning tools into Jenkins workflows.



# 5. Did you configure end-to-end pipeline?

### Answer

Yes, I have configured and maintained end-to-end CI pipelines.

A typical pipeline includes:

1. Source code checkout from GitLab
2. Build using Maven, Gradle, GCC, or other build tools
3. SonarQube code quality analysis
4. Fortify SAST scanning
5. Sonatype Lifecycle SCA scanning
6. Secret scanning
7. Container image scanning using Trivy
8. Quality gate validation
9. Artifact publishing to Nexus
10. Security report generation
11. Build status notification

For deployment activities, I have worked closely with DevOps teams and supported integration into deployment pipelines.



# 6. Can you explain how you configured Jenkins pipeline?

### Answer

A typical Jenkins pipeline implementation in our environment follows these steps:

### Step 1: Source Integration

We integrate Jenkins with GitLab using webhooks and credentials.

Whenever developers push code, Jenkins automatically triggers the pipeline.

### Step 2: Code Checkout

Pipeline pulls source code from GitLab repositories.

### Step 3: Build Stage

Applications are built using:

* Maven for Java
* Gradle for Kotlin
* GCC/G++ for C/C++
* npm for Node.js
* Python build tools where applicable

### Step 4: Code Quality & Security

Pipeline performs:

* SonarQube Analysis
* Fortify SAST
* Sonatype Lifecycle SCA
* Secret Detection
* Trivy Image Scanning

### Step 5: Quality Gates

If critical policy violations or vulnerabilities are found, the build is automatically failed.

### Step 6: Artifact Management

Approved builds are uploaded to Nexus Repository.

### Step 7: Reporting

Security reports and scan summaries are generated and made available to developers.

### Step 8: Notifications

Pipeline sends success/failure notifications through configured channels.

This approach ensures security is enforced early in the development lifecycle.



# 7. What is Jenkins?

### Answer

Jenkins is an open-source automation server used to implement Continuous Integration and Continuous Delivery (CI/CD).

It automates activities such as:

* Code checkout
* Build execution
* Testing
* Security scanning
* Artifact publishing
* Deployment automation

Jenkins supports Pipeline-as-Code using Jenkinsfiles and integrates with tools like GitLab, Maven, Docker, Kubernetes, SonarQube, Fortify, Nexus, Terraform, and Ansible.

Its primary goal is to automate software delivery while improving consistency, speed, and reliability.



# 8. Which branching strategy are you following in your project?

### Answer

We primarily follow a Feature Branch Strategy.

The workflow is:

1. Developers create feature branches from the main branch.
2. Changes are committed to feature branches.
3. Pull Requests (Merge Requests) are raised.
4. Automated CI validation runs.
5. Code reviews are performed.
6. Security and quality gates are validated.
7. Approved code is merged into the main branch.

This approach allows isolated development while maintaining code quality and security controls before merging.



# 9. How are releases handled in your project?

### Answer

Our release process is controlled through approvals and automated validations.

The process is:

1. Developer raises Merge Request.
2. Code Review is completed.
3. Jenkins pipeline executes.
4. Security scans are performed.
5. Quality gates are validated.
6. Approved code is merged into the main branch.
7. Release artifacts are generated.
8. Artifacts are stored in Nexus.
9. Deployment teams execute releases according to approved release schedules.

Only builds that pass all security and quality checks are eligible for release.



# 10. If a defect occurs in production after release, how do you handle it?

### Answer

If a production issue occurs after release, we follow a structured incident response process.

### Step 1: Assess Impact

* Identify affected applications
* Determine severity
* Evaluate business impact

### Step 2: Root Cause Analysis

Review:

* Application logs
* Deployment logs
* Jenkins execution history
* Security scan results
* Infrastructure metrics

### Step 3: Hotfix Branch

Create a dedicated hotfix branch from the production version.

### Step 4: Fix and Validate

* Implement required fix
* Execute testing
* Run security validation
* Perform code review

### Step 5: Deploy Hotfix

Deploy the validated fix through the standard release process.

### Step 6: Rollback (If Needed)

If the issue is critical and cannot wait for a fix:

* Roll back to the last stable release
* Restore known-good artifact from Nexus
* Validate service restoration

### Step 7: Post-Incident Review

Conduct RCA and implement preventive actions to avoid recurrence.

This ensures quick recovery while maintaining release governance and security compliance.



# 11. Have you worked on Python and Shell scripting?

### Answer

Yes.

I use both Python and Shell scripting regularly for DevOps and DevSecOps automation activities.

### Python Use Cases

* Security tool API integrations
* Scan report extraction and processing
* Automated report generation
* Data parsing and transformation
* Notification automation
* Vulnerability data collection
* Compliance reporting

### Shell Scripting Use Cases

* Log analysis
* Backup automation
* File management
* Service monitoring
* Cron job automation
* Linux administration tasks
* Deployment-related activities

Python is generally preferred for complex logic and API integrations, while Shell scripting is useful for Linux automation and operational tasks.



# 12. Can you write a Python script for automated file backup?

### Answer

A simple backup script copies files from a source directory to a backup directory with a timestamp.

```python
import os
import shutil
from datetime import datetime

source_dir = "/data/source"
backup_dir = "/data/backup"

timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")

destination = os.path.join(
    backup_dir,
    f"backup_{timestamp}"
)

os.makedirs(destination, exist_ok=True)

for file in os.listdir(source_dir):
    source_file = os.path.join(source_dir, file)

    if os.path.isfile(source_file):
        shutil.copy2(source_file, destination)

print("Backup completed successfully")
```

### Explanation

* Reads source files
* Creates timestamped backup folder
* Copies files preserving metadata
* Prevents overwriting previous backups

This type of script can be scheduled using cron jobs.



# 13. Can you write a Python script to read logs and filter errors?

### Answer

```python
log_file = "application.log"

with open(log_file, "r") as file:
    for line in file:
        if "ERROR" in line:
            print(line.strip())
```

### Explanation

This script:

* Opens log file
* Reads line by line
* Searches for the keyword "ERROR"
* Prints matching log entries

For large log files, this approach is memory efficient because it processes one line at a time.



# 14. What is the main use case of Python scripting in DevOps?

### Answer

Python is widely used in DevOps because it simplifies automation and integration tasks.

Common use cases include:

### Infrastructure Automation

* Provisioning resources
* Managing cloud services

### API Automation

* Calling REST APIs
* Integrating tools

### CI/CD Automation

* Pipeline utilities
* Build automation

### Monitoring

* Log parsing
* Health checks
* Alert processing

### Security Automation

* Vulnerability report extraction
* Compliance reporting
* Scan orchestration

### Example

In my current role, Python is used to interact with security tools, collect scan results, generate reports, and automate administrative tasks.



# 15. What is the use case of try-except-finally in Python?

### Answer

`try-except-finally` is used for exception handling.

It helps prevent application crashes and allows graceful error handling.

### Structure

```python
try:
    risky_operation()

except Exception as e:
    print(e)

finally:
    cleanup()
```

### Purpose

#### Try

Contains code that may generate an exception.

#### Except

Handles the exception if an error occurs.

#### Finally

Always executes regardless of success or failure.

### Real Example

```python
try:
    file = open("data.txt")

except FileNotFoundError:
    print("File not found")

finally:
    print("Execution completed")
```

### DevOps Use Case

When calling APIs or reading files, exceptions can occur. Instead of crashing, we handle errors and continue execution safely.



# 16. Can you write a basic Jenkins pipeline with parameters, environment variables, scheduled jobs, and parallel execution?

### Answer

```groovy
pipeline {

    agent any

    parameters {
        choice(
            name: 'ENV',
            choices: ['SIT', 'UAT', 'PROD'],
            description: 'Select Environment'
        )
    }

    environment {
        APP_NAME = "payment-app"
        VERSION  = "1.0"
    }

    triggers {
        cron('H 2 * * *')
    }

    stages {

        stage('Checkout') {
            steps {
                git 'https://gitlab.example.com/app.git'
            }
        }

        stage('Parallel Execution') {

            parallel {

                stage('Unit Test') {
                    steps {
                        echo "Running Unit Tests"
                    }
                }

                stage('Security Scan') {
                    steps {
                        echo "Running Security Scan"
                    }
                }

            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.ENV}"
            }
        }
    }
}
```

This demonstrates:

* Parameters
* Environment variables
* Scheduled execution
* Parallel stages



# 17. Why do we use parameters in Jenkins pipeline?

### Answer

Parameters make pipelines reusable and dynamic.

Instead of creating separate pipelines for every scenario, users provide values at runtime.

### Common Examples

#### Environment Selection

```groovy
SIT
UAT
PROD
```

#### Version Selection

```groovy
1.0
1.1
1.2
```

#### Deployment Options

```groovy
Deploy = Yes / No
```

### Benefits

* Flexibility
* Reduced duplication
* Better control
* Easier release management



# 18. Why do we use environment variables?

### Answer

Environment variables store reusable values that can be referenced throughout the pipeline.

Example:

```groovy
environment {
    APP_NAME="payment-app"
}
```

Later:

```groovy
echo "${APP_NAME}"
```

### Benefits

* Centralized configuration
* Easier maintenance
* Avoid hardcoding values
* Improves reusability

Common examples:

* URLs
* Credentials IDs
* Application names
* Version numbers



# 19. Why is the trigger (cron/schedule) section required?

### Answer

The trigger section allows Jenkins to execute jobs automatically at scheduled times.

Example:

```groovy
triggers {
    cron('H 2 * * *')
}
```

Meaning:

* Run daily around 2 AM

### Common Use Cases

* Nightly builds
* Security scans
* Backup jobs
* Health checks
* Compliance reporting

### Benefits

* Automation
* Consistency
* No manual intervention



# 20. How do you configure Jenkins agents?

### Answer

Jenkins agents are worker nodes that execute jobs.

### Configuration Steps

1. Navigate to:

```text
Manage Jenkins
→ Nodes
→ New Node
```

2. Create node

```text
Permanent Agent
```

3. Configure:

* Agent Name
* Labels
* Remote Workspace
* Launch Method

4. Connect using:

* SSH
* JNLP
* Windows Service

### Example

```text
linux-agent
docker-agent
security-agent
```

Jobs can be routed using labels.

This improves scalability and workload distribution.



# 21. What is the use of `agent any`?

### Answer

```groovy
agent any
```

means:

Jenkins can run the pipeline on any available executor or agent.

Jenkins automatically selects a suitable node.

Example:

```groovy
pipeline {
    agent any
}
```

### Benefits

* Simplicity
* No specific node dependency
* Better resource utilization

Used when the job does not require a specialized environment.



# 22. What is the use of `agent none`?

### Answer

```groovy
agent none
```

means:

Do not allocate an agent for the entire pipeline globally.

Instead, each stage explicitly defines its own agent.

Example:

```groovy
pipeline {

    agent none

    stages {

        stage('Build') {
            agent {
                label 'java-agent'
            }
        }

        stage('Security') {
            agent {
                label 'security-agent'
            }
        }
    }
}
```

### Benefits

* Efficient resource utilization
* Different stages use different agents
* Better parallel execution

This is commonly used in enterprise pipelines.



# 23. How does parallel execution work in Jenkins?

### Answer

Parallel execution allows multiple stages to run simultaneously instead of sequentially.

Example:

```groovy
stage('Testing') {

    parallel {

        stage('Unit Test') {
            steps {
                echo 'Unit Tests'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Security Scan'
            }
        }
    }
}
```

### Benefits

* Faster pipeline execution
* Better resource utilization
* Reduced overall build time

### Real Example

In DevSecOps:

* SAST Scan
* SCA Scan
* Secret Scan

can run in parallel.

Instead of taking:

```text
10 + 10 + 10 = 30 minutes
```

they may complete in approximately:

```text
10 minutes
```

depending on agent availability.



# 24. If one stage already uses an agent, how do you handle parallel execution requiring another agent?

### Answer

For true parallel execution, Jenkins requires multiple executors or multiple agents.

Example:

```groovy
parallel {

    stage('Build') {

        agent {
            label 'build-agent'
        }

        steps {
            echo 'Build'
        }
    }

    stage('Security') {

        agent {
            label 'security-agent'
        }

        steps {
            echo 'Security Scan'
        }
    }
}
```

### Important Point

If only one executor is available:

```text
Parallel stages become queued.
```

They cannot execute simultaneously.

For effective parallelism:

* Multiple Jenkins agents
* Multiple executors
* Proper agent labels

must be configured.

### Real-World Example

A security scan may run on:

```text
security-agent
```

while the build runs on:

```text
build-agent
```

This reduces build time and prevents resource contention.




## 25. How do you handle Jenkins agent CPU high load or agent down situations?

**Answer:**

In my projects, Jenkins controllers and agents are monitored continuously. If an agent shows high CPU utilization or becomes unavailable:

1. Verify agent status from Jenkins Dashboard.
2. Check system resources using:

   ```bash
   top
   htop
   free -m
   df -h
   ```
3. Review agent logs and Jenkins logs.
4. Identify resource-intensive builds.
5. Move workloads to other available agents using labels.
6. Restart Jenkins agent service if required.
7. Clean old workspaces and unused Docker images.
8. Scale additional agents if the workload is consistently high.

If an agent goes down during execution:

* Jenkins marks the build as failed.
* After restoring the agent, rerun the pipeline from the failed stage or trigger a new build.
* For critical pipelines, maintain multiple agents to avoid a single point of failure.



## 26. How do you handle Jenkins pipeline failures?

**Answer:**

Whenever a pipeline fails, I follow a structured troubleshooting approach:

1. Identify the failed stage.
2. Review console output.
3. Determine whether the issue is:

   * SCM issue
   * Build issue
   * Dependency issue
   * Security scan issue
   * Infrastructure issue
   * Deployment issue
4. Fix the root cause.
5. Re-run the pipeline.
6. Validate deployment success.

In production environments, I also verify rollback procedures and ensure application stability before proceeding.



## 27. How do you debug pipeline failures?

**Answer:**

My debugging process is:

### Step 1: Identify Failed Stage

Examples:

* Checkout
* Build
* Test
* Security Scan
* Docker Build
* Deployment

### Step 2: Review Console Logs

```groovy
View Console Output
```

Look for:

* Compilation errors
* Missing dependencies
* Authentication failures
* Network issues
* Agent failures

### Step 3: Verify Environment

```bash
java -version
docker version
kubectl version
```

### Step 4: Verify Credentials

Check:

* Git credentials
* Nexus credentials
* Vault secrets
* Cloud credentials

### Step 5: Reproduce Manually

Run the failed command manually on the agent.

Example:

```bash
mvn clean package
```

This helps isolate Jenkins-specific issues from application issues.



# 28. How do you deploy into different environments (SIT/UAT/Production) using Jenkinsfile?

**Answer:**

In my projects, deployments are controlled using parameters and environment-specific configurations.

Example:

```groovy
pipeline {
    agent any

    parameters {
        choice(
            name: 'ENV',
            choices: ['SIT','UAT','PROD'],
            description: 'Select Environment'
        )
    }

    stages {

        stage('Deploy') {
            steps {

                script {

                    if(params.ENV == 'SIT'){
                        sh './deploy-sit.sh'
                    }

                    else if(params.ENV == 'UAT'){
                        sh './deploy-uat.sh'
                    }

                    else {
                        input "Approve Production Deployment"
                        sh './deploy-prod.sh'
                    }
                }
            }
        }
    }
}
```

This ensures controlled deployments and production approvals.



## 29. How do you manage multiple environments in pipeline scripts?

**Answer:**

I manage environments using:

### Parameters

```groovy
parameters {
   choice(
      name: 'ENV',
      choices: ['DEV','SIT','UAT','PROD']
   )
}
```

### Environment Variables

```groovy
environment {
   SIT_URL = "sit.company.com"
   UAT_URL = "uat.company.com"
}
```

### Separate Config Files

```yaml
sit.yaml
uat.yaml
prod.yaml
```

### Separate Credentials

Jenkins Credentials Store:

* SIT credentials
* UAT credentials
* PROD credentials

This prevents hardcoding and improves security.



# 30. Differentiate Declarative vs Scripted Pipeline

| Declarative Pipeline          | Scripted Pipeline       |
| -- | -- |
| Easier to read                | More flexible           |
| Structured syntax             | Full Groovy scripting   |
| Recommended for most projects | Used for advanced logic |
| Better validation             | Less validation         |
| Simpler maintenance           | More coding effort      |

### Declarative Example

```groovy
pipeline {
   agent any

   stages {
      stage('Build'){
         steps {
            sh 'mvn clean package'
         }
      }
   }
}
```

### Scripted Example

```groovy
node {
   stage('Build') {
      sh 'mvn clean package'
   }
}
```

Most of my pipelines are Declarative because they are easier to maintain and standardize.



## 31. How do you optimize Jenkins pipeline performance?

**Answer:**

I use multiple techniques:

### Parallel Execution

```groovy
parallel {
   stage('SAST')
   stage('SCA')
}
```

### Dedicated Agents

Assign specialized agents:

* Build Agent
* Security Agent
* Deployment Agent

### Dependency Caching

Examples:

* Maven Cache
* NPM Cache
* Docker Layer Cache

### Workspace Cleanup

```groovy
cleanWs()
```

### Shared Libraries

Avoid duplicate code.

### Incremental Builds

Build only changed components when possible.

### Containerized Agents

Provide consistent and faster execution environments.



# 32. Can you explain Docker architecture?

**Answer:**

Docker architecture consists of:

### Docker Client

Commands executed by users:

```bash
docker build
docker run
docker pull
```

### Docker Daemon (dockerd)

Handles:

* Image management
* Container lifecycle
* Networking
* Storage

### Docker Registry

Stores images.

Examples:

* Docker Hub
* Nexus
* Harbor
* ECR

### Docker Objects

* Images
* Containers
* Volumes
* Networks

Flow:

```text
Developer
    ↓
Docker Client
    ↓
Docker Daemon
    ↓
Image Registry
    ↓
Containers
```



## 33. Can you write a basic Dockerfile?

**Answer:**

```dockerfile
FROM eclipse-temurin:17-jre

WORKDIR /app

COPY target/app.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","app.jar"]
```

### Build

```bash
docker build -t app:v1 .
```

### Run

```bash
docker run -d -p 8080:8080 app:v1
```



## 34. Difference between COPY and ADD?

| COPY                           | ADD                                          |
|  | -- |
| Copies local files             | Copies files + additional features           |
| Recommended for most use cases | Used only when extra functionality is needed |
| Simple file copy               | Can extract tar archives automatically       |
| No URL support                 | Can download from URL                        |

Example:

```dockerfile
COPY app.jar /app/
```

```dockerfile
ADD app.tar.gz /app/
```

Generally, I prefer COPY because it is predictable and secure.



## 35. Difference between CMD and ENTRYPOINT?

| CMD                          | ENTRYPOINT          |
| - | - |
| Default command              | Main executable     |
| Can be overridden completely | Harder to override  |
| Provides arguments           | Defines application |

Example:

```dockerfile
CMD ["java","-version"]
```

```dockerfile
ENTRYPOINT ["java","-jar","app.jar"]
```

Best practice:

```dockerfile
ENTRYPOINT ["java","-jar","app.jar"]
CMD ["--spring.profiles.active=prod"]
```



## 36. Command to build a Docker image?

**Answer:**

```bash
docker build -t myapp:v1 .
```

### Explanation

```text
-t = tag image
myapp = image name
v1 = version
. = Dockerfile location
```



## 37. How do you create/run a Docker container?

**Answer:**

```bash
docker run -d \
--name myapp \
-p 8080:8080 \
myapp:v1
```

### Verify

```bash
docker ps
```



## 38. How do you stop a Docker container?

**Answer:**

### Stop

```bash
docker stop myapp
```

or

```bash
docker stop <container-id>
```

### Remove

```bash
docker rm myapp
```



## 39. How do you reduce Docker image size?

**Answer:**

Best practices:

### Use Lightweight Base Images

```dockerfile
FROM alpine
```

### Use Multi-Stage Builds

Keep build tools out of final image.

### Remove Temporary Files

```dockerfile
RUN rm -rf /tmp/*
```

### Minimize Layers

Combine commands:

```dockerfile
RUN apt-get update && \
    apt-get install -y curl && \
    apt-get clean
```

### Ignore Unnecessary Files

Use:

```text
.dockerignore
```

Examples:

```text
.git
target/
logs/
```



## 40. What is the importance of Multi-Stage Docker Builds?

**Answer:**

Multi-stage builds separate build and runtime environments.

Benefits:

* Smaller images
* Better security
* Faster deployments
* Reduced attack surface

Only the final artifact is copied into the runtime image.



## 41. Why do we use Multi-Stage Builds?

**Answer:**

Example:

### Stage 1

```dockerfile
FROM maven:3.9 AS builder
```

Compile application.

### Stage 2

```dockerfile
FROM eclipse-temurin:17-jre
```

Run application.

Copy only:

```dockerfile
COPY --from=builder app.jar .
```

Result:

* Build tools not included
* Smaller image
* Faster startup
* Less vulnerability exposure



## 42. What is the use of ARG instruction in Dockerfile?

**Answer:**

`ARG` defines build-time variables.

Example:

```dockerfile
ARG VERSION=1.0
```

Usage:

```dockerfile
FROM ubuntu:${VERSION}
```

Build:

```bash
docker build \
--build-arg VERSION=22.04 \
-t app .
```

Used only during image build.



## 43. What is the use of ENV instruction in Dockerfile?

**Answer:**

`ENV` defines runtime environment variables.

Example:

```dockerfile
ENV APP_ENV=production
```

Application can access:

```bash
echo $APP_ENV
```

Container run:

```bash
docker run myapp
```

Difference:

| ARG                        | ENV                            |
| -- |  |
| Build time                 | Runtime                        |
| Not available after build  | Available inside container     |
| Used during image creation | Used by application at runtime |

A common pattern is using `ARG` for build versions and `ENV` for application configuration.



# 44. What Linux commands do you use daily?

**Answer:**

As a DevSecOps Engineer, I regularly use Linux commands for troubleshooting, log analysis, deployments, file management, and process monitoring.

### File & Directory Operations

```bash
pwd
ls -lrt
cd
mkdir
rm -rf
cp
mv
touch
```

### File Content Operations

```bash
cat
less
more
head
tail
tail -f
```

### Process Monitoring

```bash
ps -ef
top
htop
kill
kill -9
```

### Disk & Memory Monitoring

```bash
df -h
du -sh
free -m
vmstat
```

### Network Troubleshooting

```bash
ping
curl
wget
netstat -tulpn
ss -tulpn
nslookup
traceroute
```

### Log Analysis

```bash
grep
awk
sed
cut
sort
uniq
```

### Permission Management

```bash
chmod
chown
```

### Service Management

```bash
systemctl status
systemctl start
systemctl stop
systemctl restart
journalctl
```

**Real-time Example:**

When a Jenkins deployment fails, I typically use:

```bash
tail -f application.log
ps -ef | grep java
df -h
free -m
```

to identify application, resource, or infrastructure issues.



# 45. Which command do you use to filter logs in Shell (equivalent of Python log filtering)?

**Answer:**

The most common command is:

```bash
grep
```

### Example

Find ERROR logs:

```bash
grep "ERROR" application.log
```

Case-insensitive search:

```bash
grep -i "error" application.log
```

Count errors:

```bash
grep -c "ERROR" application.log
```

Monitor live logs:

```bash
tail -f application.log | grep "ERROR"
```

**Real-Time Example:**

When a deployment fails, I immediately search for:

```bash
grep -i "exception" application.log
grep -i "error" application.log
```

to identify the root cause.



# 46. What is the difference between find and grep?

| find                         | grep                       |
| - | -- |
| Searches files/directories   | Searches text inside files |
| Works on file system objects | Works on content           |
| Searches by name, size, date | Searches by patterns       |
| Returns matching files       | Returns matching lines     |

### Example of find

```bash
find /opt -name "*.log"
```

Returns log files.

### Example of grep

```bash
grep "ERROR" app.log
```

Returns lines containing ERROR.



# 47. Write a find/grep command example.

**Answer:**

### Find all log files

```bash
find /var/log -name "*.log"
```

### Find all Jenkins logs

```bash
find /opt/jenkins -name "*.log"
```

### Search ERROR in logs

```bash
grep "ERROR" app.log
```

### Combined Example

Find all log files and search ERROR messages:

```bash
find /var/log -name "*.log" -exec grep "ERROR" {} \;
```

or

```bash
find /var/log -name "*.log" | xargs grep "ERROR"
```

This is commonly used during production troubleshooting.



# 48. What is Terraform architecture/lifecycle?

**Answer:**

Terraform follows an Infrastructure as Code (IaC) model.

### Terraform Workflow

```text
Developer
    ↓
terraform init
    ↓
terraform plan
    ↓
terraform apply
    ↓
Infrastructure Created
    ↓
terraform destroy (if required)
```

### 1. terraform init

Downloads:

* Providers
* Modules

Example:

```bash
terraform init
```



### 2. terraform plan

Shows proposed changes.

```bash
terraform plan
```



### 3. terraform apply

Creates or modifies infrastructure.

```bash
terraform apply
```



### 4. terraform destroy

Removes infrastructure.

```bash
terraform destroy
```



### Architecture Components

1. Terraform Configuration Files
2. Providers (AWS/Azure/GCP)
3. State File
4. Modules
5. Resources

**Real-Time Example:**

In my projects, Terraform is used for provisioning:

* AWS EC2
* S3
* RDS
* EKS
* Security Groups
* Networking Components

through reusable modules.



# 49. What is the use of Terraform state files?

**Answer:**

Terraform state file (`terraform.tfstate`) stores the current state of infrastructure.

Terraform uses it to understand:

* What resources exist
* Current configuration
* Resource IDs
* Dependencies

Without state files, Terraform cannot accurately determine changes.



### Example

Created:

```hcl
resource "aws_instance" "web" {
}
```

Terraform stores:

```text
Instance ID
Public IP
Current configuration
```

inside:

```text
terraform.tfstate
```



### Benefits

* Tracks infrastructure
* Detects drift
* Calculates changes
* Enables updates



### Best Practice

Store remotely:

* AWS S3 + DynamoDB Locking
* Azure Storage Account
* Terraform Cloud

Never store production state locally.



# 50. If state file is missing, how do you recover infrastructure?

**Answer:**

Loss of a state file is a serious issue because Terraform loses tracking of existing resources.

### Recovery Methods

### Method 1: Restore Backup

Best option.

Restore:

```text
terraform.tfstate.backup
```

or retrieve from:

* S3
* Terraform Cloud
* Remote backend



### Method 2: Import Existing Resources

If infrastructure exists:

```bash
terraform import aws_instance.web i-123456
```

Terraform re-associates resources with state.



### Method 3: Rebuild State

Use:

```bash
terraform import
```

for all resources.

Then verify:

```bash
terraform plan
```



### Interview Point

"In enterprise environments, we use remote backends with versioning enabled to avoid state file loss and to support team collaboration."



# 51. What are Python data types?

**Answer:**

Python provides several built-in data types.

### Numeric

```python
int
float
complex
```

Example:

```python
a = 10
b = 10.5
c = 2+3j
```



### String

```python
str
```

Example:

```python
name = "Yuvaraju"
```



### Boolean

```python
bool
```

Example:

```python
status = True
```



### List

Ordered and mutable.

```python
tools = ["Jenkins","Docker","Kubernetes"]
```



### Tuple

Ordered and immutable.

```python
tools = ("Jenkins","Docker")
```



### Set

Unique values only.

```python
tools = {"Jenkins","Docker"}
```



### Dictionary

Key-value pairs.

```python
employee = {
    "name":"Yuvaraju",
    "role":"DevSecOps"
}
```



### NoneType

Represents no value.

```python
value = None
```

**DevOps Example:**

In automation scripts, I commonly use:

* Lists for server inventories
* Dictionaries for configuration data
* Strings for paths and commands
* Booleans for deployment decisions



# 52. In case of CTO/lead/agent issue or difficult situation, how do you handle it?

**Answer:**

I follow a structured incident-management approach.

### Step 1: Assess Impact

Understand:

* Business impact
* Number of affected users
* Production impact



### Step 2: Gather Facts

Collect:

* Logs
* Monitoring alerts
* Error messages
* Infrastructure status



### Step 3: Communicate

Inform:

* Technical Lead
* DevOps Team
* Stakeholders

with accurate updates.



### Step 4: Resolve

Implement:

* Rollback
* Agent recovery
* Infrastructure fixes
* Configuration correction

depending on the issue.



### Step 5: RCA

After resolution:

* Perform Root Cause Analysis
* Document lessons learned
* Implement preventive controls



### Real-Time Example

If a deployment fails in production due to an agent issue:

1. Stop further deployments.
2. Switch workload to another agent.
3. Validate deployment status.
4. Rollback if required.
5. Communicate status updates.
6. Complete RCA.



# 53. If an agent suddenly goes down during execution, what will you do?

**Answer:**

### Immediate Actions

#### Step 1: Identify Failure

Check:

```text
Build Console Output
Jenkins Dashboard
Agent Status
```



#### Step 2: Verify Agent Health

Login to agent server.

Check:

```bash
systemctl status jenkins-agent
top
free -m
df -h
```



#### Step 3: Determine Cause

Possible reasons:

* High CPU
* Memory exhaustion
* Disk full
* Network issue
* JVM crash
* Server reboot



#### Step 4: Restore Agent

Restart:

```bash
systemctl restart jenkins-agent
```



#### Step 5: Resume Build

If supported:

```text
Restart From Stage
```

or rerun pipeline.



#### Step 6: Prevent Future Occurrences

* Increase resources
* Configure additional agents
* Implement monitoring alerts
* Balance workloads



### Interview-Level Answer

"If an agent fails during execution, I first identify the cause using Jenkins and system logs, restore the agent or redirect workloads to another available agent, rerun the failed stage, and then perform RCA to prevent recurrence."



# 54. In which location are you currently working?

**Answer:**

"I am currently working in CURRENT LoCATION. I am employed by CURRENT COMPANY and currently deployed to a client engagement where I work on DevSecOps and application security initiatives."

*(Adjust the city if your current official work location differs.)*



# 55. Are you comfortable with Bangalore location?

**Answer:**

"Yes, I am comfortable with Bangalore and open to working from the Bangalore location. I understand it is one of the major technology hubs, and I am flexible regarding relocation and work arrangements based on project requirements."


