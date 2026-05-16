# CI/CD Module

# Chapter 1: Understanding CI/CD

## What is CI/CD?

Continuous Integration and Continuous Delivery/Deployment (CI/CD)

CI/CD is a practice that involves automating the process of integrating, testing, and releasing code. It helps teams deliver software faster and more reliably.  

CI/CD is made up of two parts: Continuous Integration (CI) and Continuous Delivery/Deployment (CD).

### Continuous Integration (CI)

Continuous Integration (CI) is the practice of frequently integrating code changes into a shared repository. Instead of merging code at the end, developers integrate changes multiple times a day.  

- How CI works:
  - Developers push code changes regularly  
  - Automated tests run on each change  
  - Errors are detected and fixed early  

CI helps reduce merge conflicts and keeps the codebase stable.

### Continuous Delivery vs Continuous Deployment

Both are part of CD but have slightly different purposes.

### Continuous Delivery
Continuous Delivery ensures that code is always in a deployable state after passing all stages of testing.  

- Code is ready to be released at any time  
- Deployment is manual but reliable  

### Continuous Deployment
Continuous Deployment takes it a step further by automatically releasing every change that passes the pipeline.  

- Fully automated deployment process  
- No manual intervention required  

### CI/CD in Practice

In a production environment, CI/CD pipelines automate the process of building, testing, and deploying applications. This allows teams to:  

- Catch errors early  
- Release updates quickly  
- Maintain a stable and reliable system

## CI/CD Pipeline Overview

A CI/CD pipeline is a series of steps that code changes go through from the moment they are committed to being deployed to production.

The process starts when a developer makes changes and pushes code using git (add, commit, push).

CI/CD pipeline flow:

1- Code commit triggers the pipeline  
2- Build process starts automatically  
3- Code is compiled and dependencies are installed  
4- Build status is shared with the team  
5- Automated tests are executed  
6- Test results are communicated to the team  
7- Successful builds are delivered to a staging environment  
9- Code is deployed to production  

### How the Pipeline Works

- Code Commit: Developer pushes changes to the repository  

- Build Trigger: Commit starts an automated build process  

- Build: Code is compiled and dependencies are assembled  

- Test: Automated tests check for issues and ensure functionality  

- Staging: Build is deployed to a staging environment for further testing  

- Production: Final deployment where users can access the application  

### Why CI/CD is Important

CI/CD improves the software development process in several ways:

- Fast Delivery: Automates integration and deployment, enabling quicker releases  

- Improved Quality: Continuous testing helps catch bugs early  

- Reduced Risk: Smaller, incremental changes are easier to test and deploy  

- Better Collaboration: Frequent integration reduces conflicts and improves teamwork

## Overview of CI/CD tools

CI/CD tools help automate the process of integrating, testing, and deploying code. Different tools offer different features, and the choice depends on your workflow and team needs.

### Common CI/CD Tools

#### GitLab CI/CD
- Integrated directly into GitLab  
- Strong integration with GitLab version control  
- User-friendly and easy to use  
- Good choice if you are already using GitLab  

#### Jenkins
- Open-source and highly flexible  
- Supports many plugins for customization  
- Very powerful but can be complex to manage  
- Widely used in the industry  

#### CircleCI
- Cloud-based CI/CD tool  
- Known for speed and simplicity  
- Integrates well with GitHub and Bitbucket  
- Popular with startups and small teams  

#### Travis CI
- Cloud-based and easy to use  
- Integrates well with GitHub  
- Designed for automatic testing and deployment  
- Good for quick setup and simple workflows  

#### GitHub Actions
- Built directly into GitHub  
- Strong integration with repositories  
- Supports automation for build, test, and deployment  
- Widely used for open-source and modern projects  

## Cloud Provider CI/CD Tools

Cloud platforms also provide their own CI/CD services:

- AWS  
- Azure  
- GCP  

These tools integrate closely with their respective cloud environments.

## Role of CI/CD in Devops

CI/CD is a core part of DevOps and enables continuous development, testing, and deployment of applications. The process is often represented as an infinity loop because it is continuous.

<img width="713" height="356" alt="image" src="https://github.com/user-attachments/assets/74e2d7f9-ca3c-42a6-a97d-18fec771eef4" />

- CI (left side of the loop):
  - Code → Build → Test  

- CD (right side of the loop):
  - Release → Deploy → Monitor  


### How CI/CD Works in DevOps

#### Continuous Integration (CI)
- Code:
  - Developers write and commit code frequently to version control systems (GitHub, GitLab, Bitbucket)  

