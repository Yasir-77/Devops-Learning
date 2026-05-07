# CI/CD Module

## Understanding CI/CD

### What is CI/CD?

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
