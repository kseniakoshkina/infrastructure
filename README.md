# Infrastructure

## Theory [2]

As usual, we will start with a few theoretical questions:

* [0.5] What is Docker, and how it differs from dependencies management systems? From virtual machines?

Docker is a software development tool and a virtualization technology that makes it easy to develop, deploy, and manage applications by using containers. A container refers to a lightweight, stand-alone, executable package of a piece of software that contains all the libraries, configuration files, dependencies, and other necessary parts to operate the application.

Compared with dependencies management systems, dependency management is a technique for declaring, resolving and using dependencies required by the project in an automated fashion. A dependency manager operates at source code level. It's role is to setup the right dependencies for a particular application. It therefore implies that a dependency manager is something used by developers, not users or system admin.

A Virtual Machine is created to perform tasks that if otherwise performed directly on the host environment, may prove to be risky. VMs are isolated from the rest of the system; the software inside the virtual machine cannot tamper with the host computer. Therefore, implementing tasks such as accessing virus-infected data and testing of operating systems are done using virtual machines. 

Differences between Docker and VMs:


*   OS Support and Architecture - VMs have the host OS and guest OS inside each VM. A guest OS can be any OS, like Linux or Windows, irrespective of the host OS. In contrast, Docker containers host on a single physical server with a host OS, which shares among them.
*   Security - Virtual Machines are stand-alone with their kernel and security features. Therefore, applications needing more privileges and security run on virtual machines. 
*   Portability - VMs are isolated from their OS, and so they are not ported across multiple platforms without incurring compatibility issues. At the development level, if an application is to be tested on different platforms, then Docker containers must be considered. 
*   Performance - Virtual Machines are more resource-intensive than Docker containers as the virtual machines need to load the entire OS to start. The lightweight architecture of Docker containers is less resource-intensive than virtual machines. 


* [0.5] What are the advantages and disadvantages of using containers over other approaches?

**Container**

**Pros:**

* **Portability**

As a part of a distributed system, containers are highly portable.

Because containers pack microservices and their dependencies in a small-sized package, it’s easy to move containers around, even across environments, such as the public cloud, private cloud, and hybrid cloud, as well as the multi-cloud and bare-metal environments.

* **Effective resource usage**

Code packaged within containers share most of the dependencies needed to run the containers, including an operating system, libraries, and frameworks.

Unlike in virtual machines, there’s only one copy of necessary files in each hardware, leading to more effective resource usage. This also results in a lighter container, which means you can fit more containers within a physical server.

* **Easier to maintain**

As containers use a microservices-based architecture, your code is broken down into manageable pieces that can be handled individually. Hence, you can update and maintain a container without worrying it will affect other parts of your application.

* **Highly Scalable**

Container orchestration platforms are created to help you manage your containers. Container orchestrators, like Kubernetes or Docker Swarm, automate most of your container management process, including scaling, networking, and deployment.

Containerized applications are highly scalable, and they can scale up and down quickly by spinning up new nodes and/or pods when the needs call for it.

**Cons:**

* **Lacking Security measures**

Containers provide lightweight isolation from the host OS and containers within the same system. This leads to a weaker security boundary compared to virtual machines.

However, mature container users are paying more attention to security, as they try to improve collaboration between DevOps and Security, according to StackRox.

* **Runs only one OS**

This can be a benefit if you only use one OS, but if you need to be able to use it across different OS’s this is a negative. You can run an earlier version of the same OS using lightweight virtual machines.


|                   | Docker                                                                                       | VMs                                                                                     |
|-------------------|----------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| Boot-Time         | Boots in a few seconds                                                                       | Boots in a few minutes                                                                  |
| Runs on           | Make use of the execution engine                                                             | Make use of the hypervisor                                                              |
| Memory Efficiency | No space is needed to virtualize, hence less memory                                          | Requires entire OS to be loaded before starting the surface, so less efficient          |
| Isolation         | Prone to adversities as no provisions for isolation systems                                  | Interference possibility is minimum because of the efficient isolation mechanism        |
| Deployment        | Deploying is easy as only a single image, containerized can be used across all platforms     | Deployment is comparatively lengthy as separate instances are responsible for execution |
| Usage             | Docker has a complex usage mechanism consisting of both third party and docker managed tools | Tools are easy to use and simpler to work with                                          |


