Introduction to CICD


A CI/CD pipeline, or continuous integration and continuous deployment, is the backbone of modern DevOps environment. It bridges the gap between development and operations teams by automating the building, testing, and deployment of applications.

Continuous integration is a modern software development practice in which incremental code changes are made frequently and reliably. Automated build and test steps triggered by CI ensure that the code changes being merged into the repository are reliable. This practice mainly encourages small modification in the code over large changes infrequently. Each change in the code activates a build that runs test to identify any broken parts of the code, as shown in the blue area on the diagram.

Continuous deployment marked on the green area, on the other hand, goes one step further, as it allows developers to deploy every piece of there code, be it new features or bug fixes, right up to the production environment, using either an automated continuous deployment or a manual continuous delivery process. Continuous feedback stages, like operate and monitor in gray region, are also a key part of the DevOps process, which helps you monitor performance, optimize infrastructure, and notify of any potential issues. These services are also covered in the later modules.

This diagram best represents the OCI DevOps workflow, right from committing the code changes until its deployment on the live servers. The heart of the workflow is the build and the deployment pipelines within the continuous integration and continuous deployment. The build pipeline follows a user-defined flow to build the code, test the package, and deliver them as a code artifacts in the OCI artifact registry, or as ready-to-ship image in the container registry. The deployment pipeline then uses the build image from the container registry and a Kubernetes manifest to deploy the most recent version of the applications to a staging environment.

After final test and approvals, the pipeline pushes the image to the desired production environment, which can be a group of computer hosts, a container engine, or a function. This is completely based on the architecture design of the software application.

You might also want to move an existing application from on-premises or another cloud service provider to OCI. OCI DevOps as a service provides the flexibility to integrate with your existing CI/CD workflows, thus offering a robust DevOps solution. 

