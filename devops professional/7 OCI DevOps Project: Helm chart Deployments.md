 Helm Overview

 what basically is Helm? A typical application deployed to Kubernetes will have objects such as deployments, services, secrets, persistent volumes, persistent volume claims, ingress, and so on. And with its declarative nature, you define everything through the YAML files.

When we deploy a application to Kubernetes cluster, we may need to create multiple services. A large application can contain more than 40 microservices, and each service can contain multiple Kubernetes resources such as service, deployment, secret, et cetera. Now imagine the same application needs to be deployed in different environments, such as test, QA, and prod environment with configurations meeting those environments specifications. It will get very cumbersome and inefficient to deploy the Kubernetes resources one by one based on the YAML files. Also, these YAML files are extremely complicated to maintain and prone to errors.

So the question arises, do we have a more efficient way to manage these Kubernetes resources files? The answer is, yes. You can use Helm Chart Package to create and manage your applications based on the Chart Package through the Helm command. Helm helps you manage Kubernetes applications and Helm Charts help you define, install, and upgrade even the most complex Kubernetes application. Consider Helm for Kubernetes just the way we have Pip for Python and Yum for CentOS. Helm is an official Kubernetes project and is part of the Cloud Native Computing Foundation.

Let's take a look at the Helm architecture. The core is the Helm Client and the Helm Chart Package. The Helm command can download the Helm Chart Package from the repository and read the kubeconfig file and construct HTTP requests for cube API server REST API interface. By calling the REST API interface provided by Kubernetes, all the Kubernetes resources that are defined in the YAML format contained within the Chart Package are created in the Kubernetes ecosystem. The latest version of Helm is Helm version 3 as I record this video.

To better understand Helm, there are three concepts we need to get familiar with. The first one is the Helm Chart. The Helm Chart represents a Helm package. It contains all the resource definition files in YAML format needed to run an application, tool, or service. A chart usually comes with default configuration values in its values.yaml file. Some applications may be fully default values, but you will typically need to overwrite some of the configuration to meet your needs.

The next concept is release. A release is an instance of a chart running in the Kubernetes cluster. One chart can often be installed many times into the same cluster. Each time it is installed, a new release is created. Consider a WordPress chart. If you want two WordPress running in your cluster, you can install that chart twice. Each one will have its own release, which will in turn have its own release name. For example, if we run Helm install A WordPress, release A is created. And if we reinstall the same package as Helm Install B WordPress, a new release B is created.

The third concept is the chart repository. Similar to GitHub repository where source code is maintained and Docker Hub where images are stored, chart repository is a place to store and share Helm charts. Helm search hub command searches through the artifact hub from the dozens of repositories. You can add custom repositories in the local Helm client using the Helm repo add command and search through these repositories using the Helm search repo command.

So as you can see from the example, I've added a custom repository using the Helm repo add bitnami command-- bitnami is my custom repository-- and then I'm using the Helm search repo to search into the bitnami repository for the WordPress chart. To wrap up, in this lesson, we realized the importance of Helm and covered its architecture along with three basic concepts like Helm Chart, release, and chart repository. I

