DevOps IAM Policies


Before you begin using the DevOps service, you must meet the certain prerequisites, which includes creating users and assigning them to groups that can manage DevOps services. Alternatively, you may also choose to add existing users to the group. The next step is to create dynamic groups for DevOps resources, like code repositories and build and deployment pipelines, as they will be interacting with other OCI services. For instance, the deployment pipeline will need appropriate access to manage target environments like compute instance group, OKE, or functions.

The last step is to grant users permission to access the various DevOps resources. You must create IAM policies or user groups as well as dynamic groups. The policy statement must reflect who has what kind of access to various DevOps resources. Also make a note that, by default, users in the Administrators group have access to all the DevOps resources. For more information about IAM policies, you can review the OCI foundation course and also follow the official Oracle documentations.

These are the policy options for all the DevOps resources. The Permissions listed here, like inspect, read, create, update, delete, cancel, move, are the atomic units of authorization, which are pretty much self-explanatory. They control a user's ability to perform operations on resources. The purpose of Verbs is to simplify the process of granting multiple related permissions that cover a broad set of access or a particular operational scenario. So as you go from inspect to read, use, and manage, the level of access generally increases, and the permissions granted are cumulative.

Resource Type here specifies which resources under the DevOps project can be controlled. Make a note to assign the permission to all the DevOps resources, use the devops-family aggregate type. You can create groups, dynamic groups, and policies using the OCI Console, and use either the Policy Builder or a manual editor to create policies.

This is the syntax for creating DevOps policies based on standard IAM policy syntax. First you create dynamic groups, then you provide them the needed permissions. Although you can create a single dynamic group for all the resources types listed here, as you can see from the examples, we have created dynamic groups for devopsrepository, devopsbuildpipeline, and devopsdeploypipeline. You can group them together, but my advice here will be to have separate dynamic groups for each resource type, as it gives you more granular control in terms of managing access to the resources in the compartment or tenancy.

Later, once the dynamic groups are created, you have to provide policies or write policies to allow those dynamic groups to manage those resources that you wish to in a particular compartment.

Let's take a look at a couple of examples for creating DevOps policies based on standard IAM policy syntax, which is essentially to allow a user or a pipeline to perform an action on a resource type in a given location. Dynamic groups have been created named CoderepoDynamicGroup and BuildDynamicGroup. They are each being given permissions to manage items in a compartment. Note that the CoderepoDynamicGroup is allowed to manage all the resources of DevOps family in the compartment.


