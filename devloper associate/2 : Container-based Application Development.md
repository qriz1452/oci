Now Playing : Introduction to Containerization

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



--------

Now Playing : Docker Component


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


-----------

Now Playing : Working with Docker Images


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


---------

Now Playing : Introduction to OCIR


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



-------

Now Playing : Managing OCIR


Managing OCIR can be done in three ways. Starting with managing the repository itself, followed by managing the images within the repository, and, last but not the least, managing the overall security of your repository alongside the images. Let's understand each one in more detail.

You can create an empty repository in a compartment and give it a name that's unique across all the compartments in the entire tenancy. There is a limit to the number of repositories you can have in a given region in a tenancy. So when you no longer need a repository, it makes sense to delete it from the Oracle Cloud Infrastructure registry. Make a note that when you delete a repository, it can take up to 48 hours for the deletion to take effect and for the storage to actually be released.

When you create a new repository in Oracle Cloud Infrastructure Registry, you specify the compartment in which you want to create it. Having created the repository in one compartment, you can subsequently move it to a different compartment. The reasons can be many. It can be to change the users who are authorized to use the repository or to change how the billing for a repository is charged.

Let's have a look at how to manage images. You can view the images stored on OCIR using the OCI Console or using Docker images command from your Docker client after logging in to the OCIR repo. To push an image, you first used the Docker tag command to create a copy of the local source image as a new image. As a name for the new image, you specify the fully-qualified part to the target location in your container registry where you want to push the image, including the name of a repository.

In order to pull an image, you must be logged in into the OCIR registry using the auth token and use the Docker pull command followed by a fully-qualified name of the image you wish to download on your Docker client. When you no longer need an old image or you simply want to clean up the list of image tags in a repository, you can delete images from the Oracle Cloud Infrastructure Registry. You can undelete an image you've previously deleted for up to 48 hours after you deleted it. After that time, the image is permanently removed from the container registry.

You can set up image retention policies to automatically delete images that meet particular selection criteria. Criterias can be images that have not been pulled for a certain number of days or images that have not been tagged for a certain number of days. It can also be images that have not been given particular Docker tags specified as exempt from the automatic deletion.

There's an hourly process that checks images against the selection criteria, and any that meet the selection criteria are automatically deleted. In each region in a tenancy, there's a global image retention policy. The default criteria of the policy is to retain all images so that no images are automatically deleted. However, you can change the global image retention policy so that the images are deleted if they meet certain criteria that you specify.

A region's global image retention policy applies to all the repository within that region unless it is explicitly overridden by one or more custom image retention policies. Only one custom image retention policy at a time can be applied to a repository. If a repository has already been added to a custom retention policy and you want to add repository to a different custom retention policy, you have to remove the policy from the first retention policy before adding it to the second one.

Make a note-- the global image retention policy are specific to a particular region. To delete images consistently in different regions in your tenancy, you need to set up image retention policies in each region with identical selection criteria. If you want to prevent the images from being deleted on the basis of Docker tags they've been given, you need to specify those tags as exempt in a comma separated list. When you want to clean up the list of images in a repository without actually deleting the images, you can remove the tags from the images in OCIR. Removing images is referred to as untagging.

During the deployment of an application to a Kubernetes cluster, you'll typically want one or more images to be pulled from a Docker registry. In the Applications Manifest file, you specify the image that you wish to pull, the registry to pull them from, and the credentials to use when pulling the images.

If you want the application to pull images that reside within the Container Registry, you will have to perform two steps. The first one is, you have to use the kubectl to create a Docker registry secret. The secret contains Oracle Cloud Infrastructure credentials to use when pulling the image. The next step is, you have to specify the image to pull from the container registry, including the repository location and the Docker registry secret to use in the application's manifest file.

While managing security, you are given fine grained control over the operations that users are allowed to perform on repositories within the Container Registry. Using the concept of users and groups, you can control repository access by setting up identity access management policies at the tenancy and at the compartment level. These are examples of some of the policies that you can use to control access to your container registry. You can write policies to allow inspect, read, use, and manage operations on the repository based on the requirements.

Before you can push and pull Docker images to and from the container registry, you must already have an Oracle Cloud Infrastructure username and an authentication token. It is not uncommon for the operating system packages included in images to have vulnerabilities. Managing these vulnerabilities enables you to strengthen the security posture of your system and respond quickly when new vulnerabilities are discovered.

You can set up Oracle Cloud Infrastructure Registry to scan images in a repository for security vulnerabilities published in the publicly available common vulnerabilities and exposure databases. To perform image scanning, container registry makes use of the Oracle Cloud infrastructure vulnerability-scanning service and vulnerability scanning REST API.

You need to define certain policies for scanning images for vulnerabilities. Policies like to allow the vulnerability-scanning service to read the repositories within your tenancy or the compartment. Again, policy like to allow vulnerability-scanning service to read compartments within your tenancy or any parent compartment where you are managing your repository.

Preparing for container registry-- before you can push and pull Docker images to and from Oracle Cloud Infrastructure Registry, you need to have the following in place. The first thing is, your tenancy must be subscribed to one or more of the regions in which the container registry is available. You can check the same within the Oracle documentation.

The next thing is, you need to have access to the Docker command line interface to push and pull images on your local machine. The third thing is, users must belong to a group to which a policy grounds the appropriate permission or belong to a tenancies administrator group, which by default have access permissions on the container registry. Lastly, user must already have an Oracle Cloud Infrastructure username and an authentication token which enables them to perform operations on the container registry.



----------

Now Playing : OCIR Images Concepts


The Open Container Initiative is an open governance structure for the express purpose of creating open industry standards around container formats and runtimes. It was established in June 2015 by Docker and other leaders in the container industry.

