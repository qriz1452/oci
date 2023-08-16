 Introduction to Observability 

In this lesson, we are going to look at the key services and capabilities of the Observability platform, and how it addresses the priorities of DevOps. We will start with looking into the top priorities that could be addressed with Observability.

Number one, information systems end-to-end protection, which means maintaining the end-to-end security of all information systems, whether it could be the physical data center, networks, or applications. Number two, understanding the internal workflow of systems. DevOps would require a complete understanding of the internal workings of their systems, and that would help them to choose the right metrics to monitor proactively.

Maximize agility in application delivery. The ability to quickly deliver applications with having continuous monitoring to identify issues in the early stages. For example, finding performance issues with applications. And we refer to this concept as the shift left monitoring. This process would monitor constantly for health checks and find performance issues early during the process. Accelerate MTTD or mean time to detection and MTTR or mean time to resolution. This is one of the top priority in how quickly to detect issues or the mean time to detect, and how quickly to resolve them or mean time to resolve.

Reduced cost for breaches and operations. DevOps would also need to introduce processes or workflows that would reduce the overall cost of any breaches, and including operational efficiencies benefiting to that cost savings. With proactive monitoring and quick resolution, the overall cost can be reduced. Improve services and customer satisfaction. DevOps engineer would also look to improve Cloud Services with leveraging the data sets and metrics, and consuming them with best practices, which can all add values to the customer.

Let's now look into the end-to-end workflow of DevOps and define observability in this architecture. DevOps practitioners are continuously making changes to their code, and it gets checked in or committed into the code repository. The code repo is a platform where you host the entire code, including any software archives. So it is really important to monitor these code repos or let's say, if you want to monitor the total size of this repository.

The next stage is the build pipeline. And it is the stage where this code gets compiled and makes it ready for deployment. The build pipeline would also create necessary build artifacts. For example, the files created during the build process, the distribution packages, raw files, logs, and reports. The practitioners would need to know whether the bill is successful, and get notified if there are any failures.

And then the deploy pipeline is where the code is deployed into the target environment. If you are deploying a container-based application, it would pull an image stored in the container registry and deploy into the OKE cluster, or you could deploy as a compute instance or as functions, which is the serverless solution of Oracle Cloud Infrastructure.

And similarly, there is always a need to monitor if the deployment is successful, and get notified if there are any failures. Infrastructurous code and configuration management are two main components in this workflow. For example, having [? terror ?] from conflicts, you can specify the required plug-ins to install, the matching infrastructure service to create, or use Ansible scripts or puppet manifest for keeping a consistent configurations across the systems.

During this process, there are a number of nodes created and could also follow a number of CRUD operations like create, read, update, delete operations into the object storage, or it could be running a SQL database instance. There are Observability services that lets you monitor such operations that are occurring in the environment. And once the application is ready, end users can connect using HTTPS over a web application firewall or through an SSH using the bastion service.

Monitoring for connectivity is a critical step and helps operations to capture failures before the end users finds the problem. As we saw previously, the end-to-end protection of information systems is a top priority. So using services like vault to centrally manage the encryption keys and secret credentials, having the right IAM policies, [? plow ?] [? guard ?] and vulnerability scanning for monitoring the security postures of the environment.

So it is important to know the changes that are occurring in the environment and get notified for the major ones. All these requirements are achieved through an Observability platform that have services for monitoring, notifications, logging events, et cetera. And that tells us Observability is a core platform for DevOps that enables for CICD, continuous integration, continuous deployment capturing continuous feedback with testing, monitoring, and continuous operations.

Let's look into some of the key services that are related to Observability. Monitoring enables users to gain insights on Cloud Infrastructure and workloads with out-of-the-box metrics. Users can configure alarms with thresholds to detect and respond to infrastructure and application anomalies.

