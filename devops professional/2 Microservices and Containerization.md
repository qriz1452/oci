Microservices Architecture: Overview





 Let's start by understanding what are microservices. The term "microservices" is generally meant to describe an approach to software development that involves decomposing application functionality into individual components that can be deployed separately from each other and typically communicate via application programming interfaces or APIs.

Microservices basically utilize integration, API management, and cloud deployment technologies, which gives developers the freedom to independently develop and deploy services as per their requirement.

Microservices are used to design an application that is multilingual. This helps teams which work somewhat independently of each other. This allows developers to use different programming languages and technologies without affecting the overall architectural structure of the software development. One developer might use Node.js to code specific app feature, and the other might use Python. That's absolutely fine.

Loosely coupled with other services-- in a loosely coupled environment, you can easily work with the least elastic component to address any slowdowns or performance gaps. Loose couplings enables the isolation of microservices that lead to better productivity.

Easy to maintain and independently deployable-- following code is easier since the services are isolated and less dependent, which also makes it easier to deploy them in little pieces without affecting other services. So when a change is required in certain part of the application, only the related services can be modified and redeployed. There is no need to modify and redeploy the entire application.

Easily scalable and highly available-- microservices are easy to scale and integrate without third-party services. Although not a simple task, but maintaining high availability with microservices can be done using application methods like load balancing techniques and using API gateways.

Failure resistant-- you can build resilient microservices by including fault tolerance policies in your code. For example, in a movie ticket application, different microservices might support scheduling, purchasing, and customer preferences. If one service fails, fault tolerance policies help limit the error and keep it from taking down the whole application.

Let's take a look at a microservices architecture for a sample e-commerce application. The API layer is the entry point for all the client requests to a microservice. The API layer also enables microservices to communicate with each other using the HTTP, gRPC, and other TCP/UDP protocols.

The logic layer focuses on a single business task, minimizing the dependencies on the other microservice. This layer can be written in different language for each microservice. As you can see, this e-commerce application makes use of three microservices. One is coded in Java, the other one in Python, and the third one in Go. So this makes it multilingual.

The data store layer provides a persistence mechanism, such as a database storage engine, log files, and so on. Developers can consider using separate persistent data store for each microservice. As you can see over here, there is a separate data store for Container 2, and there's a separate data store for Container 3 that is using Go.

Typically, each microservice runs in a container that provides a lightweight runtime environment. And these can be scaled up or down as per the user requirements and managed using the orchestration tools like Kubernetes.

Let's understand the difference between a microservices architecture and a monolithic architecture. In a monolithic architecture, the entire application is built as a single unit, which contains the business logic, user interface, and data access layer. These three services are defined within the application as a single instance.

So basically, these three services will share the same resources and database, which makes them dependent on each other. The problem here is if one service within a monolithic application stops working, and then that application will stop.

On the other side, in the microservice architecture, the business logic is organized as multiple, loosely coupled services, where each service has their own resources, which make them independent autonomous services. So even if a single service crashes, it will not affect the other services running within the application.

Let's take a detailed look at how microservices differ from monolithic architectures. So when it comes to unit design, microservices architecture are loosely coupled services. Whereas monolithic architectures are designed, developed, and deployed as a single instance.