Following the Docker's release, a large community emerged around the idea of using containers as the standard unit of software delivery. As companies started using containers to package and deploy their softwares frequently, the Docker's container runtime did not meet all the technical and business needs that the engineering teams could have.

So in response to this, the community started developing new runtimes with different implementations and capabilities. To make sure that all container runtimes could run images produced by any built tool, the community started the Open Container Initiative to define industry standards around container image formats and runtimes.

Oracle joined the Open Container Initiative to promote and achieve the initiative's primary goal, that is to host an open source technical community and build a vendor neutral, portable, and open specification and runtime for container based solutions.

The OCI specification is divided into two parts. One is the image specification, and the other one is the runtime specification. Now, these two covers the different phases of the container lifecycle. The OCI image specification defines how to create an Open Container Initiative image, and the runtime specification outlines how to run a file system bundle that is unpacked on the disk.

At a high level, an OCI implementation would download an OCI image then unpack that image into an OCI runtime file system bundle. At this point, the OCI runtime bundle would be run by an OCI run time. So it's important to understand that our Oracle's container registry is an implementation of that OCI runtime specification.

Let's take a closer look at the OCI specifications. Let's talk about image spec. The image spec defines how to create an OCI image and which includes things like image manifest, file system serialization, and image configuration. The image manifest basically provides a configuration and set of layers for a single container image for a specific architecture or an operating system.

File system serialization talks about how to sterilize our file system and file system changes like remove files into a blob called a layer. The image configuration specification outlines the JSON format describing images for use within a container runtime and execution tools and its relationship to file system change sets described within the layers.

Talking about runtime specification, the OCI runtime specification defines how to run the OCI image bundle as a container. So in a nutshell, the container runtime does some of the following tasks. Tasks like container image management, container lifecycle management, container creation, and container resource management.

Let's have a look at some of the popular container runtimes. Container d is a CNCF project, and it manages the complete container lifecycle of its whole system. Rkt is an application container engine developed for modern production Cloud native environments.

Cri-o is an implementation of the Kubernetes container runtime interface to enable using the Open Container Initiative compatible runtimes. It is a lightweight alternative to using Docker as the runtime for Kubernetes. Runc is a CLI tool for spawning and running containers according to the OCI specification. It was developed by Docker and donated to OCI as the first OCI runtime spec compliant reference implementation.

Some of the runtimes like Rkt does most of the task by itself, whereas runtimes like Container d does some of the high level functions and uses other runtimes like Runc for some of the low level tasks.

Let's understand the OCI image layout specification. The OCI image layout is a slash separated layout of OCI content addressable blobs and location addressable references. Now, this layout may be used in a variety of different transport mechanisms. For example, archive formats like tar or zip, shared filesystem environment like NFS, or network file fetching, for example, http, ftp, and rsync.

The OCI image layout consists of OCI layout file. This JSON object serves as a marker for the base of an open container image layout and to provide the version of the image layout in use. The index dot JSON file is a must file to have in the OCI image layout. This file is an entry point for the references and descriptors of the image layout. The image index is a multi descriptor entry point.

Object names in the blob subdirectories are composed of a directory for each hash algorithm, the children of which will contain the actual content. When given an image layout and the references, a tool can create an OCI runtime specification bundle by following the references to find the manifest, possibly using the image index, and applying the file system layers in the specified order, later converting the image configuration into an OCI runtime specification config dot JSON.

So at a high level, the combination of image manifest, image configuration, and one or more system serializations known as layers is called the OCI image. Let's talk about layers within an image. A layer is read-only, and a layer contains the differences between the preceding layer and the current layer.

On top of the layers, there is a writable layer, which is also called the container layer. Any changes to the file system during the container runtime are only returned to this layer, which includes addition, modifications, and deletions of files without changing the content of the original image at the lower layers.

This greatly improves the efficiency of image distribution. Container layer exists only during the container runtime, and it will be deleted when the container is deleted. Multiple different containers can be created from the same image, and only multiple different writable layers need to be created.

Containers that have been changed at runtime can also be repackaged into new image by adding the writable layer to the read-only layers of the new image. After an image has been pushed to an OCI repository, to make sure you're working with the correct image or to identify the image that you no longer need, you could easily view and find out detailed image information, including their layers in the Oracle Cloud Infrastructure Registry.

So this is a snapshot from the OCIR, where if you select a particular image, you get to see all the layers associated with that image. So putting it all together, let's summarize the entire learning using an illustration. The developer creates a Docker file, which consists of syntax for defining the steps needed to create the image and run it.

We use the Docker build command to create the image according to those specifications. We then push the image to a Docker registry, in our case, OCIR, that is Oracle Cloud Infrastructure Registry, also known as OCI Container Registry. And since, the Docker image includes all the elements needed to run an application as a container, users will run an image which builds one or more instances of that respective container that is then deployed to a Docker runtime, such as Oracle container engine for Kubernetes cluster, Oracle functions, or perhaps running your own compute virtual machines.


![image](https://github.com/qriz1452/oci/assets/112246222/b4901513-293d-4bf1-b74f-1fe20d4389be)

![image](https://github.com/qriz1452/oci/assets/112246222/f40edacc-1093-403f-bfa1-908b02da2c5e)

![image](https://github.com/qriz1452/oci/assets/112246222/758677c2-3491-4f61-af14-580035e019d8)

![image](https://github.com/qriz1452/oci/assets/112246222/36af6043-4e01-4b3a-bd21-b021c572d980)

![image](https://github.com/qriz1452/oci/assets/112246222/75a4f545-d814-48f4-8ff0-8b38154b0ae7)



------




















