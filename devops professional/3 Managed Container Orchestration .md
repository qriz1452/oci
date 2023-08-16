 Introduction to Kubernetes


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



![image](https://github.com/qriz1452/oci/assets/112246222/2f7aeb0d-894e-401f-a2dd-d45224ee3a10)



![image](https://github.com/qriz1452/oci/assets/112246222/92f9bfd6-fdce-42a0-b744-e39e6a9c41d8)

![image](https://github.com/qriz1452/oci/assets/112246222/3949ebed-3b44-468c-a38d-561d4b645cb3)

![image](https://github.com/qriz1452/oci/assets/112246222/14c9684e-030e-4e00-9e79-62e609c8c838)



--------------------





 Overview of Kubernetes Architecture and it's main components

 


the Kubernetes cluster has two main components. One is the control plane, which you can see on the left side of the image on the screen. And one is the data plane, which you can see on the right-hand side of the image on the screen.

The control plane hosts the components used to manage the Kubernetes cluster. And the data plane basically hosts all the worker nodes that can be virtual machines or physical machines. These worker nodes basically host pods which run one or more containers. The containers running within these pods are making use of Docker images, which are managed within the image registry. In case of OCI, it is the container registry.

Talking about node, it is the smallest unit of computing hardware within the Kubernetes. Its work is to encapsulate one or more applications as containers. A node is a worker machine that has a container runtime environment within it.

Talking about pods, a pod is a basic object of Kubernetes, and it is in charge of encapsulating containers, storage resources, and network IPs. One pod represents one instance of an application within Kubernetes. And these pods are launched in a Kubernetes cluster, which is composed of nodes. This means that a pod runs on a node but can easily be instantiated on another node.

A pod can even contain more than one container if these containers are relatively tightly coupled. Pod is usually meant to run one application container inside of it, but you can run multiple containers inside one pod. Usually, it is only the case if you have one main application container and a helper container or some sidecar containers that has to run inside of that pod.

Every pod is assigned a unique private IP address, using which the pods can communicate with one another. Pods are meant to be ephemeral, which means they die easily. And if they do, upon recreation, they are assigned a new private IP address. In fact, Kubernetes can scale a number of these pods to adapt for the incoming traffic, consequently creating or deleting pods on demand.

Kubernetes guarantees the availability of pods and replicas specified but not the liveliness of each individual pod. This means that other pods that need to communicate with this application or component cannot rely on the underlying individual pod's IP address. So the question here is, how does Kubernetes manage this traffic to this indecisive number of pods with changing IP addresses?

This is where another component of Kubernetes called services comes in as a solution. A service gets allocated a virtual IP address and lives until explicitly destroyed. Request to the services get redirected to the appropriate pods, does the services of a stable endpoint used for inter-component or application communication.

And the best part here is that the lifecycle of service and the pods are not connected. So even if the pod dies, the Service and the IP address will stay, so you don't have to change their endpoints anymore.

There are two types of services that you can create. The external service is created to allow external users to connect the containerized applications within the pod. The URL can be seen on the screen. It is basically the combination of IP address and the pod number. Internal services can also be created that restrict the communication within the cluster. Services can be exposed in different ways by specifying a particular type.

There are three types in which you can define services. The first one is the ClusterIP, which is the default service type that exposes services on an internal IP within the cluster. This type makes the service only reachable from within the cluster.

You can specify the type of service as NodePort. NodePort basically exposes the service on the same port of each selected node in the cluster using a network address translation and makes the service accessible from the outside of the cluster using the node IP and the NodePort combination. This is basically a superset of ClusterIP.

You can also go for a LoadBalancer type, which basically creates an external load balancer in the current cloud. OCI supports LoadBalancer types. It also assigns a fixed external IP to the service. And the LoadBalancer type is a superset of NodePort.

Moving on to another component, which is an ingress. An ingress is used when we have multiple services on our cluster, and we want the user requests routed to the services based on their pod, and also, if you want to talk to your application with a secure protocol and a domain name.

Consider an example for an e-commerce web application. Let's say I have two services. One is the Place Order, and one is the Cancel Order in our cluster. When we type, let's say, www.xyz.com/placeorder, we should be routed to the Place Order service. And when the user types www.xyz.com/cancelorder, we should be rotated to the Cancel Order service. These routings will be performed by an ingress.

Unlike NodePort or LoadBalancer, ingress is not actually a type of service. Instead, it is an entry point that sits in front of the multiple services within the cluster. It can be defined as a collection of routing rules that govern how external users access services running inside a Kubernetes cluster. Ingress is most useful if you want to expose multiple services under the same IP address, and these services all use the same Layer 7 protocol, typically HTTP.

A deployment is an object in Kubernetes that lets you manage a set of identical pods. Without a deployment, you will need to create, update, and delete a bunch of pods manually. With the deployment, you declare a single object in a YAML file, and the object is responsible for creating the pods, making sure they stay up to date and ensuring there are enough of them running.

You can also easily autoscale your applications using a Kubernetes deployment. In a nutshell, the Kubernetes deployment object lets you deploy a replica set of your pods, update the pods and the replica sets. It also allows you to roll back to your previous deployment versions. It helps you scale a deployment. It also lets you pause or continue a deployment.

Pods communicate with each other using a service. For example, my application here has a database endpoint. Let's say it's a MySQL service that it uses to communicate with the database. But where do you configure this database URL or endpoints? Usually, you would do it in the application properties file or as some kind of an external environment variable. But usually, it's inside the build image of the application.

So for example, if the endpoint of the service or the service name, in this case, changes to something else, you would have to adjust the URL in the application. And this will cause you to rebuild the entire application with a new version, and you will have to push it to the repository. You'll then have to pull that new image into your pod and restart the whole thing. For a small change like database URL, this is a bit tedious.

So for that purpose, Kubernetes has a component called ConfigMap. ConfigMap is a Kubernetes object that maintains a key value store that can easily be used by other Kubernetes objects, such as pods, deployments, and services. Thus, you can define a ConfigMap composed of all the specific variables for your environment.

In Kubernetes, now, you just need to connect your pod to the ConfigMap, and the pod will read all the new changes that you have specified within the ConfigMap, which means you don't have to go on to build a new image every time a configuration changes.

Now, you must be wondering, if we can have a ConfigMap to manage all the environment variables and the URLs, should we be passing our username and password in the same file? The answer is no. Password or other credentials within a ConfigMap in a plain text format would be insecure, even though it's an external configuration. So for this purpose, Kubernetes has another component called secret.

Kubernetes secrets are secure objects which store sensitive data, such as passwords, OAuth tokens, and SSH keys with the encryption within your cluster. Using secrets gives you more flexibility in a pod lifecycle definition and control over how sensitive data is used. It reduces the risk of exposing the data to unauthorized users.

So secret is just like ConfigMap, but the difference is that it is used to store secret data credentials, for example, database username and passwords, and it's stored in the base64 encoded format. The kubelet service stores this secret into a temporary file system.

Let's understand the data storage concept and how it works within Kubernetes. So let's say we have this database pod that our application uses, and it has some data or generates some data. What happens when the database container or the pod gets restarted? Ideally, the data would be gone, and that's problematic and inconvenient, obviously, because you want your database data or log data to be persisted reliably for long term.

To achieve this, Kubernetes has a solution called volumes. A Kubernetes volume basically is a directory that contains data accessible to containers in a given pod within the Kubernetes platform. Volumes provide a plug-in mechanism to connect ephemeral containers with persistent data stores elsewhere.

The data within a volume will outlast the containers running within the pod. Containers can shut down and restart because they are ephemeral units. Data remains saved in the volume even if a container crashes because a container crash is not enough to cut off a pod from a node.

Talking about Stateful applications, Stateful applications are applications that store data and keep tracking it. All databases such as MySQL, Oracle, and PostgreSQL are examples of Stateful applications. In a modern web application, we see stateless applications connecting with Stateful application to serve the user request.

For example, a Node.js application is a stateless application that receives new data on each request from the user. This application is then connected with a Stateful application, such as MySQL database, to process the data. MySQL stores the data and keeps updating the database on the user's request.

Now, assume you deployed a MySQL database in the Kubernetes cluster and scaled this to another replica, and a frontend application wants to access the MySQL cluster to read and write data. The read request will be forwarded to both these pods. However, the write request will only be forwarded to the first primary pod. And the data will be synchronized with other pods. You can achieve this by using the StatefulSets.

Deleting or scaling down a StatefulSet will not delete the volumes associated with the Stateful applications. This gives you your data safety. If you delete the MySQL pod or if the MySQL pod restarts, you can have access to the data in the same volume. So overall, a StatefulSet is a good fit for those applications that require unique network identifiers; stable persistent storage; ordered, graceful deployment and scaling; as well as ordered, automatic rolling updates.

To wrap up, in this lesson, we covered Kubernetes components, starting with the nodes, pods, and the services. We understood how communication takes place between pods. We also saw ingress component, which is used to route traffic into the cluster. We also looked at the external configuration using ConfigMaps and managing sensitive information using Secrets. 


![image](https://github.com/qriz1452/oci/assets/112246222/50caa3de-b11f-4338-961b-ddae534004ef)


![image](https://github.com/qriz1452/oci/assets/112246222/dc87419d-07e2-4b9d-8d69-a6a6178edcb3)

![image](https://github.com/qriz1452/oci/assets/112246222/b4bc9154-a05a-4e45-9b31-cc9e69263006)


![image](https://github.com/qriz1452/oci/assets/112246222/eeb15b6e-256d-447a-a7f2-372495d86883)


![image](https://github.com/qriz1452/oci/assets/112246222/bccb85b0-9a42-4dd6-a431-9675453778de)


![image](https://github.com/qriz1452/oci/assets/112246222/5b1c0077-a48f-4c1a-a271-cff2ddf9bf55)


![image](https://github.com/qriz1452/oci/assets/112246222/c775b4f4-5775-4c1d-ab93-82b6d2c9b7f9)


![image](https://github.com/qriz1452/oci/assets/112246222/83ddf29f-4345-4432-8104-272c6ffddc6b)


![image](https://github.com/qriz1452/oci/assets/112246222/4bf6bb68-ee6f-4853-9606-2ddfc3994104)



----------------------

Components of Kubernetes Architecture and its features



Kubernetes architecture components include the Kubernetes control plane and the nodes in the cluster.

A cluster has one master node and multiple worker nodes. The master node handles scheduling, changes in state, and handles updates. The nodes within the cluster are routinely replaced. An entire Kubernetes system contains multiple clusters, and these clusters can be done in cloud or on premises.

The control plane is the nerve center that houses Kubernetes cluster architecture components that control the cluster. The control plane machine components include the Kubernetes APIserver, Kubernetes scheduler, Kubernetes control manager, and etcd. Let's take a look at each of these components.

To begin with, let's understand about APIserver. The APIserver accesses the interface that enables communication between other components within the cluster. It is also the entry point for the external request to the clusters which must go through its HTTP API. Any access and authentication, such as deployments of ports and other Kubernetes API objects, are handled by the APIserver using the kubectl commands or using the REST API calls.

Etcd-- etcd is a database that stores the data in the form of key values. Kubernetes components stores all kind of information in etcd like metrics, configuration, and other metadata about ports, services, and deployments of the Kubernetes cluster.

Talking about kube-scheduler, the scheduler's responsibility is to assign ports to nodes within your cluster. The scheduler will use information such as compute requests and limits defined within your manifest, as well as finding the right node candidate based on its available resources to appropriately assign your workload to a particular node.

Kubernetes controller manager is a daemon, which runs the Kubernetes cluster using several controller functions. Functions like replication controller, endpoint controller, namespace controller, service account controller, DaemonSets controller, and job controllers are used.

This controller watches the objects it manages in the cluster. It observes them for their desired state and current state via the API server. If the current state and the desired state of the managed objects don't match, the controller takes corrective steps to derive object status towards the desired state. The Kubernetes controller also performs core lifecycle functions.

We also have a cloud controller manager within the control pane. Cloud controller manager runs controllers that interact with the underlying cloud providers. Cloud controller manager binary is an alpha feature introduced in Kubernetes release 1.6. Cloud controller manager runs cloud provider-specific controller loops only.

Now, let's understand different components within the Kubernetes worker node. The node components run on every node, maintaining running ports and providing Kubernetes runtime environment. Kubernetes node components include a container runtime engine, a kubelet service, and a Kubernetes proxy service.

The kubelet service is responsible for node-level port management. APIserver put HTTP requests on kubelet APIs to execute port definition from the manifest file on the worker. Its functionality is to watch for new or change port specification from master node and ensure that the ports within the node that it resides are healthy and the state of ports matches the port specification.

Kube-proxy-- kube-proxy is a networking proxy and a load balancer that facilitates communication between the node and the APIserver and enables communications within the ports. Container runtime engine-- each compute node runs and manages container lifecycles using a container runtime engine. Kubernetes supports Open Container Initiative-compliant runtimes, such as Docker, CRI-O, and rkt.

Kubernetes features are countless. We will discuss a few of the key features here. The first one are the health checks. Health checks are used to check the container's readiness and liveness status.

Readiness probes are intended to let Kubernetes know if the app is ready to serve the traffic. Kubernetes will always make sure the readiness probe passes before allowing a service to send traffic to the port. How can you know if your app is still alive or dead? Liveness probes help here. If your app is dead, Kubernetes removes the old port and replaces it with a new one.

Networking-- it plays a significant role in container orchestration to isolate independent containers, connect coupled containers, and provide access to containers from the external clients. Service discovery-- it allows containers to discover other containers and establish connections to them.

Load balancing works in conjunction with container replication, scaling, and service discovery. Load balancing is a dedicated service that knows which replicas are running and provides an endpoint that is exposed to the clients. Logging-- this allows us to oversee the application behavior. One has to check logs. For example, multiple logs are generated in each port.

The rolling update allows you to update a deployed containerized application with minimal downtime using different update scenarios. The typical way to update such an application is to provide new images for its containers. Containers, in a production environment, can grow from few to many in no time. Kubernetes makes managing multiple containers an easy task.

Automatic bin packing is an algorithm that selects specific host for a specific container or a set of containers using different rules, including current loads of the host, co-location constraints, and availability constraints. Kubernetes intelligently positions containers based on required resources and other constraints without compromising the availability.

Container replication ensures that a specific number of equivalent containers' replicas are running at any time. If there are too many containers, the surplus will be stopped. And if there are too few, new containers will be started. Container autoscaling automatically changes the number of running containers based on CPU utilization or other application-provided metrics.

Volume management is used to control persistent storage for containers. According to best practices, containers should be stateless and the files in the containers should be ephemeral so that even when a container crashes and gets restarted, the changes to the files will not be lost.

And lastly, resource usage monitoring-- resources such as CPU and RAM must be monitored within the Kubernetes environment. Kubernetes resource usage looks at the amount of resources that are utilized by a container or port within the Kubernetes environment. It is very important to keep an eye on the resource usage of the ports and containers as more usage translates to more cost. 


![image](https://github.com/qriz1452/oci/assets/112246222/81753af4-5387-40b5-a815-e344dba865ed)


![image](https://github.com/qriz1452/oci/assets/112246222/79650ba5-9642-47e2-8d53-4397ed2f0f25)




----------------------

: Introduction to OKE


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


![image](https://github.com/qriz1452/oci/assets/112246222/0e73d97d-66c4-47a2-8d91-11d06b53ac08)


![image](https://github.com/qriz1452/oci/assets/112246222/05e11629-7541-45fb-ba77-9c4f551033c0)


![image](https://github.com/qriz1452/oci/assets/112246222/c8963ac1-d02d-48d6-a5c0-e4ff5e7d38fd)


![image](https://github.com/qriz1452/oci/assets/112246222/004dc400-3ad4-45e8-a78b-f5e6a07c93e5)


![image](https://github.com/qriz1452/oci/assets/112246222/30c16529-4867-4827-afea-61ba74913699)


![image](https://github.com/qriz1452/oci/assets/112246222/44563818-4b6b-44c3-96a0-ef0eb2766366)




-------------
Prerequisite to create an OKE Cluster



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


![image](https://github.com/qriz1452/oci/assets/112246222/6b2ff96a-ba56-45f6-bd35-afe50e56fc0b)

![image](https://github.com/qriz1452/oci/assets/112246222/a7c1b72c-7d03-4ce1-b043-c62ba22421f4)

![image](https://github.com/qriz1452/oci/assets/112246222/fd7f1846-23ac-4670-9833-c07ee4e3e098)


![image](https://github.com/qriz1452/oci/assets/112246222/ccdba590-9ac8-4b0c-83f1-eb471a8d875c)


![image](https://github.com/qriz1452/oci/assets/112246222/dea8b14f-25ea-4d77-a219-4e745180f0a7)

![image](https://github.com/qriz1452/oci/assets/112246222/fe6cb4de-f4a3-4439-b796-2068585faa91)

![image](https://github.com/qriz1452/oci/assets/112246222/a24ca5e6-7deb-4918-a051-fb82e28ac084)


![image](https://github.com/qriz1452/oci/assets/112246222/da18d9d8-a456-44d5-86a2-2dacca4d4387)


--------------------------


 Creating OKE Cluster on OCI


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

![image](https://github.com/qriz1452/oci/assets/112246222/a2871d7a-28e1-4e16-9242-05282214afa5)




------------------



 Setting Up Cluster Access

 





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



![image](https://github.com/qriz1452/oci/assets/112246222/effa254e-f43e-495f-a983-bb0ef0ebaaf1)

![image](https://github.com/qriz1452/oci/assets/112246222/e83dcbbd-c7ef-44a1-bd76-9400d6c142d4)

![image](https://github.com/qriz1452/oci/assets/112246222/82bb959d-6eca-4578-9ab8-876adde62dc7)


![image](https://github.com/qriz1452/oci/assets/112246222/4a4fa3f2-54ea-40ca-bc3c-fd544a9736e4)

![image](https://github.com/qriz1452/oci/assets/112246222/ea533eef-9d5c-4553-a32d-c03fa5c7f056)

![image](https://github.com/qriz1452/oci/assets/112246222/166816a7-f8b6-48e4-90b7-6f632b1bcbd9)


----------------------------

 Deploying an Application to OKE



In this lesson, we will be talking about how to deploy a Python Flask application on the Oracle Kubernetes Engine. We will see how to create an app and build a Docker image for the app. We will also see how to push the Docker image to the OCI container registry.

The application container image stored on the OCI Registry will be pulled by the container cluster and then be deployed on the Oracle Kubernetes Engine. We will also make the app available on the internet, using the load balancer. And all of this will be done using the OCI Cloud Shell.

Let's look into detail the key task that we need to perform as part of this deployment. The first thing that we need to take care of is to create a compartment. Compartment is the location where all the project resources will be managed. So we need to make sure that the users have required policy to manage all the resources within the compartment. The next step is to create a Kubernetes cluster on OCI within our compartment using the quick create option. We will then build a Python application in a Flask framework within the Cloud Shell provided by OCI.

Once we are done creating the Python application, we will create a Docker image out of it. This Docker image will be then stored in the OCI container registry. We will then use Cloud Shell to deploy the Docker application to our OKE cluster. Once the application is deployed on the cluster, we will connect to the application from the internet. 


![image](https://github.com/qriz1452/oci/assets/112246222/a3343fb7-3a28-493d-aaa0-9526b25cc8bc)

![image](https://github.com/qriz1452/oci/assets/112246222/5ab1c7b1-3a29-433f-b162-5276f30ae97d)


----------------

 Observing an OKE Cluster

 
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


![image](https://github.com/qriz1452/oci/assets/112246222/bb924e44-3d11-49ef-b35a-de247bce722d)


------------

Accessing the OKE Dashboard

The Kubernetes Dashboard is a web-based management interface that enables you to deploy and edit containerized applications. It helps you to assess the status of containerized application and troubleshoot the containerized applications.

The Kubernetes Dashboard is not deployed in the clusters by default. However, you can deploy the Kubernetes Dashboard in your clusters that you create either using the manual approach or an automated approach. Let's have a look at the steps that you need to follow in order to deploy the Kubernetes Dashboard manually.

The first thing that you have to do is you'll have to deploy the Kubernetes Dashboard to the OKE cluster by applying the kubectl command. The next step is to create the service account and cluster role binding in your cluster. After which you need to obtain an authentication token for the service account that you created. And, lastly, you should enable the kubectl proxy so that you can open the ports and access the Kubernetes Dashboard using the token that you generated in the previous step.

The URL to access the Kubernetes Dashboard when deployed manually looks somewhat like this. Remember, when you manually deploy the Kubernetes Dashboard, it is deployed in the kube-dashboard namespace and not the kube-system namespace.

Let's take a look at a few considerations before using the OKE Dashboard. You cannot run the Kubernetes Dashboard when you are managing your cluster access through Cloud Shell. The sessions created in Cloud Shell do not allow for any incoming connections, and there is no public IP address available, which makes it difficult to access the Kubernetes Dashboard from within the Cloud Shell.

We do not recommend installing the Kubernetes Dashboard on production clusters due to the lack of extensible authentication support. If you do install the Kubernetes Dashboard, we recommend that you restrict the access within the cluster instead of exposing it externally via a load balancer or an ingress controller. The Kubernetes Dashboard is a common attack vector used to gain access to the Kubernetes cluster.

To have container engine for Kubernetes automatically deploy the Kubernetes Dashboard during the cluster creation, you can create the cluster using the API and set the Is Kubernetes Dashboard Enabled attribute to true, which deploys the Kubernetes Dashboard in the kube-system namespace. Also, remember, you cannot add the dashboard as an add-on onto the existing clusters. 

![image](https://github.com/qriz1452/oci/assets/112246222/500ba944-21a1-48f7-9ce1-adef9c7a82cd)

![image](https://github.com/qriz1452/oci/assets/112246222/752ba784-e5ca-4fa3-87af-eca683c61425)




-------------


