* [0.5] Explain how Docker works: what are Dockerfiles, how are containers created, and how are they run and destroyed?

A **Dockerfile** is a text document that contains all the commands a user could call on the command line to assemble an image. This page describes the commands you can use in a Dockerfile.

**Containers can be changed with special commands: descriptions below.**

The docker container **create** (or shorthand: docker create) command creates a new container from the specified image, without starting it.

When creating a container, the docker daemon creates a writeable container layer over the specified image and prepares it for running the specified command.
The docker **create** command shares most of its options with the docker run command (which performs a docker create before starting it). Refer to the docker run command section and the Docker run reference for details on the available flags and options.

The docker **run** command first creates a writeable container layer over the specified image, and then starts it using the specified command. 

The docker **kill** subcommand kills one or more containers. The main process inside the container is sent SIGKILL signal (default), or the signal that is specified with the --signal option.

**Also, in fact, there are more commands that can be used to modify Docker.**


* [0.25] Name and describe at least one Docker competitor (i.e., a tool based on the same containerization technology).

We'll describe **AWS Lambda**.

AWS Lambda is a compute service that lets you run code without provisioning or managing servers. Lambda runs your code on a high-availability compute infrastructure and performs all of the administration of the compute resources, including server and operating system maintenance, capacity provisioning and automatic scaling, and logging. With Lambda, you can run code for virtually any type of application or backend service. All you need to do is supply your code in one of the languages that Lambda supports.

When to use Lambda
Lambda is an ideal compute service for many application scenarios, as long as you can run your application code using the Lambda standard runtime environment and within the resources that Lambda provides. For example, you can use Lambda for:

File processing: Use Amazon Simple Storage Service (Amazon S3) to trigger Lambda data processing in real time after an upload.

Stream processing: Use Lambda and Amazon Kinesis to process real-time streaming data for application activity tracking, transaction order processing, clickstream analysis, data cleansing, log filtering, indexing, social media analysis, Internet of Things (IoT) device data telemetry, and metering.

Web applications: Combine Lambda with other AWS services to build powerful web applications that automatically scale up and down and run in a highly available configuration across multiple data centers.

IoT backends: Build serverless backends using Lambda to handle web, mobile, IoT, and third-party API requests.

Mobile backends: Build backends using Lambda and Amazon API Gateway to authenticate and process API requests. Use AWS Amplify to easily integrate your backend with your iOS, Android, Web, and React Native frontends.

* [0.25] What is conda? How it differs from apt, yarn, and others?

Conda is an open-source, cross-platform, language-agnostic package manager and environment management system. It was originally developed to solve difficult package management challenges faced by Python data scientists, and today is a popular package manager for Python and R.

Conda allows users to easily install different versions of binary software packages and any required libraries appropriate for their computing platform. Also, it allows users to switch between package versions and download and install updates from a software repository. Conda is written in the Python programming language, but can manage projects containing code written in any language (e.g., R), including multi-language projects. Conda can install Python,while similar Python-based cross-platform package managers (such as wheel or pip) cannot.

A popular Conda channel for bioinformatics software is Bioconda, which provides multiple software distributions for computational biology.

The conda version is a collection of python scripts whereas the apt version is based on a C library. 

The big difference between Conda and the pip package manager is in how package dependencies are managed, which is a significant challenge for Python data science and the reason Conda was created. Before Pip 20.3, Pip installed all Python package dependencies required, whether or not those conflict with other packages previously installed. Conda checks the current environment, everything that has been installed, any version limitations that the user specifies and figures out how to install compatible dependencies.