Logging can ingest log data from hundreds of sources using the CNCF open source data collector called Fluentd, which helps to collect logs like for audit we see in flow logs that can be used for diagnosing security issues. You can quickly search and discover logs which is based on Cloud Event standards by Cloud Native Computing Foundation or CNCF. And logging can be integrated with other OCI services like streaming, monitoring, and functions.

Application performance monitoring or APM provides a comprehensive set of features to monitor applications and diagnose any performance issues. OCI notifications is a highly available low latency service that follows a published subscribe pattern that can send alerts and messages to Oracle functions, email, and also including Slack channels and PagerDuty.

The Event Service track resource changes using events, and it eliminates the complexity of manually tracking changes across Cloud resources. And you can respond to changes in near-real-time using functions, streaming, and notifications. The platform enables you to have Observability across infrastructure environments, middleware, and application tiers. And so you can provide faster feedback to developers.

Let's look into some of the core use cases of this platform. Monitoring to inform business decisions. With transforming the collected data, you can make it accessible for different audiences and help them make decisions. For example, sharing operations data upstream to analyze whether the reported values are high or low or whether you're anticipating any operational changes or determining the technology use that has impacted the reported numbers in a positive or negative way.

Gaining insights into the environment. Observability is about instrumenting your systems with tools to collect actionable data to know when and why the issue occur. OCI's Observability platform provides you the right set of tools or the ability to build tools to quickly troubleshoot issues that are impacting in end users.

Proactive issue identification and notification. The platform offers the capability to identify issues proactively before it gets reported or before it impacts the resource and have different communication channels for notifying users. Productivity and operational efficiencies with automation. You have the capabilities to automate tasks with also having to execute more number of tasks that are in high priority. 

