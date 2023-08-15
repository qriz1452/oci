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


