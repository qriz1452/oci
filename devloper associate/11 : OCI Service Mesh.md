Now Playing : OCI Service Mesh Overview


Let's try to understand using a scenario. Tricia is happy that they moved away from the traditional monolith application development approach to microservices-based application development. However, she is facing another set of problems in ensuring secure communication and faster connectivity among them, as well as challenges in end-to-end visibility of those microservices.

In an effort to address these issues, she discusses her concerns with Mo at OCI. Let's hear what she has to say and what Mo has to offer. Tricia is concerned about the security, monitoring, and connection of microservices in her bookstore application. She wonders if OCI DevOps has an automatic way to address these issues. Mo assures her that they do and asks for more detail about her requirements.

Tricia informs Mo that the bookstore application is built using microservices, built with different technologies. Tricia explains that each microservice has a separate business logic and that the communication between the microservices inside the Kubernetes cluster is insecure since it sends simple plain text. Tricia highlights that developers needs to write additional security logic for authentication and authorization of service to service communication, making the overall code very complex.

Tricia also points out that additional communication logic is needed for ports inside the cluster to communicate faster, which further complicates the code. Tricia adds that monitoring agents and monitoring logic must be implemented to observe the logs and performance of microservices.

Mo recognizes that Tricia is spending too much time ensuring the security, traffic management, and end-to-end visibility of a microservices-based application. Tricia agrees and points out that it leads to a degradation in developer's productivity. Mo has a solution for Tricia's problem, which is OCI Service Mesh. Tricia is intrigued and wants to know more about what Service Mesh is and how it works.

So let's jump in and start exploring the concept of Service Mesh together. OCI Service Mesh is a free Oracle managed service that allows for communication among all microservices within a cloud native application. It encrypts all communications between microservices to provide an additional layer of security.

With OCI Service Mesh, security, observability, and network traffic management can be achieved without changing the application logic. This means that developers can focus on writing code for business logic rather than worrying about adding security and observability features. OCI Service Mesh collects telemetry, metrics, and logs to provide end-to-end visibility of the microservices within the application.

For example, let's say you have a microservice that handles payment processing for your e-commerce website. OCI Service Mesh, you can ensure that this microservice can communicate securely with other microservices such as the Order Management microservice without needing to add additional authentication or authorization logic in your code.

Additionally, you can monitor the performance of these microservices, including metrics, such as response time and error rate to identify and address any issues that may arise. Without Service Mesh, developers are required to spend more time and effort on developing the security, connectivity, and monitoring logic. With Service Mesh, you can automatically add features to your cloud native microservice application, which includes managing security, controlling traffic, and adding observability features without changing your application's source code.

Service Mesh is implemented as a sidecar proxy that runs alongside each microservice in your application. The sidecar proxies intercept all traffic going in and out of the microservices and add additional features, such as encryption, traffic routing, and monitoring.

When two microservices need to communicate with each other, the sidecar proxies handle the communication instead of the microservices themselves. By offloading the responsibility of security, traffic management, and monitoring to OCI Service Mesh, developers can focus on building the core business logic of their microservices. This leads to increased developer productivity and faster time to market for the application.