![image](https://github.com/qriz1452/oci/assets/112246222/16adf093-5fbf-428f-a2fb-b4f1c5fda198)

![image](https://github.com/qriz1452/oci/assets/112246222/3befc9e6-753d-47ca-99e4-9dce73004d1f)


----------------


 Monitoring Introduction


 
Monitoring is one of the foundational services of the OCI observability and management platform. The main purpose of the monitoring service is it enables you to actively and passively monitor cloud resources.

Active is about being proactive or being predictive in monitoring, and passive is about reactive monitoring using real-time data collected from cloud resources. The surveys use a concept called matrix that contains the data to be monitored and then under the concept called Alarms to alert for any of the problems being reported.

There are different ways you can access these metrics and alarm data. You can use the OCI Cloud Console or using CLI, the command line interface, and using APIs. There are a wide range of dashboards that you can access metric data in different graphical representations. And these are accessible through a single pane of glass window.

DevOps is about continuous integration and continuous delivery of your application. Monitoring service gives you the ability to monitor the internal processes involved in a DevOps cycle. Let's now look into the concept of metrics. Metrics are logically grouped within different metric namespaces. And these namespaces are like logical collection of multiple metrics.

You can see in the screenshot, you have a metric namespace dropdown and we have selected the OCI compute agent. And this namespace provides new metrics like the CPU and memory utilization of your compute instances. There are different types of metrics that can relay metric data.

The service metrics are those metrics from OCI cloud resources. Custom metrics are your own custom metrics that can be published using an API called post-metric data. Dimension is another concept in the monitoring service. You can use dimensions for providing filters to the metric data.

Let's say, if you want to filter the metric data by a specific resource ID of a compute instance or maybe filter by the shape used by the compute instance, you can add multiple dimensions with a name value pair and access metrics based on those selections. The next field, as you see in the screenshot, is a time period that is select along with the metric.

You can choose a start time and an end time to filter metrics within this period. Metric data is relayed as raw data points into the service. And then it is aggregated to make it presentable to the user. Interval and statistics are two different functions that are used to aggregate these raw data points.

Interval is a time interval you provide within the start and end time period, which will aggregate the data depending on the statistic condition. Statistics is another aggregation function. For example, you wanted to look the maximum reported value of the CPU utilization. Metric Stream is defined as an individual set of aggregated data.

Taking an example here, if you have 10 compute instances, and let's say, we are using the metric for memory utilization, the data would represent 10 individual metric streams. And in this screenshot, you can refer to the different colors in the graph section, which represent each instance. In the console, you are provided with an option to aggregate these multiple metric streams into a single stream of data. And this capability is referred as one of the grouping function.

Let's look into some of the metric namespaces, specifically, for DevOps. The oci_devops_code_repos is a namespace, and it gives you metrics to monitor the total number of code repositories, the number of push and pull executed on those code repositories, and also, the total size of each repositories.

The oci_devops_build is another namespace, and it is used to monitor the build pipeline. For example, you can monitor the time taken by the build run, the number of times the build have succeeded or failed, et cetera. oci_devops_deployment is used for monitoring the deployment pipeline.

And here, you can monitor the time taken for each deployment or the number of times the deployment has failed its execution. Application dependency management or ADM is used to detect security vulnerabilities in application dependencies. So there are metrics for vulnerability dependencies and that are combined in a namespace called oci_adm. Then we have the oci_computecontainer instance providing you CPU and memory in use, both in percentage and in terms of actual resources.

Now, there are hundreds of metrics that are emitted from different cloud resources. And it becomes difficult to remember each and every metric. So this lesson is more focused on the concepts of monitoring surveys and referring some of the examples used in a DevOps process. Alarms is one of the core concepts in monitoring. And this enables you to configure alerts and notifications.

The diagram here represents the workflow. You have configured a DevOps project. The monitoring service collects metrics as raw metric data. We then choose the metric namespaces for oci_devops_build and oci_devops_deployment to aggregate this data. There are three alarms created from three different matrices from these namespaces.

The first one is the build execution time. And if it goes beyond 60 seconds, it should trigger an alarm. The second alarm is for reporting build success and the third alarm for any deployment failures. When the alarm state changes from OK state to a firing state or even from the firing state back to the OK state, it sends a notification message with a topic, which has an email address configured as a subscription.

There are also other destinations in the notification service like, for example, you can notify Slack channels or sending to a pager duty or texting an SMS message and so on. Similar to the notification service, monitoring is also integrated with the OCI streaming service so that it can send these alarm data into a configured stream.

There are multiple components involved in creating an alarm query. To define an alarm query, you must specify the metric, the statistic, interval, and the trigger rule. Alarms have different states once you have created them. The OK State means the alarm is not in firing state. Firing means the alarm state has been changed from OK to Firing.

Reset is when the alarm is not detecting any metric firing or maybe the metric is no longer emitted. Repeat is referred when the alarm is maintaining a firing status and you have configured to repeat notifications to those destinations. Suppression is another configuration used to avoid publishing messages during a specified time range.

This is usually useful to suspend alarm notifications during a system maintenance time. To wrap up, we looked into an overview of the monitoring service, the key concepts of using metrics and alarms.

![image](https://github.com/qriz1452/oci/assets/112246222/912bb5c9-e62a-47dd-acf2-e473c5f7144a)


![image](https://github.com/qriz1452/oci/assets/112246222/623a036e-c0f9-489a-ba96-474d4958b902)


-------------

 Monitoring Queries


Monitoring Query Language, or MQL, is a simple, powerful language that enables users to query metrics and create alarms based on specific conditions. There are two modes in the OCI Console where you can create these queries, the basic mode or the advanced mode.

MQL expressions are a set of components that use a syntax-based structure. And the main purpose of these MQL expressions is to search for specific metric data points and aggregate them. The queries in the form of expressions are visible only when switching into the advanced mode of the service.

You will have to follow the MQL syntax, which will go on these expressions for querying metrics. So an MQL expressions have a set of components. The first component is the metric. We saw metric is a measurement that is related to the resource in the query. The statistic is a function applied to convert a set of raw data points into an aggregated data.

The interval is used along with the statistic function. And it is the time window at what intervals the data should be aggregated. Dimensions is an optional component. And it can be used as a filter for the aggregated data. Grouping function is another optional component. And it is also used for aggregation. And then finally, the comparison operations, it is used for defining alarms. And it is one another optional component.

We will look at the query components in details with reference to a few examples. And these are some of the metric namespaces and metrics that are part of each namespace. Now, it is difficult to remember the exact name of each metric. But just try to understand the different classifications and the purpose of using metrics in a metric query.

Each metric represents a unit. For example, the BuildSuccess metric is measured in count. So it refers the number of times that build have succeeded. And the same way, BuildFailures refers to the number of times that build has failed. The BuildRunExecutionTime is measured in seconds. And it is the amount of time taken by the builds.

There are metrics for monitoring the CodeRepository, DevOps deployments, and then the oci_containerinstance with metrics for CpuUtilization and MemoryUtilization that is measured in percentage. The CpuUsed metric is a metric that is measured in total virtual CPUs, and MemoryUsed, in total bytes of the memory that is in use.

Interval is a time window used within a time range of the query. So what this means, for example, you have provided a start date and an end date for the query. And you wanted to look for the maximum reported utilization of a resource every 5 minutes. So you choose 5 minutes as interval.

The values provided for the interval would depend upon the specified time range in the metric query. There are more interval values supported for smaller time ranges. The interval can be specified through the basic mode or advanced mode. With the basic mode, you can choose 1 minute or 5 minutes or 1 hour.

With advanced mode, there are further options, like you can provide a range like 1 minute to 60 minutes, or 1 hour to 24 hours, or even one day. Dimensions are optional qualifiers that can be added to corresponding metrics.

Grouping function is another optional component you can use to group or combine metric data by using grouping function. Statistic is one of the core component in a query, for example, whether a resource is absent or measuring the average, or count, or the minimum utilization of a particular resource. Comparison operators are used for defining alarms. You can specify if the statistic is greater than a value or equal or not equal to a value.

Here are some example sample queries along with the syntax to use. The syntax of a basic query starts with a metric, the interval, which is in square brackets, and then followed by .statistic function. And all of these components are mandatory to form a query.

An example shown is the BuildSuccess metric. 5 minute is the interval. And the statistic used is a sum. This query returns the total successful build pipelines completed at every 5 minute interval of the selected time range window.

In the next query, we are using dimensions with providing a dimension name and a dimension value. In the example, we use deployment failure as the metric, the interval as 5 minute. Dimension is the project ID with the value of the project's OCID, followed by the statistic sum. This is creating for the total failures in the deployment pipeline in every 5 minutes.

In the third example, we are introducing the grouping function. And using the metric CPU utilization, we are looking at the number of hosts with a utilization greater than 80%. This is also referred as a nested query, which means you have multiple embedded queries. And these are typically used with creating alarms.

Finally, the last example, this is another nested query. We are listing a grouping function inside the query. The metric in the example is the success rate. And we are looking at the number of availability domains with a success rate lower than 0.99. 

![image](https://github.com/qriz1452/oci/assets/112246222/724d02fc-4069-4185-96e8-ad65d9d5d973)

![image](https://github.com/qriz1452/oci/assets/112246222/2f010748-38c8-4319-87e6-6038ae77ee29)

![image](https://github.com/qriz1452/oci/assets/112246222/7ade60fb-b9c0-4323-a7d5-bd9a12be3179)


---------


Logging Service


Oracle Cloud Infrastructure logging is a highly scalable service, part of observability and management. And it provides a fully managed single pane of glass window for all the logs in your tenancy. Now, to define log, a log is a first-class OCR resource that stores and captures log events that are collected in a given context, like security operations.

The logging service provides a centralized management for all the logs in your tenancy, and it can aggregate all logs from sources like OCI services and displayed in a unified console. Logging provides access to logs collected from different OCI resources, like the compute instances, Virtual Cloud Network, or VCN, object storage, et cetera. These logs include critical diagnostic information that describes how resources are performing and being accessed.

As the log file contains sensitive information and data relating to security, for example, the traffic flow patterns, user activity authentication, the service provides a secure management for audit, infrastructure, database, and application-related logs. There are different ways you can access these logs. You can access and search using the OCI Console, SDK, and REST API.

You can run rule-based actions on log events like taking an action on specific log events. Logging service has a feature called Service Connector that will move logs to other destination like monitoring, so you can create alarms on log events or moving logs into object storage or any other third party tools.

A log group is defined as a collection of logs stored in a compartment. So when you enable a log for a resource, you would also need to create or specify a log group. Log groups are logical containers for logs. Using log groups, you can streamline log management like you can segregate the logs into different log groups based on various purposes. And so you can quickly navigate into the log for better results.

Logs and log groups are searchable, actionable, and transportable. This means you can move the log groups, let's say, from one compartment to another. And all the logs contained in the log group would move along with it to the new compartment. Using the log group, you can limit access to sensitive logs with enabling IAM policies. And so you don't have to rely on complex compartment hierarchies to secure your log information.

For example, the default lobby group in a single compartment is where you store the logs for the entire tenancy. You then grant access to the compartment for log administrators with IAM policies. Let's say some projects contain Personally Identifiable Information, or PII. And those logs need to be viewed only by a selected group of log administrators. Log groups allow you to put such logs that contain PII into a separate group, and then use IAM policy to restrict access to all, but providing access to a few log administrators.

Logging service classifies logs into three different types. One of the most important log type in a security context is the audit logs. Audit logs are log events emitted by Oracle Cloud Infrastructure or its service. These events are REST API actions executed by any OCI resource like a user or a cloud service. These logs can be accessed from the console and available in the audit page under Logging Service.

The second category of logs is the service logs. These are logs emitted by the native OCI services, like the DevOps service, API gateway, object storage, VCN, et cetera. Each of these services has got predefined logging categories that you can enable or disable on your respective resources.

The third type of log is the custom logs. These are logs that contain diagnostic information from custom applications that are running on Oracle Cloud Infrastructure, or other cloud providers, or even resources running in an on-premises environment. Custom logs can be ingested through the API or configuring the Unified Monitoring Agent.

Let's look into some of the concepts logging service. Service Log Category-- OCI services provide log categories for different types of logs that are available for resources. For example, the object storage service supports load categories like the read and write access events for storage buckets. The read access even captures all download events of that bucket. And write access events captures all right or upload events on that bucket.

Each service can have different log categories for resources. The log categories for one service is independent, which means it has got no relation to other log categories of another service.

The Service Connector Hub is a feature that allows you to move logging data to other services in Oracle Cloud Infrastructure. For example, you can use the hub move to log data to monitoring and set up an alarm, or sending log data into your database or object storage for archive purposes.

The Unified Monitoring Agent is a fully managed agent, and it is used to ingest custom events from your applications. Logging service uses the fluentd-based agent, which is an open source data collector based on the Cloud Native Computing Foundation, CNCF project. And it can be used to configure to run on compute instances for ingesting logs. The Agent Configuration page of Logging Service provides the configuration for this Unified Monitoring Agent, and it specifies how the custom logs are to be ingested into the logging service.

Logging service also provides features to view the filtered log data. You can visualize the data with chart widgets. You can choose stacked bar chart or pie chart, donut type, or line chart. The chart can be updated with choosing a time interval, and also selecting a logging field to group the results. The log data that is searched, filtered, or visualized can be auto-refreshed for every five minutes or 15 minutes to view the most recent logs in real time.

We will look into a log content generated by the OCI DevOps service. Service logs for DevOps projects can be enabled through the OCI Console. You would need to choose a compartment to store the log, provide a log name, a log group, and the retention period, which is between month to six months to store the logs.

Here is an example of the deployment log. The log construct is in JSON, and it contains certain fields. The spec version is the schema version of the OCI Logging Service. The type, which is the category of the log, some of the possible values are build or deployment.

The source is the name of the project where the log is associated to. It could also be an ocid1. For example, the ocid1 of the build pipeline to which the log belongs to. Subject is the ocid1 of the target resource where the deployment is getting executed.

Some of the possible values here are an instance, function, or a cluster. id is a random UUID, and it is unique to each log entry. time is when the log was generated in the DevOps service.

The next set of entries is contained within the section Oracle. So we could also refer as Oracle dot logid, which is the ocid1 the service log object. Loggroupid is the ocid1 of the loggroup. tenantid is the ocid1 of the tenancy. compartmentid is the ocid1 of the compartment that the loggroup belongs to. Injestedtime is the time the log was ingested by OCI logging service.

The next few entries are within the data section. So data dot deploymentId is the ocid1 of the deployment for which the log message is associated. deployPipelineId is the ocid1 of the deployment pipeline. deployStageId is the ocid1 of the deploystage.

The message contains the DevOps service log message. Data producer is the producer of the log message. It can be produced by the DevOps service code, or by scripts run by the customer during the deployment.

Once the logs are collected, the next step is to search the log that you're looking for. OCI logging service provides a powerful search engine tool to filter indexed logs through the console, CLI, or APIs. You can search logs based on custom queries.

There are multiple filtering options. Can filter values by log fields, search by a text or a keyword, or filter by time intervals. Each log entry can be explored in details. We can find these details with expanding the log line section and view the entire payload, which is structured in JSON format.

You can also access the Before & After View. And that shows the exact proceeding of the log entry, along with the successive logging lines in the log object. And finally, you can export these search results based on the filtering criterias into a JSON file.

There are some IAM policies required to gain access into the logs. To manage load groups or objects, the following allow policies can be created for each group. In these three examples, the policies are created for groups named as A, B, and C.

We use the verbs use, manage, read, and that is applied to the compartment named as X. To allow instances to push the logs, the instances need to have access to a configuration from the compartment. The log-content controls the permission. And in this example, it is applied to a compartment, which is having those configurations.

To view logs in the Search Console, the following allow policy is required. These are two policies that are required to allow the group to read the log group and contents of the index logs at the tenancy level.

Let's look into the end-to-end service flow of logging service, starting from collecting and managing the logs from different sources. There are different types of logs collected-- the service logs from OCI Cloud Services, audit logs, and then custom logs from your application, security 11 logs which are collected and ingested using different methods.

The second stage is where you gain access into the logging service. Search and filter for the logs that you're looking for and run analysis based on the search results. In this stage, you would also configure service connected to send the logs to other services.

In the third stage, you can take actions based on the previous stage. You can write into the streaming service or invoke an Oracle function as an action. Or you can write into an object storage bucket. 


![image](https://github.com/qriz1452/oci/assets/112246222/40723254-b920-47ed-a974-e4d0118e0022):


----------

: Events Service


Oracle Cloud Infrastructure or OCI consists of several infrastructure cloud services that enables you to build and run a wide range of applications and services in a highly available hosted environment. There are more than 80 cloud infrastructure services that produces events along with more than thousands of different event types, which you can then configure one or more rule conditions to trigger actions on any of them.

OCI events is defined as a service that allows you to create automation based on state changes of resources throughout your tenancy. And so with using events, you can enable your DevOps teams to automatically respond when a resource state is changed. An example would be you can send a notification to the team or trigger a function or script to take the next set of action.

In a DevOps project, code repositories are one of the key components in a CI/CD workflow. And it helps you to store or host the source code, including any software binaries. Developers are continuously committing code changes into this repository. And so the OCI DevOps Service emit events that are related to the changes happening to the code repositories.

The next stage is the build. The service emit events which could be related to the build process, the build run, or staging, et cetera. Or it could be with the deployment stage. Events are generated with several operations within the deployment pipeline. OCI Events Service generates events for such service operations, and it is in the form of JSON files that carries information about that specific operation.

Some of the operations indicate the changes occurred within a resource. For example, it could be a create, read, update, delete operation. Or call it as a CRUD operation. Or it could be a life cycle state change of a resource. We can get visibility across the full development life cycle with a history of the source commit through build, test, and deployment phases. There are also system events generated that could be impacting a resource. An event is emitted when a backup completes, or if the backup operation fails, or when a compute instance is created or deleted, or let's say a file in the object storage bucket has been added or updated or deleted.

You work with events by creating rules for a resource type and then restricting further by defining additional filters or tag names that match only certain events. And so these rules can be referred as customer-defined rules. Rules should also specify one or more actions to trigger when the event occurs.

Actions can include sending an event to the streaming service which is used for ingesting and consuming high volume of data streams in real-time. Or you can invoke an Oracle function, which is the serverless platform that lets you create, run, and scale applications without managing an infrastructure. Or it could be sending to a topic with subscriptions of a notification service.

So to summarize what we covered so far, there are three main concepts in the event service. Number one is the event. Event is a structured message in JSON format. And it represents a change in an OCI cloud resource initiated either by the OCI system or executed by a user. Events are represented as well-formatted messages that defines what is the event, where the event is originated from, and other metadata that you can use for analyzing the activity.

The next concept is the rules. A rule is another JSON object or configuration filters that you can create and subscribe to an event type and then trigger an action when that particular event occurs. Rules can filter all incoming events with one or more field values. And then based on the rule definition, you can decide what actions to take on that event.

The third concept is actions. An action is specified for the rule to trigger when the filter finds a matching event. And so actions are those responses that a user would define when an event rule condition is matched. Rules can have one or more actions defined to be executed when they are triggered. There are predefined set of actions that you can choose to be executed. As we saw previously, you can use services like the notification service, streaming, or Oracle functions to create actions.

Let's take a deeper look into an event. An event is a structured, lightweight message that denotes the change in a resource. Events have a derived context with a structure, and it is guaranteed to be actionable and even can be a user-initiated CRUD operation, like an object storage bucket is created or a bucket is updated or deleted. It could also reflect a life cycle state change in a resource like a compute instance is stopped, or the instance is launched, or a backup is starting. Or it could be an OCI system event, such as a hardware failure.

So what are the constructs that forms together an event? Each event has an envelope that is the container for all event messages. And it follows the cloud event standard format.

This envelope includes the event source, which is the OCI service that generated the events, such as the DevOps project, object storage, or compute. It also include an event type and the timestamp for when the event occurred. The event also have an inner payload that contains the service specific data to describe the change occurred in the resource, including any tags that are associated to the resource.

Let's look into some of the event types of the DevOps service. Event messages use a combination of an event type and a data payload from the resource to identify state changes. So, essentially, event types are organized by the service and by the resource type.

There are several event types in the DevOps service and for the resources that are part of it like for the DevOps project, deployment artifacts, code repositories, collections, the target environments, build pipeline in stages, build run, trigger, and finally for deployments. For example, with looking into the build pipeline, there are different events for each operations like the create build pipeline begin is when a build pipeline creation is initiated. And create build pipeline end is when it gets complete. Similarly, when a pipeline is updated or deleted, the service provides you events from the time the task was initiated and then it was complete.

Application Dependency Management or ADM is a feature that automatically discovers and maps dependencies between different components of your applications. And knowledge base is a key concept in ADM and these are some of the events related to the knowledge base. For example, there are event types with creating, updating, and deleting knowledge base. A vulnerability audit describes the vulnerabilities of your applications and its dependencies. Similar to the knowledge base, there are event types with creating, updating, and deleting vulnerability audits.

What does an event look like? Here is an example event, which is in JSON format. There are common attributes in the event envelope, which are the same across all the events, and it includes the event type, the source, and event time.

The data payload will depend upon which OCI service that produced the event, along with the specific event type. It defines more details. And in this example, the event was from the DevOps project for the type createproject.begin and the resource named my test resource project was created under the given compartment and availability domain.

We looked into some of the event types. And here are some of the operations that you can match and trigger a rule to run the next set of actions. For example, when a DevOps project is created, updated, or deleted, a deployment artifact is created, updated, or deleted. A code repository is created, mirrored, updated, deleted, or listed. A connection is created, updated, or deleted. A deployment environment or the target environment is created, updated, or deleted.

A build pipeline or a build pipeline stage is created, updated, or deleted. A build run execution is created, updated, or deleted. A trigger is created, updated, or deleted. A deployment pipeline and a deployment pipeline stage is created, updated, or deleted. And, finally, a deployment is created or updated.

Let's now look into rules, which is another key concept of the event service. Rules are defined as OCI objects. And to interact with the event service, you should always create and manage rules. Rules are the configuration that would allow you to select which event types to be monitored, secondly, which particular resource or resources are to be filtered and to be monitored, and, finally, automatically trigger one or more actions when those events occur.

So to create a rule, you would specify a name for the rule and the compartment where you want it to be created. Rules are supported for nested compartments. So if you want to set up a tenancy wide rule, you could create a rule in the rule compartment. The next step is the trigger condition, which is the event types along with any other property filters. Like you could filter using tags or any other condition criteria, for example, a condition where if an object storage bucket has been deleted that has a tag production don't delete.

The response action is about what to be executed once the trigger condition has been met. We can have multiple actions for each rule. For example, you can choose to notify a user on a Slack channel through the notification service and also trigger a function call that will execute the backup scripts. OCI events metrics enables you to monitor performance of your rules by using metrics and alarms of the monitoring service.

The events metrics measure the success of those rules you have created with matching the patterns delivery, the quality, and scope of the emitted events in your tenancy. For each rule, there are three key metrics, the total number of events that were matched by that rule, how many were successfully delivered into the corresponding actions, and also the failed deliveries by a rule. You can also view these metrics in the telemetry dashboards and see how the rules are behaving. You can also view the total number of events that were emitted by all resources in an entire compartment.

Here is an example with an end-to-end workflow of the events service with an action. We start with the request to provision an Oracle Autonomous Transaction Processing Database instance. And once the provisioning succeeds, a create instance and event is received by the events service.

Now a rule has been created on that event, which then triggers an action to invoke Oracle functions. That function contains the logic to run scripts to create schemas and tables and import the golden data into the newly provisioned ATP instance. At the same time, another action is triggered through the notification service which both sends an email to an administrator as well as creating a PagerDuty incident.

We will now look into some of the core use cases of the events service. Automate Cloud Operations. As a DevOps engineer, you can automate the end-to-end provisioning workflows or use automation for your scaling requirements or for security and tagging of cloud resources. Simplify Cloud Governance. By integrating events with other services like OCI functions, you can better protect the entire cloud infrastructure estate. You can use functions for creation and deletion of an instance that violates security guidelines or use it for updating the route tables, security list, et cetera.

Build Events-Driven Microservices and Serverless Applications. You can also use events service with functions for a faster events-driven serverless application development. Gaining Insights into Security Operations. Security operations can use events with services like streaming to route events to security incident management systems for deeper analysis. 

![image](https://github.com/qriz1452/oci/assets/112246222/f6d6f51a-1819-4c11-b48e-32783903ca00)

![image](https://github.com/qriz1452/oci/assets/112246222/f73ec63f-5bc3-4d95-9b7c-1c02c9768926)

![image](https://github.com/qriz1452/oci/assets/112246222/50c90e10-9fcc-4b93-99ea-077df874ade6)

![image](https://github.com/qriz1452/oci/assets/112246222/1316e4bb-f4fc-449b-9f6b-23f5536c581d)


-------





















 





























