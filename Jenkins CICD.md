# What is CI/CD Pipeline?

A pipeline is a process that drives software development through a path of building, testing, and deploying code, also known as CI/CD. By automating the process, the objective is to minimize human error and maintain a consistent process for how software is released.

## Continuous Integration

Continuous Integration is a development practice in which the developers are required to commit changes to the source code in a shared repository several times a day or more frequently. Every commit made in the repository is then built. This allows the teams to detect the problems early. 

![image](https://user-images.githubusercontent.com/110366380/201050940-fc4aaaa8-fbe7-4a78-8895-6fa24769aebf.png)

## Continuous Delivery

Continuous delivery is an extension of continuous integration since it automatically deploys all code changes to a testing and/or production environment after the build stage. 

This means that on top of automated testing, we have an automated release process and we can deploy your application any time by clicking a button.

## Continuous Deployment

Continuous deployment goes one step further than continuous delivery. With this practice, every change that passes all stages of our production pipeline is released. There's no human intervention, and only a failed test will prevent a new change to be deployed to production.

![image](https://user-images.githubusercontent.com/110366380/201050731-24462ae0-7d32-4065-a94e-26fdf90f15ba.png)

## Difference between Continuous Integration, Continuous Delivery and Continuous Deployment

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/201051618-3e12b204-e7f1-4196-8a91-d1dcdaaedc9a.png">
</p>

![image](https://user-images.githubusercontent.com/110366380/201051919-0bca5410-94bc-4f22-8b9b-bced75eaa9fe.png)


## Webhook 

A Webhook is a mechanism to automatically trigger the build of a Jenkins project in response to a commit pushed to a Git repository.

![image](https://user-images.githubusercontent.com/110366380/200541014-88ad21be-3b07-4313-8ea2-069c2c9aba1c.png)

## Jenkins

Jenkins is an open-source automation tool written in Java with plugins built for Continuous Integration purposes. Jenkins is used to build and test our software projects continuously making it easier for developers to integrate changes to the project, and making it easier for users to obtain a fresh build. It also allows us to continuously deliver the software by integrating with a large number of testing and deployment technologies.

### Jenkins Stages

<p align="center">
  <img src="https://user-images.githubusercontent.com/110366380/200539483-96927056-397f-4305-93a6-f0975257d398.png">
</p>

### How it works!

Jenkins runs as a server on a variety of platforms including Windows, MacOS, Unix variants and especially, Linux. 
- It requires a Java 8 VM and above and can be run on the Oracle JRE or OpenJDK. 
- Normally it runs as a Java servlet within a Jetty application server. It can be run on other Java application servers such as Apache Tomcat. 
- Jenkins has been adapted to run in a Docker container. There are read-only Jenkins images available in the Docker Hub online repository.

To operate Jenkins, pipelines are created. A pipeline is a series of steps the Jenkins server will take to perform the required tasks of the CI/CD process. 

- These are stored in a plain text Jenkinsfile. The Jenkinsfile uses a curly bracket syntax that looks similar to JSON. 
- Steps in the pipeline are declared as commands with parameters and encapsulated in curly brackets. 
- The Jenkins server reads the Jenkinsfile and executes its commands, pushing the code down the pipeline from committed source code to production runtime. 
- A Jenkinsfile can be created through a GUI or by writing code directly.

### Benefits of using Jenkins

- It is an open-source tool with great community support.
- It is easy to install.
- It has 1000+ plugins to ease your work. If a plugin does not exist, we can code it and share it with the community.
- It is built with Java and hence, it is portable to all the major platforms.
    
### Who is using Jenkins.

The most popular companies using `Jenkins` are:

- Facebook
- Netflix
- Udemy
- LinkedIn
- Twich

## Alternatives to Jenkins.

These are the most commonly used alternatives to Jenkins

- GoCD - An Open source Continuous Integration server. 
- Integrity - A continuous integration server which works only with GitHub.
- CruiseControl -It is both CI tool and an extensible framework. It is used for building a custom continuous build process.