![image](https://github.com/qriz1452/oci/assets/112246222/3dd1518b-008e-4339-a80b-b526419f4ed3)

![image](https://github.com/qriz1452/oci/assets/112246222/0eca869a-7984-4b8d-9551-000f1599e74c)


![image](https://github.com/qriz1452/oci/assets/112246222/13da0dee-5d6a-4b09-9449-2364b8640dfc)


![image](https://github.com/qriz1452/oci/assets/112246222/93e697d5-62cb-40af-a93a-73a079962734)


When it comes to functionality reuse, microservices define APIs that expose their functionality to any other client. Whereas in case of monolithic architecture, the functionality reuse is very limited. When it comes to communication within the application, microservices makes use of REST API calls based on the HTTP protocol. Whereas monolithic architectures make use of internal procedures and function calls.

Talking about technological flexibility, microservices architecture offer better flexibility as they show support for multiple programming languages and framework that best suits the problem. Whereas in monolithic architecture, you have to write the entire application using a single programming language.

Talking about data management, within microservices architecture, every microservice can manage their own data store, hence making it decentralized. Whereas in monolithic architecture, you must maintain a centralized database.

When it comes to deployment, microservices architecture can be deployed independently. Every microservice can be coded and deployed independently of each other. Whereas in monolithic architecture, you will have to write the entire code at once and then deploy it.

And again, if you have to make some changes, then you have to redeploy the entire application. Which is also why maintainability is easier in microservices architecture as you are managing small piece of codes at a time. Whereas in monolithic architecture it's very complex to maintain the entire piece of code.

Talking about resiliency and fault tolerance, microservices architectures show high resilience. Whereas monolithic architecture show low resilience. And at the end, talking about scalability, you can easily scale each microservice independently of the other services. Whereas in monolithic architecture, you must scale the entire application.

Communication mechanism in microservices architecture-- as we all know, microservices are distributed in nature. So to communicate with one another, they make use of inter-service communication on network level. Each microservice has its own instance and processes. Therefore, services must interact using an inter-service communication protocol like HTTP, gRPC, or message brokers like AMQP protocol.

Before we design our microservices communication, we should understand about communication styles. In general, there are two criteria to classify these communication systems-- based on the type of protocol that is either synchronous or asynchronous, and based on the number of receivers, which can be single or multiple.

Synchronous communication is using HTTP, HTTPS, or gRPC protocol for returning synchronized responses. The client usually sends a request and waits for a response from the service, which means client code logs that thread until they receive response from the service.

Talking about asynchronous communication-- in this case, the subprocesses are not logged, and protocols that are compatible with many operating systems and cloud environments are used. The most popular protocol for this asynchronous communication is AMQP protocol, that is advanced message queuing protocol. So when using AMQP protocols, the client sends the message using message broker systems. The popular ones are Kafka and RabbitMQ.

Remember, inter-service communication can result in a lot of network traffic. For that reason, serialization, speed, and payload size becomes more important. So if you are communicating between services internally within our microservices cluster, we might also use binary format communication mechanism like gRPC. GRPC is one of the best way to communicate for internal microservice communication.

The second classification criteria of microservice communication protocol is the number of receivers distinguishing between one or many receivers. In case of a single receiver, each request must be processed by a receiver or a service. One example of this type of communication is a command pattern.

And a good example, in case of many receiver, is the event-driven microservice architecture, which is based on a messaging agent or even bus interface that broadcasts the data updates among different microservices using events.

Normally, microservices-based applications use systems that combine different communication styles. The most common type is a single-receiver communication via an asynchronous protocol, with HTTP and HTTPS being one of the most used.




------------------------------


 Design Methodology of Microservices


 The 12-factor methodology is a set of 12 best practices to develop applications which are supposed to run as a service. 12-factor app principles got very popular as it aligns with the microservices principle. Let's look at each of them.

The first one is codebase. This principle states that an app should be tracked in a single code repository and must not shared repository with any other application. Usually in microservices, every services have their own codebase. And having an independent codebase helps you to easy the CI/CD process for your applications.

The next one is dependencies. All the application packages should be managed through package managers like SBT, Maven, or Gradle. For example, Maven requires us to describe a project dependencies in an XML file, typically known as Project Object Model or POM. Again, in a noncontainerized environment, you can go for configuration management tools like Chef, Ansible, et cetera to install the system-level dependencies. But for a containerized environment, you can always go for a Docker file.

Configuration-- configuration says that you must externalize the configurations from the application. All the configuration data should be stored separately from the code in the environment as variables and not in the code repository and should be read in by the code at runtime. Having a separate config file makes it easy to update the config values without touching the actual codebase, thus eliminating the need for redeploying applications when the config values are changed. You can use configuration management tools like Ansible or Chef to automate this process.

Backing services-- a 12-factor app can automatically swap the application from one provider to another without making any further modifications to the codebase. Let us say you would like to change the database server from on-premises MySQL to OCI Database Cloud Service. To do so, you should not make any code changes to your application. Only configuration change should be able to take care of it.

Build, release, and run-- strictly separate the build and run stages is what this factor promotes. You can use the CI/CD tools to automate the builds and deployment process. Docker images make it easy to separate the build, release, and run stages more efficiently. Images should be created from every commit and treated as a deployment artifact.

Processes-- by adopting the stateless nature of REST, your services can be horizontally scaled as per the needs with zero impact. If your system still requires to maintain the state, you can use resources like Redis, Memcached or DataStore to store the state instead of in memory. Never assume that any caged-in memory or on-disk will be available during the feature request or job.

Port binding-- application should be self-contained instead of deploying them into any of the external web servers. To make the port-binding factor more useful for microservices, you must allow access to the persistent data owned by a service only by the way of service APIs. This prevents implicit service contracts between microservices.

Concurrency-- this principle advocates to opt in for the horizontal scaling instead of vertical scaling. While vertical scaling requires adding additional hardware to the system, horizontal scaling works by adding additional instances of the application. In microservices architecture, by adopting the containerization, applications can be scaled horizontally as per the demands.

Disposability-- the system should not get impacted when new instances are added or existing ones are taken down. This is known as system disposability. Systems do crash due to various reasons. The system should ensure that the impact would be minimal, and the application should be stored in a valid state. Services deployed in Docker containers do this automatically as it's an inherent feature of containers that they can be stopped and started instantly.

Development and production parity-- you must always keep the development, staging, and production as similar as possible to avoid the risk of bugs showing up in the later stages of your software development lifecycle. Containers work well for this as they enable you to run the exact same execution environment all the way from local development through the production.

Logs-- logs become paramount in troubleshooting the production issues for understanding the user behavior. Log provides visibility into behavior of a running application. Logs should be streamed to a chosen location rather than dumping them into a log file. Observability and monitoring help you achieve this in a microservices-based architecture, which we will be also covering in our later modules.

Admin processes-- the idea here is to separate the administrative task from the rest of the app to prevent one of task from causing issues with your running applications. For example, doing data cleanup, running analytics for a presentation, or turning on and off features for A/B testing.

After understanding microservices and differences between microservices and monolithic architecture, let us also look at the top benefits of microservices. The primary benefit of microservice architecture is its loosely-coupled components. These components can easily be developed, replaced, and scaled individually.

Microservices are not organized around technical capabilities of a particular product but rather business capabilities as the end goal is user experience and customer satisfaction. As with microservices, the choice of programming language can be multilingual. Also, the development teams can work in parallel on different pieces of code. It improves the productivity and, at the same time, the speed of deployment.

Increased fault tolerance and fault isolation-- microservices offer fallback mechanisms so that in case one microservice fails, the other microservices around it won't get hampered and they can still make progress. Greater scalability and flexibility-- this is one of the important features that microservices offer-- its ability to scale horizontally. This means that any deployed service can be duplicated in order to avoid slow execution bottlenecks.

Simplified security monitoring-- the ability to isolate each service facilitates better security management and monitoring. It's always easier to isolate threats with the modular arrangement. Autonomous, cross-functional teams-- specific microservices can be assigned to specific development teams, which allows them to focus solely on one service or feature this means teams can work autonomously without worrying what's going on with the rest of the application.

Let's take a look at some of the drawbacks of microservices design. Microservices designs are more complex. Communication between services can be complex at times. An application can include dozens or even hundreds of different services, and they all need to communicate securely.

More expensive than monoliths-- for microservices architecture to work for your organization, you need sufficient hosting infrastructure with security and maintenance support. You also need skilled development teams who will understand and manage all of these services for you. Any microservice initiative requires organizations to make changes to their internal culture. Before they can start the migration process, there should already be a mature, agile, and DevOps culture in place.

Microservice's design presents harder debugging problems. Debugging becomes more challenging with microservices. With an application consisting of multiple microservices and with each microservice having its own set of logs, tracing the source of the problem can be difficult at times.

Global testing is difficult. While unit testing may be easier with microservices, integration testing is not. The components are distributed, and developers can't test an entire system from their individual machines.

![image](https://github.com/qriz1452/oci/assets/112246222/e8be792c-933c-416c-aad9-fae503a8451d)

![image](https://github.com/qriz1452/oci/assets/112246222/5794ffb2-3bf6-4645-8683-8b7487761971)


![image](https://github.com/qriz1452/oci/assets/112246222/f8256b6f-e5ce-4c59-a37c-76e2f5252839)



-------------------------------------------------


Introduction to Containerization


To understand containerization, let's think about physical containers for a while. The modern shipping industry can effectively transport cargo thanks to the containers. Imagine how difficult it would be to transport mix of goods like clothes, spices, fragile items, and perishable items that need a controlled temperature. Instead of having ships specialized on transporting certain kinds of cargo, we just pull all things in separate containers and send them all together on the same ship. Containerization Explained in the IT world works basically the same way. Containerization is the process of packaging software code, its required dependencies, configurations, and other details into a container to be easily deployed in the same or different computing environment. In simpler terms, containerization is the encapsulation of an application and its required environment.

The containerization process extends the capabilities virtualization has provided compared to bare-metal solutions. Containers offer more flexibility as they are much easier and faster to deploy. It requires fewer resources to run and are generally more manageable.

Let's talk about containerization benefits. Containers are lightweight. Containers require less system resources than traditional or hardware virtual machine environments because they don't include operating system images. Containers have an inherently smaller capacity than a virtual machine and requires less startup time allowing for more containers to run on a single compute capacity as one virtual machine.

Other container layers like common binaries and libraries can also be shared among multiple containers, making containers inherently smaller in capacity than a virtual machine and faster to start up. Containers are portable. Containers can run anywhere as long as container engine supports the underlying operating system. It is possible to run containers on Linux, Windows, and Mac OS and many other operating systems.

Containers can run in virtual machines or even in bare metal servers, locally on a developer's laptop as well. They can easily be moved between on-premise machines and public cloud. And, across all these environments, they continue to work consistently. Containers provide security. Isolating applications as containers prevents malicious code from affecting other containerized applications or the host system. You can also define security permissions to automatically block access to unwanted components that seek to enter other containers or limit communications.

Let's understand what Docker is. Docker is a tool designed to make it easier to create, deploy, and run applications by using containers. Docker eliminates the inevitable confusion that comes when a developer has been working on their local machine on a project for days or weeks and as soon as it's deployed to a new environment, the application won't run, most likely because there's a host of installed dependencies that are necessary to run that application.

With Docker, your development environment will be exactly the same as your production environment and exactly the same as everyone else's development environment. This helps us alleviate the problem of "its broken on my machine." Docker is also a go-to containerization solution for more and more DevOps solution that makes development, testing, deployment, and monitoring any modern application automated, safe, reliable, fast, and efficient.

OK, so the question is, when to use Docker containers? We can use Docker containers for fast, consistent delivery of your applications. Docker containers makes it easy to put new versions of software with new business features into production very quickly and to quickly roll back to a previous version if the need arises. They also make it easier to implement strategies like blue green deployments.

Docker can be used while implementing microservices. They allow you to containerize your microservices and simplify the delivery and management of those microservices. Containerization provides individual microservices with their own isolated workload environments, making them independently deployable and scalable.

Docker can be used for responsive deployment and scaling. Let's say you want to scale your application to new market or branches. But the question is, will it handle the growing number of users? Docker won't automatically make your app scalable, but can help with this.

Docker containers can be launched in many copies that may run in parallel. So the more users you have, the more containers you can launch, for example, in the Cloud. Before you do so, your software has to be prepared for running multiple instances at the same time. But if the scalability blockers are already removed, Docker containers will come in very handy to launch a scalable application.



---------------------------------------------------------------

 Docker Component




Let's talk about various Docker components. The image on the screen represents various components of Docker architecture that work together to achieve containerization goals. Talking about Docker client, a developer or a DevOps professional communicates with Docker engine through the Docker client, which may be run on the same computer as Docker engine in case of development environments or through a remote shell.

So whenever a developer fires a Docker command, the client sends them to the Docker Daemon which carries them out. The communication between the Docker client and the Docker host is usually taken place through REST APIs. The Docker clients can communicate with more than one Daemon at a time. Docker Daemon is a persistent background process that manages Docker images, containers, networks, and storage volumes. The Docker Daemon constantly listens to the Docker API request from the Docker clients and processes them.

Docker registries are services that provide locations from where you can store and download Docker images. In other words, a Docker registry contains repositories that host one or more Docker images. Public registries include Docker Hub and Docker Cloud and private registries can also be used. Oracle Cloud Infrastructure offers you services like OCIR, which is also called a container registry, where you can host your own private or public registry.

Let's understand how virtual machines are different from containers. As you see from the diagram, a hypervisor or a virtual machine monitor is a software, firmware, or hardware that creates and run virtual machines. It is placed between the hardware and the virtual machines, and it is necessary to virtualize the server.

Within each virtual machine runs a unique guest operating system. VMs with different operating systems can run on the same physical server. A Linux VM can sit alongside a Windows VM and so on. Each VM has its own binaries, libraries, and application that IT services. And the VM may be many gigabytes in size.

This technique provides a variety of benefits like the ability to consolidate applications into a single system, cost savings through reduced footprints and faster server provisioning. But this approach has its own drawbacks. Each VM includes a separate operating system image, which adds overhead in memory and storage footprint. As it turns out, this issue adds complexity to all the stages of software development lifecycle from development and test to production and disaster recovery as well.

It also severely limits the portability of applications between different cloud providers and traditional data centers. And this is where containers come to the rescue. Containers sit on top of a physical server and its host operating system-- typically, Linux or Windows. Each container shares the host OS kernel and usually the binaries and libraries as well. But the shared components are read only.

Sharing OS resources such as libraries significantly reduces the need to reproduce the operating system code. A server can run multiple workloads with a single operating system installation. Containers are thus exceptionally lightweight. They are only megabytes in size and take just seconds to start.

What this means in practice is you can put two or three times as many applications on a single server with containers than you can put on a virtual machine. Compared to containers, virtual machines take minutes to run and are order of magnitude larger than an equivalent container measured in gigabytes versus megabytes. You should use a virtual machine when you want to run applications that specifically require a new OS, also when isolation and security are your priority over everything else. In most scenarios, a container will provide a lighter, faster, and more cost-effective solution than the virtual machines.

Let's discuss a few Docker commands that you will be using while you work with Docker. So in order to create and run a container, the command is Docker run. And you can specify the image name that you want to run within the container.

There are other parameters that you can parse like -p for ports, -d to run it and detach mode, and likewise. Starting a stopped container. You can use the Docker start command followed by a container name or a container ID to start that stopped container. To stop a running container, you can use the Docker stop command and provide container name or ID as an argument.

To restart a running container, you should use Docker restart command followed by container name or its ID as an argument. To get the details of a running container, you can use the Docker inspect command and parse the container name and ID as argument. You can also see the container logs using Docker logs command.

To list all the running containers within your environment, you can use the Docker ps command. And if you want to see all the running as well as stopped containers, you can do a Docker ps minus A. To remove a container, you can use Docker RM command, and you can parse the container name or ID as an argument.


![image](https://github.com/qriz1452/oci/assets/112246222/4ac8d4df-01cf-4638-9584-1a8c378648a6)

![image](https://github.com/qriz1452/oci/assets/112246222/7f06b234-9d48-4db4-a359-ab2132984f4e)

![image](https://github.com/qriz1452/oci/assets/112246222/01403c80-8c98-45f3-8bbf-7fd6fb919537)



-----------------------------

Working with docker images 

Let's understand what a Docker file is. A Docker file is a text file that defines a Docker image. You'll use a Docker file to create your own custom Docker image-- in other words, to define your custom environment to be used in a Docker container.

You'll want to create your own Docker file when existing images won't meet your project needs to a different runtime requirements, which means that learning about Docker files is an essential part of working with Docker. Docker file is a step-by-step definition of building up a Docker image. It provides a set of standard instructions to be used in Docker file that Docker will execute when you issue a Docker build command.

Let's understand each of the commands used here. Every Docker file must start with From instruction. The idea behind this is that you need a starting point to build your image. It can be from scratch or from an existing image available in the Docker registry.

The run command is used to execute a command and will wait till the command finishes its execution. Since most of the images are Linux-based, a good practice is to set up a directory you will work in. That's the purpose of work directory line. It defines a directory and moves you in.

The copy instruction helps you to copy your source code into the image. ENV provides default values for variables that can be accessed within the containers. If your app needs to be reached from outside the container, you must open its listening port using the exposed command.

Once your application is ready to run, the last thing to do is to specify how to execute it. You must add the CMD line with the same command with all the arguments you used locally to launch your application. This command can also be used to execute commands at runtime for the containers, but we can be more flexible using the entry point command.

Labels are used in Docker file to help organize your Docker images. Labels are key value pairs and simply adds custom metadata to your Docker images. As you can see from the example, we have specified the key value pair as maintainer, which specifies who is the one maintaining this Docker file.

Let's take a look at various Docker commands that will be handy when we work with Docker container images. In order to pull an image from the Docker Hub, you can use the Docker image pull command by specifying the image name as the argument. To build an image using Docker file, you need to use the Docker build command, and then you need to specify the Docker file path where the Docker file is stored.

To build an image from a running container, you can use the Docker commit command and providing the arguments like the container name or the ID and then the image name that you wish to store it as. Tagging a Docker image-- you can use the Docker tag command to tag your source image into the target image format.

Pushing an image to Docker Hub-- in order to push your image from local repository to your Docker Hub repository, you need to first log in into your Docker Hub. And, then, you can use the Docker image push command followed by the image name that you wish to push to the Docker registry.

List container images-- at any point in time to check the number of images that you have in a local repository, you can use the Docker image list or the Docker images command. Building an image from your system-- in order to remove an image from your system, you can use Docker image remove or Docker RMI command by supplying the image name as argument to these commands.


![image](https://github.com/qriz1452/oci/assets/112246222/7ddaa055-4301-4c99-a468-e20ccbf2935a)


![image](https://github.com/qriz1452/oci/assets/112246222/7981d840-d7b3-4ce3-884b-b5a5fbd50691)



---------------------------


 Introduction to OCIR


Let me introduce you to Oracle Cloud Infrastructure Registry. Let's first understand what is it. Oracle Cloud Infrastructure Registry, also known as container registry, is an Oracle-managed registry that enables you to simplify your development to production workflow. Container registry makes it easy for you as a developer to store, share, and manage container images. And the highly available and scalable architecture of Oracle Cloud Infrastructure ensures you can reliably deploy your applications.

So you don't have to worry about operational issues or scaling the underlying infrastructure. You can use container registry as a private Docker registry for internal use pushing and pulling Docker images to and from the container registry using the Docker V2 API and the standard Docker command line interface. You can also use container registry as a public Docker registry, enabling any user with internet access and knowledge of appropriate URL to pull images from the public repository in container registry.

Let's take a look at what problem does it solve. Without a registry, it is hard for the development teams to maintain a consistent set of Docker images for their containerized applications. Developers, testers, and CICD systems need to use registry to store images created during the application development process. OCIR makes it possible to iterate on code faster and push it to the production more frequently.

Without a managed registry, it is hard to enforce access rights and security policies for images. OCIR is integrated with identity access management, which provides easy authentication with native Oracle Cloud Infrastructure identity. It is hard to find right images and have them available in the region of deployment.

Container registry is an Open Container Initiative compliant registry. As a result, you can store any artifacts that conform to Open Container Initiative specifications such as Docker images, manifest lists, and Helm charts.

If you are familiar with the function service of OCI, the function service also makes use of OCIR. The function code in OCI is packaged as a Docker image and pushed through the OCIR. And the event triggers can be configured in the event service to make sure when the function is invoked.

Let's take a look at some key benefits of OCIR. Integration-- OCIR provides full integration with container engine for Kubernetes. When it comes to security, registries can be made private or can be made public by an admin.

Regional availability-- you can easily pull container images quickly from the same region as your deployments. High availability-- it leverages OCI for high performance, high availability, and low latency image push and pull to or from the OCIR. Anywhere access-- you can use Docker CLI to push and pull images from anywhere, may it be cloud, on premises, or through your personal laptops.

In each region that is enabled for your tenancy, you can create up to 500 repositories in Oracle Cloud Infrastructure Registry, consuming a maximum of 400 GB in total. And each repository can hold up to 100,000 images at a time.

Before we move further, let's take a look at container registry concepts. What are Docker images? Docker image is basically a read-only template with instructions for creating a Docker container. It holds the application that you want Docker to run as a container along with any dependencies that are required.

Repository-- it's a meaningfully named collection of related images, which are grouped together for convenience in a container registry. There are different versions of the same source image, which are grouped into the same repository. For example, as you can see, we have a repository called mahendra_project/acme-web-app. Now, you can have multiple images stored under this repository. The only thing that you need to keep changing is the image version.

Every image version is given a tag. And the tag uniquely identifies the image. Depending upon your need, a repository can be made private or public. One important thing to note is that user needs to have an OCI username and authentication token before being able to push, pull an image from the OCIR.

When working with repositories and container registry, you will find it helpful to have a clear understanding of following terms and how they relate to each other. The region key-- the region key identifies the container registry region that you are using. For example, as you can see over here, the IAD specifies the US East, Ashburn region, whereas the US-Phoenix-1 specifies the US West, Phoenix region.

Repository name-- repository name is the name of repository in container registry to and from which you can push and pull images. Repository names can include one or more slash characters and are unique across all the compartments in the entire tenancy. You should note that although a repository name can include slash characters, the slash does not represent a hierarchical directory structure. It is simply one character in the string of characters.

As a convenience, you might choose to start the name of several different repositories with the same string-- perhaps ending in a slash such as project01/. Such a string is sometimes called a repository name prefix. But a repository named project01 acme-web-app may not have a relationship with project name project01/mytest-app.

Tenancy namespace-- a tenancy namespace is an autogenerated random and immutable string of alphanumeric characters. For example, the namespace of acme-dev tenancy might be this random string. How to locate your tenancy namespace will be shown during the demo.

Registry identifier-- a registry identifier is the combination of your container registry region key and the tenancy namespace. It has the following structure. As you can see, it starts with the region key and followed by the tenancy namespace. Also make a note, the tenancy namespace can be a random string or it can be a regular name.

A tag or image tag is a string used to refer to a particular image in an known repository. Image name-- the term image name is sometimes used as a shorthand way to refer to a particular image in a particular repository. In this context, an image name has the structure repository name along with tag separated by a colon.

Image path-- an image path is a fully qualified path to a particular image in a registry. It extends the repository path by adding tags associated with the image. It has the following structure. It starts with the region key followed by the tenancy namespace, the repo namespace followed by tag separated by a colon. You can always refer Oracle's documentation to identify the region key for the region you are working in.


![image](https://github.com/qriz1452/oci/assets/112246222/6b4bc356-6afa-4e5a-9ec0-ff45f6d08eb0)

![image](https://github.com/qriz1452/oci/assets/112246222/e0a73a5b-cee2-46d1-89bc-e299d2d79dbc)

![image](https://github.com/qriz1452/oci/assets/112246222/34b97e99-ee60-48ae-b486-f8770be1313e)

![image](https://github.com/qriz1452/oci/assets/112246222/dc27c97e-908d-4118-ba4e-33bbf313860d)


---------------------------

 Introduction to Container Instances


 Meet Alex. Alex wants to test his containerized application but without deploying it on the OKE as the scale is not large. At the same time, the application he wants to containerize are running isolated web applications or RESTful APIs. He is also looking for a simple, quick, and secure way to run containers without managing any servers.

One way for Alex to run his containerized applications without using Kubernetes is to provision a virtual machine, install container runtime, and run the application on it. But this process still increases the operational complexity as it would require him to manage virtual machines and servers, patch the operating systems, and update the container runtime regularly.

Containers have become the favored method of packing, deploying, and managing modern applications. Among container solutions, OCI Container Instances offers the quickest and the most straightforward way to launch containers. By eliminating the operational complexities, OCI Container Instances enable users to run, containerize the applications without having to manage any infrastructure.

Users only need to supply the container images for their applications. And OCI takes care of the underlying container runtime and compute resources. The containers are hosted on fully managed compute infrastructure that's specifically designed for container workloads, providing robust workload isolation for enhanced security.

Optimized for container workloads, a container instance is isolated at the hypervisor level and doesn't share the underlying OS kernel or CPU or memory resources with any other container instances. With this second layer of defense, containers of different applications no longer share the same OS kernel, which reduces the attack surface.

![image](https://github.com/qriz1452/oci/assets/112246222/971b2361-d0c7-4f3c-aace-033ea3943060)

![image](https://github.com/qriz1452/oci/assets/112246222/ae3834c3-4bc0-4f7e-a9d7-2cf09538d9b3)



------------------



 Features and Use Cases of Container Instances


 Meet Alex. Alex wants to test his containerized application but without deploying it on the OKE as the scale is not large. At the same time, the application he wants to containerize are running isolated web applications or RESTful APIs. He is also looking for a simple, quick, and secure way to run containers without managing any servers.

One way for Alex to run his containerized applications without using Kubernetes is to provision a virtual machine, install container runtime, and run the application on it. But this process still increases the operational complexity as it would require him to manage virtual machines and servers, patch the operating systems, and update the container runtime regularly.

Containers have become the favored method of packing, deploying, and managing modern applications. Among container solutions, OCI Container Instances offers the quickest and the most straightforward way to launch containers. By eliminating the operational complexities, OCI Container Instances enable users to run, containerize the applications without having to manage any infrastructure.

Users only need to supply the container images for their applications. And OCI takes care of the underlying container runtime and compute resources. The containers are hosted on fully managed compute infrastructure that's specifically designed for container workloads, providing robust workload isolation for enhanced security.

Optimized for container workloads, a container instance is isolated at the hypervisor level and doesn't share the underlying OS kernel or CPU or memory resources with any other container instances. With this second layer of defense, containers of different applications no longer share the same OS kernel, which reduces the attack surface.

![image](https://github.com/qriz1452/oci/assets/112246222/7eec1a77-78ba-42f2-b41e-f80c8df814ac)


![image](https://github.com/qriz1452/oci/assets/112246222/2148a060-cfed-4f99-a908-fcc8ecc88b65)

![image](https://github.com/qriz1452/oci/assets/112246222/1ababd8e-206e-4382-8743-67d13797a43f)


![image](https://github.com/qriz1452/oci/assets/112246222/5b98b859-a932-439f-8cdd-dbd5e736960c)


--------------------------

 Working with Container Instances



One is the compute-container-instances. The other one is the compute-containers. These two individual resources can also be clubbed as aggregate resource type under the compute-container-family.

There are different permissions associated to different level of access. For example, inspect level of access provides you only with inspect permission, whereas read allows you both inspect and read. In the case of use level of access, you get inspect, read, update, start, stop, and restart permissions. Whereas with the manage level of access, you get access to all the permissions that are listed out here.

Also make a note, for compute container instances, all permissions has prefix COMPUTE_CONTAINER_INSTANCE underscore the permission name. Talking about the compute containers individual resource type, here as you can see, the permissions are different as compared to the previous slide. You get inspect, read, update, log retrieve, create, and delete permissions based on the different level of access.

Also make a note, all permissions here has prefix COMPUTE_CONTAINER underscore the permission name. Let's take a look at some of the policy syntax. For example, policies to let users create container instances.

Here, you can allow a user group to manage compute container family within a given compartment. But also remember the user groups must have adequate OCI IAM policies to use other OCI supporting resources that are required to create OCI container instances.

Another example is if you wish to control the access to container instance using the network security groups, the user groups should be allowed to use network security groups in the given compartment.

Let's take a look at container instances shapes that are managed by OCI. A shape is a template that determines the number of OCPUs, amount of memory, and other resources that are allocated to a container instance. As you can see, we have standard E3, or standard E4.Flex shapes, which lets you customize the number of OCPUs ranging from 1 to 64 OCPU, and the amount of memory when launching your container instance.

For both the flex shapes E3 or E4, you get up to 15 GB of ephemeral storage. The network bandwidth can range from 1 Gbps per OCPU and can go maximum up to 40 Gbps. And at the max, you can have 1 VNIC associated to a container instance shape.

When you create a container instance, you choose how many OCPUs and how much memory it needs for the containers that will run on it. The network bandwidth scales proportionally to the number of OCPUs. This customization allows you to build container instances that fits your workload, which lets you get the best performance and the lowest cost.

Let's discuss the basic details which we can configure while creating container instances. Talking about configuring networking. In the networking part, you can configure the primary network and subnet. You can specify the virtual cloud network and subnet to create the instance in. You can choose from either selecting existing virtual cloud network, or creating a new virtual cloud network, or even entering the subnet OCID.

You can also assign a public IPv4 address to your compute instance. If the subnet is public, you can assign the instance a public IP address so that your instance is accessible over the internet. Under the Advanced options in the Networking section, you can use network security groups to control traffic.

You can also use an available IP address of your choice from the subnet's CIDR. A host name can also be used for DNS within the cloud network. In the Advanced settings, you can configure various advanced options. For example, you can configure graceful shutdown timeout in seconds. This sets the amount of time container instance waits for the OS to shut down before powering off.

You also get an option to configure the container restart policy. Customers can configure restart policies to restart containers within a container instance in case of failure ensuring that the application is always up. You can choose from always, never, and on failure options for your container restart policy.

Tagging. If you have permissions to create a resource, then you also have the permissions to apply free-form tags to that resource. The next step is to configure containers. In the Configure containers section, you get to configure image options.

Under Image options, you get to choose an image source. Here you have two options to choose from. One is the OCI Container Registry, which is the Oracle-managed registry that enables you to store, share, and manage container images.

And other option is to use External registry. Container images can be pulled from any external registry such as GHCR, Quay.io, Docker Hub, or other private registries. You can also configure environment variables used by the container within the environmental variables section. Some of the use cases could be storing a port number in a variable, or storing a password in a variable, or a username for that matter.

Again, you get an option to tag your containers. So if you have permissions to create a resource, you also have the permission to apply free-form tags to that resource. And in the Configure containers, you also can configure advanced settings. Under the Advanced Settings in the Resource tab, you can configure the number of resources that the container consumes in absolutes or percentages.

By default, the containers use all resources in the container instance. So with the help of resource throttling, we can limit the CPU and memory usage in absolutes or percentage. Under the Startup option tab, you can configure working directory and ENTRYPOINT arguments for the containers. These working directory and ENTRYPOINT arguments will override the existing arguments using which these containers were created.

And then you have the Tags tab, which helps you organize your resources according to the business needs. Now before we move ahead, let's take a look at some of the important points, which are good to know when working with container instances.

First thing is setup of IAM policies. Appropriate IAM policies should be assigned to the user groups which are dealing with container instances. Creating a container instance. You can create a maximum of 60 containers on each container instance. Managing container instances. You can start, stop, and restart a container instance. Container instances uses standard shapes which pause billing when a container instance stops.

Metrics. You can monitor the health, capacity, and performance of your OCI container instances by using various metrics. On deleting a container instance, when the containers are deleted by the service, any data on the ephemeral storage is lost.

![image](https://github.com/qriz1452/oci/assets/112246222/26599c6d-5970-4cf7-9561-1298c3083344)

![image](https://github.com/qriz1452/oci/assets/112246222/dd88105f-c03d-4a80-a36e-b34f57219dd8)


