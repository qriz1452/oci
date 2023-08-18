Now Playing : Monitoring and Troubleshooting Cloud Native Applications




several OCI services that can help facilitate troubleshooting for the OCI Cloud native developer, at a minimum, you'll be wanting to learn more about, and leverage the capabilities of, the OCI monitoring, logging, and APM services. In addition, there are numerous open source libraries, tools, and services that we recommend you consider for monitoring, troubleshooting, and debugging, depending on your requirements and preferences.

So allow me to highlight the lesson topics and demonstration videos you'll discover in this training module. We'll start with a full overview of the OCI monitoring service and how it can be leveraged to collect metrics for most OCI resources, to include the services you'll use for Cloud native deployments, such as serverless functions, OKE, and API Gateway. Likewise, the following lesson provides an overview of the OCI logging service, to include not only the ability to capture both service and custom log data, but features which allow you to search and analyze and dynamically execute downstream actions, based on that data.

We then launch into a series of demos, this one showing the built-in Oracle function metrics as well as enabling function logs. This demo shows the API Gateway deployment metrics and how to enable and view gateway log messages. And finally, this one, which shows not only built-in OKE metrics and viewing OKE audit logs, but how you can add custom logs to capture application log messages.

Next, we transition to APM, starting with a brief overview into the comprehensive capabilities of the Application Performance Monitoring service, followed by this demo, which shows how to provision a new APM domain, as well as enabling and using tracing for Oracle functions. Then, in this demo, we further explore configuring APM tracer and browser agents, and adding traces and spans within the application code.

