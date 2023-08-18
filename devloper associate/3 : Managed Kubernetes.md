Now Playing : Module Introduction

So now that you've learned about microservices architecture concepts and containerization in the previous learning modules of this course, the scope of this module is to learn more about using Oracle's managed Kubernetes service, which is called container engine for Kubernetes, or OKE for short.

The VisionStays solution includes three microservices booking hotel and customer all deployed to an OKE cluster. So to put this upcoming module into perspective, leveraging managed Kubernetes, specifically an OKE cluster, provides a robust platform for deploying most, if not all, of your microservices implementations

![image](https://github.com/qriz1452/oci/assets/112246222/b7f0cd17-7201-4216-bea1-c8261c2c7c12)


---------

Now Playing : Introduction to Kubernetes

So you've heard of Kubernetes but you don't know what it is, or you've been playing with Docker and containers and you want to know how to take it to the next level. In this lesson, we are going to take a look at what Kubernetes is and see when and where we might want to use it. So let's get started.

While deploying and managing microservices in a distributed environment, you may run into following issues. Issues such as failures or container crashes. Issues such as scheduling containers to specific machines depending upon the configuration. You also might face issues while upgrading or rolling back the applications which you have containerized. Scaling up or scaling down containers across a set of machines can be troublesome.

Meet Jamal. Jamal loves working with containers. A container is a standard unit of software that packages up goods and all its dependencies so the application runs quickly and reliably from one computing environment to another. Think of them as lightweight virtual machines.

He designs his applications using containers and sees that it's working great. So Jamal then gives a go ahead to Tricia from operations to deploy the application in the production servers. The application becomes popular over time. And, now, to keep up with the increasing demand and to manage the growing workload, Tricia needs to scale her resources.

Now, instead of a handful, she has to deal with hundreds of containers. Tricia is overwhelmed. She needs a simple way to automate the entire process. This is where Mo comes in and introduces Tricia to Kubernetes.

So what is Kubernetes? Kubernetes is a portable, extensible, open source platform for managing containerized workloads and services that facilitates both declarative configuration and automation. Well, if the definition isn't clear to you, here's an analogy. You can think of a Kubernetes as you would a conductor for an orchestra. Similar to how a conductor would say how many violins are needed, which one play first, and how loud it should play, Kubernetes would say, how many webserver front-end containers or back-end database containers are needed, what they serve, and how many resources are to be dedicated to each one.

In Kubernetes, there is a master node, and there are multiple worker nodes. Each worker node can handle multiple pods. Pods are just a bunch of containers clustered together as a working unit.

So Trisha starts designing her application using pods. Once Trisha has her pods ready, she tells the master node the pod definitions and how many she wants to be deployed within the desired state. For example, Trisha here wants to deploy three containers having microservice A and two containers of microservice B and C each.

From that point, Kubernetes is in control. It takes the pods and deploys them to the worker nodes as per their availability and load status. Let's say if a worker node goes down, Kubernetes starts new pods on the functioning worker node.

Tricia doesn't have to worry about complexity of managing containers anymore. She can spend time on observability and managing security of the application. Tricia is happy to see the end results.

So, in a nutshell, Kubernetes can containerized applications of any scale without any downtime. Kubernetes can self-heal containerized applications, making them resilient to unexpected failures. Kubernetes can autoscale containerized applications as for the workload and ensure optimal utilization of cloud resources. Kubernetes also greatly simplifies the process of deployment operations. With Kubernetes, however complex an operation is, it could be performed reliably by executing a couple of commands at the most.

![image](https://github.com/qriz1452/oci/assets/112246222/eee4bf05-d826-4b3d-b537-a1a6418ab2b7)



----------

Now Playing : Introduction to OKE


Oracle Cloud Infrastructure Container Engine for Kubernetes is a fully managed, scalable, and highly available service that you can use to deploy your containerized applications to the cloud. Use Container Engine for Kubernetes-- sometimes also abbreviated as OKE-- when your development teams wants to reliably build, deploy, and manage cloud-native applications. You specify the compute resources that your applications require, and container engine for Kubernetes provisions them on OCI in an existing OCI tenancy.

Container engine for Kubernetes makes use of the open source system Kubernetes. You can access container engine for Kubernetes to define and create Kubernetes cluster using the console and the REST API. You can access the cluster you create using the Kubernetes command line-- that is kubectl-- or using Kubernetes dashboards and the Kubernetes API.

When invited to use container engine for Kubernetes? You can use OKE when it is too complex, costly, and time consuming to build and maintain Kubernetes environment. Managing various components of your Kubernetes cluster like the API server, scheduler, HCD, also managing components of your data plane, performing in-place upgrades, deploying parallel clusters, managing your container networking and storage, these can be difficult at times.

You must also use OCI OKE when it is hard to integrate Kubernetes with the registry and other CI/CD tools for container lifecycle management. You must use OKE when it is difficult to manage and control your team's access to the production clusters.

Let's understand the key benefits of OKE. The key benefit that OKE offers is that it enables developers to get started and deploy containers quickly without worrying about the underlying complexities. It gives DevOps teams visibility and control for Kubernetes management. You must also go for OKE as it combines the production grade container orchestration of open Kubernetes with controlled security, IM, and highly predictable performance of Oracle's next generation cloud Infrastructure.

When it comes to managing components of a cluster, all the master node or the control plane node components like the kube control manager, the kube API, kube scheduler, etcd and cloud controller manager are managed by the Oracle. We make sure that there are multiple copies of these master components created across different availability domains.

We also manage the Kubernetes Dashboard and things like self-healing mechanism of cluster and worker nodes as well. These are all created and managed within the Oracle tenancy. At the customer end, the customer needs to manage whatever work nodes they are creating using different compute shapes as these are created and managed in the user tenancy.

Let's look at the node pool in a little bit more detail. We saw that a node pool is a subset of worker nodes within a cluster that all have the same configuration. So this effectively becomes the unit of scaling infrastructure in OKE clusters.

Compute capacity and cluster is managed by scaling the node pools or creating new node pools. Remember, a node pool can be scaled to zero. That means a pool with no nodes in it.

You can also create and manage these node pools to meet the various demands and workload types based on from their needs. Clusters can have multiple node pools, and they can be heterogeneous. For example, a node pool with four core VMs and another one with 16 core VMs and maybe a third one that is completely different, which uses a bare-metal machine.

On the screen here, we have two node pools, one with standard x86 E3 flagships, which are AMD CPU-based machines, and you can configure the number of CPUs that you have on these VMs. We also see another node pool which is ARM-based and uses A1 bare-metal machines. The replacement configuration also seems to be different in the image with the ARM-based node pool being only deployed in availability domain one and two, whereas the standard x86 node pool uses all three availability domains. A configuration like this is perfectly valid. Workloads can also be targeted to specific nodes using standard Kubernetes methods like label selectors.

Let's now review some of the shapes and operating systems that are supported for OKE worker nodes. Most shapes are supported with a couple of exceptions like bare metal with RDMA or microchips that are provided in the Always Free tier. Likewise, most versions of the Oracle Linux are supported as well as custom images based on supported Oracle Linux versions.

Custom images can be based on official images only. There are some considerations here though. Container engine for Kubernetes installs Kubernetes on top of a custom image. And Kubernetes' other installation software might change certain kernel configurations.

Custom images must have access to a YAML repository, which can be a public or a private repository. Custom images must not use a customized cloud-init. You can perform postprovisioning customizations either using SSH or Daemon search.

As a best practice, ensure that you create a custom image from the most up to date base image. Note that the console currently does not let you use a custom image. You have to use the API or CLI to create node pools that use custom images. We are always improving and expanding our support. Use the OCI command given on the screen to identify the latest supported images and shapes as we continually expand different options.

Let's now consider Kubernetes version support in OKE. Kubernetes is a fast-evolving technology, and frequent upgrade cycles are part of the Kubernetes lifecycle. The open source Kubernetes project itself is supported for three minor versions. Container engine for Kubernetes supports three versions of Kubernetes for new clusters. That means you usually have three choices for Kubernetes version when you create a new cluster.

Version support moves like a rolling window. When OKE adds new support for a new version of Kubernetes, the oldest supported version will have at least 30 days for the continued support. The console will warn you if your cluster is on a version that is soon to be unsupported.

OKE sticks to the Kubernetes project version SKU policy, which is basically to allow the worker nodes that are one version or two version behind the control pane Kubernetes version. But the Kubernetes version on the worker nodes cannot be more than two minor versions behind, and they also cannot be ahead of the control plane version.



-------

Now Playing : Prerequisite to create an OKE Cluster

The first prerequisite, is that you should have an access to an Oracle Cloud Infrastructure tenancy. The tenancy must be subscribed to one or more regions in which the container engine for Kubernetes is available.

The next prerequisite, is to ensure that you have sufficient quota on the resources required to create your OKE cluster. Those resources include compute-instance quota, block-volume quota, and load-balancer quota based on the type of cluster you wish to create.

Within your tenancy, there must already be a compartment to contain necessary network resources such as VCN, subnets, internet gateway, route table, and security list.

Configuring network resources, within the compartment that you have created, you must ensure that all the network resources which I just mentioned, must be appropriately configured in each region in which you want to create and deploy the clusters. To create and manage clusters, you must either belong to the tenancy's administrator group or to a group to which the policy grants the appropriate container engine for Kubernetes permissions.

To perform Kubernetes operations on the cluster, you must be able to run the Kubernetes command-line tool, which is kubectl. You can use the kubectl installation included in the Cloud Shell, or you can use a local installation of kubectl. You must always set up your own copy of clusters kubeconfig configuration file.

Let's take a quick look at some networking configuration. At the time of cluster creation, especially when you are using the API or you are using the Custom Create workflow, you can provide a custom CIDR block for the pods and services. Let's look at what this is and how this impacts the cluster.

The Kubernetes support networking, ensures that every port in the cluster gets an IP address. With OKE you have this ability to provide CIDR blocks from where these port IP addresses are located to the ports and services.

Here on the screen, we can see that the port CIDR block is set to 10.244.0.0/16. That gives us a total of 65,000 IP addresses. We can also see from the image, that the OKE has assigned /25 for each of these nodes.

We are dividing this last 16 CIDR block for the ports into /25 blocks for each of the nodes. Using that, we can get up to 512 such blocks of /25 from our /16 larger block. This means that we can provision 512 nodes in our cluster before exhausting the port CIDR block.

This sets a limit of 512 nodes in a cluster when we use the default configuration. To support more nodes, we need to choose a larger CIDR block for the port CIDR when we are creating the cluster. Remember, that the port CIDR block cannot be changed once the cluster is created. We need to think and plan for this ahead of time.

While on this topic of networking, let's also look at some design consideration or best practices, in general, for our VCN and subnet design. The design of the VCN, itself, is important to OKE and pretty much for any other workload that you deploy on the Cloud provider.

You should ask yourself, what needs to be on this VCN besides the cluster, like other VM-based workloads, other databases, or maybe you have multiple clusters, and they all need to communicate with each other. These are all elements that factor into that design.

An OKE cluster needs at least two subnets to function. One of the subnets is for the worker nodes and the other one is for any load balancer that you might create like, for instance, when you deploy a service of type load balancer.

However, as you can see in the screen, we recommend one more subnet, the Kubernetes endpoint subnet. This is where the Kubernetes API endpoints will be placed. Remember, that each subnet can have a security list that controls the ingress and egress traffic.

Putting the Kubernetes API endpoint in its own subnet, ensures that it can be protected with dedicated security list to restrict access. The Kubernetes API endpoint subnet, only requires a small CIDR block, since the cluster only requires one IP address in the subnet. You can also segregate the worker nodes into multiple subnets if you want to design it that way.

You'll notice, that in this example on the screen right now, all three submits that we have created are public. This means a few things. Firstly, the API endpoint is reachable from the internet if a public IP is attached to it.

That means you can communicate with the cluster using the cluster's API endpoint, using clients like Kubectl, regardless of where you are. Kubernetes will still authenticate you, but it is reachable from anywhere to anyone. You can also modify the ingress rule on the subnet to modify the security list on that subnet to restrict access to specific source CIDRs.

Secondly, this type of a design means the load balancer is also reachable from the internet or specific source CIDRs. This is useful when you're deploying an internet-facing web application, or one that is exposed to the user outside the VCN in general.

The worker nodes are also visible in this use case. You can have public IPs for the working nodes. This is, again, useful when you want to SSH directly into those nodes, very easily, so that you either perform some troubleshooting or maintenance or run some stuff there.

This configuration is one of the simplest and might be good for several use cases. However, having everything public, might expose more of your cluster then you potentially want to or need to. Let's look at a small variation in this.

Here, in this type of design, the worker nodes, or the subnets for the worker nodes, are private. So they are not reachable from outside the VCN. This is useful when you want to restrict access and visibility of your worker nodes.

In this configuration, your VCN should also have the service gateway and a NAT gateway so that the vocal nodes can reach out to external locations, like image repositories, to pull down the Docker images or access other OCA services more efficiently.

To ssh into the nodes, you will also need a bastion, a host that you can jump through to reach your nodes. The security rules on the subnet for the worker node, should ensure that the worker node can still access the control plane, and the load balancers can access the worker nodes hosting the ports.

Let's look at one more variation for this. In addition to the worker nodes, the Kubernetes endpoint is also private now. This means that the Kubernetes API server, is only available within the VCN, so external sources cannot communicate with it.

This is typically in cases where you want to limit the accessibility of the API server itself and manage that access through a bastion or some mechanism like a CICD pipeline that is internal to the VCN. As before, the route tables will now need to include paths to the service gateways and NAT gateways for the Kubernetes API endpoint subnets.

Now, we are not simply relying on the API server authenticating, as we are limiting who can see the API server itself. Inherently, this leads itself to better security practices, since we are reducing our attack surface. Since the load balancer are still exposed, they can still expose applications to the internet.

Now, finally, let's take a look at the design, where all these subnets are private. In this configuration, the cluster can be accessed from within the VCN, and the application's deployed are also restricted to within the VCN.

This is suitable for workloads that are, essentially internal and private. It is also suitable when applications are run in a private VCN and select services are exposed to the outside, by pairing that VCN with another VCN that might act as a broker or more complex network topologies.

Let's take a look at the required policies in order to work with OKE. To create, update, and delete cluster and node pools, users that are not members of the administrator group, must have permissions to work with the cluster-related resources. To give users the necessary access, you must create a policy with several required policy statements for the groups to which those users belong.

The policy statements mentioned on the screen, are required to enable users to use container engine for Kubernetes to create, update, delete cluster and node pools. In the policy statement, you should replace location with either tenancy, if you are creating the policy in the tenancy's root compartment. Or you should replace it with compartment followed by the compartment name if you are creating the policy in an individual compartment.

Also, make a node that allows service OKE to manage all resources in the tenancy. This particular policy must be set in the root compartment of your tenancy. These policies on the screen are required when you're using the Custom Create option while creating the Oracle Kubernetes Engine clusters.

The policies required to create a cluster using the Quick Create workflow are given on the screen. A similar thing to note, is to allow service OKE to manage all resources in the tenancy. And this particular policy, must be set in the root compartment of your tenancy.

![image](https://github.com/qriz1452/oci/assets/112246222/87401053-b999-4ee4-a6ca-5fee81496b65)

--------------

Now Playing : Creating OKE Cluster on OCI




We will start with the cluster creation process. Primarily, we have three paths to create a cluster. The quick create, the custom create-- these are workflows that are available through the console. And you can also create clusters through the API directly or using tools that leverage the API like the OCI CLI or automation tools like Terraform.

The quick create workflow assumes a set of defaults and makes the cluster creation process quick and simple. This is great for a user starting out with OKE and experimenting with it. It exposes a limited set of options so that it does not overwhelm a new user.

The Custom Create workflow on the other hand, gives the users more control over creation process. Importantly, it brings the ability to use your own networking components that are precreated. This is very common because when you start out using an OKE cluster, you might already want that cluster to be placed in an existing VCN of sorts.

The other controls that are exposed by this custom create workflow include encryption options for Kubernetes secret, enabling the choice to enable port security policies, using custom CIDR blocks for ports and services, and customizing the node placement. This is in addition to all the options that are exposed by the quick create workflow like the ability to choose Kubernetes version or endpoint visibility and so on.

Lastly, we have the API-driven or the SDK-based approach, which offers the maximum control over the creation process. This is the preferred method for large-scale production quality deployments as the automation makes the long-term management of the infrastructure easier and much more predictable and reproducible. This is also the only method in which you can provide custom images for your worker nodes. And, obviously, all the options exposed by the custom create and quick create are available here.

Let's look at some cluster design best practices. Creating an OKE cluster is easy as we saw. But designing one that meets your needs for now and the future needs a balancing act. There are several choices you might make. And the criteria that will influence your design, including the node types, the characteristics of the workload, the operational considerations, the security posture, and the cost optimisation, these all play a part. These all are vectors in our design.

For instance, about node types, if you want 96 cores in your cluster, how will you provision that 96 cores? Will you use 48 instances with two cores each, or would you just use four instances with 24 cores each, or something in between? The design process that happens here is that, with larger nodes, they will offer easier management because you have fewer nodes to manage. But if there is a failure on one node, it wipes out a large chunk of our application footprint, so the failure surface is slightly higher.

On the other hand, if we have really small nodes, then you might end up with too many nodes. And the components that run on the nodes also require resources, so you are spending a large chunk of resource on a node to run the cluster itself then for your workload. These are all vectors that play a part in that design process.

When you use certain node types, you will want to manage those workloads differently. Like, for instance, nodes that have GPUs attached to it, nodes that have ARM-based processor on it, or SBC shapes on it, there are a lot of workload characteristics that you need to consider when designing a cluster. And there is operational consideration as well because you need to think about how you upgrade the cluster and how many applications you are deploying onto the cluster.

For instance, think about two applications on a single cluster and these two applications are built by two different teams, and you want to upgrade the cluster. You, basically, want to make sure both these applications are good with the upgrade. And maybe one application will do their testing, and they're good. But the other application is not ready to move up to a newer version of Kubernetes. That's going to block your upgrade. These are operational considerations that you should keep in mind when you design your cluster as well.

Obviously, there are implications to cost optimization and scaling. For instance, when you use a fewer number of nodes that are really large and you just exceeded your threshold for your scaling threshold and you need to create a new instance, but the instance getting created is going to create way more capacity than you actually need. Since that unit of scaling is essentially the configuration of a node pool, that shape that you use for a node pool is very important. These are just a few of those design vectors. Real applications and real cluster design is more of an art, and you really need to consider all these angles when you design the sizing for your cluster.

![image](https://github.com/qriz1452/oci/assets/112246222/377bd950-0ea0-428c-b0b7-8b0b616bf3b3)

---------

Now Playing : Setting Up Cluster Access

Kubeconfig organizes information regarding clusters, namespaces, users, and authentication techniques.

By default, it is located in the .kube directory under the home directory of user with the file name config. If there is any other kubeconfig file, then you can refer it by setting its path to the environment variable kubeconfig. There are three sections in this file-- namely cluster, users, and context. Let's understand each of them one by one.

The clusters is a list of cluster objects that holds the information regarding various clusters the user would like to operate upon using this kubeconfig file. Each cluster object is composed of details about the server and one of the possible authentication details. The user's is a list of user object that holds the information regarding different users of the cluster and their authentication details. Users can authenticate themselves by using certificates, authentication tokens, or basic authentication like username and password.

Context are the list of context objects with the combination of cluster, username, and namespace. In the example, the context staging-admin means use the credential of admin user to access the OCI staged namespace of staging cluster. It is important to have defined the cluster and the user object under the respective sections of the kubeconfig file so that they are successfully referred. Finally, there is one field in the kubeconfig file called the current context that sets the default context to be used.

Let's understand the kubeconfig file in more detail. The authentication token generated by the OCI CLI command in the kubeconfig file are appropriate to authenticate individual users accessing the cluster using kubectl. The authentication tokens generated by the OCI CLI command in the kubeconfig file are short lived plus test code and specific to individual users. As a result, you cannot share kubeconfig files between users to access Kubernetes cluster.

The OCI CLI command in the kubeconfig file uses your current CLI profile when generating an authentication token. If you have defined multiple profiles in different tenancies in the CLI configuration file, you need to set the OCI_CLI_ProfileEnvironment variable to the name of the profile defined in the CLI configuration file before running the kubectl commands.

The generated authentication tokens are unsuitable if you want other processes and tools to access the cluster, such as continuous integration and continuous delivery tools. In this case, consider creating a Kubernetes service account and adding its associated authentication token to the queue config file.

An IAM policy might have been defined to restrict cluster access to only users that have been verified with multifactor authentication. If such a policy exists, you have to add the --profile and --auth arguments to the kubeconfig file to enable multi-factor authentication verified user to access the cluster using kubectl. Container engine for Kubernetes is currently support kubeconfig version 2.0.0 files and no longer support kubeconfig version 1.0.0 files. Enhancement in kubeconfig version 2.0.0 files provides security improvements for your Kubernetes environment, including short-lived cluster scope tokens with automated refreshing and support for instance principles to access Kubernetes cluster.

Let's also understand the kubectl tool. Kubernetes command line tool, kubectl, is used to perform operations on a cluster. Before you can use kubectl to access a cluster, you have to specify the cluster on which to perform operations by setting up the cluster's kubeconfig file. You can use the kubectl installation included in the Cloud Shell, or you can use a local installation of kubectl.

The version of kubectl you use must be compatible with the version of Kubernetes artists running on the cluster. In case of the Cloud Shell, kubectl is regularly updated, so it is always compatible with the version of Kubernetes currently supported by container engine for Kubernetes. You must configure a bastion host to access a cluster with a private Kubernetes API endpoint.

Setting up a cluster access can be done using two methods. The first one is setting up Cloud Shell to access the cluster, where you need to run an Oracle Cloud Infrastructure CLI command in the Cloud Shell window to set up the kubeconfig file. You need to set up the kubeconfig file and verify that the kubectl can access the cluster. Here, most of the things are preconfigured.

The other approach would be to set up local access to the cluster. Here, you need to generate an API sign-in key pair and upload the public key of the API sign-in key pair. You need to install and configure the Oracle Cloud Infrastructure command line interface, later set up the kubeconfig file, and verify that the kubectl can access the cluster.



--------

Now Playing : Deploying an Application to OKE


In this lesson, we will be talking about how to deploy a Python Flask application on the Oracle Kubernetes Engine. We will see how to create an app and build a Docker image for the app. We will also see how to push the Docker image to the OCI container registry.

The application container image stored on the OCI Registry will be pulled by the container cluster and then be deployed on the Oracle Kubernetes Engine. We will also make the app available on the internet, using the load balancer. And all of this will be done using the OCI Cloud Shell.

Let's look into detail the key task that we need to perform as part of this deployment. The first thing that we need to take care of is to create a compartment. Compartment is the location where all the project resources will be managed. So we need to make sure that the users have required policy to manage all the resources within the compartment. The next step is to create a Kubernetes cluster on OCI within our compartment using the quick create option. We will then build a Python application in a Flask framework within the Cloud Shell provided by OCI.

Once we are done creating the Python application, we will create a Docker image out of it. This Docker image will be then stored in the OCI container registry. We will then use Cloud Shell to deploy the Docker application to our OKE cluster. Once the application is deployed on the cluster, we will connect to the application from the internet.

To wrap up-- in this lesson, we saw how to create an Oracle Cloud Infrastructure account to set up a Kubernetes cluster. We saw all the steps required in order to create the Python application with the Flask framework. We also saw how we can leverage OCI services like container registry and OKE in order to deploy our application to the cluster using Cloud Shell.



--------

Now Playing : Observing an OKE Cluster

Let's understand some concepts on monitoring an OKE cluster. Having created a cluster, you can monitor the overall status of the cluster itself and the nodes along with the node pools within it. In addition to monitoring the overall status of cluster, node pools, and the nodes, you can monitor their health, capacity, and performance at the more granular level using metrics, alarms, notifications. These topics will be covered in greater detail in the observability services module.

Many OKE service requests do not take effect immediately. For example, the creation of a node pool isn't completed until all the required instances are active. In these cases, the request is fulfilled asynchronously, and its progress is tracked by an associated work request.

A work request is an activity log that provides visibility into in-progress asynchronous operations, which enables you to track each step in the operations progress. If an operation fails, a work request can help you determine which step of the process had an error. Some operations affect multiple resources. For example, creating a node pool also affects instances. A work requests provides a list of resources that an operation affects.

We can also monitor the summary of status of individual cluster and its control node planes. Cluster can have one of the following statuses. The cluster can be in creating state, which means cluster is in process of being created. The cluster can then move to the active state, which indicates cluster is running normally. The cluster can also go into a failed state, which indicates the cluster is not running due to an unrecoverable error.

The cluster may show its status as deleting. This happens when the cluster is in the process of being deleted. The cluster status reflects deleted when the cluster has been deleted and all the resources have been released. The cluster can also show its status as updating when the version of Kubernetes on the control plane node is in the process of being upgraded. Also make a note that the clusters summary status is not necessarily directly related to the status of node pools and the nodes within the cluster.

You also get to see a detailed summary of each worker node in the node pool. The worker nodes can have one of the following statuses. They can be in creating state, which means the node is being created. It can then go to an active status, which means the node is running normally. It can also go to an inactive status, which means that the node still exists, but it is not running.

The node will show deleting status when the node is in the process of being deleted. The node status changes to deleted when the node has been deleted. And the node status reflects updating when the node is in the process of being updated.

We can also monitor the status of our work request. Resources managed by container engine for Kubernetes can only support one work request at a time. Work requests launched while another work request is in progress will fail and return a conflict because some operations depend on the completion of other operations. You must monitor each operation's work request and confirm it has succeeded before proceeding to the next operation. A create node pool work request has a status of succeeded when the workflow successfully creates an instance and the instance is registered with an active status.

Let's take a look at the various work request statuses. The work request status shows accepted when the request is in the work request queue to be processed. That status changes to in progress when a work request record exists for the specified request but no associated work completed record exist.

The status can change to succeeded when a work request record exists for the request and the associated work completed record has the state succeeded. The status may show failed when a work request record exists for this request and an associated work completed record has the state failed. The work request status can reflect canceling when the work request is in the process of canceling. And it shows canceled in the work request has been canceled.

--------

Now Playing : Accessing the OKE Dashboard

The Kubernetes Dashboard is a web-based management interface that enables you to deploy and edit containerized applications. It helps you to assess the status of containerized application and troubleshoot the containerized applications.

The Kubernetes Dashboard is not deployed in the clusters by default. However, you can deploy the Kubernetes Dashboard in your clusters that you create either using the manual approach or an automated approach. Let's have a look at the steps that you need to follow in order to deploy the Kubernetes Dashboard manually.

The first thing that you have to do is you'll have to deploy the Kubernetes Dashboard to the OKE cluster by applying the kubectl command. The next step is to create the service account and cluster role binding in your cluster. After which you need to obtain an authentication token for the service account that you created. And, lastly, you should enable the kubectl proxy so that you can open the ports and access the Kubernetes Dashboard using the token that you generated in the previous step.

The URL to access the Kubernetes Dashboard when deployed manually looks somewhat like this. Remember, when you manually deploy the Kubernetes Dashboard, it is deployed in the kube-dashboard namespace and not the kube-system namespace.

Let's take a look at a few considerations before using the OKE Dashboard. You cannot run the Kubernetes Dashboard when you are managing your cluster access through Cloud Shell. The sessions created in Cloud Shell do not allow for any incoming connections, and there is no public IP address available, which makes it difficult to access the Kubernetes Dashboard from within the Cloud Shell.

We do not recommend installing the Kubernetes Dashboard on production clusters due to the lack of extensible authentication support. If you do install the Kubernetes Dashboard, we recommend that you restrict the access within the cluster instead of exposing it externally via a load balancer or an ingress controller. The Kubernetes Dashboard is a common attack vector used to gain access to the Kubernetes cluster.

To have container engine for Kubernetes automatically deploy the Kubernetes Dashboard during the cluster creation, you can create the cluster using the API and set the Is Kubernetes Dashboard Enabled attribute to true, which deploys the Kubernetes Dashboard in the kube-system namespace. Also, remember, you cannot add the dashboard as an add-on onto the existing clusters.

-------

Now Playing : Scaling and Deleting the OKE Cluster


Scaling Kubernetes cluster and node pools-- we often see applications face dynamic demands. For example, a company's Ecommerce application might face an increase in the site's visit because of the discounted sales offering or during the festive seasons. Their Kubernetes cluster has to adapt to these fluctuating demands or they risk availability issues related to underprovisioning resources or the extra cost of overprovisioning them.

You can easily scale the clusters you create using OKE to optimize your resource usage. You can do so by changing the number of node pools in the cluster to scale the cluster up and down. You can also change the worker nodes in a node pool to scale the node pool up and down. But these are manual processes. And manual scaling works for predictable workloads but might not be suitable for unpredictable ones and puts an unnecessary burden on the cluster administrator, which is why OKE also provides a provision where you can enable autoscaling to automatically scale node pools and pods.

Let's understand what is this Kubernetes cluster autoscaler. The Kubernetes cluster autoscaler is a standalone program that lets you add worker nodes to the node pool. It can also help you remove worker nodes from a node pool. It increases or decreases the size of a node pool automatically. The autoscaler works on a per-node pool basis and includes resource request limits in the pod specifications.

How to use Kubernetes cluster autoscaler. In order to use the Kubernetes cluster autoscaler, you first need to deploy the Kubernetes metric server to collect resource metrics from each worker node in the cluster. Then you can use Kubernetes Horizontal Pod Autoscaler to adjust the number of pods in a deployment. You can also go for Kubernetes Vertical Pod Autoscaler to adjust the resource request and limits for the containers running in a deployments pod.

So when to use the Kubernetes Horizontal Pod Autoscaler? The Kubernetes Horizontal Pod Autoscaler will automatically scale the number of pods based on the resources CPU or memory utilization or based on some other metrics. They help you scale out or scale in your applications, and you can set a target metric percentage for the horizontal pod autoscaler to meet when scaling applications.

As you can see from the example over here, this command creates a horizontal pod autoscaler for the deployment that maintains a minimum of one and a maximum of 10 replicas of previously created pods controlled by the deployment. The horizontal pod autoscaler increases and decreases the number of replicas of the deployment to maintain an average CPU utilization of 50% across all pods. Remember, you can scale applications manually by updating manifest file without using the horizontal pod autoscaler.

Kubernetes Vertical Pod Autoscaler is used when you wish to set requests automatically based on usage to make sure that the appropriate resource amount is available for each pod. You can also maintain ratios between limits and requests that were specified in container's initial configuration. The Vertical Pod Autoscaler lets you scale down pods that are overrequesting resources based on their usage over time. They also help you scale up the pods that are underrequesting resources based on their usage over time.

You can delete a cluster along with its control plane nodes, worker nodes, and node pools. When you delete a cluster, no other resources created during the cluster creation process or associated with the cluster, such as VCN, internet gateways, NAT gateways, route tables, et cetera are deleted automatically. If you want to delete these resources, you have to do so manually.

The container engine for Kubernetes creates worker nodes in a cluster with an autogenerated name in the format given on the screen. Do not change the autogenerated name of the worker nodes. If you do change the autogenerated name of the worker node and then delete the cluster, the renamed worker nodes are not deleted. You would have to delete the renamed worker node manually.



--------

Now Playing : OKE: Tagging Cluster Resources


When working with Oracle Container Engine for Kubernetes, you can leverage OCI tagging to add metadata to cluster resources. Tags are used to organize and locate resources based on your business needs. So then, what are your tagging options?

First, the cluster resource itself can be described using one or more tags. Then, as you create each node pool, you can define node pool tags. For the nodes that are added to the node pool, you can choose to have them simply inherit the node pool tags or create node tags that will be applied for each provisioned instance.

For block volumes, you can choose to have them inherit the cluster tags or define initial block volume tags that will be applied to each block volume when it is created by a Kubernetes persistent volume claim in the cluster. And in a similar manner, you can choose to have load balancers inherit the cluster tags as well or define initial load balancer tags to be applied when they are created by load balancer Kubernetes service deployments in the cluster.

As a reminder, the OCI tagging service provides two ways for you to add tags to resources. Tag administrators can first create defined tags that specify value choices in advance. Then users, such as an OKE cluster administrator, can apply those defined tags or add freeform tags to provide other metadata to be applied as well.

You'll find tagging useful for various use cases, such as resource tracking, for example, to report all OCI resources, like compute instances, load balancers, and block volumes that are associated with a Kubernetes cluster. Or you may wish to apply application-specific tags to load balancers and block volumes in order to track resources for a given application running in a cluster.

Other use cases involve grouping authorizations for identity and access management policies, for example, to authorize worker nodes to access a designated object storage bucket using instance principles for those nodes as part of a node pool dynamic group tag. A cost-tracking example would be to obtain detailed cost reports for the running of Kubernetes clusters categorized by application or by line of business.

Let's now take a quick look as to how tags can be applied to various resource types using the Custom Create Wizard. Let's navigate over to Developer Services and OKE. And we'll look at creating a new cluster using the Custom Create Wizard. When you launch the workflow, aside for the normal setups you can do, right underneath at the beginning under Advanced Options is where you have the option to come down and add either cluster tags and/or initial load balancer tags and/or initial block volume tags.

And you can add one or more in each of these sections. So for example, if I had a particular tag namespace that was a defined tag already in place-- I'm going to take a look at bill_codes. And there are some options here. We're going to just give that a value. I can add another one. Let's do something with the Finance namespace. And there's a CostCenter.

And we have an option as to which one that applies to. And then we could even add freeform tags as well. Maybe there's a dev team involved that wants to identify this resource. And we'll add that in place. So you can add one or more tags in each of these sections as you see fit.

So let's press on and show what would be involved in with the node pool. Let me quickly update these values so I can get to the next screen. So here's my node pool. And after you define your node pool, down at the bottom, under Advanced Options, is where you have both no pool tags that you can define for the pool itself as well as specific node instance tags that you could apply to those nodes.

Now, you don't have to necessarily do this at cluster creation time. You can also do it to an existing cluster. So if I look at my cluster that's already defined and click on the Cluster Tags tab, that's where I can add cluster resource tags. There's the initial load balancer tags. That's where I can add those for the load balancers. And there's the one for block volumes as well.

If you want to modify a node pool, simply go to Node Pools, select the pool. And once again, you have two tabs, one for node pool tabs that you can add and one for the node tags themselves in this area. However, you're not limited to just using the OCI Console. For example, when creating a cluster with the OCI command line interface, you can add one or more defined or freeform tags as shown here in this example.

The same is true when you're creating node pools in the cluster. You can apply those node pool tags as shown here in this example or, as part of that same create command, you can instead choose to define node-level tags as shown here or even decide to add other tags to be applied to the node instances when they are provisioned.

When creating the cluster with a CLI, these service-lb properties are used for defining the initial load balancer tags as shown in this example. Likewise, these persistent volume properties can also be added to define the initial tags for block volumes that are created as a persistent volume claim within the cluster.

And finally, regardless of whether you provisioned your OKE cluster using the CLI or the Custom Create Wizard in the console, the initial tags for block volumes can be overridden when they are provisioned as a persistent volume claim in the cluster. And you do this by using the override parameters in the manifest file for that storage class definition as shown in this example. Likewise, when deploying a new Kubernetes service of type load balancer to your cluster, you can edit the manifest file to override values for both defined and freeform tags as shown here.

![image](https://github.com/qriz1452/oci/assets/112246222/cc034e8c-8b6b-4942-bbb0-ae92ed930540)

![image](https://github.com/qriz1452/oci/assets/112246222/fe26072e-08c9-4ff6-b5a2-38e085c9d4b6)


-----

Now Playing : OKE: User-Managed Keys


In this lesson, we'll discuss the options you have for using your own OCI Vault keys for block or boot volumes associated with OKE worker node instances. But before we discuss using your own keys, let's review how Oracle Cloud manages data encryption.

You see, by default, data on boot and block volumes used by OKE is encrypted using an Oracle-managed master encryption key. Therefore, even if you're not leveraging the Vault service, stored data, often referred to as data at rest, is always encrypted in the block volume service. You cannot turn it off, which is an important point to keep in mind.

So then, Oracle-managed keys means that we use a master encryption key from an internal Oracle-managed vault which will generate a data encryption key to the block volume service for encrypting and decrypting data. However, when you decide not to use Oracle-managed keys, this is where you are choosing to use a key from your own vault. As you can see here in this boot volume example, you simply locate your vault, then choose the key you wish to use for all the boot volumes for worker node instances within the node pool.

So then, before we can specify our own key for block or boot volume encryption, you have to first create a suitable master encryption key in a vault that you have access to or obtain the name and OCID of such a key if it already is available to you.

Next, you need to create an OCI Identity and Access Management policy authorizing both the OKE and block storage services to use your master encryption key. Here is an example limiting access to just one specific key. Now you can use that key to handle data encryption and decryption in worker node pool boot volumes or in other block volumes that are provisioned as persistent volume claims for your OKE cluster.

Let's first look at specifying boot volumes. Here we are in our OCI Console. And first thing's first. Let's go take a look under Identity and Security and at our Vault service. And we'll look at the vault that I've created already for this demonstration. It's appropriately called our demo vault. And inside the demo vault, I do indeed have a master encryption key that I've already created that uses the AES algorithm, which is required. And here is that particular key.

In fact, I can also, if I need to, which we might use for later for block volumes, I'll need to get a hold of that OCID, that unique identifier, by copying it. Of course, you can see what that entire OCID looks like. Now that we've seen where the key is and what it's called, let's navigate over to our Kubernetes cluster. And in my Kubernetes cluster, I already have a cluster that I've got created. And what we can do when we're defining this for the boot volume is, when we're first creating a cluster, we can run through the wizard and assign that.

Or as I'll show you now, we can actually do it to an existing cluster. I simply go down to my existing node pool. And in that existing node pool, when I click on the option to edit it, I'll have the option to make that change for the boot volume. So if you'll notice, in addition to specifying a different custom volume size or whether or not I want to enable in-transit encryption, here's the option for encrypting the volume with a key I manage.

I'm simply now locating the vault. In this case, it's already been selected, and there's only one key, and I'm locating the key. And I just simply click to save those changes, and it becomes applied for that node pool.

For the other use case, when your Kubernetes persistent volume claims are backed by the Block Volume service, you have the option to encrypt all of your volumes and their backups using your keys as well. First, we see here an example manifest file for defining a storage-class persistent volume that will be encrypted with an Oracle-managed key. Since this is the default when you are setting the attachment type to paravirtualized, instead, you can specify the master encryption key to be used by the block storage service by adding the KMS key ID property and providing the side of the key from your vault you wish to use.

![image](https://github.com/qriz1452/oci/assets/112246222/c9285a61-d629-41c9-9306-d90f19f17be8)

--------

Now Playing : OKE: Custom cloud-init Scripts



In this lesson, we look at how to customize OKE cluster instances used for [? worker ?] nodes by editing cloud-init startup scripts. Cloud-init is the industry standard method for cloud instance initialization supported by all major cloud providers. OKE uses cloud-init to set up the instances hosting the worker nodes in your cluster and installs a default startup script on each instance as shown here.

But because the default host configuration set by OKE doesn't necessarily match every use case, you may need to make your own customizations to those instances hosting those worker nodes. For example, configuring various options on the kubelet, which is the primary node agent on worker nodes, this example sets log verbosity to debug level.

To change from the default initialization script, when editing the node pool, head down to the bottom of the page, and expand the Advanced Options section. Then click the Link to download the template, which will contain the command to execute that default OKE init script. Then you edit to add your own logic.

So what are the use cases? Well, in addition to configuring the kubelet extra-args options as I just mentioned in the previous slide, you can configure a security-enhanced Linux policy on all worker node hosts for security and compliance purposes, perhaps unassign an instance's [INAUDIBLE] public IP on startup, and then reassign the instance a reserved public IP instead. You can configure a corporate proxy or customize yum proxies or perhaps install mandated antivirus software or other security tools.

Keep in mind, you have the flexibility to include your custom logic in the script either before or after the OKE init script command, which must always be included for instance initialization for worker nodes in OKE. OK, that's it for this lesson on customizing cloud-init startup scripts. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/4e96348d-313d-4330-b090-a75d7c5611d8)

![image](https://github.com/qriz1452/oci/assets/112246222/5df896f9-5810-4da4-8a10-05012099f5eb)

---------
Now Playing : OKE: File Storage for PVCs

. In this lesson, we'll explore an additional option you have for provisioning persistent volume claims in OKE. First, let's start with a review. Since a container's root file system is ephemeral, in order to provide a durable location for storing and retrieving data, you can create and use persistent volumes to store data outside of containers.

A persistent volume claim is a request for storage, which is met by binding the PVC to a persistent volume, which provides an abstraction layer to the underlying storage. Well, prior to the January 2022 release of OKE, the primary option for provisioning persistent volume claims was to attach block volumes from the OCI Block Volume service.

Now, you can instead choose to mount OCI File Storage service file systems. These file systems are mounted inside containers running on clusters created by OKE using a CSI driver deployed on the clusters. To create a PVC on a file system in the File Storage Service, we first need to create a file system with a mount target. In the OCI Console, you navigate to Storage, then File Systems. Then click the Create File System button.

The file storage service creates a default name leveraging a current timestamp. But you can change the default name for the file system if you wish. You can also edit the export and mount target information or just choose to accept the defaults. When you're satisfied, click the Create button, and the file system is provisioned within a few seconds.

Next, you need to create security rules in either a security list or a network security group for both the mount target that exports the file system and for the cluster's worker node instances. The details for those required rules will depend on whether or not the mount target and cluster entities are in the same or different subnets. This slide illustrates the same-subnet scenario. Either way, of course, all of those rules' requirements are fully described in the File Storage Service documentation.

Next, you'll need to create a persistent volume that is backed by that file system. You do this by first creating a manifest file to define the PV. Here, in this example, we've defined a PV named fss-pv. And in the CSI section, the volume handle includes the OCID of the file system, the IP address of the mount target, and the mount path. Then you'll use a kubectl create command to add it to the cluster.

To create the PVC that is provisioned by the PVC you created, you'll need another manifest file to define the PVC and set the volume name to the name of the PV you just created. And finally, of course, you'll use the kubectl create command again to add it to the cluster. OK, that's it for this lesson on using OCI File Storage for persistent volume claims. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/1705b9f9-779a-43dd-a711-b73cb172bec8)

![image](https://github.com/qriz1452/oci/assets/112246222/35273103-92f7-4d50-bb0a-06547b2a7440)

------

Now Playing : OKE: Capacity Reservations

. In this lesson, we look at using capacity reservations for worker nodes in your OKE cluster. As a reminder, the Compute service enables you to create capacity reservations to ensure that compute capacity is available for workloads when required during critical events, such as disaster recovery or unexpected workload spikes. Once you've created a capacity reservation in the Compute service, you can then specify that capacity reservation when using to define a node pool's placement configuration which will then be leveraged when scaling the nodes in the pool.

Now, if your region has more than one availability domain, and you're using all three ADs for your node pool, as in this example, then you'll need to create a separate capacity reservation for each AD. In fact, we'll look at this in just a moment in the demo. Specifying the capacity reservation ensures that the node pool's worker nodes are created with new compute instances from that reserved capacity. In this example, our node pool has a total capacity of 60 worker node instances.

Let's now take a closer look at how this is managed in the OCI Console. OK, so prior to specifying a capacity reservation for our cluster, one must first exist. So I go to Compute and Capacity Reservations. You can see I've already created three of them, but I wanted to demonstrate real quickly how easy it is to create one.

You simply click on Create. I'll call this Demo. And I'm going to associate it with, in this case, one of my three availability domains. Of course, some regions only have one availability domain.

And then, in this section, is where you decide-- you can either dynamically let it choose a fault domain, or you can specify one. Then, of course, you specify one or more compute shapes. In my particular use case, I've been using the VM standard E2.1, with just one core and 8 memory and then just specify some sort of a count of whatever should be appropriate. And you can actually add additional shapes as well if you need to.

For example, maybe I want to add a few more of these and allow for maybe up to two of those. And so forth. Once you've done that, it gives you a review. That's how it's done, and you simply create it. Now, for our demonstration purposes, what I've done is created three I intend to use, one assigned to the AD1 availability domain. And we can see its capacity configuration is for 20 of those.

If I wanted to add another one, I could. Or if I wanted to edit the configuration and simply change the count, I could do that as well. Or I could edit to make a change for this one by simply adding some more capacity. For example, I could add another virtual machine type and a specify account and add that configuration to our shape. And now we'd have both of those.

I'm going to revert that back in just a moment. Let's go back and look at the other two, though, real quick. The AD2, of course, has got a capacity of 20 of those shapes. And the AD3 has a capacity of 20. I'm going to go back and fix the one that I changed and simply delete that configuration.

So now that we've validated our three capacity reservations, let's head over to our cluster configuration. Show how you would then specify this when creating a new cluster. First thing's first, you can't use the Quick Create wizard.

You have to use the Custom Create in order to make this specification. So I'll launch that workflow. And we'll simply select a VCN that already exists for us. Select one for the load balancer. Select one for the API endpoint subnet.

And when I advanced to now configuring my pool, I'm going to specify that shape that I decided we're going to be using. And let's go ahead and use the next to latest version of Linux, and we'll go ahead and set up six nodes. And now, if you'll notice, down below is where we can do the placement configuration, of course.

So one for activity domain, the first one, assign it to the private subnet. And when you expand the options, that's where you see the default is on demand capacity. Here's where you specify the capacity reservation. And you then look for one of those. That's the one that's associated with this activity domain.

We'll add another one for the AD2. And of course, over there, I just created that Demo one. We're going to be using this one and one more row to assign nodes to the AD3, specifying our capacity of 20. And we click on Next. And there's a summary of creating my configuration.

Now, I'm not going to actually create the cluster right now. It just would take a while. But you can see the overview of the configuration, the subnet, the capacity reservation, and so forth. What we can do, though, is make a change to an existing cluster. I want to show you how that would be done. I already have a cluster here that has one node pool. Let me slide down here, show you that I have one node pool.

And there's two ways you can make a change to add a capacity reservation. One would be to add a new node pool and then, with that new node pool, just like I did a moment ago, go ahead and define what that should be-- number of nodes, assign the availability domains, use advanced options to do the capacity reservation, and so forth.

And the other way to do it is to modify the existing pool. I actually use different names right here. So this was my one I had from before. And the way to make a change there-- notice the placement configurations are configured the same. But it's an on-demand capacity. So to make that change, instead of clicking edit, you click scale, and now I could change the number of nodes or leave it the same.

But here's where I can now go through. Right now I can go into all three availability domains. But if I look at each one of them, they're all set to on-demand capacity. So here's where I could make a change by, let's say, temporarily increasing this now or leave it the same and go in and change that to a capacity reservation accordingly. Let me go ahead and do that real quick.

And as I make these changes then and click on Scale, it will automatically now add instances. Let's say, if I increase this to-- let's just do six nodes for fun and scaled us out. So what this is going to do is going to take, from that reservation, those additional five that get instantiated.

And if we can wait for just a moment, we could then take a look at the nodes in that pool. And here they are becoming-- well, this is the one that was already running. The rest of these are beginning to be instantiated.

And we'll just wait a moment for them to become ready. OK, now that they're all provisioned and ready, I can go take a look at a couple of things. First of all, I can see my placement configurations up here with the capacity reservations. If I were to select one of these, for example this instance, I can look at it from the compute service. And in that general information page, in the compute service, I can look to see it's the capacity type is not on demand, but capacity reservation and which reservation it's associated with.

And if we wanted to navigate over and take a look at those capacity reservations, I can now see that out of that 20 capacity, 2 of them have been used. You can even navigate to see the other instances associated with that reservation right here. And notice it automatically puts them in two separate fault domains.

The other thing I wanted to point out to you is, that very first instance that was already running, if I go take a look at it, it will actually show me that, as opposed to a capacity reservation, it still is listed as on demand. And the reason why it's going to be listed as on demand for capacity type is because it was still running. So if I want for it to count against that capacity reservation, I would need to go ahead and terminate this virtual machine instance and then let OKE provision another one against the capacity reservation.

---------

Now Playing : OKE: Network Security Groups

we look at the capability that allows you to leverage network security groups in your OKE cluster. In addition to using security list rules to control access to resources in your OKE cluster, you can also choose to append additional rules defined in one or more network security groups. Now, as a reminder, when creating a new OKE cluster, you must select a public or private subnet for the API server, and for the node pools containing your worker nodes, and you also select one or more subnets for load balancers.

Now, although rules for ingress and egress traffic are commonly defined in security list rules that are associated with those subnets, you may wish to add specific access rules that would apply to the API server, or worker nodes, or to a load balancer. For the API server, you can assign an NSG if it is already defined in the VCN if you use the Custom Create wizard as shown here.

However, if you've already provisioned your OKE cluster, you can create a new NSG in the VCN, then assign it later using the Edit Cluster wizard. Likewise, if you've already created one or more NSGs and you're using the Custom Create wizard, you can assign them as you're defining the node pool, or you can assign one or more NSGs later using the Edit Cluster wizard.

Let's now take a closer look at those options in the OCI Console. Let's start out by looking at an existing OKE cluster. In this case, I have OKE Demo. And when I click on that cluster, I can see its basic information to include the VCN it's associated with. And if I wish to edit or make a change to add a network security group, I need to make sure that those security groups actually already exist.

So for this particular example, I'm going to go ahead and navigate over, open up a new tab, and look at the VCN that's associated with this cluster. In this VCN, you'll notice, down here, I have four network security groups that I've created ahead of time. And what I have in mind is using one for my work nodes, using one for my API server, and I've got a couple that can be leveraged for load balancer services.

Now that we see that they're there, let's go back to our cluster itself. And if I wish to edit the cluster, I can edit the Kubernetes API server endpoint. That's one way. Or I can just work on updating the nodes in the node pool. Let's do that one first. I go to my node pool. And in the node pool, I click on Edit. And there, I can see I can change options like the shape of my nodes, and the images, and so forth. But in this case, I simply am looking to add a network security group to control traffic. And I'll select that cluster worker nodes that I had earlier and save those changes.

Now that that's done, let's go back and take a look at our cluster, and go ahead and edit and make a change to the network security groups to control the API server. Same thing. I click on that, choose the appropriate network security group-- or I can actually add more than one to any of these if I need to. But usually, one is sufficient. And then I simply would click on Save to make that change. And that's going to take a little bit longer because it involves the control plane.

Now, let's switch back over to our clusters and show what it looks like when you're creating a brand-new cluster. In this case, I'm going to use the Custom Create wizard, launching that workflow. And when I do, I'm just going to be presented with some options as to which VCN that already exists. I'm just going to leverage the same one I had for the other cluster. I need a subnet for my load balancer. I'll choose a public subnet. And for my API server, as typical, I'll use a private subnet.

And then right below that is the opportunity to go ahead and define the network security group I wish to use. So in this case, I'm going to use that Kubernetes API network security group. And when I click on Next, it allows me, then, to define my node pool. When I define my node pool, right there, I have-- once I choose the shape of my servers and how many nodes-- here's where I would now choose a network security group for them. In this case, I'm going to choose that one, and then I would simply click on Next and Configure to finish the configuration of my cluster.

Now that we've seen how to assign network security groups to the API server and to the worker nodes, how do we specify an NSG for an OCI load balancer that gets automatically created by OKE whenever you deploy a new Kubernetes load balancer service to your cluster?

Well, first, you need to locate the OCID, or Oracle Cloud Identifier, of the network security group you wish to assign. Then, in the manifest file, you add this annotation in the metadata section, providing the OCID of the network security group to be used. OK, that's it for this lesson on leveraging network security groups in OKE. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/b41b141e-cb4e-445a-b6f8-adcfbe95d7cb)

--------
Now Playing : Serverless OKE Clusters

we'll take a look at a newer OKE feature that provides for serverless clusters. While OKE is a managed Kubernetes service, when creating a new cluster, you can now choose either managed nodes where you select either specific bare metal or virtual machine shapes or the virtual nodes option, which provides for a conceptual serverless OKE cluster.

With virtual nodes, you can ensure reliable operations of Kubernetes at scale without needing to manage any worker node infrastructure. There's no constraint on CPU and memory resources at the node level since pods are executed on right-sized virtual machine instances based on the CPU and memory requirements specified in the pods deployment spec.

You can scale your deployments using Kubernetes Horizontal Pod Autoscaler without having to add or remove worker nodes from your cluster or configuring the cluster autoscaler. This also simplifies Kubernetes cluster upgrades. A single click operation triggers the upgrade of all Kubernetes components in both the cluster control plane and data plane.

First, the cluster control plane and virtual nodes are upgraded without any impact on workloads. Then kube proxy running on each pod is upgraded. Pods then restart asynchronously onto the same virtual node. Virtual nodes allow you to select a compute shape to assign to your pods, allowing you to control the performance of your applications.

Pods can scale up to the maximum CPU and memory supported by this selected shape, for example, with AMD E3 and E4 shapes, you can scale up to 64 cores and 1 terabyte of memory. Virtual nodes improve security, primarily because pods don't share any underlying kernel, memory, or CPU resources.

Each Kubernetes pod natively connects to your virtual Cloud network through a dedicated V-neck. So each pod benefits from the security features provided by VCNs, including security rules, flow logs, and routing policies.

And finally, you optimize the cost of running Kubernetes workloads because you pay for the exact compute resources consumed by each Kubernetes pod instead of paying for whole servers that might have unused capacity. When using virtual nodes, resource allocation is at the pod level rather than at the node pool level.

Let's quickly take a look at the provisioning process using the OCI Console. So this time under Kubernetes service, we click on Create Cluster. Now for demonstration, I'll just use Quick Create, although you can use Custom Create if you wish.

When you submit, you'll notice the difference now is that once you decide to give it a name, you can still use and choose which Kubernetes version you would like to use for your cluster. But now instead of just managed node type, where you choose a specific shape and image, if you select on virtual, essentially then that goes away.

You still have an opportunity to define whether or not you want to use public or private endpoints for the Kubernetes API. But then now notice that the node count is still available to you, which you can choose, as well as, of course, the pod shape.

Pods will be provisioned in virtual machines using either E3-- AMD E3 or AMD E4. And that wraps up this overview lesson on OKE virtual nodes. To learn more details, please be sure to review our online documentation. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/f60b6970-b4af-467e-b10b-e0c52fdc1625)



--------














































