![image](https://github.com/qriz1452/oci/assets/112246222/570d4edc-67ca-4bd8-b292-2d4cce6c335d)



-------------------

: DevOps Projects and Code Repositories



The first step in building and deploying applications using OCI DevOps service is to create a DevOps project. A DevOps project is a logical grouping of DevOps resources needed to implement a CI/CD workflow. As part of creating the project, you create private repositories, code repositories to store and manage source code. You'll also create OCI artifacts and container registries to house artifacts to be used in deployments.

Then you're going to create environments. These acts as a reference to the OCI Compute resources to which artifacts are deployed. It could be a function application, a group of compute instances, or a container engine for Kubernetes cluster.

Next, you'll have to create build pipelines where you can define a set of stages for the build process like building, testing, and compiling software artifacts and delivering these artifacts to OCI repositories and optionally triggering a deployment.

Next, create a deployment pipeline where you can define sequence of steps for deploying a set of artifacts to the target environments. In order to manage users and pipelines access to DevOps resources, you'll create IAM dynamic groups and policies, something we covered in our previous lesson.

You will have to set up a notification topic and subscription that will publish important messages about the project events. Project notifications keep you apprised of important events and the latest DevOp project status. They also alert you if you need to take any necessary action such as approving a workflow.

You must enable logging as DevOps services use the OCR logging service to record the output it generates during the pipeline runs. This means that the build logs are available for use in other OCI tools. Remember, creating a DevOps project does not have to be done in one particular order. But resources like repositories, registries, and environments must be created before the build and the deployment pipelines can be created.

Let's take a look at the benefits of using DevOps project. DevOps projects lets you keep track of all your software delivery lifecycle resources in one place and share them easily. It enables faster software delivery as using DevOps project reduces the change driven errors and decreases the time customers spend on building and deploying releases manually.

It helps you enhance security and reduce risk in delivery. Automation mainly reduces the chance of human errors that might introduce a security vulnerability. Security bugs can be resolved quickly by rolling outer fix in time.

DevOps project provides the feature to enable logging, monitoring, and notification for all your DevOps resources. DevOps logs emit all the DevOps project resources logs, which can be used for troubleshooting and optimally managing OCI resources. You can create a DevOps project in the OCI Console, or by using an API or command line interface.

Let's understand the code repositories in detailed. Code repositories a centralized code creation version control and management systems. They archive previous stages of code and related documentation. Code repository branches are localized copies of code that developers can check out to work on without impacting other developers. This allows for multiple users to edit code simultaneously and check their changes before merging them into the main code branch.

Code repositories have strong version control and collaboration capabilities that are critical for DevOps because DevOps workflows include frequent and small code changes. Within the DevOps project, you can create your own private code repositories in the OCI code repository, which is like git to grant users permission to access your code repositories and other resources, you must create an IAM policies.

Now, once you have an OCI code repository, you can clone it using HTTPS or SSH to create a local copy, add or remove files, commit changes, and work on different branches using Git operations. Remember, an OCID is assigned to the repository upon creation. And make a note that you pay only for the storage and no additional charges are to be paid for the repository. You can also edit, clone, and delete repositories or mirror an external code repositories such as GitHub, GitLab, Bitbucket Cloud, Visual Builder Studio, Bitbucket Server, and GitLab Server.

Now, remember before creating the external connection in order to mirror an existing code repository, you must store the tokens or credentials in OCI Vault for authentication purposes. So in order to mirror third party repositories, which are hosted on GitHub Enterprise Cloud, GitLab SAS, GitLab Servers, and Visual Builder Studio, you will have to retrieve a personal access token, also known as PAT, from those providers and store your personal access token securely in an OCI Vault.

In case you want to mirror a Bitbucket Cloud, then you need your Bitbucket username and create an app password, which should be then stored in an OCI Vault. And for Bitbucket Server, you'll have to create an STDP access token and then store the access token in an OCI Vault.

After you define an external connection, changes to your existing Git repo are automatically replicated in the OCI code repository. Code repositories are mirrored every 15 minutes by default, but this can be customized. Mirroring your external code in the OCI code repository speeds up the build process as the code is retrieved from an internal location rather than from a server, which is further away.

![image](https://github.com/qriz1452/oci/assets/112246222/59c3d031-79b2-4ba5-b59e-749162810a0b)

![image](https://github.com/qriz1452/oci/assets/112246222/8925d638-598c-419e-931b-ddc03e806ae7)

![image](https://github.com/qriz1452/oci/assets/112246222/95ebdf15-f8b6-43cc-94ad-eae43acf5b7d)


------------------

Artifacts and Registeries 


An artifact is a reference to any binary, package, manifest, image, or other files that make up your application, which is deployed on target environments. They are used to specify software package versions for deployment and must be defined with parameters like name, type, and location before a build is run.

OCI has two types of registries for storing, sharing, and managing artifacts-- Container Registry, also called Oracle Cloud Infrastructure Registry, or OCIR, is an open standard-based Oracle-managed service that stores multiple versions of Docker or other container images plus related files like Helm charts. These images can be pushed to a Kubernetes cluster for deployment using OKE.

Container Registry was covered in greater detail in the previous module, so let's discuss the other type of registry that is the Artifact Registry. Artifact Registry is a placeholder for a software package, library, .zip file, or other types of files used for deploying applications. These files are fetched and used when the deployment pipeline is triggered. So let's look at the Artifact Registry in more detail.

This slide will cover the concept of Artifact Registry, which will help you manage your artifacts. The first point is the repository and artifact names. When you create a repository to group similar artifacts, you give it a repository name. If you leave the name blank, the system automatically generates a name that you can change later. When you upload an artifact to a repository, you specify your path and version for it. Based on your input, an artifact name is assigned that combines these two elements, as you can see in the example over here. Note that slashes do not create a directory structure, but you can use them to organize the repository.

Versioning-- because of incremental updates to artifacts, you can assign versions to artifacts. This way, you can associate builds with artifacts version and roll back to previous versions when required.

Immutability-- when you create a repository, you can designate it as immutable, which means that the artifacts uploaded to it becomes immutable. These artifacts are used as is and cannot be replaced. Immutable repositories ensure the integrity of the artifacts it manages. This means that rollbacks will always use the exact file from the last working version of the deployment and ensure that a developer's code change does not affect code created by others. Note that if you delete an immutable artifact, you cannot assign its name to another artifact.

Service limits-- in each region that is enabled for your tenancy, you can create up to 500 repositories in Artifact Registry, consuming a maximum of 500 GB in total. You are charged for the stored artifacts only. You can also integrate external Artifact Registries with your OCI DevOps.

You can create references to these four types of artifacts in OCI DevOps. All but the container image can either point to an Artifact Registry or can be defined inline. Let's try to understand each one in detail.

Container image repository-- it's a collection of related container images, which is used to manage different versions of an application. Deployment configuration is a YAML file that defines the artifacts for deployment and their locations to fetch them from. Kubernetes manifest-- it's a specification of a Kubernetes API object that describes the desired state of an object that Kubernetes will maintain when you apply the manifest. General artifacts-- general artifacts include file types like binaries, ZIP files, or other files. 


![image](https://github.com/qriz1452/oci/assets/112246222/d027c3f5-9364-4465-af64-79bfb5fb44cd)

![image](https://github.com/qriz1452/oci/assets/112246222/3daee8d4-6e25-4222-a640-31cc2438a305)

![image](https://github.com/qriz1452/oci/assets/112246222/5f1c44f3-30ea-4c09-80fb-d240fb7b20a6)


---------------

: Environments



An environment is a collection of your computing resources where artifacts are deployed. You can also consider them as a target platform for your applications. Different target runtime environments supported in OCI include group of compute instances running Oracle Linux and CentOS, Oracle Container Engine for Kubernetes, and function applications.

Before you create references to a target environment, you must first create a target environment if it doesn't already exist in the OCI console. Environment can be created in different OCI region than the region of the deployment pipeline. This allows developers to extend their deployment to multiple OCI regions. Which environment you choose for deployment depends on your needs based on flexibility, security, speed, and several other factors. This graph here helps us examine trade-offs between control, security, and cost with that of flexibility, portability, and speed for the choice of target environments that are available.

Let's take a closer look at each environment. Bare metal is the least versatile, most costly option, but it provides the most control and security. It's a good option for projects that require a more constant, larger, or separate and secure space.

With virtual machines, different operating systems can run on a single machine, and VMs can be commissioned and decommissioned more easily than bare metal. This allows for more versatility, scaling and resource sharing. Shared applications and physical hardware provide cost savings, disaster recovery, speed, and faster provisioning. Each VM still requires its own operating system. This can be a benefit, as you can run multiple applications requiring different operating systems on a single piece of infrastructure. But it uses more resources and spins up in minutes, not seconds.

Kubernetes clusters runs group of application containers that are portable, lightweight, isolated, and standardized. They contain everything needed to run an application, so you don't need to rely on what is on the host, which speeds up the coding process. They also share OS, bug fixes, patches, and often binaries and libraries, so they spin up more quickly and require fewer IT resources to deploy and manage than VMs, making it ideal for high-density environments and for small and medium deployments, where you need to do more with fewer resources.

Functions. Functions make computing power or backend services available on demand. You only need to select the required managed services. The serverless provider manages the underlying servers, so the user can focus on writing and deploying code. Functions also deploy in milliseconds, not seconds, so the application can go live as soon as the code is uploaded. Functions are best with dynamic workloads whose usage is changed frequently because you're paying for services only as you use them. 


![image](https://github.com/qriz1452/oci/assets/112246222/bb8bc48a-7815-48ed-b44b-1f08bf27884d)



![image](https://github.com/qriz1452/oci/assets/112246222/d26290fd-2d0e-424d-a653-d8fdfa8b8feb)


![image](https://github.com/qriz1452/oci/assets/112246222/34382d3f-2357-4a87-9f7f-3212712ec80b)

![image](https://github.com/qriz1452/oci/assets/112246222/ddd34e01-c642-4266-b897-8ab603a226b0)



------------------





