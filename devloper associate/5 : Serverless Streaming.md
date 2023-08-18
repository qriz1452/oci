Now Playing : Serverless Streaming: Introduction

where I mentioned the case study workshop which uses this VisionStays cloud native reference architecture.

After the primary logic of the application microservices has been implemented, later in the workshop we leverage a stream. Thus, the scope of this module is to learn more about the capabilities, features, and use cases for using serverless streaming, specifically the OCI streaming service.

The use case for the hands-on workshop will be to add logic to the Booking microservice to publish messages when those new hotel bookings are made which could later be consumed by one or more downstream applications. Once again, as a reminder, after you've watched the videos in this module, you'll want to look at the streaming solution in the workshop to experience that use case example.



![image](https://github.com/qriz1452/oci/assets/112246222/8ba1dc9e-8579-47ad-b087-5e877ea023a5)

-------

Now Playing : Streaming: Introduction


The distributed nature of Cloud applications requires a messaging infrastructure that connects the components and services, ideally, in a loosely coupled manner in order to maximize scalability. So then, clearly, a synchronous messaging models are now widely used instead of relying on older, more traditional request-response synchronous communications. And these provide many benefits. But also bring challenges, such as the ordering of messages, poison message management, item potency, and other issues.

Here we see three additional options. A queue like a buffer operates so that any given message is only consumed by one receiver. Although, multiple receivers can be connected to a queue. A topic, on the other hand, is like a broadcasting station. In that, once you publish messages to a topic, anyone interested in those messages can subscribe.

So in this model, all published messages are immediately received by all the subscribers of the topic unless you've applied a messaging filtering pattern. However, a real time distributed data streaming solution provides some additional advantages beyond just queues or topics. These are most useful for systems such as financial processing, internet of things and real time maintenance solutions. For instance, the processing of financial transactions requires real time messaging to block fraudulent transactions as they occur.

Another great example is within the emerging world of IoT devices. Consider a large office building with many rooms. Each with many devices, for example, smoke detectors. These devices are linked to a central server and send messages to the server. So what happens, if one of the detectors picks up the start of a fire? The device sends a message to the server. Requiring it to open the fire suppression sprinklers in that room. Now if the server takes too long to receive process and respond to the message, the fire could quickly spread causing untold harm, including the loss of life.

So by way of contrast, typical messaging systems such as JMS are not near as real time. While the messaging processing is asynchronous, it also uses an explicit imperative programming paradigm which can be substantially slower as opposed to processing streaming data. Which leads us to Apache Kafka, which has certainly emerged as a de facto standard distributed streaming data processing platform.

A little bit of history here, Kafka was originally developed and LinkedIn in 2011. And since its emergence source emerges a year later, it has improved a lot since then. Today, it's a whole platform allowing you to redundantly store tremendous amounts of data. Have a message burst with huge throughput. I'm talking millions of messages per second. And use real time stream processing on the data that goes through it all at once.

So then, why does this lesson, so far, sound like a commercial for Kafka? Well, in a way, it is. However, even when deploying a Kafka platform cluster to a Cloud Service provider, such as AWS or even Oracle, there are still numerous operational and management challenges. Such as the load balancing of topics between nodes, patching the operating systems and zookeeper management, handling high availability, ensuring in data encryption as well as handling authentication and authorization.

Which now leads me to this, so what is the OCI Streaming Service? Essentially, you get all the benefits of Apache Kafka without the management overhead. OSS is a serverless enterprise grade Kafka-based distributed streaming platform, which is really differentiated on its operational cost and performance.

Let's dive in a bit deeper. Partially, because this is a serverless platform, you eliminate the maintenance and patching of software online. And you have greater ease of operations as it integrates directly with OCI monitoring and other core services.

Additionally, you don't pay for provision, the capacity. You pay only for the usage based on simple and minimal pricing dimensions to include no additional cost or data transfer. And perhaps, most importantly, it scales both out and back in as needed on demand while providing built-in fault tolerance since it replicates data across availability domains within an OCI tenancy region.

So the key here is that this is not just a proprietary streaming service. While you can produce and consume messages using our native API, OSS is compatible with most Kafka APIs. Allowing you to use applications for Kafka to send messages to and receive messages from the streaming service without having to rewrite your code. Which means that current Apache Kafka users can offload the set of maintenance and infrastructure management that hosting your own zookeeper. And Kafka cluster is required which is sort of the best of both worlds.

To extend Kafka interoperability even further, you can also leverage Kafka's mirror maker tool which allows you to consume records from a source Kafka cluster topic and copy them to a destination cluster stream on OCI streaming. For example, you can mirror data from Kafka clusters hosted on premises or on other public Clouds to OSS. Or use mirroring to enable cross region disaster recovery of streaming data by replicating data between regions.

So to wrap up this introductory lesson, OCI streaming provides a robust and scalable distributed streaming solution while providing for Kafka interoperability and messaging framework capabilities.

![image](https://github.com/qriz1452/oci/assets/112246222/1c2ba9e1-78d3-4a90-9f26-b322fc57c12d)
![image](https://github.com/qriz1452/oci/assets/112246222/61bdbbe9-ca9f-4bb6-84c1-91531fd140f0)

![image](https://github.com/qriz1452/oci/assets/112246222/ad7066a3-de19-4ce2-b87c-ae89a3a68b38)
![image](https://github.com/qriz1452/oci/assets/112246222/32d5ddcb-6589-4019-9145-fe96fce1cca7)

![image](https://github.com/qriz1452/oci/assets/112246222/085c4d9f-d3fc-4c12-ba13-d684abc479b2)

----------

Now Playing : Streaming: Features

Let's start by discussing security and the OCI streaming service with regard to message security.

Streaming data is always encrypted both while in transit and while it is at rest inside OSS. Additionally, Oracle automatically applies security updates for the entire stack monthly or occasionally, off cycle, for high impact security vulnerabilities. Since it is fully integrated with OCI authentication and authorization, customers get fine-grained access control with OCI identity and access management policies.

Everything from the provisioning of streams, stream pools, and partitions to controlling who can produce and consume streaming data. Incidentally, Kafka users can use OSS Kafka endpoints and authenticate with plain SASL or Simple Access and Security Later API. For example, embedding the users off spoken password. Additionally, you could choose to enable a private endpoint for a stream pool. So that streaming traffic is routed to their streaming instances without traversing the internet.

This provides a private stream experience which completely blocks access to the stream resources from public endpoints. Again, by default, all encryption related matters are handled by Oracle. But you can manage your own encryption keys using OCI Vault which allows you to bring your own AES symmetric keys for you to manage rotate, disable, and delete them as needed in.

Because encryption keys are managed at the stream pool level, you could use a different encryption key for each logical stream grouping or virtual Kafka cluster. For reliability, the streaming service replicates data synchronously across geographically distributed availability domains. Automatically providing fault tolerance and greater durability.

OSS provides a service level agreement availability guarantee of 99.95%. So now, let's shift gears to briefly look at some examples of just how deeply integrated we have positioned the streaming service to include out of the box integration with hundreds of OCI services as well as numerous third party products.

For example, you can build serverless real time data processing pipelines leveraging OCI streaming and Oracle functions. You focus on creating streaming applications instead of managing infrastructure. And take advantage of concurrent processing by executing parallel data processing across all partitions in an OSS stream.

Essentially, collecting from various data sources upstream and properly responding to key message, business events, and operational triggers in real time. You can load massive volumes of streaming data into data lakes using OCI object storage and then run analytics.

This example provides for delivering streaming data directly to public storage without writing an application or managing infrastructure which can scale to match the data throughput without any intervention. Or expand the use case executing serverless ETL logic using Oracle functions to transform the incoming source data before sending it on to object storage.

This line introduces two-key integration capabilities. The OCI Service Connector Hub as well as a wide variety of connectors using Kafka Connect but more about those later. Leveraging the service connector, you could capture and stream OCI service application or audit logs available by way of the OCI logging service. And then analyze in near real time using your other existing systems or tools.

You could build sequences of events from the stream like user sessions and a click stream. Leveraging scalable and robust high throughput real time notifications pipelines. Perhaps, identifying events of interest and react to data through alarms and notifications without managing any infrastructure.

This example involves streaming change data captures or streaming data from Oracle applications that are located in on premises databases leveraging Oracle Golden Gate. You can even use the Oracle Golden Gate connector for Big Data to build an event-driven application. And in addition to supporting external clients that wish to use the OCI streaming service API, OSS can connect with hundreds of third party products using Kafka Connect framework as I mentioned earlier in the lesson.

So let's put this all together. Streaming can utilize the entire Kafka Connect ecosystem and Service Connector Hub to interface directly with databases, OpEx stores or any microservice on the Oracle Cloud as well as any number of external third party applications. Additionally, Kafka Connectors can easily and automatically create topics, publish or consume messages while taking advantage of the streaming services high throughput and durability.

Let me summarize this important capability. In addition to direct integration to certain OCI native services using service connector or using Oracle Kafka connectors for other Oracle services, there is a huge number of third party Kafka source and sync connectors you can leverage.

All of which are available on the confluent Hub website. So to wrap up, we've learned about key features for security and reliability. As well as overviewing the extensive number of integration capabilities to both Oracle services as well as third party systems and products.

![image](https://github.com/qriz1452/oci/assets/112246222/fb894c24-13eb-421e-ba61-039bedd78b6c)
![image](https://github.com/qriz1452/oci/assets/112246222/1cf90e73-112e-47de-a104-91b298cb01f2)
![image](https://github.com/qriz1452/oci/assets/112246222/645c0598-92e0-41a7-a1b6-e35b3dc736ee)
![image](https://github.com/qriz1452/oci/assets/112246222/b3a830ce-cdc3-434b-8a90-a5948603e740)
![image](https://github.com/qriz1452/oci/assets/112246222/4dbaf030-b824-4af3-92fb-c24cebf0a5d7)
![image](https://github.com/qriz1452/oci/assets/112246222/53cb2f87-f115-4464-8372-013fce092197)
![image](https://github.com/qriz1452/oci/assets/112246222/af1fbf7b-bd4b-4fb3-b861-f749ff9dfeae)
![image](https://github.com/qriz1452/oci/assets/112246222/26fcc462-7d85-44f7-90ec-c93bb9f4c37b)
![image](https://github.com/qriz1452/oci/assets/112246222/9bc68e5f-0058-4099-9590-c3985e9a8dda)
![image](https://github.com/qriz1452/oci/assets/112246222/56a1b28a-9e64-412e-a2d6-167196499983)
![image](https://github.com/qriz1452/oci/assets/112246222/58759b9c-e7a7-48ee-9f04-6ed9c34519d0)
![image](https://github.com/qriz1452/oci/assets/112246222/ba4d8f87-9936-4f9b-b0b8-bba0aafcb15e)


========

Now Playing : Streaming: Fundamentals

As we continue learning more about the OCI Streaming service, let's now look at some key fundamental usage concepts. We'll start with some definitions. A message is any base64 encoded unit of data that is stored in a stream. Essentially, an array of bytes. The streaming service is schema agnostic. In other words, it accepts any message format to include XML, JSON, CSV, and even compressed formats such as GZIP. So naturally, producers and consumers will need to agree upon the message format.

A key is an identifier used for grouping as messages with the same key or written key, the same partition. The streaming service ensures that any consumer of a given partition will always read that partition's messages in exactly the same order as they were written. A stream is essentially a partitioned append-only log of messages. You can think of it as an ever-growing data set where new records keep arriving.

A stream pool is a grouping that you can use to organize and manage streams. It provides the ability to share configuration settings across multiple streams. For example, users can define security settings such as custom encryption keys to encrypt the data of all streams inside the pool, or set up explicit access permission policies. A stream pool also enables you to create a private endpoint for streams as restricting internet access to all the streams within the pool.

A partition is a section of a stream allowing for multiple producers to write, and multiple consumers to read from a stream. In addition, in OCI Streaming, each partition can be hosted on a different node, which means that a single stream can be scaled horizontally across multiple servers to provide performance far beyond the ability of a single server. Each message within a partition has an identifier called an offset. Consumers can read messages starting from a specific offset, and are allowed to read from any offset point they choose.

Consumers can also commit the latest process offset so they can resume their work without replaying, or missing a message if they stop and then have to restart. A cursor serves as a pointer to a location in a stream, which could be a specific offset within a specific partition or a timestamp.

Here's how OCI Streaming works. A producer publishes messages to a stream, which are then distributed among the partitions using the messages key. Partitions allow you to distribute a stream by splitting messages across multiple nodes, which allow for multiple consumers to read a stream in parallel. Each message within a stream is marked with an offset value so a consumer can pick up where it left off if it's interrupted. Additionally, a consumer group is a set of consumers that coordinate the consumption of messages from all the partitions in a stream. Consumer groups also provide for load balancing as new consumers join the group, as well as rebalancing as consumers leave the group.

Some design considerations. The OCI Streaming service supports message retention of up to a maximum of seven days. The current maximum single message size supported is one megabyte. However, each partition can handle up to 1,000 messages per second up to a total of one megabyte, of course. Additionally, each partition can handle up to five read API calls per second for a total read rate of two megabytes per second. And while each OCI tendency has a limit of five partitions by default, you can request more.

So at this point, if you have any experience working with Apache Kafka, you may be saying to yourself, hey, all this is what I can do already pretty much with Kafka. Why not just provision some compute virtual machines in OCI and install a Kafka cluster myself? Why should I use OCI Streaming? And you'd be right. You could. But, as I mentioned in the first introductory lesson, the benefits in leveraging OCI Streaming are really important.

But to underscore some of these advantages we talked about earlier, essentially, you get out of the box native integrations with many OCI services, and you can reduce administrative costs by eliminating expensive manual monitoring and management. You reduce runtime costs since it leverages pay per use pricing, so you're not charge for provisioned capacity. There are more development options since you can use numerous OCI SDKs as well as Kafka APIs. OCI Streaming has a 99.95% uptime guaranteed SLA, and is fully fall tolerant. And besides, if you're already using Kafka, we provide for easy migration of existing Kafka clusters.

So how do we use OCI Streaming? Well, before publishing or consuming messages, you must first create a stream. You can do this manually in the Oracle Cloud Infrastructure console, or perhaps choose to automate this task by leveraging either the OCI Command Line Interface, the REST-based streaming API, or by applying a configured resource manager stack.

When you create a stream, you need to specify whether it should become a member of an existing stream pool or a member of a new, automatically created one. Keep in mind that stream names within a pool must be unique. And finally, when creating a stream, in addition to the retention period, which, again, can be up to seven days, you'll want to consider the number of partitions to use. Again, a partition essentially functions as a base throughput unit in a stream that enables the horizontal scale and parallelism of production and consumption, which, again, currently is a capacity of one megabyte per second data input and two megabyte data per second output.

So you specify the number of partitions you need based on the throughput requirements of your application or the intended use case. For example, you can create a stream with 10 partitions to achieve a throughput of 10 megabytes per second input and 20 megabytes per second output from a single stream. You can also create streams much more by using the OCI Streaming SDKs. Oracle Cloud Infrastructure provides SDKs so you can interact with Streaming without having to create a framework. These SDKs, all of which are available for download on GitHub, by the way, allow for you to handle tasks such as managing streams and stream pools, as well as handling Kafka Connect configurations.

But, in addition, in the online documentation, Oracle provides separate quick starts for each of these programming language SDKs, which provide examples on how to publish and consume messages programmatically. As to those scenarios where you need long-term storage or you wish to later run Hadoop Spark job, or perhaps you don't have any other active stream subscribers, you can set up a service connector to automatically archive a stream to an OCI object storage bucket. Without writing any code, you leverage the OCI service connector hub to create a new service connector, then define the source as a streaming service stream, and the target as a specific object storage bucket.

This configuration allows you to start archiving from the latest position or from the oldest position in the stream. In this example for batching, the service connector will write to the bucket once 100 megabytes has been cued in the stream, or every 60 seconds. Whichever comes first.

Another scenario for creating a service connector would be to automatically set up the delivery of log messages to a stream. In this example, we're interested in all maintenance reminder log messages that get emitted from any autonomous container database in this particular OCI compartment. And, of course, the streaming service provides metrics showing how the service is performing. These are automatically available, and you can use these metrics, for example, to understand the produce versus consume latency for a real time application, or calculate and validate the price of service usage, or monitor changes in throughput over time, or even check the time that the last message was consumed.

Monitoring also allows you to ensure that a stream is healthy. A healthy stream would have both put and get messages latency metrics that are very low, as well as both put and get throttled records, and message failure metrics very close to 0. To be more proactive, you can also consider setting alarms on one or more of these metrics. For example, a substantial increase in out message total throughput could indicate that the one megabyte per second per partition limit will soon be reached, and that event will trigger the throttling mechanism. Decrease, on the other hand, might mean that the client producer is having an issue or maybe is about to stop.

![image](https://github.com/qriz1452/oci/assets/112246222/6f2831e7-f49e-4845-b0f4-e33ceffb534f)
![image](https://github.com/qriz1452/oci/assets/112246222/c5b7f5a1-15cf-49cd-920b-f43de6527f79)

![image](https://github.com/qriz1452/oci/assets/112246222/90b585df-677c-46cc-84fc-84aca3a56449)
![image](https://github.com/qriz1452/oci/assets/112246222/8e2db71a-815f-452c-ab0d-e3939ce1cf39)
![image](https://github.com/qriz1452/oci/assets/112246222/854cf45e-e8b0-49b6-af41-4536f0f99e7b)

------

Streaming: Use Cases 


You can use the OCI Streaming Service in various types of scenarios to include the decoupling of components of large systems. Producers and consumers can use Streaming as an asynchronous messaging bus and act independently at their own pace.

You can use the streaming service as an alternative for traditional files scraping approaches to help make critical operational data more quickly available for indexing, analysis, and visualization. Many customers use Streaming for capturing activity from websites or mobile apps such as pageview, searches, or other user actions. They use this information for real-time monitoring and analytics, and in data warehousing systems for offline processing and reporting. Or consider Streaming as a unified entry point for cloud components to report their lifecycle events for audit, accounting, and related activities.

Let's consider three use case categories starting with having 0SS serve as an integration platform for some of your on-premises systems. For example, you could set up retrieving the CDC logs from an on-premise database and back them up in OCI object storage. Or perhaps, integrate applications such as Oracle EBS, PeopleSoft or SAP to connect to the Cloud with Oracle Integration and the Streaming service leveraging Kafka connectors.

Cloud-native message bus examples might include the use of Streaming to decouple components of large systems to build new and robust micro service architectures. Or consider aggregating batch and stream pipelines by using both streaming and data flow to create more extensive data processing pipelines. The main premise behind a copper architecture is that you can perform both real time and batch processing, especially for analytics with a single technology stack.

And as a real time analytics engine, you can stream both OCI Service and custom application logs through OSS. And then by using Kafka Connect for Splunk, analyze them in real time. Or perhaps stream e-Commerce transaction orders to OSS, process each one dynamically using Oracle functions, and then store the data in a backend database.

Let's now look at some more examples. Here, OCI Streaming is used to capture change data generated from a database. Immediately saves the logs as a backup on object storage. Then the data is pushed downstream. A real world customer example happens to be a finance company that currently uses OSS to migrate some of the change data capture logs from their Oracle databases to streaming and subsequently on to an ATP database for further analysis. In this case, they leverage the OCI streaming service Kafka compatibility to interact with their on-premise Oracle database using the JDBC Kafka connect framework.

This use case involves publishing Oracle blockchain platform event notifications to multiple authenticated subscribers, securely and reliably. Now, although a chaincode in the blockchain can publish events itself by either using the Hyperledger Fabric SDK or by using Blockchain Platform REST API, there are several limitations and concerns. Most importantly, those event notifications are not guaranteed to be delivered.

To avoid those limitations, we can use the REST API with an event relay app, which could be implemented as a say a serverless function. It receives the event payload in the JSON format from blockchain, then re-formats the message to be compatible with the Apache Kafka API. Then leveraging OCI Vault to retrieve the appropriate credentials, the relay app then could publish the event to a stream. From there, multiple blockchain consumers can subscribe to the stream and start receiving the events that they are authorized to receive.

This use case leverages OCI Streaming to capture events generated from IoT devices, and then use the processing capabilities of Oracle functions and Autonomous Data Warehouse to generate insights to send alerts. In this example, we're looking at an IoT enabled devices and vehicles. First, the IoT data generated from sensors in a vehicle is published to OCI Streaming to then be assumed by a function. The function processes the data in real time, which includes running analytics, models that generate diagnostics and route efficiency. Drivers can then react on the alerts to minimize breakdowns and optimize route decisions.

One of Oracle's customers is a re-sync company which organizes international sailing competitions using high performance catamarans. Teams compete across a season of multiple events around the world. Well, they use OSS as a high throughput transport layer to ingest real time IoT sensor and bio-metric data from all the sailboats during a live competition. And then share the statistics as dashboards to numerous partners both as mobile and web apps.

In general, internet of things enabled workloads need to scale efficiency in real time, because as we deploy more devices and sensors, the volume and variety of stream data is bound to grow. So here is a partial example reference architecture for designing an IoT solution. Notice that we leverage serverless Oracle functions as well as an Oracle Autonomous Database in OCI to automate and scale the processing of streamed IoT data.

In this architecture, data from the IoT devices flows in through an API gateway to the functions, which then use the streaming service to upload the data to the database. Meanwhile, users outside the Cloud can access the data through a flask based web server running on an OCI compute instance.

Our next use case is a predictive maintenance example involving enterprise data warehousing. This high level diagram shows the technology solution within the overall business context where the goal is to discover, understand, and ingest the incoming data. Then transform and create so that the data can be analyzed driving towards the ability to measure, predict and act on those analytics quickly.

So at a high level, we're using data science and machine learning to analyze streaming and log data to provide context and insight for actionable events downstream. Specifically, we could use Oracle Data Integrator or the data integration service to load and optimize data into an object storage bucket. Meanwhile, at the same time, OCI Streaming is used for ingesting continuous high volume streams of data from real time sensors into object storage.

Data science is then used to build, train and manage machine learning models and OCI. Well, data flow could be used to run Apache Spark applications. Incidentally, the Terraform code for this particular reference architecture is available on GitHub. For real time Log Analytics, first the OCI logging service has been configured to ingest the OCI service and custom application logs that are needed. Next, a Service Connector configuration is created to transport logs from logging to streaming.

Once the log messages are on the stream, this provides for temporary persistence as well as the ability to connect with a third party security information and event management tool, in this case Splunk, which then performs the real time Log Analytics. The specific customer example is a company that converts surveillance video into actionable insights for the retail industry. They stream a large volume of OCI service logs ranging from Virtual Cloud Network, flow logs, load balancer and audit logs all to OCI Streaming. In turn, they use Streaming's Kafka Connect functionality to integrate with on-premises Splunk clusters to analyze that log data in near real time.

In our last example, we're seeking to use OCI Streaming as the asynchronous messaging backplane in our architecture to loosely couple the components of distributed on-premises and SaaS applications, providing real time data transport to any number of destinations.

And so by now you should begin to get a feel for the wide variety of use cases for leveraging OCI Streaming. And in the three previous OSS lessons, we covered many of the features, as well as the fundamental concepts involved with Streaming.

![image](https://github.com/qriz1452/oci/assets/112246222/f43cabf6-44c0-4900-9bf4-c09aab0866f1)
![image](https://github.com/qriz1452/oci/assets/112246222/bdc96571-05e5-4bd3-affc-b71d2025812f)
![image](https://github.com/qriz1452/oci/assets/112246222/b924272c-0720-4688-81bb-0ecc512e5424)
![image](https://github.com/qriz1452/oci/assets/112246222/50ccc5f7-53da-431f-b0c6-d795e9ab98de)
![image](https://github.com/qriz1452/oci/assets/112246222/1e16df1a-2324-478d-b830-206dad26b7a2)
![image](https://github.com/qriz1452/oci/assets/112246222/16c18eb0-64ab-4ee6-b37e-ec990133b460)
![image](https://github.com/qriz1452/oci/assets/112246222/e43dc425-50e5-440d-ac13-6fd5cdbef927)
![image](https://github.com/qriz1452/oci/assets/112246222/efa5b0a5-7d2c-4b46-8e1c-211014badd69)
![image](https://github.com/qriz1452/oci/assets/112246222/eb30cf54-cbdb-433e-9489-39252a830a78)


------------


