Then, in this final lesson, we'll see an example of using an open source debugging service, Rookout, for troubleshooting a container application written in Java. And while all video lessons and demos in this module will provide excellent information on these topics to get you started, be sure to also explore the OCI online documentation and Help Center, as well as the Oracle Developer Resource Center for Cloud native. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/ccff41da-d0c9-4686-a442-5dfd61ad1bba)
![image](https://github.com/qriz1452/oci/assets/112246222/2a7f5c56-f8eb-42a5-b90f-765a7abd90b8)



--------
Now Playing : Monitoring

OCI Monitoring is part of Observability and Management Service. There are different use cases and features that would allow you to integrate the Monitoring Service with other services of Oracle Cloud Infrastructure. Let's look into some of those features.

The very first feature is that it enables you to actively and passively monitor cloud resources from Oracle Cloud Infrastructure or external resources with having integration with services like the Service Connector Hub. The Monitoring Service users a concept called Metrics to monitor resources. And another concept of Alarms to notify you when these metrics meet alarm-specified triggers.

You can access Metrics and Alarm data using different ways using the OCI Console, CLI, Command Line Interface, or using APIs. Metrics are emitted into Monitoring Service as raw data points or it could be timestamp value pairs with filters like dimensions and metadata. We will look into these terminologies in the next slide.

The alarm feature of Monitoring Service publish the alarm messages which can be configured to destination managed by the Notification Service. In the Notification Service, each destination is referred as a topic, which is the channel for communicating those messages to a subscription, and the subscription is an endpoint for the topic.

Let's look into some of the key concepts of Monitoring Service. A Metric is one of the key concept. And it refers to a measurement that could be related to health, the capacity or performance of a given resource. In a security context, metrics are also highly used for troubleshooting requirements like having an aggregated view for all the dropped packets by a security list.

Within the Metric, there is a Metric namespace, which is an indicator of a resource or a service or an application that is emitting the metric data. For example, there are metric definitions emitted by Oracle Cloud Agent Software on compute instances, and that corresponding metric namespace used would be the OCI Compute Agent.

Metric definition is a set of references, qualifiers, and other information provided by the above metric namespace for a given metric. Dimension is referred as a qualifier in the metric definition. For example, the resource identifier or resource ID is a qualifier in the definition of OCI Compute Agent Metrics and it is used to filter the data based on specified resource ID.

Metadata is another type of reference in the metric definition. For example, the unit mentioned in bytes is provided in the definition of OCI Compute Agent for the metric disk bytes read.

A Data point is a timestamp value pair for the specified metric. It can be either raw or aggregated. Raw data points are posted by the metric namespace to the monitoring service using an operation called Post Metric Data Operation. Aggregated data points is created from raw data point with applying certain functions.

Statistic is one such aggregation function applied to the given set of raw data points and the aggregated data becomes the result of applying a statistic and interval to a selection of raw data points. Metric stream is an individual set of aggregated data for a metric. A stream can be either specified to a single resource or aggregated across all the resources in a compartment.

The Alarm is the feature that uses the alarm query to evaluate and the destinations to be notified when the alarm is in firing state. The Alarm Query is written in Monitoring Query Language, or MQL expression, which will run the evaluation for the alarm.

Frequency is the time period between each posted raw data point of a given metric. Frequency can vary based on the metric. The default service metric typically have a frequency of 60 seconds, which means one data point is posted in every one minute.

The Interval is the time window used to convert a given set of raw data points. The Resolution is the period between time windows or the regularity at which the time windows shift. For example, you would use a resolution of 1 minute to retrieve aggregations every minute.

Trigger Rule is the condition that must be met for the alarm to be in the firing state. Notification Destination is the notifying protocol along with other details for sending the messages when the alarm transitions into another state. The Message is the content that alarms feature publishes to those configured notification destination.

Resource Group is a custom string with a custom metric that can be used as a filter to aggregate your results. Suppression is a configuration that can be used to avoid publishing messages during a specified time range. This configuration is used for suspending alarm notification, let's say during your system maintenance.

Here is an end-to-end workflow of Monitoring Service, starting with the metric collection followed by the notification through the alarms feature. Metrics are collected from a variety of sources, like it can be automatically posted by Oracle Cloud Infrastructure services like the compute Autonomous Database, et cetera.

It can also be using the custom metrics publish using the monitoring API or the data sent to the new or existing metrics using the Service Connect Hub. In this example, we are looking at the compute service post metrics, like the CPU utilization, elected through the OCI Compute Agent namespace from those monitoring enabled compute instances.

As we saw previously, metrics are emitted into Monitoring Service as raw data points or timestamp value pairs. When you query a metric, the Monitoring Service returns the aggregated data according to the specified parameters. You can specify a range like the last 24 hours, statistic, and interval to collect those aggregated metric data.

This data can be accessible from the OCI Console or using APIs, SDK, CLI, or even using customers' third-party monitoring applications. OCI Console shows the monitoring charge per metric for the selected resources. The aggregated data in each of those charts will be based on your selected statistic and interval.

The alarms feature notify you when the metrics meet alarm-specified triggers. Given this example, with alarms feature, you would create a condition for which the CPU utilization is greater than 80%, it triggers the alarm. The Monitoring Service would then publish the alarm messages to those configured destination, which are managed by the Notification Service.

The Metrics feature relays metric data that is collected from your cloud resources. And so, metric is defined as a measurement that could be related to the health, the capacity, or performance of a given resource. By creating for this data, you can get to know how well the systems and processes are working, and so you can achieve the service levels that you commit to your customers.

There are several service metrics that you can choose from the Metric namespace dropdown like the oci_blockstore, metrics that provides the overall oci_compute_infrastructure_health, logging, compute agent, objectstorage, service_connector_hub, and oci_vcn.

For example, with choosing the oci_computeagent namespace, you can monitor the CPU and memory utilization or the disk throughput or the network throughput with transmit or receive bytes from your compute instances. You can use this data to determine when to launch additional instances or use it for troubleshooting issues with your instance or for a better understanding of your system behavior.

The metric query can be composed of three attributes that you can choose when creating a query, the Namespace, the Dimension, and the Metadata. We saw the Namespace is an indicator of the resource type or it could be a service or application that is emitting the metric data. The Dimension is used as a filter or the qualifier like providing a specific resource ID. The Metadata is the quantifier, like for example, the total units in bytes for the disk bytes read.

The Monitoring Service also provides a metric explorer where you can dive into more details of a specific metric and it shows multiple resource metric together. The explorer can be used with a metric query language. And using this interface, you can create complex queries.

The Alarms feature of Monitoring Service works with a Notification Service to notify you when the alarms are triggered. The illustration here shows the flow starting with the resources, like the Compute, Database, Networking, or a custom application imaging metrics into the Monitoring Service.

An Alarm Query must have a metric, Statistic, Interval, and a Trigger Rule like setting a threshold or absence condition. When the alarm is triggered, the service sends an alarm message to the configured topic in the notification service, and from there, it sends the message to all the subscription like email, OCI functions, or tools that are using our HTTPS or a Slack channel or as an SMS text message.

There are three states for the alarm, Firing, which means the alarm is detected, Reset means the alarm is not detecting the metric firing or the metric is no longer being emitted, Suspended means the alarm is suspended or post.


![image](https://github.com/qriz1452/oci/assets/112246222/14a0bbdf-8d6b-4e07-8579-37bfef6950e9)

![image](https://github.com/qriz1452/oci/assets/112246222/71aadefa-39c6-41b8-a516-07efd700acee)

=========

Now Playing : Logging

Oracle Cloud Infrastructure Logging is a highly scalable service, part of Observability and Management. And it provides a fully managed single pane of glass window for all the logs in your tenancy. Now, to define log, a log is a first-class OCI resource that stores and captures log events that are collected in a given context, like security operations.

The Logging service provides a centralized management for all the logs in your tenancy. And it can aggregate all logs from sources like OCI services and display it in a unified console. Logging provides access to logs collected from different OCI resources, like the Compute instances, Virtual Cloud Network, or VCN, Object Storage, et cetera. These logs include critical diagnostic information that describes how resources are performing and being accessed.

As the log file contains sensitive information and data relating to security-- for example, the traffic flow patterns, user activity, authentication-- the service provides a secure management for audit, infrastructure, database, and application-related logs. There are different ways you can access these logs. You can access and search using the OCI console, SDK, and REST API.

You can run rule-based actions on log events, like taking an action on specific log events. Logging service has a feature called Service Connector that will move logs to other destination, like Monitoring so you can create alarms on log events, or moving logs into Object Storage or any other third-party tools.

A log group is defined as a collection of logs stored in a compartment. So when you enable a log for a resource, you would also need to create or specify a log group. Log groups are logical containers for logs. Using log groups, you can streamline log management. Like, you can segregate the logs into different log groups based on various purposes. And so you can quickly navigate into the log for better results.

Logs and log groups are searchable, actionable, and transportable. This means you can move the log groups, let's say, from one compartment to another. And all the logs contained in the log group would move along with it to the new compartment. Using the log group, you can limit access to sensitive logs with enabling IAM policies. And so you don't have to rely on complex compartment hierarchies to secure your log information.

For example, the default log group in a single compartment is where you store the logs for the entire tenancy. You then grant access to the compartment for log administrators with IAM policies.

Let's say some projects contain personally identifiable information, or PII, and those logs need to be viewed only by a selected group of log administrators. Log groups allow you to put such logs that contain PII into a separate log group. And then use IAM policy to restrict access to all but providing access to a few log administrators.

Let's look into some of the concepts of Logging service. Service log category-- OCI services provide log categories for different types of logs that are available for resources. For example, the Object Storage service supports log categories like the read and write access events for storage buckets. The read access even captures all download events of that bucket. And write access events captures all write or upload events on that bucket.

Each service can have different log categories for resources. The log categories for one service is independent, which means it has got no relation to other log categories of another service.

The Service Connector Hub is a feature that allows you to move Logging data to other services in Oracle Cloud Infrastructure. For example, you can use the Hub, move the log data to Monitoring, and set up an alarm, or sending log data into Databases or Object Storage for archive purposes.

The Unified Monitoring Agent is a fully managed agent. And it is used to ingest custom events from your applications. Logging service uses the Fluentd-based agent, which is an open-source data collector based on the Cloud Native Computing Foundation, CNCF, project. And it can be used to configure to run on Compute instances for ingesting logs.

The Agent Configuration page of Logging service provides the configuration for this Unified Monitoring Agent. And it specifies how the custom logs are to be ingested into the Logging service.

Logging service classifies logs into three different types. One of the most important log types in a security context is the Audit logs. Audit logs are log events emitted by Oracle Cloud Infrastructure Audit service. These events are REST API actions executed by any OCI resource, like a user or a cloud service. These logs can be accessed from the console and available in the Audit page under Logging Service.

We have a dedicated lesson on Audit service. And I would highly recommend you to go through that lesson. And that covers further more details about Audit logs.

The second category of logs is the service logs. As the name states, these are logs emitted by OCI native services, like the API Gateway, Events, Functions, Object Storage, and VCN Flow Logs. Each of these services has got pre-defined logging categories that you can enable or disable on your respective resources.

We looked into the log categories of Object Storage in our previous slide. And similarly, you can choose the log category of flow logs for your VCN subnet that will collect all traffic patterns of TCP, UDP, or ICMP, along with other parameters like the source and destination of the request.

The third type of log is the custom logs. These are logs that contain diagnostic information from custom applications that are running on Oracle Cloud Infrastructure or other cloud providers or even resources running in an on-premises environment. Custom logs can be ingested through the API or configuring the Unified Monitoring Agent.

Once the logs are collected, the next step is to search the log that you're looking for. OCI Logging service provides a powerful search engine tool to filter indexed logs through the console. You can search logs based on custom queries. There are multiple filtering options and filter values by log fields, search by a text or a keyword, or filter by time intervals.

Each log entry can be explored in details. You can find these details with expanding the log line section and view the entire payload, which is structured in JSON format. You can also access the Before and After view. And that shows the exact proceeding of the log entry along with the successive logging lines in the log object. And finally, you can export these search results based on the filtering criteria into a JSON file.

Logging service also provides features to view the filtered log data. You can visualize the data with chart widgets. You can choose stacked bar chart, or a pie chart, donut type, or line chart. The chart can be updated with choosing a time interval and also selecting a logging field to group the results. The log data that is searched, filtered, or visualized can be auto refreshed for every five minutes or 15 minutes to view the most recent logs in real time.

There are some IAM policies required to gain access into the logs. To manage log groups or objects, the following Allow policies can be created for each group. In these three examples, the policies are created for groups named as A, B, and C. And that is applied to the compartment named as X.

To allow instances to push the logs, the instances need to have access to a configuration from the compartment. The log content controls this permission. And in this example, it is applied to a compartment X which is having those configurations. The view logs in the search console, the following Allow policy is required. These are two policies that are required to allow the group to read the log group and contents of the indexed logs at the tenancy level.

Let's look into the end-to-end service flow of Logging service, starting from collecting and managing the logs from different sources. There are different types of logs collected-- the service logs from OCI Cloud Services, Audit logs, and then custom logs from your application, security-level logs which are collected and ingested using different methods.

The second stage is where you gain access into the Logging service, search and filter for the logs that you're looking for, and run analysis based on the search results. In this stage, you would also configure Service Connector to send the logs to other services.

In the third stage, you can take actions based on the previous stage. You can write into the streaming service or invoke an Oracle function as an action. Or you can write into an Object Storage bucket.

![image](https://github.com/qriz1452/oci/assets/112246222/18ee42b5-acd7-4ef6-b9ca-12a90c238047)

![image](https://github.com/qriz1452/oci/assets/112246222/913c85ca-3d2c-4a9d-a06e-2def1a7ba21a)

![image](https://github.com/qriz1452/oci/assets/112246222/02ec32d7-09ed-469a-8944-d2d8b7479a77)

![image](https://github.com/qriz1452/oci/assets/112246222/0b4012e0-6509-421d-a079-c995529d283e)


---------

Now Playing : Application Performance Monitoring


It's an excellent tool for rapid troubleshooting. Basically, it gives you the availability to find issues quickly. It will provide you with visibility into the performance and availability of your applications and will allow you to deliver a consistent user experience. All of your end user and application performance information, along with the associated application logs, are brought together into a unified data set.

So let's take a look at the features. Distributed tracing service basically will allow you to monitor and alert. Getting automatic alerts on performance availability and load analysis will allow you to have consistent diagnostics and get insights into the application behavior. It enables DevOps teams to track every step of every transaction-- not sampling, not aggregation, of every transaction, of new and older applications running on OCI, on premises, or even on another public Cloud.

End user monitoring-- browser instrumentation enables the collection of data from browser to app. Session diagnostics traces each individual user session. And this combined with server side tracing. And user monitoring tracks the actual experience of each end user all the time, no matter where and how they access the application.

Synthetic monitoring-- so browser and scripted browser monitors monitors a single URL or created scripts. You can work with REST APIs. And this combined with server side tracing. The OCI advantage points execute the monitoring from multiple locations. So basically, synthetic monitoring is a proactive monitoring that helps developers and operators prevent issues before users are impacted.

Server monitoring-- basically, it will collect metrics from any component. AppServer metric collection collect metrics from Java virtual machines. And this will allow you to integrate with OCI monitoring and logging analytic services.

So application performance-- with the dashboard, customers can look to the actual dashboard for all the metrics that have been collected and calculate and drill down when they see any anomaly. So this is a wrap up. Thank you very much.


---






------













