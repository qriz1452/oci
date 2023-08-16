![image](https://github.com/qriz1452/oci/assets/112246222/8e2aba02-f0b1-4060-8802-45e2f3ed0187)![image](https://github.com/qriz1452/oci/assets/112246222/ee121229-2f6b-4acb-9fee-338f85531501)![image](https://github.com/qriz1452/oci/assets/112246222/b2f38e49-88a1-4fef-aa89-ade3d402fc75)![image](https://github.com/qriz1452/oci/assets/112246222/972abe08-273f-4a64-a44e-497c95f5f545)![image](https://github.com/qriz1452/oci/assets/112246222/715584a5-f3f6-4aa1-afbf-cdef0ea4252e) Introduction to Kubernetes


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


![image](https://github.com/qriz1452/oci/assets/112246222/bf90afe2-f2f6-4ae5-b274-3a331e4e76de)


![image](https://github.com/qriz1452/oci/assets/112246222/8799178d-f953-4bb9-9434-9f8aa363a00a)

------------------------

 Overview of Kubernetes Architecture and it's main components



Talking about the Kubernetes architecture, the Kubernetes cluster has two main components. One is the control plane, which you can see on the left side of the image on the screen. And one is the data plane, which you can see on the right-hand side of the image on the screen.

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




![image](https://github.com/qriz1452/oci/assets/112246222/739c2187-780f-4bb3-b11a-66a4aaa4a806)

![image](https://github.com/qriz1452/oci/assets/112246222/78a5bc0f-f94c-40d8-8805-86f453a54adb)


![image](https://github.com/qriz1452/oci/assets/112246222/bb68bd3f-cd06-4e90-9d2e-be41e23f39e9)


![image](https://github.com/qriz1452/oci/assets/112246222/b5f69181-a76a-4248-9271-7ab4fce7d1e4)



![image](https://github.com/qriz1452/oci/assets/112246222/5d990efa-a398-44ae-882a-4a64128ffd4c)

![image](https://github.com/qriz1452/oci/assets/112246222/5ea0f8e3-98ad-4bf7-b56c-881be1ed0948)

![Screenshot 2023-08-16 103035](https://github.com/qriz1452/oci/assets/112246222/8c1b0b16-4231-4ce4-a1f2-7c143238872b)


















 

