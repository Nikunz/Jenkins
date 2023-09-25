## Jenkins Pipeline for Deploying Java Web Application using master and slave configuration.
- This repository contains a jenkins pipeline script to automate the deployment of a java web application to a tomcat server.

## Pre-requisites:
- Ec2 t2medium instances for Jenkins Master, Jenkins Slave, sonarqube, nexus and Tomcat.
- java version `open-jdk-11` for all the instances.
- Build tool `maven` installed on slave jenkins node.
-  sonarqube, nexus and Tomcat Ec2 instances with `sonarqube, nexus and Tomcat installed`.
-  Jenkins server set up with the necessary plugins installed `(e.g., Git, Maven, SSH Agent, Nexus Artifact Uploader)`
- Credentials configured in Jenkins for accessing `Git repositories, SonarQube, Nexus, and Tomcat`.
- A Java web application hosted on a Git repository `(example: https://github.com/Nikunz/simple-app.git)`.

## Pipeline overview
- The Jenkins Pipeline is divided into the following stages:
    1. `**Git Checkout**`: This stage retrieves the source code of the Java web application from the specified Git repository.

    2. `**Build Maven Application**`: In this stage, the pipeline builds the Maven application using the configured Maven tool.
    
    3.`**Generate SonarQube Analysis**`: The SonarQube stage analyzes the code using `SonarQube's static code analysis`. The results are sent to the SonarQube instance for review.
    
    4. `**Upload War file to Nexus**`: The pipeline uploads the built WAR file to a Nexus repository. This step ensures artifact management and version control.
    
    5. `**Deploy War file to Tomcat**`: In this final stage, the pipeline uses SSH to transfer the built WAR file to the Tomcat server. It then gracefully shuts down and restarts the Tomcat server to deploy the application.
    
## Usage
    
   1. Create a new Jenkins pipeline job in your Jenkins server.
   2. In the pipeline configuration, specify the pipeline script from this repository.
   3. Configure the necessary credentials for Git, SonarQube, Nexus, and Tomcat in Jenkins.
   4. Adjust the URLs, versions, and paths according to your environment.
    
## Important Note
    
   - This pipeline serves as a template and may require modifications to fit your specific environment and deployment needs.
   - Ensure that you review and test each stage thoroughly before using this pipeline in a production environment.
   - Use appropriate security measures for credentials, SSH connections, and other sensitive information.
 
## Errors

   - Check permissions for all the dependent software installed inorder to avoid exceptions.
   - Ensure that the Git repository URL and branch are correct.`A typo or incorrect URL can lead to failures during the Git checkout stage`.
   - make sure to access the applications with the `public ip's accordingly whenever you start and restart the instances`.
   - Verify that the credentials `IDs (jenkinssonartoken, nexus-credentials, tomcat-credentials)` used in the pipeline match the credentials configured in Jenkins. Incorrect credentials can lead to `authentication failures`.
   - If the Maven build fails, check for errors in the project's `pom.xml file, dependencies, or build configuration`.
   - Verify that the path to the `WAR file in the nexusArtifactUploader` step matches the actual location of the built `WAR file in your project`.
   - Ensure that the commands to `shutdown and startup Tomcat are correct`. Incorrect commands can prevent proper deployment.

##Note:
This CICD development project is referenced from "https://github.com/bcreddydevops/chinna-app" and for clear instructions on how to deploy the app follow this video "https://www.youtube.com/watch?v=BT5ZmZmQaIU"
  
