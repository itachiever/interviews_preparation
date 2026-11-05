
## Interview Question: 1st Round

1. Can you walk me through one of the security tool integrations you have implemented with GitHub?

2. Have you worked with Cycode or any other application security tools such as Snyk Code, SonarQube, or similar tools?

3. Does your current security platform provide application security scanning, CI/CD pipeline protection, and native security scanning capabilities?

4. Are you comfortable writing a small GitHub Actions workflow of around 5–10 lines?

5. Suppose we already have a centrally maintained reusable security workflow. Can you write a caller workflow that triggers whenever a pull request is raised against the `main` branch and securely passes scanner credentials (secret key and secret ID)?

6. How would you define the workflow name, configure the pull request trigger, specify the required branch, configure permissions, invoke an existing reusable workflow, and pass secrets securely?

7. Do you have practical hands-on experience with Python scripting?

8. Suppose a security scanner returns JSON data containing scan status and vulnerability findings. Can you write a Python function that checks the JSON data and raises an error if it finds any high- or critical-severity vulnerabilities?

9. How would you load the JSON data, extract the findings, iterate through them, check their severity, and raise an exception when a high or critical vulnerability is identified?

10. Suppose a developer accidentally commits production credentials (secret keys and IDs) directly into the main branch, and those credentials also make it into the production environment. As a DevSecOps engineer, how would you contain the damage and prevent other team members from accessing the exposed credentials?

11. After rotating or revoking the compromised credentials, how would you remove the exposed credentials from Git history so that team members cannot retrieve them when pulling the main branch?

12. If you have implemented secret scanning in your CI/CD workflow, how would you distinguish between test secrets and active production secrets, considering that scanners identify both as secrets?

13. Suppose an internal pull request workflow cannot access scanner credentials, so the team forks the scanner credentials from another pull request. A team member suggests using `pull_request_target` and checking out the entire contributor branch. Would you accept this solution? Why or why not?

14. If you reject the `pull_request_target` approach, what alternative solution would you suggest to securely provide scanner credentials to the workflow?

15. Is there anything else you would like to ask me about the role or the opportunity?

## Questions asked by me to interviewer
1. Is this opportunity for an internal project or a specific client, and which domain does the project belong to?
2. Are you currently using Cycode as your application security platform?
3. What challenges are you currently facing with Cycode, and are you using any alternative solutions to address them?
4. Are you using AWS EKS for your platform and infrastructure?
5. Are you using Terraform for infrastructure provisioning and resource management?
