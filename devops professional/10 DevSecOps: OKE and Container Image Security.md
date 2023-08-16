 Security for OKE: Overview

 A Kubernetes Cluster is a group of nodes which can be physical or virtual machines. The node's capacity, its number of CPUs and amount of memory is defined when the node is created, but their shape can be scaled later on as needed.

A cluster is comprised of control plane nodes, Oracle will typically manage three of these for high availability, as well as worker nodes that you organize into one or more node pools. And just like other Oracle Cloud Infrastructure services, OKE itself is an OCI Service and can be managed and administered using the OCI Console, CLI, or REST API.

The Kubernetes Cluster control plane implements core Kubernetes functionality running a number of core Kubernetes processes to include the kube-apiserver to support API operations requested from the Kubernetes command line tool, commonly referred to as kubectl, as well as other command line tools.

The kube-apiserver also includes admissions controllers required for advanced Kubernetes operations. And of course, any access to expose services deployed to worker nodes is provided by those workload-specific interfaces.


---------------------


A Kubernetes Cluster is a group of nodes which can be physical or virtual machines. The node's capacity, its number of CPUs and amount of memory is defined when the node is created, but their shape can be scaled later on as needed.

A cluster is comprised of control plane nodes, Oracle will typically manage three of these for high availability, as well as worker nodes that you organize into one or more node pools. And just like other Oracle Cloud Infrastructure services, OKE itself is an OCI Service and can be managed and administered using the OCI Console, CLI, or REST API.

The Kubernetes Cluster control plane implements core Kubernetes functionality running a number of core Kubernetes processes to include the kube-apiserver to support API operations requested from the Kubernetes command line tool, commonly referred to as kubectl, as well as other command line tools.

The kube-apiserver also includes admissions controllers required for advanced Kubernetes operations. And of course, any access to expose services deployed to worker nodes is provided by those workload-specific interfaces.

And so in the next seven videos, I'll be discussing best practices and recommendations with regard to OKE Security starting with controlling access to your provisioned OKE clusters by leveraging both OCI Identity and Access Management policies, as well as Kubernetes role-based access control rules.

Encrypting sensitive data objects such as authentication tokens and credentials as Kubernetes Secrets when they are stored in etcd. Using Pod Security Policies and OKE to limit or restrict access to resources, leveraging node pool security for OKE clusters and pods, defining the network access rules for communications to and from pods, multi-tenancy usage models for Kubernetes Clusters and how they provide for isolation, and finally, enhancing container image security using signature verification and vulnerability scanning.


-------

 Security for OKE: IAM Policies and RBAC


 For most operations on Kubernetes clusters created and managed by OKE, OCI Identity and Access Management provides access control, a user's permissions to access clusters comes from the groups to which they belong, and of course, the permissions for the group is defined by policy statements. For example, IAM provides control over whether a user can even create or delete clusters, whether someone can add, remove, or modify node pools, as well as which Kubernetes object operations a user can perform on a cluster, such as viewing resources or creating pods or deployments.

So for example, in a development environment to allow access to all operations, it's easy to get started with a policy such as this. However, for production environments, you'll want to consider more specific and limited access based on the security best practice of least privilege by allowing only certain permissions based on the actual responsibilities of the user.

Kubernetes contains an integrated Role-Based Access Control, or RBAC component. So in addition to IAM, the Kubernetes RBAC Authorizer can enforce additional fine-grained access control for users on clusters via Kubernetes RBAC roles and cluster roles mapped by role bindings and cluster role bindings.

A Kubernetes role is similar to an IAM policy in that it indicates a collection of permissions. These permissions combine verbs such as get, create, and delete with resources, such as pods, services, and nodes. For example, a Role might include both read and list permissions for pods, however, it would be scoped to a specific namespace.

A Cluster Role is just like a role, but it can be used anywhere in the cluster and not limited to namespaces. A Role Binding maps a role to a user or group, granting permissions for resources in that namespace.

Similarly, a Cluster Role Binding maps the cluster role to users, granting permissions across the entire cluster. OCI, IAM, and the Kubernetes RBAC Authorizer work together to enable users who have been successfully authorized by at least one of them to complete the required Kubernetes operations.

