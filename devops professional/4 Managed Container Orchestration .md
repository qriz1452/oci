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