![image](https://github.com/qriz1452/oci/assets/112246222/423f333b-59ae-42ef-b983-b5d2b012420d)

![image](https://github.com/qriz1452/oci/assets/112246222/3adb5d36-5997-445a-af3a-38ba57d6782e)


![image](https://github.com/qriz1452/oci/assets/112246222/1984d528-99d4-42d3-a023-e39be4ec841d)

![image](https://github.com/qriz1452/oci/assets/112246222/e4da108f-950e-4d4a-9e06-b56a8504fcbe)

![image](https://github.com/qriz1452/oci/assets/112246222/5a94491b-61a4-4593-80be-40abaeb3471b)

![image](https://github.com/qriz1452/oci/assets/112246222/e6888ba0-ba77-4234-856f-2d03bf8a3326)



----------------

 Helm chart structure and basic commands


Helm packages are called charts, and they consist of a few YAML configuration files and some templates that are rendered into Kubernetes manifest files. Let's understand the basic directory structure of a chart and their functions.

The first directory that we're talking about is templates. This directory contains template files that are combined with the configuration values and rendered into the Kubernetes manifest, like deployment service, et cetera. The templates use the Go programming language's template format. The next file is the values.yaml file. This is the file that holds the default configuration values for the template files.

Next is the chart.yaml file. It is a YAML file with metadata about chart, such as the chart name and version, maintainer information, a relevant website, charts dependencies, and search keywords. The license file is a plain license for the chart. We also have a README.md file, which is basically a file with information for users of the chart. And we have the charts directory.

Manually-managed chart dependencies can be placed in this directory. Charts can also contain files that describes the installation, configuration usage, and license of a chart. In Helm, it can be understood that it mainly contains two types of files-- template files and configuration files. There are usually multiple template files and one configuration file. Make a note-- a template directive is enclosed in double opening and closing curly brackets.

Helm Template provides powerful template rendering capabilities. And Helm can render the values in the configuration file into the template files and finally generate a resource definition file. Let's take a look at some of the basic Helm commands. The Helm install command will install a chart from a repository, so you should ensure that you have set up the repository first. The Helm list command will help you see all the charts that have been deployed on your cluster.

The Helm upgrade command upgrades your release with new values and provides a new revision number to your existing release. The Helm rollback command is used to rollback a release to a previous revision. The first argument of the rollback command is the name of the release; the second is a revision version number. If this argument is omitted, it will roll back to the previous release.

And we have the Helm uninstall command. This command takes a release name and uninstalls the release. It removes all the resources associated with the last release of the chart, as well as the release history, freeing it up for future use. Also remember the values.yaml file is very important for templates. This file contains the default values for a chart. These values may be overridden by users during Helm install or Helm upgrade command, 

![image](https://github.com/qriz1452/oci/assets/112246222/c46b6234-40ba-4279-bfa8-d45b67d67354)
![image](https://github.com/qriz1452/oci/assets/112246222/1e7d9b7b-f17c-4111-9382-ee952f295b3e)
![image](https://github.com/qriz1452/oci/assets/112246222/c3b473df-0ffd-4bed-877c-dd57298d0aa9)


---------------

: Helm chart deployment to OKE

OCI DevOps service supports deployment of Helm charts to container engine for Kubernetes clusters. This new feature of OCI DevOps service enables developers to easily create containers integration and delivery pipelines that includes Helm chat package deployments to their OKE clusters.

Now, developers can add a specific Helm charge stage to the deployment pipelines to automate the deployment and automatically roll back on OKE environments. Let's take a look at a few key points to note before you execute the Helm chart deployment to OKE.

Before you begin, you must create a container engine for Kubernetes cluster. And you can deploy it to both public and private OKE clusters. You can build your Helm chart in a DevOps build pipeline and then push it through the OCI Container Registry to use in your deployment.

You can also push Helm charts to a container registry if it is compatible with the Open Container Initiative. The Helm charts must be located in the OCI Container Registry repository for deployment. And lastly, Helm chart contains templates of Kubernetes YAML manifest files and the values.yaml file to supply the default template values. The values.yaml is a generic file that is located in the OCI Artifact Registry. You must create a reference to this file. 


![image](https://github.com/qriz1452/oci/assets/112246222/bdddc255-6165-403d-8d50-f343bfe04554)
![image](https://github.com/qriz1452/oci/assets/112246222/de7bf3c9-27ae-453a-a83c-4aa1174372cc)



--------

Continuous Testing and OCI Support for External Tools


continuous testing, let's think about this-- if an automated pipeline is handling the software release process, is there still a chance to test the code before it's made available to the end users? Do I still need testing?

The answer would be a definite yes. Adopting a pipeline does not mean software testing should be sacrificed to streamline the release process. The very basis of DevOps pipeline is to make the release process reliable and easily repeatable while reducing the chances of errors, delays, and any sort of miscommunication. New or existing automated tests can be easily and smoothly integrated into the pipeline. Unit tests, smoke tests, regression [? suites ?] can all be run as part of a release pipeline.

As you progress further in the pipeline, the test automation spans further from the code level into the areas like API testing, performance testing, load testing, and endurance testing. Overall, the highlights of continuous testing are that it should be part of your continuous development process. Doing so will help identify bugs early in the SDLC and will reduce the number and complexity of errors. Testing, which are repetitive in nature, can be automated to speed up the execution. In this way, continuous testing supports the DevOps goal of speeding up software delivery process to deliver high-quality software to the end users.

Testing can span every stage of your software development lifecycle. The blinking stars on the diagram shows where you can automate testing in your SDLC. Each step of the SDLC involves different forms of testing. This minimizes backtracking in the case that you have detected an error. Again, as you'll see, testing is carried out at different stages. It is no longer the responsibility of one particular team. Shared testing responsibilities allow everyone to understand the impacts behind each change.

Let's walk through a sample scenario. Say several developers have reviewed and approved a code merge to the working branch of a code repository. Once the code is merged, the CI/CD pipeline picks up the changes in the code repository and tells the build runner to build the code. If the build is successful, the code is ready to be deployed by the CD pipeline.

Unit tests should be run by the build server as a sanity check. Then a suit of automated software tests can be kicked off against the successful build as a further check that the code changes have not broken any existing feature. If any of these steps fail, the pipeline will notify the responsible parties that it's breaking the build, and the deployment is then terminated. On the other hand, a successful run will result in deployment to production environments.

Whether you are migrating on-prem workloads to OCI or developing new applications on OCI, you can use the OCI DevOps service to simplify your software delivery lifecycle. One of our DevOp tenets is to improve the developer experience for OCI developers, regardless of what CI/CD tool sets they use. Customers invest in their DevOps tooling to gain speed and reliability of software delivery. Our OCI DevOps works with the customer's existing DevOp tool choices like Jenkins, GitLab, GitHub, Spinnaker, and the list goes on.

You might also want to move an existing application from on premises or another cloud to OCI. The OCI DevOps service has the flexibility to integrate with your existing CI/CD workflows. If you are migrating and want to keep your existing CI workflow, you can move the deployment process to the OCI DevOps and trigger a deployment from an existing CI pipeline to orchestrate your release steps with the OCI DevOps deployment pipelines in the Oracle Cloud.

Let's take a look at the external tools and plugins that are supported on the OCI platform. The first one is Chef Knife Plugin. We all know Chef is a very popular tool that helps us provision infrastructure as a code. The Knife OCI plugin allows users to interact with the OCI infrastructure through the Chef Knife.

We have the Ansible collection that makes it easier to provision resources in the Cloud Infrastructure through Ansible. The Grafana plugin makes queries to the OCI monitoring services and displays them on the Grafana dashboard. We also have support for the external Jenkins tool, such as OCI DevOps Plugin. This plugin lets you upload artifacts and run deployments on the OCI through the Jenkins tools. Similarly, we have a Compute Jenkins plugin that allows users to access and manage cloud resources on the OCI through their external Jenkins tools.

We have Terraform provider that helps you connect Terraform to a given OCI service in order to manage infrastructure as a code. Also, we have a Terraform Kubernetes installer that helps you manage Kubernetes installation on the OCI Infrastructure through Terraform scripts.

Let's look at an example on how you can bring your OCI to integrate with the CD for automation. Jenkins is a popular product for automating the continuous integration and continuous delivery and deployment pipelines for workloads in the Oracle Cloud. In this architecture, Jenkins is hosted on OCI to centralize build automation and scale the deployment by using the OCI registry and the container engine for Kubernetes.

GitHub is used to manage source code, and GitHub provides a web integration, so Jenkins can start running automated builds and test after each code check-in. A sample web application is deployed as part of the CI/CD pipeline, which end users can access from the Container Engine for Kubernetes cluster.

Note-- a Jenkins plugin for OCI DevOps deployment is available to trigger a deployment pipeline as part of the Jenkins build, which you already saw in the previous slide. When the Jenkins build come to the point where the software that was built, tested, QAed, and registered in an artifact repository, it's ready for actual rollout on the OCI. The plugin allows easy triggering of the deployment pipeline, set up in the OCI DevOps. Existing build pipelines can be integrated in this way with the OCI-native benefits offered by the OCI DevOps. 

![image](https://github.com/qriz1452/oci/assets/112246222/a2187fa4-064e-4b0b-aff1-13100558dcf7)

![image](https://github.com/qriz1452/oci/assets/112246222/cb029be2-893b-48f7-a782-e3598aebf6f4)
![image](https://github.com/qriz1452/oci/assets/112246222/a77132a5-7897-4b40-b950-cc62aa4c28da)
![image](https://github.com/qriz1452/oci/assets/112246222/c2d42731-78ca-4c5f-9046-3fa46e55bc30)
























 