When a user attempts to perform an operation on a cluster, IAM first determines whether the group to which they belong has the appropriate and sufficient permissions. If the intended operation also requires additional permissions granted via a Kubernetes role or cluster role, the Kubernetes RBAC Authorizer kicks in.

There are a set of preconfigured roles which offer reasonable default separation of responsibility depending on what actions a client might want to perform, and you can learn more about these in the Kubernetes documentation. However, it's important to understand how updates on one object may cause actions in other places.

For example, a user may not be explicitly allowed to create pods directly, but allowing them to create a deployment, which creates pods on their behalf, will actually let them create those pods indirectly. Another example, deleting a node from the API will result in the pod scheduled to that node being terminated and recreated on other nodes.

So while the pre-configured roles represent a balance between flexibility and the common use cases, more limited roles are recommended to prevent accidental privilege escalation. Fortunately, you can define additional RBAC roles specific to your organizational needs.

Bottom line, you should always follow the principle of least privilege to ensure users and Kubernetes service accounts have the minimal set of privileges required. To learn more, you'll want to review the Oracle documentation with regard to the Identity and Access Management policies that impact OKE management, as well as the Kubernetes documentation for leveraging RBAC roles. 


![image](https://github.com/qriz1452/oci/assets/112246222/d1ce831c-872e-4942-bb1e-931a857830ed)


-----

 Security for OKE: Kubernetes Secrets


The Kubernetes Cluster Control plane stores sensitive configuration data, such as authentication token, certificates, and credentials as Kubernetes secret objects in etcd. Etcd is actually an open source distributed key value store that Kubernetes uses for cluster coordination and state management.

Within an OKE cluster, etcd writes and reads data to and from block storage volumes in the OCI block volumes service. By default, Oracle encrypts data in block volumes at REST, including etcd and Kubernetes Secrets, using a master encryption key.

However, for additional control over the lifecycle of the master encryption key, you can choose to manage the key yourself. You do this by specifying which key to use as well as control over when the key is rotated. This master encryption key is stored in the OCI Vault Service.

So how does this work when protecting data such as Kubernetes Secrets? First, the Kubernetes API server generates a new data encryption key, or DEK, using the AES-CBC encryption algorithm with PKCS#7 padding and a new DEK is generated for each encryption use case. It then encrypts the data with the data encryption key.

Next, after retrieving your master encryption key from the OCI Vault, it encrypts the DEK with the master key, a concept known as envelope encryption. Then finally, it stores the encrypted DEK together with the encrypted data inside etcd. This way, data is encrypted by a unique DEK, which is itself encrypted by the master key.

And even though etcd has both encrypted data and the data encryption key, the master key is never exposed outside of the OCI Vault. So even if both the API server and etcd were somehow compromised at the same time, your secrets are still secret.

Before you can create a cluster for which you want to manage the master encryption key yourself, you have to first create a suitable password encryption key in the Vault or obtain the name and OCID of such a key, if it already is available to you.

Then create a dynamic group in OCI Identity and Access Management that includes all clusters in the compartment in which you are going to create the new cluster. Then create a policy authorizing the dynamic group to use the master encryption key.

You then create the cluster using the Custom Create workflow and open the Advanced Options to specify that instead of using an Oracle-managed key, you want to manage the master encryption key yourself, then indicate the Vault and the key you wish to use for the cluster. Afterwards, you can optionally restrict the use of the master encryption key by modifying the dynamic group to include just that cluster, if you wish.

Keep in mind that you can only select this option to manage the master encryption key yourself when using the Custom Create workflow since the Quick Create workflow wizard does not provide this option. 

![image](https://github.com/qriz1452/oci/assets/112246222/9919f76b-1d03-49e5-b2e4-af544830784c)

--------

Security for OKE: Cluster Security


You can control the operations that pods are allowed to perform on a cluster you've created with OKE by setting up Pod Security Policies for the cluster, which are a way to ensure that pods meet security related conditions before they can be accepted by the cluster.

For example, you can use Pod Security Policies to limit the storage choices available to pods, such as the volume types that pod containers can use or setting up the requirements for using a determined read-only root file system. Restrict the host networking in ports that pods can access or prevent pods from running as the root user, as well as the ability to use a privilege escalation.

Having defined a Pod Security Policy for a cluster, you have to authorize the requesting user or target Pod Service Account to use the policy. You do this by creating an RBAC role or cluster role to access the Pod Security Policy and then creating a role binding between the role and the requesting user or target Pod Service Account.

You can then specify whether a cluster enforces the Pod Security Policies defined for it by enabling the cluster's Pod Security Policy Admission Controller. By design, each call made to a Kubernetes API goes through a sequential process of authentication and authorization. It means that regardless if it's a human user or a service account, both checks will always occur.

On the other hand, Admission Controllers are optional but strongly recommended plug-ins that are compiled into the kube-apiserver binary with the objective to broaden security options. Admission Controllers intercept requests after they passed the authentication and authorization checks and then executes its code just before the object's persistence.

You can also use Pod Security Policies to provide default values for pods, which is known as mutating the pod. While the outcome of either authentication or authorization check is a Boolean, like allow or deny the request, Admission Controllers are more diverse. Some Admission Controllers validate requests, some mutate requests, and some can do both.

When supported, Admission Controllers first mutate and then validate the request, if the request fails, either the mutating phase or the validating phase, the entire request is denied. Once enabled, the Pod Security Policy Admission Controller validates all requests related to creating or updating pods. In that regard, the Pod Security Policy Admission Controller uses the policies previously created by the cluster administrator.

In other words, since Pod Security Policies are applied at a cluster level, once they are active, only pods that comply with the established Pod Security Policies, or PSP, will be created or updated. Now before using this, be aware that users and service accounts will not be allowed to create or update pods until they comply with all Pod Security Policy Admission Controller validations.

So then, how do you set this up in OKE? First, we need to define the Pod Security Policy by saving it in a file. For example, this policy, taken from the Kubernetes documentation, simply prevents the creation of privileged pods. Then we use the kubectl command to create the policy.

Next, to create an RBAC role to access the policy, we first need to define the role and save it to a file. In this example, we create a cluster role. Then once again, we use the kubectl command to create the role. Next, we create the role binding to authorize the application pods to use a security policy by once again defining and saving the role binding in a file then executing the Create command once again.

Finally, having defined a Pod Security Policy and authorized application pods to use it, we enable the clusters Pod Security Policy Admission Controller to enforce the Pod Security Policy. We do this by navigating to the OKE cluster in the OCI Console, you'll notice that by default, the Pod Security Policies are not enforced. Now we click here to edit then simply select the button to now enforce those policies.

Notice here the Warning that if no policies are defined, the Admission Controller will prevent any pods from being created in the cluster. Incidentally, while I showed you how this is done in the OCI Console, we can also enable the PSP Admission Controller using the OCI Command Line Interface or REST API in a script, if desired. 


------


 Security for OKE: Node Pool Security

Node pools in a cluster can span compartments. However, while using multiple compartments provides a convenient way to group and manage work nodes, it does not provide any isolation between the worker nodes in the cluster. Any workload can be scheduled across any node pool regardless of the compartment.

However, a valid use case for using more than one compartment for node pools would be to more easily create certain dynamic groups and identity and access management policies for worker nodes. But to be clear, an invalid use case would be putting each node pool running a customer workload in a separate compartment under the false assumption that the compartments are providing some sort of a security boundary or isolation.

We recommend only using private subnets for all instances in your node pools. A service gateway should be configured to provide access to Oracle Cloud Infrastructure services. Remember that a service gateway cannot be used if the subnets are public with an internet gateway. So then if your applications running in the private subnet require access to the internet, you should add a NAT or network address translation gateway to facilitate that outbound access.

By default, a pod may be scheduled on any node in the cluster. Kubernetes offers a rich set of policies for controlling the placement of pods onto nodes. For many clusters, the use of these policies to separate workloads can be a convention that authors adopt or enforce via tooling.

However, these placement controls are not adequate in a multi-tenant environment when users with deployment capabilities are untrusted. If you have untrusted users deploying code, then you should consider creating a separate cluster for that group of users. We'll explore this actually a little bit more in a later video.

Next, you can choose to limit access given to instance principles. By default, all pods on a node are able to access the instance principle certificates using the instance metadata endpoint. In order to avoid privilege escalation by way of instance principles, you should isolate workloads across node pools with different dynamic groups so that pods in a given node pool have the minimal set of privileges required to function.

For example, assume you have two workloads both which require different access. A log archive or application requires access to manage buckets and objects and object storage. And this host monitor application requires access to the compute API to manage instances. Well, the simplest approach would be to schedule them in the same node pool and provide the instance principal with all the required access. However, this increases the impact in the event one of the workloads becomes compromised. So a better approach would be to schedule the workloads on separate node pools with the limited set of access the instance principles require for the applicable workload.

And, finally, the preferred way to block container access to an instance's metadata is using a network policy plug-in with the default policy of deny-all. You would then explicitly grant access to pods and networks using network policy resources and Kubernetes via label selectors. We'll talk about this in another video later on.

However, if you don't have a network policy plug-in installed, you can use an iptables rule to restrict access from all pods on the host, as shown in this example. But for this reason, we recommend that you do not use this approach to block only a subset of pods on a host. To learn more about node instance security options and limiting pod access, we recommend that you visit the Oracle Help Center for OKE to include the online documentation and reference architectures. 


-----
 
 Security for OKE: Network Security



OKE offers various options to secure communication to and from the workloads in your cluster.

For the best network security posture, you should consider using a combination of security lists to secure host-level network communication as well as network policies to secure pod-level network communication. Let's look at each of these in turn.

Network administrators can define security list rules on node pool subnets to restrict access to and from worker nodes. Defining security list rules allows you to enforce network restrictions that cannot be overridden on the hosts in your cluster.

Now because all pod-to-pod communication occurs in a VXLAN overlay network on the worker nodes, you can't use security list rules to restrict pod-to-pod communications. However you can use security list rules to restrict access to and from your worker nodes.

Please keep in mind that there is a minimum set of security list rules that must exist on node pool subnets to ensure that the cluster can function. So prior to making any changes to your security list rules, you should consult our OKE documentation, which provides information on the minimum set of security list rules required.

In addition, as shown here in this example, you should consider restricting your cluster resources to only private networks, so none are directly accessible from the internet. If you need to expose a workload, such as a web application to external clients, the best practice is to provision an OCI API gateway on a public subnet within the VCN then create a deployment that can access the private cluster load balancer.

For other external access requirements, you can add an OCI bastion host to provide connectivity to a node instance via SAH or also consider adding a public OCI load balancer for other applications that need external HTTP or TCP/IP access.

Network policies in Kubernetes allow administrators to define how groups of pods are able to communicate with other pods in the cluster. Additionally, policies allow you to define how groups of pods are able to communicate with services outside the cluster, for example, Oracle Cloud Infrastructure services.

To restrict access using network policies, you need to install a network plugin. The most commonly used are CNI-type plugins that follow the container network interface specification. Once configured, network plugins enforce the network policies you've defined for the cluster.

To be clear, in a Kubernetes cluster, by default, all pods are non-isolated, which means that all ingress and egress traffic is allowed. However once a network policy is applied and has a matching selector, the pod becomes completely isolated, which means it will reject all traffic that is not explicitly permitted by one or more policies. The order of policies is not important since an aggregate of all policies is applied.

To use network policies, you have to install and configure a network provider that supports network policy resources. You'll then normally create one or more cluster namespaces to separate pod deployments. Then finally, you'll create Kubernetes network policy resources to isolate pods as required.

There are numerous network plugin options, and you can use any of them. However, we have provided an example in our online documentation for installing and using Calico. Calico is an open source networking and network security solution for containers, virtual machines, and native host-based workloads. Incidentally, only open source Calico is supported since Oracle does not support Calico enterprise.

So now to manually install Calico in your OKE cluster from your OCI instance client machine or if you're using OCI Cloud Shell, follow the normal steps to set up the clusters kubeconfig configuration file. Remember that you must set up your own kubeconfig file and not use one from another user.

Now using a curl command, you'll download the Calico policy-only manifest for the Kubernetes API data store. The URL differs according to the version of Calico that you want to install. Just refer to their documentation for instructions.

The Calico YAML file includes multiple references to the pod CIDR block values. So in the downloaded YAML file, you'll need to replace the default value with the actual pod CIDR block values of the cluster when you created it with OKE, such as in this example.

The Calico YAML file defines a deployment named calico-typha which has a replica count of one by default. So you will likely need to change the replica count for large clusters or production environments. In fact, Calico recommends that it has at least one replica for every 200 nodes, but at a minimum, three replicas in production environments to reduce the impact of rolling upgrades and failures.

You'll then install and configure Calico by executing the Apply kubectl command on the YAML file. And having installed Calico on your OKE cluster, you can now create Kubernetes network policy resources to define the isolation of pods as required. The Calico documentation provides several network policy examples and tutorials on how to use them. 





 


![image](https://github.com/qriz1452/oci/assets/112246222/a54f7c1d-a1b7-4ad9-b9d1-8b514408bed3)
![image](https://github.com/qriz1452/oci/assets/112246222/c87fc24d-ab4b-40d7-bcec-d028e1b37794)
![image](https://github.com/qriz1452/oci/assets/112246222/b9fd9dca-c616-4769-9766-9003d893c78e)



------

Security for OKE: Multi-Tenant Considerations


The secure sharing of Kubernetes control plane and worker node resources allows for maximizing productivity and saving costs in both cases. Essentially, there are two common usage models for Kubernetes that can make it easier to operationalize tenancy related use cases, namespaces-as-a-service and clusters-as-a-service. Let's explore both of these a bit further.

With the namespaces-as-a-service model, tenants share a cluster and tenant application workloads are restricted to one or more nain spaces assigned to that tenant. The cluster control plane resources, such as API server and scheduler, and worker node resources, such as CPU memory and storage, are available for use across all tenants. Now, to isolate tenant workloads, each namespace must also contain RBAC rolle permissions and role bindings for controlling access to the namespace itself, network policies to prevent network traffic across tenants, and resource quotas that are used to limit usage and ensure fairness across tenants.

In OKE, we could implement by leveraging OCI quotas or budgets at the compartment level and then, of course, define Kubernetes resource quotas as well. With this model, tenants share cluster-wide resources, such as cluster roles and custom resource definitions. As well as a result, you cannot create or update these cluster-wide resources yourself.

Let's learn more a little bit more about namespaces, shall we? When a cluster is first provisioned, Kubernetes has three initial namespaces-- default, which is used for pod deployments when a namespace is not specified; kube-system, used for objects created by the Kubernetes system itself; and kube-public, which is mainly there for cluster-wide usage, as it's visible and readable to every user in the cluster.

So in a namespaces-as-a-service usage model, the administrator creates additional namespaces and then restricts them using RBAC roles and role bindings to a specific group of users. And now it serves as their virtual cluster. So why do you need to use namespaces in a word isolation?

Isolation has many advantages, including that it supports secure and clean environments. A Kubernetes namespace allows us to partition our cluster into separate subdivisions. In this usage model, you have different teams or projects sharing the same cluster. If everyone were to deploy their application in the same default namespace, it could end up being chaotic. You would, therefore, create a namespace for the different teams, projects, or project stages. For instance, you could have a namespace for different development teams and another one for testing.

Pods and services in the different namespaces are invisible to each other, which means there won't be any conflict, as users can continue to safely deploy their applications in their own virtual cluster. Most folks will leverage namespaces for security and governance purposes, including reducing the privileges of users with limitations. So you can limit almost everything, from which roles can access a namespace to their quota levels for cluster resources. For example, you can use resource quotas and RBAC configurations to confirm that a namespace is accessible only by the appropriate service accounts. Namespaces can also be helpful for budgeting purposes if you have a hard budget on how much you can use in your OCI tenancy.

With the clusters-as-a-service usage model, each tenant gets their own cluster. Now, this model allows teams of users to have different versions of cluster-wide resources, such as custom resource definitions. And it provides full isolation of the Kubernetes control plane. Essentially, a workload cluster is assigned to a tenant. And they have full control over all cluster resources.

Now, note that in some enterprises, a central platform team may be responsible for managing required add-on services, such as security and monitoring, and for providing cluster lifecycle management services, such as patching and upgrades. A tenant administrator may also be restricted from modifying the centrally-managed services and other critical cluster information. For example, you might not allow for them to actually create and delete their own clusters themselves.

So which usage model should you use? Bottom line, when using OKE, it is recommended that you do not deploy and run mutually distrusted workloads in the same cluster. In other words in most situations, especially in production, you should employ a clusters-as-a-service usage model.

For example, you should not provision just one OKE cluster to run application workloads for both development and production. Additionally, you should consider having separate clusters if you have multiple tenants, teams, or users accessing the same cluster with differing levels of trust. While both Kubernetes and the OKE service itself offer methods to isolate workloads-- we've talked about those in this lesson-- currently these methods are still not sufficient for what we would consider for hard, secure multi-tenancy.

However, for use cases where hard multi-tenancy is not needed, especially in development environments, then the namespaces-as-a-service usage model will allow for more optimal utilization of OCI resources. In this model, you'll run multiple Kubernetes workloads, pods, and services that will share the cluster-wide resources. Keep in mind you'll still need to ensure proper isolation of pods for governance and security, as we have discussed in other videos in this lesson.

Another consideration is that you can always choose to employ a hybrid of these two usage models, creating separate clusters deployed on separate node pool instances for certain tenants, and then also using additional namespaces to provide more granular isolation for their separate teams. And that wraps up this video on multi-tenant considerations for clusters in OKE. For more details on the specifics of configuration and implementation, be sure to consult both the Kubernetes documentation as well as our Help Center resources for OKE. 



---------


 Security for OKE: Image Security

For compliance and security reasons, system administrators often want to deploy software into production system only when they are satisfied that the software comes from a trusted source and the software has not been modified since it was published, thus compromising its integrity.

Container image signature verification ensures the authenticity and integrity of container images and ensures that the image used at runtime is the same image that was published and hasn't been tampered with. So it helps prevent potential man-in-the-middle attacks. Container images are signed in the OCI Registry using an asymmetric master encryption key from the OCI Vault, then the signatures are viewed and verified ensuring that the integrity of the image isn't compromised.

To further enhance security, you can configure clusters you've created with OKE to only allow the deployment of images from the OCI Registry that have been signed by a specific master encryption key. To make this happen, administrators define policies that will require image signature verification.

This is done by first adding policies to allow the cluster to access the OCI Vault as well as the images in the Registry. You then enable signature verification at the OKE Cluster level, under Resources, we click Image Verification, then click Enable, then select the Vault and the master encryption key used to sign the images.

This signature verification policy will permit the use of images for deployed pods signed with only this master encryption key, although the policy can be updated to add additional keys if needed. Developers easily sign the container images as part of their build process. After they push the image to the registry, they execute this OCI command to sign the image once they've obtained the image ID.

OKE then enforces these policies by validating that the image is appropriately signed prior to being used in a pod deployment. From now on, the cluster will only allow the pooling of images from the registry that have been signed using the master encryption keys included in the image verification policy.

Now while we're discussing images, an additional consideration and best practice, because image tags are mutable, we recommend that you only pull your Container Docker images using the image digests and not pull images using tags. Image digests are the SHA-256 digests of your image, which allows Docker to verify the image it downloaded is what you expected. As a reminder, of course, you can always retrieve the actual image digest IDs by executing the Docker images command when needed.

To further assist your security policy for images to be used in OKE Cluster deployments, you can also leverage the OCI Registry to enable scanning of container image repositories and to view scan results. When repository scanning is enabled, the OCI vulnerability scanning service scans the images pushed into the repository for security vulnerabilities published in the Common Vulnerabilities and Exposures, or CVE database.

In addition, these images are automatically rescanned when new vulnerabilities are added to the list of threats. So to access the scanning information, just navigate to the image in the repository, then in the scan results, you can see a list of potential vulnerabilities identified with the vulnerability description, risk level, and a link to the CVE database. 

![image](https://github.com/qriz1452/oci/assets/112246222/6c8c5966-b1b2-4ba2-a215-9dc0d901d302)


--------

 

























 




