- Build:
  - Code is automatically compiled and dependencies are installed  

- Test:
  - Automated tests verify that changes do not introduce bugs  

#### Continuous Delivery/Deployment (CD)
- Release:
  - Tested code is prepared for staging or production  

- Deploy:
  - Application is deployed to production and made available to users  

- Monitor:
  - System is monitored to ensure performance and stability
  - 

### Benefits of CI/CD in DevOps

- Collaboration: Encourages frequent integration and shared responsibility among teams  

- Automation: Reduces manual work and minimizes human error, ensures consistent and reliable processes  

- Continuous Feedback: Provides quick feedback on code changes, helps identify and fix issues early  

- Consistency: Ensures code works across different environments, reduces "it works on my machine" issues  


## CI/CD in DevOps Architecture

### Overview of CI/CD in DevOps

CI/CD plays a central role in the DevOps lifecycle by automating the integration, testing, deployment, and monitoring of applications.

The DevOps pipeline is commonly divided into three main stages:

- Source Control  
- CI/CD  
- Monitoring and Logging  

### Source Control

Source control is where developers store and manage code using version control systems.

- Common tools:
  - GitHub  
  - GitLab  
  - Bitbucket  

Source control allows multiple developers to collaborate, track changes, and manage project history efficiently.

### CI/CD Stage

Once code is pushed to source control, the CI/CD pipeline automates the process of:

- Building the application  
- Running automated tests  
- Deploying the application  

This ensures code changes are continuously integrated, tested, and delivered reliably.

### Monitoring and Logging

After deployment, applications must be monitored to ensure they are running correctly.

- Common tools:
  - Prometheus  
  - Grafana  
  - ELK Stack  

Monitoring and logging help track performance, detect issues, and collect logs for troubleshooting and improvements.

### Continuous Feedback Loop

The DevOps process is continuous. Monitoring may identify issues that require developers to return to the code or CI/CD pipeline to make improvements and redeploy changes.

--- 

# Chapter 2: GitHub Actions and CI/CD Workflow

## Overview of CI/CD with GitHub Actions

GitHub Actions is used to automate CI/CD workflows directly from a GitHub repository. It allows code to be automatically built, tested, packaged, deployed, and monitored after changes are committed.

The workflow is usually defined in a YAML file, which tells GitHub Actions what steps to run when certain events happen, such as a code commit or push.

### GitHub Actions Workflow

The process starts when developers write code, make changes, and commit those changes to a GitHub repository.

- GitHub Actions workflow:
  - Developer writes or updates code
  - Code is committed and pushed to GitHub
  - GitHub Actions workflow is triggered
  - Workflow enters the CI/CD pipeline
  - Code is built
  - Automated tests are run
  - Test results are checked
  - Code is packaged
  - Application is deployed
  - Application is monitored after deployment

### CI Pipeline Steps

#### Build
The build stage compiles the code and installs or resolves any required dependencies. This ensures the application is set up correctly before testing.

#### Automated Tests
Automated tests are run to check that the new code does not break existing functionality and that new features work as expected. If the tests pass, the workflow continues to the next stage. If the tests fail, the pipeline stops and developers are notified so the issue can be fixed.

### Packaging and Deployment

If the build and tests are successful, the code is packaged into a deployable version. Examples include: Docker image, Compiled binary and Application build artifact

The packaged application can then be deployed to a staging, testing, or production environment depending on the workflow configuration.

### Monitoring

After deployment, the application should be continuously monitored to ensure it is running smoothly. Monitoring helps identify issues quickly so they can be fixed before they affect users.

## Use Cases for GitHub Actions

GitHub Actions can automate different parts of the development workflow, helping teams improve efficiency, reduce manual work, and maintain code quality.

## Common Use Cases

### Continuous Integration (CI)

GitHub Actions can automatically build and test code whenever changes are pushed to a repository.

- Common tasks:
  - Run unit tests on pull requests  
  - Validate code before merging  
  - Detect issues early  

This helps maintain code quality and ensures new changes do not break existing functionality.

### Continuous Deployment (CD)

After code successfully passes all tests, GitHub Actions can automatically deploy applications to different environments.

- Deployment targets:
  - AWS  
  - Azure  
  - GCP  

This allows faster and more reliable software releases with less manual intervention.

### Workflow Automation

GitHub Actions can automate repetitive tasks within a project workflow.

- Examples:
  - Updating project boards  
  - Moving tasks between columns  
  - Managing issues and pull requests  

Automation helps keep projects organized and reduces manual effort.








