![image](https://github.com/qriz1452/oci/assets/112246222/441b46e0-2d5c-4520-a741-82f0850507db)



------------------

Now Playing : Features and Benefits of OCI Service Mesh




The first feature that we'll be covering is security. Service Mesh ensures secure communication by encrypting all traffic between microservices and authenticating them before allowing communication. Service Mesh allows for declarative access policies, which means that access to microservices can be controlled without changing the underlying application logic. The next feature we'll talk about is observability.

Service Mesh provides detailed telemetry data on each microservice, allowing for easy tracking of the overall health of the application. Service Mesh also provides centralized access logging, making it easy to monitor and troubleshoot any issues that arise. And next, we have connectivity.

Service Mesh allows for traffic routing rules to be set up, which enables network traffic management between microservices. It also provides ingress traffic management using routing rules, making it easier to manage incoming traffic to the application.

Let's talk about some of the benefits of OCI Service Mesh. Talking about zero trust security. OCI Service Mesh uses strong encryption and mutual authentication to ensure that all communication between microservices is secure. Policies can be used to control which microservice are allowed to communicate with each other, ensuring that only authorized traffic is allowed.

Microservices access control. By decoupling network and security configuration from the microservices themselves, OCI Service Mesh allows developers to focus on building and deploying microservices without worrying about how they will securely communicate with each other.

End-to-end visibility. OCI Service Mesh automatically captures telemetry data for all traffic between microservices, allowing developers to monitor the health and performance of their application in real time. This telemetry data can be used to identify performance issues or failures, allowing for quick remediation and improving the overall reliability of the application. Additionally, the captured telemetry data can be used to gain insights into how the application is being used and where improvements can be made.

Lastly, dynamic traffic control. The centralized traffic control provided by OCI Service Mesh allows for dynamic load balancing and traffic management across microservices. By abstracting communication between microservices and applying different load balancing policies to traffic-- specific subsets of microservice instance, developers can optimize traffic flow and reduce latency. This helps to ensure that the resources are being used efficiently, and the application is performing at its best.

Now let's understand what organizations can benefit from OCI Service Mesh. OCI Service Mesh is specifically designed for organizations that are building applications using microservices architecture. If you are building cloud native apps, where they are packaged as containers and run on Kubernetes, OCI Service Mesh can help you manage the communication between microservices in a secure and efficient way.

If you are using multiple languages or frameworks to build your microservices, OCI Service Mesh provides a consistent way to manage the communication between them. Whether you're using HTTP, TCP, or gRPC for service communication, OCI Service Mesh can help you manage the traffic and ensure that your microservices are communicating with each other in a secure and efficient way.


![image](https://github.com/qriz1452/oci/assets/112246222/1179438f-355f-4fbb-a0d2-c45dd1ca57ae)

![image](https://github.com/qriz1452/oci/assets/112246222/923b585f-9ca3-4a12-bfd8-5d3e1eb7b260)

--------

Now Playing : Service Mesh Architecture and Concepts

In this lesson, we will explore the service mesh architecture and how microservices communicate within it. We will also learn how to configure cloud-native applications using Service Mesh resources. Let's start with a quick rundown of the service mesh components.

The picture on the screen displays a high-level diagram of Service Mesh with two services enclosed in a mesh. The architecture diagram shows how user traffic travels through ingress gateway to the connected proxy server. A proxy is a network proxy that is deployed alongside each service instance in a cluster.

The proxy intercepts incoming and outgoing network traffic for the service and can apply various functions to the traffic, such as load balancing, traffic shaping, encryption, and protocol conversion. The main benefit of using proxies in a service mesh is that they enable fine-grained control over how traffic flows between services. Popular proxies used in service meshes include Envoy, Linkerd, and STO, all of which offer a rich set of features for managing traffic within a service mesh.

The service mesh uses access policies to allow ingress/egress gateway traffic and microservices communication within the service mesh. This allows for secure communication between services and ensures that only authorized traffic is allowed to the service mesh. Service Mesh takes care of security, traffic management, and observability by offloading these responsibilities from application developers. The service mesh improves developer productivity and allows them to focus on building and improving their applications.

The data plane of the Kubernetes Service Mesh is made up of proxies, which the control plane controls. This ensures that the proxies are functioning correctly and that traffic is being handled efficiently and securely. Now that we have covered the high-level overview of the service mesh architecture, let's dive deeper into the different components of the service mesh and how they work together to provide these benefits.

To better understand the service mesh architecture, we will be using an example of a cloud-native application called Bookstore. Let's take a look at the Bookstore application components along with the service mesh resources, as shown on the screen. The Bookstore application is composed of four microservices developed using different programming languages. The first microservice we'll look at is the Product Page service, which is responsible for displaying the main UI service information of a book.

This microservice is implemented using Python. Moving on, we have the Details service, which provides details about each book. This microservice is implemented using Ruby. Next, we have Reviews service, which provides reviews associated with a particular book. This microservice is implemented using Java and calls the Rating service.

The Review service has multiple versions with different behaviors for each version. Version 1 does not call the Rating service, while version 2 and version 3 do. In addition, version 2 displays each rating as one to five black stars while version 3 displays each rating as one to five red stars.

And you can see the arrows from version 2 and version 3 pointing to the ratings. The Ratings service provides the rating data for a review and it's implemented using Node. Now that we have looked at the Bookstore application components, let's dive into the service mesh resources that are used to manage and control microservices communication.

At the top level, we have Mesh resource, which is the core component of the service mesh. It provides the global view of all microservices and their interactions within the mesh. Next, we have Virtual Service, which is used to define routing rules and policies for a group of microservices. It might contain virtual deployments, virtual service route tables, and virtual deployment bindings.

Ingress Gateway is another Service Mesh resource that is used to configure the external entry point to the service mesh. It might contain ingress gateway route tables and ingress gateway deployment. Finally, we have Access Policies, which is used to configure which service can communicate with which other microservice. It's an important security feature of the service mesh. Now let's take a look at sample deployment code associated with each of these Service Mesh resources.

Service Mesh. The Mesh resource is the top-level container resource that represents the logical boundary of application traffic between the services that reside within it. With the Mesh resource, you can manage the traffic coming into the mesh, define services available in the mesh, and manage the traffic between the services you define. Now let's take a look at some snippets of code to implement the Mesh resource.

Within the deployment code, the Kubernetes object is specified as Mesh. The service mesh namespace is specified. In our case, it's bookinfo. And remember, for the Bookstore application, the namespace bookinfo remains common throughout all the deployment code for various OCI Service Mesh resources. In the spec section, you have to specify the OCID of compartment where Service Mesh resides.

We also need to specify the OCID of Certificate Authority for the service mesh. You need to specify the type of security traffic you want to accept. In this case, it is permissive, which accepts both raw and TLS traffic. The traffic mode can be set to DISABLED, PERMISSIVE, or STRICT depending on your specific needs. Moving forward, we will review the Ingress Gateway resource.

In this slide, we will take a closer look at the ingress gateway in a service mesh deployment. The ingress gateway sits at the edge of the service mesh and is responsible for managing ingress, TCP, or HTTP traffic into the mesh. It allows resources outside the mesh to communicate with resources inside the mesh. The ingress gateway defines a set of rules for how external traffic communicates with the mesh.

It determines whether encryption is required on all incoming and outgoing traffic. The ingress gateway supports mTLS, that is Mutual TLS, which provides encryption and authentication for inbound connections. The encrypted connection can be configured with OCI Certificate service to automatically manage certificates, making certificate management a seamless process.

Additionally, the ingress gateway allows TLS passthrough connections. This means that the virtual service can handle TLS on its own, rather than relying on the ingress gateway to handle the encryption. This provides more flexibility in how you manage your TLS connections within the service mesh. Now let's try to decode the deployment code for ingress gateway.

The kind field specifies the type of object being defined, which in this case is ingress gateway. The apiVersion specifies the version of OCI Service Mesh API being used to define the object, which is servicemesh.oci.oracle.com/v1beta1. The metadata section provides metadata about the object being defined, including its name and namespace. So in this case, the name for the ingress gateway resource is bookinfo-ingress-gateway. And the namespace is bookinfo.

Next, we have the spec section, which specifies the configuration details for the ingress gateway. Here we need to specify the compartment ID where the ingress gateway will be created. The mesh section specifies the service mesh that this ingress gateway will be part of. Here you need to provide the reference. And this field specifies the name of the service mesh that this ingress gateway will be part of, which is bookinfo.

Next is host section. This specifies the host that this ingress gateway will handle traffic for. Under the host section, you can specify the name for the host. You can also specify host names for the host, which can include port number if needed. Next is the listeners field, which specifies the listener configuration for the host.

This includes port, protocol, and TLS configuration for the listener. The TLS mode in this example is currently set to DISABLED. Next, we have accessLogging. This field specifies the configuration for access logging. isEnabled, this field specifies whether the access logging is enabled for the ingress gateway object. And, in this case, it is set to true.

Moving on, let's discuss the ingress gateway route table. In the world of service mesh deployments, the ingress gateway is a critical component responsible for handling incoming traffic from the external sources. In order to ensure that this traffic is properly routed to the appropriate virtual services within the mesh, ingress gateway route tables are used. These route tables define the rules that govern which virtual services are accessible from the ingress gateway deployment and can be customized to include one or more tables per gateway.

These tables are then used to direct incoming requests to their appropriate destination within the mesh. When using the HTTP protocol, additional routing options are available, including support for gRPC headers, path rewriting, and host name rewriting. All of these features work together to ensure that traffic is properly directed to its intended destination. Let's break down the different parts of this code and what they do.

Like always, the apiVersion field specifies the API version of ingress gateway route table resource being created. Kind field specifies the type of resource being created. In this case, it is IngressGatewayRouteTable. The metadata section provides metadata about the resource, including its name and the namespace it belongs to. In our case, it's bookinfo. And the name for the ingress gateway route table is bookinfo-ingress-gateway-route-table.

The specs section defines the specification of the ingress gateway route table, where we have the compartment ID, which specifies where the ingress gateway route table will be created. The ingressGateway section identifies the ingress gateway to which this ingress gateway route table will be associated. In this case, the reference field specifies the name of the ingress gateway, which is bookinfo-ingress-gateway. And the routeRules section specifies the routing rules for the ingress gateway route table.

If you observe closely, we have the httpRoute. This field specifies the HTTP traffic will be routed. And we have the destination, which specifies the destination virtual service for this route rule. In this case, the reference field specifies the name of the virtual service, which is the productpage. Also, we have the ingressGatewayHost. This is the field that specifies the ingress gateway hostname for this route rule, which in our case is bookinfoHost.

Phew, that was a long lesson. Let's take a break here and pick up where we left off in the next one. Remember to give yourself time to process what you've learned. See you in the next one.

![image](https://github.com/qriz1452/oci/assets/112246222/08cf6e5b-c063-4793-9fae-7918850bbf21)
![image](https://github.com/qriz1452/oci/assets/112246222/ffe43275-8ece-49a3-9125-ef6a1c979e34)
![image](https://github.com/qriz1452/oci/assets/112246222/9cd454b0-28d0-496f-9b14-b26d1e702c2d)
![image](https://github.com/qriz1452/oci/assets/112246222/1e73e2b8-024c-4255-9a35-2b3808e2409a)


---------

Now Playing : OCI Service Mesh Resources ? Virtual Service
In the world of microservices, a virtual service represents a customer-managed microservice in the mesh. It acts as a proxy for the actual service and allows for easy configuration and management within the Service Mesh. Each virtual service has its own configuration for the service hostname, TLS certificates, and CA bundles. This enables secure communication between services while maintaining control over the certificate and CA chains.

One of the key benefits of using virtual services is the ability to support multiple versions of application through virtual deployments. This means that different versions of the same service can co-exist in the mesh, which allows for easy testing and rollout of new features.

Now, let's break down the different components of this manifest for virtual service. The kind field specifies that the Kubernetes resource being created is virtual service. The metadata section specifies the metadata for virtual service, which includes the name and the namespace it belongs to. The spec section specifies the mesh reference for the virtual service, which in this case is the named bookinfo.

The default routing policy section specifies the default routing policy for the virtual service, which in this case is uniform, which means that the traffic will be evenly distributed across all the endpoints associated with the virtual service. The compartment ID field specifies the compartment ID for the virtual service. And we have the host section that specifies host associated with the virtual service.

In this example, there are two hosts. One is the reviews:9080, and the other one is just the reviews. These are the endpoints that the virtual service will route traffic to. The first host specifies the endpoint with port number 9080, while the second host does not specify a port number and will use the default port for the service.

Moving on to virtual deployments. A virtual deployment represents a specific version of a virtual service within the mesh. It maps to a group of ports running a specific version of the actual microservice managed by the customer. Each virtual deployment has its own configuration for network protocol, logging, service discovery type, and hostname. This allows for customized configuration of each version of the service based on specific requirements and use cases.

Virtual deployments enable easy management and scaling of microservices by allowing the customers to control the deployment of new versions of their service while also managing control over configuration details. By deploying multiple versions of a service through virtual deployments, customers can ensure seamless transition to new versions while minimizing disruption to end users.

Let's break down the different sections of this manifest. Like always, kind specifies the Kubernetes resource being created, which in this case is virtual deployment. Then we have the API version, and we have the metadata section that specifies the metadata for the virtual deployment, including the name and the namespace it belongs to.

The name is reviews-v1, and the namespace is Bookinfo. Then we have the spec section, which specifies the virtual service that the virtual deployment belongs to. In this case, the virtual deployment reviews-v1 is associated to the virtual service named reviews. You need to specify the compartment ID where the virtual deployment resides.

Next, we have the listener section that specifies the listener configuration for the virtual deployment. The listener listens on port 9080 and uses the protocol HTTP. Then we have the excess logging field, which specifies the access logging configuration for the virtual deployments. It is enabled, meaning that the access logs will be recorded.

And lastly, we have the service discovery field. This section specifies the service discovery configuration for the virtual deployments. In this case, the type is set to DNS, and the host name is set to reviews-v1. Similarly, these are the codes for reviews-v2 and reviews-V3. So as you can see, the only thing that has changed is the name and the host name.

Moving on, let's talk about virtual service route table. A virtual service route table allows you to set a list of routing rules that sends traffic to specific versions of deployment. For instance, you can write an A/B testing rule to route traffic based on percentages across different service versions. The route rules also allow developers to split traffic based on protocol and path. This can be incredibly useful for optimizing the performance and efficiency of your services.

As you can see on the screen, we have an example of a routing rule that sends 60% of traffic to version, which is reviews-v1, 20% of the traffic to reviews-V2, and 20% of the traffic to reviews-v3. This can be a very effective way to distribute traffic and ensure that your services are performing optimally. Now, depending on your use case, you may want to adjust the traffic distribution in your routing rules to achieve the desired outcomes.

Let's go through each part of the manifest for the virtual service route table. The API version specifies the version of OCI Service Mesh API to use, which in this case is servicemesh.oci.oracle.com/v1beta1. Kind specifies the type of Kubernetes custom resource, which is virtual service route table.

The metadata section contains metadata of VV SRT resource such as the name. Here, in this case, it's reviews-route-table, and the namespace to which this resource belongs, which of course, is bookinfo, which is common throughout all the codes. The spec section contains the specification of the VSRT resource, including compartment ID. Here, you have to specify the OCI of the compartment where the virtual service route table will reside.

The virtual service section specifies the virtual service that this VSRT is associated with. In this case, as you can see, the references towards previous virtual service, and you also have to specify the route rules. The route rules are an area of routing rules to apply for the virtual service. And in this example, there is only one HTTP routing rule specified.

The HTTP route specifies that the routing rule is for HTTP traffic, and the destination is an array of destinations to route the traffic to. In this example, there are three destinations specified, each with their respective weight that is 60, 20, and 20 for reviews-v1, v2, and v3 deployments. The rate determines the percentage of traffic that should be routed to the destination. And the virtual deployment here specifies the reference to the virtual deployment that the traffic should be routed to.

Here's gRPC, specifies whether the routing rule is for gRPC traffic, which in this case is set to false. Next, we have the path and the path type field. The path that the traffic should match for this routing rule should be specified in the path. In this case, the path is / whereas the path type specifies the type of the path. And in this example, it is prefix, which means that the traffic that starts with a / will match this path.

------

Now Playing : OCI Service Mesh Resources ? Virtual Service Deployment Binding

Now, when a virtual deployment is created in OCI Service Mesh, it needs to be associated with the ports in the Application Cluster that it represents. This is done through virtual deployment binding, which creates a relationship between the virtual deployments and the ports. Once this relationship is established, the proxy server is automatically injected as a sidecar container into the port. This enables the proxy software to handle traffic to and from the ports.

Furthermore, the virtual deployment binding allows for automatic version upgrades of the proxy software. This is achieved through the use of a ConfigMap, which contains the proxy software image and its associated configuration. When the new version of the proxy software is available, it can be easily upgraded by updating the ConfigMap. Now, let's take a look at the manifest.

This manifest describes a virtual deployment binding resource named reviews-v1-binding. That binds our virtual deployment name. We use -v1 in the Bookinfo namespace. This binding enables the virtual deployment to handle traffic to and from the service. As you can see, the kind field specifies the type of Kubernetes resource which is virtual deployment binding.

We have the metadata section, which specifies the name and the namespace. So the name for the resources, reviews-v1-binding, and the namespace where it's being deployed is Bookinfo. The specs section provides a specification for the virtual deployment binding. The virtual deployment field specifies the reference to the virtual deployment that it is associated with.

So the name is specified as reviews-v1 and the namespace where it is deployed. Similarly, we have the target which specifies the target that the virtual deployment is bound to. In this case, it is referencing to a service called reviews-v1, deployed in the namespace Bookinfo.

Moving on, let's talk about the OCI Service Mesh resource called Ingress Gateway Deployment. Ingress Gateway Deployment is a resource that is used to deploy the proxy software of an Application Cluster. It offloads the management of the deployment and ports backing the ingress gateway to OCI operator for Kubernetes. It's worth noting that Ingress Gateway Deployment is only required for Kubernetes-based workloads.

The Ingress Gateway Deployment is local to the cluster and is not replicated back to the Service Mesh control plane. This means that it only exists within the context of the cluster and is not visible or accessible outside of it. Here is an explanation of the manifest. The API version specifies the version of Kubernetes API that this manifest is using. And we have already discussed this in the previous slides.

Again, the kind section specifies the kind of Kubernetes object being created. This is Ingress Gateway Deployment. Then we have the metadata section where we specify the name and the namespace where this will be deployed. Next, in the spec section, we have the Ingress Gateway field, which specifies the reference to the Ingress Gateway resource that this deployment is associated with.

As you can see, under the reference field, we have specified a name called Bookinfo Ingress Gateway. The deployment section specifies the desired state of the deployment, and the autoscaling will specify the desired autoscaling behavior or the deployment. minPods specifies the minimum number of pods to maintain for the deployment, and maxPods specifies the maximum number of pods to maintain for the deployment.

Next, we have the port section that specifies ports that the ingress gateway will use, which includes protocol, the protocol used for the port that is DCP in this case, we have the port number-- specifies the port number for the ingress gateway, which in this case is 9080, and then we have the service port field that specifies the port number for the associated Kubernetes service. Lastly, we have the service section that specifies the type of Kubernetes service that will be created for this ingress gateway, and the type specifies the type of service. Here in this case, it is load balancer.

Moving on, let's talk about the access policy. In a Service Mesh, virtual services communicate with each other to provide application functionality, and access policy is a configuration resource that defines the access rules for virtual services in a mesh. These policies allow administrators to control how services communicate with each other. By default, all requests are denial if no access policy exists. This means that no communication is allowed between virtual services.

Access policies enable administrators to selectively allow or deny communication between services in a Service Mesh. | policies in OCI Service Mesh work on three categories of traffic. The first one is internal mesh traffic. This refers to the traffic flowing between virtual services within a mesh. Access policies can be used to control which virtual services are allowed to communicate with each other within the mesh.

The next one is the ingress traffic. Ingress traffic refers to requests that are received by a virtual service from clients outside the mesh. Access policies can be used to control which clients are allowed to send requests to a particular virtual service within the mesh. And third one is the egress traffic. Egress traffic refers to the request that are made by a virtual service to services or application outside the mesh.

Access policies can be used to control which external services or applications a particular virtual service is allowed to communicate with outside the mesh. By using access policies to control these categories of traffic, administrators can ensure that only authorized communication is allowed between virtual services and external clients or services. This provides more secure and reliable environment for running applications on OCI Service Mesh.

This code defines an access policy resource with the kind Access Policy. We also have the API version listed over here. Under the metadata section, we have specified the name for our resource which is Bookinfo-policy, and we have specified the namespace where it should be created. Now, the mesh section specifies the service mesh instance that this access policy applies to. And in this case, it is referencing to the service mesh called Bookinfo.

The compartment ID section specifies the compartment where the access policy will be created. The Rules section defines the access rules for this access policy. In this example, there are two rules defined. The first rule allows ingress traffic to product page virtual service, from the Bookinfo ingress gateway, ingress gateway service.

As you can see, the action says allow, and the source is ingress gateway referencing the name of the ingress gateway, which is Bookinfo-ingress-gateway. And the destination is the virtual service, and the reference to the virtual services product page. As you can see from the table here, the source can be ingress gateway. The destination can be a virtual service. In this case, it's bookinfo ingress gateway talking to product page virtual service.

The second rule allows traffic between product page virtual service and reviews virtual service. As you can see from the table, you can also allow traffic to move between two virtual services. In this case, it is from product page to the reviews virtual service. Now, each rule has an action field that says Allow or Deny and specifies the source and the destination. It can be defined using various criteria such as virtual service names, their IP addresses, and more. Now, once this access policy resource is created, it will be enforced by the OCI Service Mesh instance specified under the mesh section, which is the bookinfo mesh service.

To wrap up, in this and the previous lesson, we have gained knowledge about the Service Mesh architecture and its virtual resources, including ingress gateways, ingress gateway roundtables, virtual services, virtual service route tables, virtual servers deployments, virtual servers deployment bindings, ingress gateway deployments, access policies, and all their configuration details.



---------
Now Playing : Developing Cloud Native Applications using OCI Service Mesh


Let's start with Service Mesh policies. So there are two types of policies in regards to Service Mesh. The first one is Service Mesh access policies. These policies determine which services within the Service Mesh are allowed to communicate with each other, and in which direction. For instance, we might ask ourselves, which virtual services have permission to communicate with virtual service A, or which virtual services are allowed to communicate with virtual service B?

Next, we have the IAM policies for OCI Service Mesh. IAM policies play a critical role in controlling access to various OCI resources, including Service Mesh resource, that determine which groups and users can access which resources and the type of access they are granted. For instance, we might ask ourselves, who has permission to create a Service Mesh, or who can manage virtual deployments in a specific compartment?

To understand Service Mesh's IAM policies better, let's take a closer look at the associated permission. This will give us a better understanding of the level of access we can grant to different users and groups. So as you can see, we have eight different types of individual resource types under OCI Service Mesh. And we also have an aggregate resource type with the name service-mesh-family. So you can choose to assign fine-grained policies using individual resource types or you can use the aggregate resource type, which is the service-mesh-family.

This and the subsequent slides will list the permissions covered by each of the individual resource types included in this service-mesh-family resource type. The level of access is cumulative as you go from inspect to read to use to manage. Now, as you can see, the current resource type is service-meshes, where you have the permission, such as list, read, attach, and create. And remember, for all the permissions, there is a prefix where you have to specify service_mesh, underscore, the name of the permission.

Moving on, to manage virtual services using IAM policy, you can use different permissions, such as list, read, update, attach, detach, or create, delete, and move. Again, these are all cumulative. So for inspect, you have the permission list. For read, you have read permission. For use, you have all-- list, read, update, attach, detach. And for manage, you have from list up till move. And remember, all the permissions has prefix mesh_virtual_service, underscore, the name of the permission.

Moving on, to manage virtual service route tables, you can manage permissions, such as list, read, create, delete, update, and move. And remember, the permission, again, has a prefix, which is mesh_virtual_service_route_table. Then to manage virtual deployments, you have permissions such as list, read, update, create, delete, and move. Again, the prefix changes as per the resource tab that you're trying to manage, which in this case is mesh_virtual_deployment, underscore, the name of the permission.

Moving on, to manage ingress gateways, you have the permissions such as list, read, update, attach, delete, create, delete, and move. And again, the permission has prefix mesh_ingress_gateway.

To manage access policies, you have permissions such as list, read, create, delete, update, and move. Also, make a note that no extra means that there is no incremental access. For example, the "use" verb over here has no extra permissions other than the ones that are listed, which are cumulatively acquired through "inspect" and "read" verbs. Also, note that the permission has a prefix mesh_access_policy, underscore, the name of the permission that you wish to alert.

And finally, you can also control the work request, where you can list and read the work request. There are no extra permissions allotted to "use" and "manage" verbs. Also, note these permissions has a prefix mesh_work_request, the name of the permission, either list or read.

Let's take a look at some of the policy examples to let user group work with Service Mesh. From the example, we can see that there are different user groups. One is for the virtual service users. The other is for the ingress gateway managers. And the third one is for the virtual deployment readers.

Now, the virtual service users are allowed to use virtual services within a given compartment. Similarly, for ingress gateway managers, we are giving them manage permission to manage the ingress gateway route tables. And for the virtual deployment readers, we are allowing them only read permission on the virtual deployments within a given compartment.

So this is an example of fine-grained access policy. If you want to write fewer policies, you can use the aggregate resource type. For example, if you have a MeshAdmins user group, you can give them the manage permission on the service-mesh-family resource in the compartment that you wish to.

And lastly, let's see an example that allows virtual service managers group to perform administrative operations against Mesh virtual services, including creating, deleting, and updating virtual service route tables in sales-app compartment. So as you can see from the permission, we are allowing the group VirtualServiceManagers to use service-meshes in the sales-app compartment. We are allowing them to manage virtual services in the same compartment. And we are also allowing them to manage the virtual service route tables in the sales-app compartment. So with the help of these three policies, we are allowing this particular scenario.

Before we can start using the Service Mesh within our BookStore application, we need to create two dynamic group rules. Our cluster runs three critical processes-- the Mesh Kubernetes operator, Mesh proxies, and logging agent, which require permission to access required resources for proper functioning. To accomplish this, we will define a dynamic group that includes instance principles from the worker nodes in our cluster. This dynamic group ensures that our Service Mesh processes have the necessary permission to function correctly.

So the dynamic group rule is given on the screen. Now, as you may know, the Service Mesh natively uses the certificates service to manage certificate. However, to use the certificates service effectively, it needs permissions to access the key and vault services within our compartment. To enable the necessary permissions, we will define another dynamic group specifically for the certificates service. This group will allow us to manage our certificates effectively within our tenancy.

You can use the following aggregate policies to set up developer environment for the BookStore application with Service Mesh. As you can see, the group that your user will be part of should be allowed to manage all resources in the compartment. As you can see, the dynamic group that we created for the instance should be allowed to manage all resources in the compartment. And the dynamic group that we created for the certificate should be allowed to manage all resources in the same compartment.

Deploying and configuring an application for Service Mesh can be a complex process. Developers are required to deploy the cloud-native application to a Kubernetes cluster on the data plane and configure Service Mesh resources on the control plane. So let's take a look at the steps involved in this process.

The first step is to set up the application deployment environment. This is required to configure the application deployment environment, including any dependencies that the application may require.

The second step is to set up a Kubernetes cluster on OCI using the OKE service. This cluster is necessary to deploy the cloud-native application on pods.

The third step is to set up all the required services for Service Mesh. OCI Service Mesh requires OCI Vault, master encryption key, and certificate authority to maintain encrypted service-to-service communication.

The fourth step is to deploy and configure the application for Service Mesh. The DevOps team is responsible for deploying the cloud-native application to the Kubernetes cluster on the data plane and configuring the Service Mesh resources on the control plane.

Finally, the last step is to test application deployed in OCI Service Mesh, ensuring that everything is functioning correctly. By following these steps, you can deploy and configure your application to run on the OCI Service Mesh with ease.



-------------





































