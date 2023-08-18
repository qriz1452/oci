Now Playing : Serverless Functions: Introduction


 Recall once again the learning path overview video where I mentioned the case study workshop which uses this VisionStays cloud native reference architecture. Well, one of the essential services used in VisionStays is Oracle Functions. Thus, the scope of this module is to learn more about the capabilities, features, and use cases for using serverless functions, specifically Oracle's Managed Function service.

The VisionStays workshop solution includes two functions, one that is used by third party aggregators to create a new hotel booking and the other used to retrieve details about the hotel properties. In this architecture, their implementation logic invokes corresponding microservices deployed to an OKE cluster.

Now, there are many other use cases for lightweight functions, but the important concept for serverless functions is in their flexibility to either be exposed as a service to be invoked or maybe to provide reusable logic for other applications and microservices. Once again, as a reminder, after you've watched the videos in this module, you should either review the workshop activity guide and watch the solution videos related to those two functions, or better yet, use your own OCI account to do the hands-on exercises yourself. With the complete workshop, you can replicate an end-to-end experience that includes container-based application development using serverless functions.

![image](https://github.com/qriz1452/oci/assets/112246222/43cbe600-455a-4d43-87f2-ad64ac1e1cc6)

--------

Now Playing : Functions: Service Overview

What is Oracle Functions? Oracle Functions is a serverless functions-as-a-service offering. It is fully integrated with the Oracle Cloud Infrastructure.

Functions is a container-native platform, which means your functions are deployed as Docker images and run as Docker containers. Functions is based on the open source FN Project. Functions are secured using Oracle Cloud security constructs such as networking identity and access management, compartments, and many more.

Let's look at some of the benefits of Oracle Functions. Functions is a pay-per-use platform, which means you only pay for the function execution, and you're not paying anything if your functions are idle. The platform is autonomous, so it takes care of provisioning, managing, and auto-scaling your functions for you. And as a user, you do not have to worry about any of these concerns. It's an event-driven platform. There are a number of Oracle Cloud Infrastructure services which can automatically trigger your function code for you.

So how does it work? They give you a Function CLI. You write your function code, and you run the command that will package the function code as a Docker image and push this function image to our registry. The next step, you will configure a function trigger. Now, what is a function trigger? A function trigger is the condition when you want to execute this function. An example of a function trigger is an HTTP request made to invoke the function.

Your code will run only when it is triggered. So in this example, your code will run when somebody makes a request to invoke your function. And you'll pay only for the code execution time. So there is no charge for idle time.

Let's look at the functions pricing. There are two dimensions. One is the number of function and location requests, and the second one is the resource usage, which is the amount of memory that you consume when your function was running. Functions pricing has an inbuilt generous free tier. So the first 2 million requests and 400,000 gigabyte-seconds are free per month. And above that, when you exceed the free tier, there is a small charge that you pay for using additional requests and additional gigabyte-seconds.

R3 requests are twice the number of AWS Lambda free requests, and our GB-second pricing is 15% less than AWS Lambda's pricing.

Functions is polyglot and container-native. Functions are packaged as Docker images and run as containers. This lets you package and reuse open source libraries as functions. We have great support and function development kits, or FDKs, for Python, Java, Go, Node, and Ruby, and for advanced use cases, we allow you to bring your own and customize the FN-generated Docker file. We allow you to use Micronaut microservices framework and Graal VM Native, which will help you reduce your Docker image size and memory footprint.

Let's move to functions integrations. There are a number of services in OCI that can trigger functions automatically for you, like the event service, the API Gateway, and so on. You can also use the CLI and the SDK to trigger your functions.

When your function is triggered, we pull the Docker image from the OCI registry and start the function container. In your function call, you can use any of the downstream services, like object storage, Autonomous, Compute, the Secrets service, Networking, and many other services. Any logs, metrics, and traces that are generated are sent to OCI logging, monitoring, and APM services, respectively.

![image](https://github.com/qriz1452/oci/assets/112246222/ddd912ea-7705-4c17-8d00-3c1f9aece606)

![image](https://github.com/qriz1452/oci/assets/112246222/0280763c-bd94-4f88-8c3a-a8f0fb34a2d1)

![image](https://github.com/qriz1452/oci/assets/112246222/e087d65c-d9a3-430f-8982-217c3ce4eff5)

![image](https://github.com/qriz1452/oci/assets/112246222/abf017a6-9aef-4ebb-965c-e144d2b311e7)

----

Now Playing : Functions: Triggers

welcome to the next module. This is a functions triggers. In this module, we'll be taking a look at all the services that can trigger functions automatically in Oracle Cloud Infrastructure. We'll start with the Event Service, then look at Notification Service. Then we look at the Service Connectors, followed by API Gateway. In addition to these, we also have Oracle Integration Cloud that can trigger functions, and of course, you can use the CLI and SDK as well.

Let's begin with the Event Service. Event Service provides real-time, fast alerts on state changes of OCI resources. You may have a number of other OCI resources, like compute instances, storage buckets, networks, databases, and so on. These services are constantly emitting lifecycle change events. Oracle Events Service is a nice way to keep an eye on these events and take some action based on certain lifecycle events that you're interested in.

For example, if somebody starts a compute instance, you may want to get notified. If somebody creates a public bucket, you may want to make that bucket private, for example, and so on. So Events Service lets you define rules where you can keep an eye on the events that you're interested in and perform certain actions-- which could be, you may want to write the event to a stream. You may want to send the notification email or a Slack alert to someone. Or you may want to take some corrective action using an Oracle function. Events Service follows the Cloud Events standard.

The next service they look at is the Notifications Service. Notifications Service is a fully-managed, multi-tenant pub-sub service. Again, it is fully integrated with OCI, so it integrates with Events, Monitoring, Service Connector Hub, Functions, and a number of other services. It supports a wide variety of endpoints, such as Email, PagerDuty, Slack, Functions, and so on. And finally, Notifications Service is enterprise-grade, so it's fully secure, highly reliable, has low latency, and is durable.

Up next is Service Connector Hub for Service Connectors. Service Connector Hub provides full visibility into data movement. It gives you a centralized experience to view, secure, and manage all data that's moving in the cloud. It allows you to take near-real-time actions.

Examples include easily emit log-based metrics. You can do one-click log archival, where logging becomes a source, object storage becomes a destination for your connector, and you can move logs, you can filter logs and archive them in the Object Storage Bucket. You can also perform automated remediation, alerting with functions and notification services.

Service Connectors also allow you to integrate easily with third-party tools. You can seamlessly move data to any destination using the Kafka-compatible OCI Streaming Service. You can also move logs from OCI to a third-party service like Datadog, or Splunk, or any other service of your choice.

Let's look at the API Gateway Service. The API Gateway Service is a policy enforcement point for REST APIs. It allows you to define policies to authorize, throttle, and route requests that can help you protect your back end services. API Gateway is a serverless platform. It's a network-attached device that's fully managed by Oracle. It helps you create RESTful, serverless back end APIs which can then be implemented using services like Oracle Functions.

API Gateway has integration with the authorization servers, so you can use Identity Cloud Service in Oracle or any other third-party provider that is capable of generating JSON Web Tokens, or JWT tokens.

![image](https://github.com/qriz1452/oci/assets/112246222/beb715e1-4f57-43a7-8250-4372cef3fbd2)
![image](https://github.com/qriz1452/oci/assets/112246222/b05a0fac-0361-4fb5-8122-16ee252e64f6)

![image](https://github.com/qriz1452/oci/assets/112246222/54c3e016-09ac-4ffe-828b-f6ce55bda55e)
![image](https://github.com/qriz1452/oci/assets/112246222/43e49e67-aa07-4da3-b4d9-0266a1619896)

------
Now Playing : Functions: Use Cases

Let's look at some of the common use cases of serverless and functions in the Oracle Cloud. If we have to describe serverless use cases in a single sentence, it would be you can trigger code in response to an event.

There are a number of categories of serverless use cases. We have listed some of them on this slide. The first category is event-driven governance. Examples of event-driven governance include audit logs and network flow logs.

You may want to configure an event based on an audit log or a network flow log and take some action on that event. The action could be as simple as read the logs, filter them, and send them to a downstream security incident management system, like Splunk.

The next category is web and mobile API in back ends. In this example, we have an API gateway in front of a function. The function is used to implement the REST API back-end code. And the API gateway exposes the function as a REST end point to end customers.

The third category is real-time file and stream processing. In this case, you may have data coming into an object storage bucket or data being sent on a Kafka-compatible stream. This event will trigger a function which will automatically process the data and take some action on the data. A simple action could be analyze the data and save it to an autonomous database.

And you can also use functions for machine learning, DevOps, and several other use cases. Let's look at use case number one, enforce corporate security policies and governance rules. OCI resources like compute, databases, networks, storage, and others emit resource change events via audit logs.

You can use a Service Connector with audit logs and functions to enforce corporate security policies and governance rules. For example, you may want to audit and tear down all non-compliant resources in your tenancy.

Let's say you have a policy where users should not be allowed to create compute instances with public IP addresses. You can use this pattern of audit logs, Service Connector, and functions to check for any audit events which show that a compute instance was created with a public IP address. And then, inside your function, you can remediate this by shutting down the compute instance.

Let's move to use case number two, ingest access logs in security incident management systems. In this example, we have the OCI Virtual Cloud Network, or VCN. VCNs send network access logs or flow logs to the OCI Logging service. You can use a Service Connector with Logging as the source and Functions as a target.

The function's job would be to parse the network access logs and send them to a third-party security incident management system of your choice, which could be Splunk, ELK, or any other SIM system.

Let's look at the use case number three, high volume ETL solution. This is an example with the Event service, the Object Storage, service and the Functions service. In this example, we have insurance claims XML files being uploaded to Object Storage at regular intervals.

This triggers an event rule. The event rule is configured to invoke a function. The function's job is to read the XML file, transform it, and insert it into an Oracle database. The Oracle database, in this case, is running on the Exadata Cloud Service.

This scenario is a high-volume solution. If you have more files coming into Object Storage in parallel, the Functions service will scale your functions horizontally to process these files concurrently.

Let's move to use case number four, resize virtual machines. In this example, we have an OCI virtual machine of shape VM.Standard.E2.1. OCI Compute VMs are configured to send CPU and memory usage metrics through the OCI Monitoring service.

In the Monitoring service, we can configure an alarm for high CPU or high memory utilization. When this alarm goes off, we would like to send this message to a notification topic. We have a function that is subscribed to this notification's topic.

And the function's job is to resize the Compute virtual machine instance to the next higher shape available. In this example, the function will resize the VM from E2.1 to E2.2, which is the next higher virtual machine shape available.

Let's move for to use case number five, functions as API back ends to extend Oracle Sales Cloud. We will start with the front end, which is developed using Oracle Visual Builder. The back end is Oracle Sales Cloud. And we also have an autonomous database and a data warehouse in this example.

From the Visual Builder front end, you make a REST API call through the API gateway. The API gateway triggers an authorizer function implemented within the Oracle Functions service. This function is responsible for authenticating and authorizing the incoming API requests.

Once the auth is successful, the next step is the business logic function. This is implemented as another function in the Oracle Functions service. The business logic functions can talk to the Sales Cloud instance and the autonomous databases to get data from these back ends. This pattern can be used to extend any API back ends using Functions and API Gateway.

![image](https://github.com/qriz1452/oci/assets/112246222/b2b79e27-b13d-4ac0-b662-d673b3aa187d)
![image](https://github.com/qriz1452/oci/assets/112246222/e68c8e33-4a2a-4689-b7f9-6fb5f86fee73)
![image](https://github.com/qriz1452/oci/assets/112246222/9138c38b-b3bf-41f0-9963-dc137f213110)

![image](https://github.com/qriz1452/oci/assets/112246222/32257552-bb14-4fcf-a829-ac3d1e632731)
![image](https://github.com/qriz1452/oci/assets/112246222/f290a6d9-0d3f-472c-9b1a-75504e150f88)
![image](https://github.com/qriz1452/oci/assets/112246222/48e98c44-17f5-4d2f-8fdc-1da68f2090db)


-------
Now Playing : Functions: Concepts

. So what is the functions application? Functions application is a collection of functions. It is attached to the customer's Virtual Cloud Network, which is VCN and subnet.

And this is used for network egress. Application is also a unit of workload isolation. You can enable or disable logs, function traces, and set common environment variables or function configuration.

What is a function? A function as a container image that is stored in a container registry and metadata. Metadata contains the image location, the function memory, function timeout, and any configuration parameters or environment variables required for the function's execution.

Fn CLI is a command line tool that is used to manage functions. It has various commands that help you build, package function code as a container image, and then push the image to a container registry. It also has commands to generate boilerplate function code or languages such as Java, Python, Node, Go, and Ruby.

What is the fn init command. The fn init command generates boilerplate hello world function. You can provide the runtime as a parameter. So you can select runtime as Java or Node or Python or Go or Ruby or Docker. In this example, we have given Java as the runtime language. And you can see the generated boilerplate Java function.

Let's look at the fn deploy. The fn deploy builds the container image using a multi-stage Docker build that pushes the container image to a registry-- in this case, the OCI container registry, or OCIR. And then it creates or updates the function metadata where it keeps a pointer to the function image in OCIR.

Let's look at the function configurations. As a user, you have control on the function memory. You can select one of 128 MBs, 256 MB, 512 MB, or 1 GB for your function memory.

The next parameter that you can configure is the function timeout. And today, Oracle function supports a maximum of five minutes for a function timeout.

The other configuration parameters that you can specify are environmental variables, which you can define at the function or the application level. And then within your function code, you can access these parameters at runtime. The function service will ensure that the values are the same into your functions, and they're available for you to consume. Examples of environment variables are database user name, password, secrets which are used to access REST APIs, and so on and so forth.

The other configuration is the functions service limit. Today, there are three service limits. One is the number of functions, the number of applications, and the overall function concurrent execution memory. All three elements are soft limits. And you can easily raise a service request from within the OCI Console to get these limits increased.

Moving on to functions observability. There are three key pillars-- metrics, logs, and traces. And the function service supports all three.

First, the function metrics. The function service collects metrics and sends it to the OCI Monitoring Service. You can easily view metrics in the OCI Console.

Function service integrates with OCI logging and sends your function logs to the OCI logging service by default. To generate logs, you need to have print statements or log statements inside your function code. You can also send logs to a third party service using syslog endpoints within the function service.

Function service can also generate and send traces to the application Performance Monitoring Service in OCI. And we have a troubleshooting guide in our service docs that has the list of error codes with the description and the resolution steps to help you troubleshoot functions.

Using other services from functions. A function can use other services in OCI like object storage, secrets, compute, network, and several others, or it can access services on the public internet.

Functions supports fine-grain access control. You can use functions resource principles to control what your functions can access. For example, if a function needs access to read an object storage bucket, you can put the function in a dynamic group and create a policy to allow that dynamic group to read files from that object storage bucket.

Function can access any service in OCI using a private subnet and the service gateway. Similarly, to access a public service, you can have an internet gateway in your VCN and subnet configuration.

![image](https://github.com/qriz1452/oci/assets/112246222/e675583b-1111-4aaa-a6db-c1ef291e6963)

![image](https://github.com/qriz1452/oci/assets/112246222/af1857ba-4cc0-4464-8d2c-7eb43350b01b)

![image](https://github.com/qriz1452/oci/assets/112246222/d846a8b8-6dbb-4b8a-8744-3162395a8277)
![image](https://github.com/qriz1452/oci/assets/112246222/690c0676-6eed-4a21-a670-39f08ad9353b)
![image](https://github.com/qriz1452/oci/assets/112246222/cb34191f-e1ff-4eca-980d-aeeec76d8f1f)

===========



