![image](https://github.com/qriz1452/oci/assets/112246222/f95e9993-abc9-4dc8-ac57-503fe9d429c0)

![image](https://github.com/qriz1452/oci/assets/112246222/3b2b92c9-06f0-46ed-bc7c-a9487e0102cb)


-------------------

 Build Pipelines





Continuous integration is where code is committed, built, tested, and revised more regularly and reliably. Code and build specification instructions triggers tests in a streamlined automated process that creates the desired effects. A build pipeline contains the stages that define the build process for successfully compiling, testing, and running software applications before deployment. It is the heart of continuous integration workflow.

OCI DevOps build and deployment pipelines reduce the change-driven errors and decrease the time customers spend on builds and deployments. As we see in this diagram, the chain of events start from developers, who commit source code to an OCI source code repository, which triggers the build pipeline that spins a build runner to execute the build steps, which results in artifact generation delivered to specific OCI repositories based on their types. Build pipeline also has the provision to run a deployment pipeline, which facilitates deploying software artifacts to the target environments. As this lesson is dedicated to build pipelines, let's explore the same.

To trigger a build pipeline, you must already have created and configured an OCI DevOps project and its resources, a code repository, and a build spec file. You also need to enable logging capabilities, which helps log the build pipeline activity. A build pipeline is a DevOps resource which needs adequate permissions to manage or interact with other OCI services, like reading code from code repository, publishing a container image, and deliver it to Container Registry, and trigger a deployment pipeline. It can inherit these permissions from a dynamic group it belongs to. These can be specifically defined to restrict permissions to one specific build pipeline, one code repository, and one artifact.

This is the high-level flow for the build pipeline. We'll look at each step in more detail. Pipelines can be edited to add, modify, or delete stages. You can manually run or automatically trigger a pipeline. We should monitor the progress of the pipeline to ensure its successful completion or debug during failures.

To build code, we generally need a set of instructions that tells us what and how to build. Similarly, while creating a build pipeline we first want to create the build spec file, which is a YAML file the build specification in this file contains build steps and settings that the build pipeline uses to run a build also includes a definition of the artifacts you want to deliver a build pipeline can have multiple stages to it. You always start with the Managed Build stage and then extend the pipeline using any of these optional stages to deliver artifacts, trigger deployment pipeline, or introduce wait.

Let's look at this process in more detail. The build spec file is a configuration file written in YAML and contains build steps and settings used to run a build. By default, the build specification is in the root of your primary build's source directory and is used when you run a build pipeline. If it's not there, you must provide the relative part to the file when adding the Managed Build stage. The build server will interpret this file and go through the steps that are defined in it.

The build specification is organized into four sections-- configuration of the build runner. This is the basic information needed by the build system. The build spec version, how long the entire build process should take before it's been stopped, the user running the build, and what shell should be used when executing the commands.

Setup of environment variables-- this is where the standard vault and the exported variables are configured. Steps define how build must progress within a given stage. Every step is defined using a name, a timeout limit, and command to be executed within that step. Command specified in the step runs in the same OS instance, but not in the same shell instance.

Output artifacts-- they tell the build pipeline what is the result of the build out and automatically extracts and saves the items specified for use in the later pipeline stages. Environment variables are defined in the build specification file. They can be standard variables, which act like any regular variables, which can be used in the latest apps within the particular build stage.

Vault variables are used to manage your vault secrets. These also persist across steps, but they cannot be exported outside the build spec to prevent leakage of confidential information. The exported variables are parsed out of the build process through the following stages. Only variable names here are exported. So if you want a standard variable to be exported to a subsequent build stage, you need to specify it here.

Several environment variables, such as the build run ID, or the trigger's hostname, are predefined on the build server itself. You can also create parameters that are set when the pipeline is run using the given syntax. It starts with the dollar symbol and the variable name within the curly braces.

Build specification file specifies both input and output artifacts. Input artifacts can be defined in the build specification and supplement the code repositories that drive the build. There are two types of artifacts that can be defined here. One is the artifact from any of the previous build stages, and other is the artifact from any external downloadable public URL.

The build specification file ends with the definition of the output artifacts. These artifacts are referenced in the pipeline stage for automated deployment to the target environments. They are used to specify software package versions for the deployment. DevOps artifacts can be container image, a generic artifact, or they can be defined inline. The artifact source varies depending upon the type of artifact.

OCI DevOps accepts four types of artifact references. The first is the container image you build. The next two are the YAML files, the deployment configuration file, which defines the artifacts for the instance group only, and the Kubernetes manifest, which specifies the desired state of an object that Kubernetes will maintain when you apply it.

The last type is other general artifacts. Each output artifact is given a name that later steps can refer to, a type like binary or Docker image, and the reference to a file or a container image in the local registry. The build spec should have the unique ID for the container that the build is going to create.

For a target environment like instance group, a deployment configuration file defines the commands and run steps to download an application package artifact from the specified artifact registry and place it in the target compute instance file system. The file can be defined inline or provided as a generic artifact reference during instance group deployment. DevOps admins can use the deployment configuration file to specify application packages and locations where they must be stored in the target compute instance. It can also be used to specify the steps required to deploy an application, also used to specify user-defined or building environment variables required for the deployment.

The continuous integration feature of DevOps project provides four different stages to create a build Pipeline Managed Build builds and tests your software with OCI DevOps-managed build runner. Only this stage is mandatory, and it must be the first stage of your build pipeline. Deliver Artifacts stage publishes your created software packages to OCI artifact repositories. Trigger Deployment stage starts a deployment pipeline with the results from your build. And the Wait stage allows for a specified amount of time before proceeding to the next stage. It can be used at any point in the pipeline. Let's take a look at each of these build stages in more detail.

The Managed Build stage builds and tests your software with the fast and scalable OCI DevOps service called managed build runner. The job of the build runner is to follow the instructions provided in the build_spec.yaml file, which includes request to export variables, install prerequisites, compile and package code, and build container images. You can also run several tests in this stage. Each build pipeline must have at least one Managed Build stage to start with.

The Deliver Artifacts stage maps the build output from the Managed Build stage with the version and delivers the artifacts to the OCI Container Registry and the Artifact Registry. The artifacts can be either OCI container images or generic universal file types. Make a note-- this stage can't be the first one in a build pipeline, as you first need to create artifacts using Manged Build stage before you can deliver them to a repository.

The Trigger Deployment stage automatically triggers a deployment pipeline from the build pipeline. Before you add this stage, a deployment pipeline associated with your DevOps project must exist. Recall that the OCI DevOps supports deployment to different target environments like OKE, instance group, and functions.

The Wait stage can be added when the system needs to wait a specified amount of time before moving to the next stage. It can't be added as the first stage to a build pipeline, and the pipeline must have at least one Managed Build stage first. The duration is given in seconds, for example, 300 seconds. During this duration, the build process is paused.

Running a build pipeline can be done manually by clicking the Start Manual Run button in the OCI Console or automatically, using triggers. You can create a trigger in the OCI Console for a build, which will automatically run a build pipeline on matching source code repository events in either the OCI code repository, GitLab, or GitHub. You can trigger a conditional build by adding the action of an optional event, such as a push or a pull request. Make a note-- before creating a trigger in DevOps, you must have a DevOps project, a build pipeline, and a code repository associated with the project.

The build then gathers and compiles code and associated files from the OCI code repository or mirrored GitHub repos, runs the requested unit and validation test, then publishes the resulting container image, logs, and other software artifacts to the OCI Container Registry and Artifact Repository respectively. As we studied earlier, the build pipeline can also optionally trigger a deployment pipeline, which takes care of pulling the artifacts and deploying them on the target environment. You can also edit triggers to update their details or delete them.

When it comes to managing build pipelines, create, delete, and edit operations can be performed easily using Console. You can always come back and customize the pipeline to accommodate changes. Parameters can be configured to supply values to placeholders during the build process. Build pipeline gives you the provision to monitor the progress of each build step and stage on the console, which makes it easier to troubleshoot in case of failures. Note, you can't delete the build pipeline unless you delete all the stages within it.

When you create a build pipeline in the OCI Console, you select the stages you want the build to include. When the build run starts, the console shows you a graph with a box for each stage on the left. To the right of it is the build run progress, where you can expand each stage to see the steps being taken, the time they take, and the status of each step. These steps are taken directly from the build spec file you provided.

On the far right are the log details. During the build run, the active stage is highlighted in the graph. A build run is successful if all the stages in the pipeline complete successfully. When the build run completes, you can view the results in the console's Build History section, which houses the status and results of all the previous builds.

To wrap up our discussion, in this lesson, we covered DevOps project build pipeline feature in detail. We addressed topics like build spec file, which is the main element that structures the build. We also discussed different stage options and triggers to automate the startup build and deployment pipeline. 







--------------------


 Deployment Pipeline


 

A deployment pipeline holds the requirements that must be satisfied to deliver a set of artifacts to the target environment. It's an integral part of the continuous deployment process within a DevOps project, which can be controlled by defining stages that run in serial or parallel. And it's usually triggered by a build pipeline but can also be run independently.

I believe you still remember from the previous lesson that the build pipeline had a stage, which offered us an option to trigger deployment pipeline. The last point is talking exactly about it. Before we move ahead, let us understand when and when not to implement continuous deployment within your project.

You must go for continuous deployment when you want to release features faster, when deployment is a continuous routine in your business setup, also when you want to discover issues before the release hits production. And you must go for continuous deployment when you have all the resources needed to automate your development lifecycle with less manual intervention.

You must not go for continuous deployment when it is a one-time deployment that you're planning, or when the test automation is not mature enough to confidently push your artifacts to the production in an automated environment. Again, when your business case doesn't allow you to publish to production without going through any kind of user acceptance test. Also, if your project is a high-risk, high-profile project, then you must avoid using continuous deployment.

At this point in the course, we are already well aware about the DevOps CI/CD practices. But usually, some people have a hard time understanding the difference between continuous deployment and continuous delivery. Let's address that first.

The continuous delivery process typically includes at least one manual step of approving and initiating a deploy to production. In complex projects with multiple dependencies, the continuous delivery pipeline may include additional steps, which are either manual or automatic.

On the other hand, continuous deployment is a step further by releasing every change that passes through the production pipeline directly to your clients without any human intervention. If an automated test fails, then the change will not be sent. But if everything checks out in the testing, the changes are deployed automatically.

Let's talk about some advantages of using deployment pipelines. To start your deployment, you can either automatically run a deployment from your existing continuous integration platform using triggers, or you can run your deployment on-demand. The deployment pipelines also offers you advantages in terms of deploying to different environments in multiple regions. You can use either a parallel or a serial approach to do so.

In your deployment pipeline, you can fully automate the deployment to include testing and delivery to each of your environment, such as developer, testing, staging, and production, and automatically promote the release all the way up to production. You can also set up deployments that include manual approval stages for automation with manual checks.

Let's take a look at the deployment pipeline workflow. In this diagram, you can see how a sample application is deployed using OCI DevOps. The application is already built, stored in a repo, and is ready to be deployed to three different target environments-- OKE, instance groups, and functions.

As you see in step one, the build output is stored in the container registry as an image. You can also store other artifacts in the artifact registry. In step two, the image artifacts from the registry and the configuration files from the repositories are copied into the target runtime environment.

From the step three, you can notice once these artifacts and the configuration files are pushed to the target environment, they are easily deployed and are ready to operate. From step four, what we can see is the logs from the build runs, and the deployments are sent to the OCI logging service for audit and governance. And your team can receive notifications from the events of your DevOps pipelines through the notification service. These logs can be further used for observability and management purposes.

Let's take a look at the release strategy. The deployment goes through these continuous delivery stages orchestrated by the OCI DevOps service. In this example, consider a build pipeline that executes successfully and generates artifacts for deployment. It is configured in a manner that it triggers the deployment pipeline.

The deployment pipeline here depicts how we can deploy those artifacts onto the test environment to perform regression or security testing. The test should passes, then you can promote the artifacts to your staging environment. Here we can perform smoke and UAT tests.

After staging, you can run a canary test, send a small amount of production traffic to a new artifact, and then monitor the metrics. Canary test is used as a litmus test by studying how it behaves for a small percentage of end users. This allows DevOps team to collect data to help them figure out if their code is behaving the way they want it to or not.

Upon receiving user feedback, if everything looks good, you can go ahead with full release to the production. Using the OCI DevOps service, you can automate as much as you want to, with the deployment pipeline and automated builds run without intervention.

The DevOps projects offer many options to customize your deployment pipeline. Let's look at how to manage the deployment pipeline. You can edit pipelines to add, modify, or delete stages. You can also configure parameters to override the default values.

The deployment pipeline can be done manually or triggered by the build pipeline automatically. Once the deployment pipeline is run, we get the provision to monitor the progress of every stage. Rollback is one of the highlights of deployment pipeline, which in case of failures rolls back the state of application to previous successful version deployed.

Similar to how we create stages in build pipeline, we must also create stages in the development pipeline. What changes here are the options used to create them. Let's take a closer look at each of the options available.

Let's understand some facts about working with deployment pipeline stages. You can add multiple stages to a deployment pipeline where each stage represents an action. For example, applying a Kubernetes manifest to your OKE cluster.

Stages can be added in sequence or in parallel. You can remove any stage from the pipeline if they are no longer required. Deployment pipelines offer many deployment strategies to meet your needs. You can perform rolling updates, as well as deploy using blue-green and canary release strategies.

With the ability to rollback a deployment, coupled with support for various release strategies, deployment pipeline provides the capability to minimize the failure effect due to a bad deployment. Note, OCI DevOps deployment pipelines can work across OCI regions. From a single deployment pipeline, deployments can be executed into multiple regions, in parallel or sequentially.

Displayed on the screen are the three categories that the user can choose from while creating deployment pipeline stages. The user can choose the deployment environment stage to choose the target environment where he wishes to deploy the software.

Users can also select the control stage, which will help them manage the progress of their deployment pipeline stages. They can also select the integration stage, which will help them invoke a function to run some custom logics.

Let's talk about configuring parameters. Parameters are name of placeholders that exist in the DevOps resources. They are available to all the resources within the pipeline.

All parameters using the pipeline must have a value before the pipeline is run. When the pipeline is run, you have the option to override the default value of the parameter with an argument value for that run. In situations where a parameter has both argument and default value, the argument value always takes the precedence.

All right. So if we can define parameters for both the pipelines, what happens if the same parameter is defined at both places? In that case, remember that if you set parameter in both build and deployment pipelines, the one set in the build pipeline takes precedence.

A pipeline parameter name can be used in placeholder that exists in your DevOps resources and certain API fields. The placeholders are special strings with a unique format starting with the dollar symbol and the parameter name within the curly braces. When a pipeline is run, the placeholder is substituted with the value of the corresponding pipeline parameter.

As you can see from the example, we have a code snippet from the Kubernetes manifest file and which has a placeholder in it. So this placeholder will be substituted with the parameter value, and the pipeline is run.

How to run a deployment pipeline? A deployment pipeline can be invoked automatically by setting up build pipelines through your deployment stage or manually through dashboards on the OCI Console.

We can organize our deployment pipeline by editing it as per requirement or deleting it when not required. You can always add new stages to the existing pipeline or delete the existing ones. You can also update deployment name, parameters, and artifacts used, and rerun the previously completed deployments. Remember, if you wish to delete the deployment pipeline, you must delete all the associated stages beforehand.

Selecting artifacts for deployment pipeline stage. The build artifacts that are generated and delivered by the build pipelines to the artifact registries can be mapped here in the deployment pipeline to be delivered to the target environments based on different scenarios.

For example, you can select the manifest files from the artifact registry to be applied on the OKE, or deployment file if you're trying to deploy it to the instance group, and container images or functions. The deployment view is your real-time dashboard for your deployment to see the order of stages, their progress status, and real-time logs of stages in action.

When the deployment is complete, you can view the results in the Deployment page, which houses the status and results of all previous builds. You can follow the progression of the pipeline directly from the Deployment page. Every stage that is running changes its border color to yellow. A completed stage turns green in case of success, and red in case of failure.

You can also visualize logs on the right-hand side of the page. Deployment is successful if all these stages are completed successfully. A snapshot of the pipeline is shown throughout the deployment process. The progress is tracked. After completion, a history of the actions taken is maintained. When deployment completes, you can view the status of deployment, including a snapshot of the graph.

In DevOps project, deployments can be rolled back manually or automatically. You must think of a rollback plan and configure it during this stage creation step. Configuring rollback minimizes downtime if a deployment fails.

After a deployment is completed, you can roll back a failed stage in the deployment pipeline to the previous successful release versions. During automatic rollback, other in-progress stage continues running, but the new stage cannot run, and the deployment completes as failed. There can be several reasons for rollback. Some of them are bug fixes, failed deployments, encountered vulnerabilities, and so on.

When creating a deployment pipeline for a cluster or an instance group, you can select either automatic rollback or manual rollback option from the Actions menu in the Oracle Cloud Console. If you wish to go for a manual rollback, you must identify the deployment that has failed, and then select the deployment ID to rollback based on the deployment timestamp, and then rollback.

Remember, rollback of a single stage in the pipeline is considered a new deployment, and the snapshot is provided only for that stage during the deployment. As you can see from the image over here, if you wish to go for manual rollback, you must choose no as an option for automatic rollbacks.

When creating a deployment pipeline for a cluster or an instance group, you can select automatic rollback as an option. If the validation fails, the release is automatically rolled back. And if the stage fails, the last successful release version is deployed.

During automatic rollback, other in-progress stage continues running, but new stages cannot run, and the deployment completes as failed. As you can see from the image over here, you must choose yes as an option to enable automatic rollback to last successful versions. 


![image](https://github.com/qriz1452/oci/assets/112246222/3ec43054-63cb-416b-ac34-fd4ba1b4e416)

![image](https://github.com/qriz1452/oci/assets/112246222/bdd06ff1-8f6c-4669-9161-bdc22eb21605)

![image](https://github.com/qriz1452/oci/assets/112246222/cf2c4e00-329e-4603-bd96-de8fd5d06cdb)


![image](https://github.com/qriz1452/oci/assets/112246222/fe1e36f9-9cc1-473b-9a60-7b228bcad1b0)


![image](https://github.com/qriz1452/oci/assets/112246222/5171dbef-51fb-4d81-a3ff-9c9b22ae6722)


--------------








