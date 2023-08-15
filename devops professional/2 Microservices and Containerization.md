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





