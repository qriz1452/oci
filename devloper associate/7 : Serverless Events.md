Now Playing : Events: Fundamental Concepts


OCI Events enables you to create automation based on the state changes of resources throughout your tenancy. Use the Event Service to allow your development teams to automatically respond to one or more of these events. For example, you could send a notification when a database backup completes, or perhaps trigger a function that will convert files of one format to another when a file is uploaded to an object storage bucket.

An event could be a create, read, update, or delete operation, a resource lifecycle state change, or other OCI System Events impacting a resource. For example, an event can be emitted when a backup completes or fails, or when a file in an object storage bucket is added, updated, or deleted. You work with events by creating rules about a resource type, and can then restrict further by defining additional filters or tag names that match only certain events. Rules will also specify one or more actions to trigger when the event occurs.

Actions can include sending an event to the Streaming Service invoking an Oracle function, or sending it to a topic in the Notification Service. The actual events themselves follow the Cloud Events Industry Standard Format, which is hosted by the Cloud Native Computing Foundation. This standard allows for interoperability between various Cloud providers, or even between On-Premise Systems and Cloud providers. We'll take a deeper dive into the structure and the contents of the Event Message itself in a later lesson.

Before we go further, however, the caution often comes up as to what the advantages are in using events versus programmatically developing admin client applications to poll for certain resource lifecycle changes or other resource conditions. Ultimately, polling resources continuously to track changes has many problems to include the issues we see here. And besides, even if these are not a big concern for you, as you learn more about how the Events Service is used, you'll begin to realize the advantage of using a configuration based approach that can be more quickly updated whenever additional use cases emerge, versus having to update the logic by rewriting the code in a client application.

Let's take a look at the three Events Service Concepts. An event represents a change and an OCI Cloud Resource, initiated either by the system or by a user action. An event is emitted any time at resource within a compartment is created, or its attributes are modified, or its state changes. Events are represented as well-formatted messages that define what the event is, where it originates from, and other metadata that you can use for any desired downstream activity. An event rule is a customer-defined filter on one or more field values within an event, based on that rule matching, downstream activities can take place.

Rules filter all incoming events, and based on the rule definition, decide what actions to take on that event. Rules can have one or more actions defined to execute when they are triggered. Essentially, a Rule Action is triggered by an Event Rule Condition Match. There is a predefined set of actions that you can choose from to be executed, while the content of the event that match the Rule Condition is passed on to the action. While there are literally thousands of use cases where using the Event Service can be useful, here is just one simple example.

We start with the provisioning of an Oracle Autonomous Transaction Processing Database Instance. And once that provisioning succeeds, a Create Instance in the Event is received by the Event Service. Now a rule has been created to filter on that event, which then triggers an action to invoke Oracle functions. That function contains logic to run scripts, in this case, to create schemas, and tables, and import golden data into that newly Provisioned ATP Instance. Meanwhile, another action is triggered to the Notification Service, which both sends an email to an administrator as well as creating a page or Duty Incident.

So to wrap up, in this first lesson, we started with a brief overview of the basic concepts involved with the Event Service, starting with the events themselves that are emitted from OCI Resources, which can then be automatically delivered to the Event Service by way of configured rules. We then defined one or more actions to trigger, which will be the destination for those filtered Event Messages. In our upcoming lessons, we'll take a deeper dive into more details in configuration options, as well as additional use cases. I certainly hope this recorded video lesson was useful for you, thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/7c2d13d7-767c-4ca2-99f5-6ab41d8a9fe9)


---------

Now Playing : Events: Event Messages and Event Types

As we continue learning more about the OCI Events Service, we'll now take a closer look at the Event Messages themselves and how they are organized by various Event Types depending on the specific OCI resource, let's get started. An Event was a structured lightweight message that denotes a change in a resource, unlike raw generic log entries, events have derived context and structure, and are guaranteed to be actionable. An event can be a User-Initiated CRUD operation, such as bucket created, bucket updated, or deleted.

It could reflect a life cycle state change in a resource, such as instance stopped, instance launched, or backup starting. Or an OCI system event, such as instance rebooted, hardware failure. Each event has an envelope that conforms to the CloudEvents standard format, which includes the event source, which is the OCI service-- the generated event, such as object storage or compute. An event type designation, such as backup complete or bucket created, and a timestamp for when the event occurred.

The inner payload contains detailed service-specific data to describe the change and resource in more detail, including any tags associated with the resource. Here's an example event-- nuclei JSON object syntax, and as I mentioned already, the attributes for an event envelope are the same for all events to include the event type, source, and event time. The data in the payload fields will depend upon which OCI service produced the event, as well as the specific event type it defines-- more on event types in just a moment.

Notice in this example, this resource had both free form and defined tags, and it was an object storage bucket named, my_bucket, that was deleted. As you can see, there are a wide variety of OCI resources and services that produce events, and there are many, many event types. For which you can then configure one or more event service rule conditions to trigger actions for any of them. This capability includes most native OCI services such as Compute, API gateway, and Virtual Cloud Network. But also, many Platform Cloud Services such as Oracle Integration, Digital Assistant, and Blockchain Platform.

Technically, all resource events are automatically flowing into the event service and are checked to see if they match any user-created rules. We'll discuss more about rules in a later lesson. If an event matches a rule, the user-defined action is triggered. Otherwise, the events are dropped. Services, emit events by resource type, and event messages use a combination of an event type and a data payload from the resource to identify state changes. So essentially, event types are organized by service, then by resource type.

This organization is also visible in the online documentation, and it provides one reference example per resource type since the payload contains the same attributes for all event types within that category. Over 60 OCI services are literally thousands of events types, let's look at an example to better understand this. OCI Compute Resources-- as you can see here, emit 87 different event types, and they're organized into these 10 categories of types. Well, 22 of these event types use a similar Event Payload Structure, and all of those categories as Instance Event Types.

![image](https://github.com/qriz1452/oci/assets/112246222/0c616d63-3596-46ba-b661-7a98c283885e)




----------
Now Playing : Events: Rule Actions



As you think about which events you're interested in, you must also consider where you're going to send those events, as well as what might need to happen later downstream once they've been received. So to review from an earlier lesson, there are three destination choices you'll have when adding and configuring a Rule Action. An OCI Stream, an OCI notification topic, or a specific Oracle serverless function.

However, before you can select any of these, they must first have been created as a resource within your OCI tenancy. Let's take a closer look at each general use case. It's beyond the scope of this lesson to fully dissect all the features and capabilities of OCI Streaming, so instead, I'll encourage you to learn more about this service by watching those Streaming Service Lessons in this course. Reading the Online Oracle Documentation, as well as the various blogs and tutorials that are available. However, at a high level, here is how streaming works.

A producer, in our case, the OCI Event Service, publishes a message to a stream, which is essentially an append-only log. These messages are then distributed among Oracle Managed Partitions for scalability. Partitions allow you to distribute a stream by splitting messages across multiple nodes or brokers. Each partition can be placed on a separate machine allowing multiple consumers to read a stream in parallel. A consumer reads messages from one or more partitions. Each message within a stream is marked with an offset value, so a consumer can pick up where it left off if it is interrupted.

Messages from a partition are guaranteed to be delivered in the same order they were produced. And finally, streaming is compatible with most Kafka APIs allowing you to use applications written for Kafka to receive messages from the Streaming Service to then subsequently process those event messages as appropriate. Of course, to use Streaming, we must first create a stream. You can use the OCI Console, the OCI Command Line Interface, or SDKs, the Streaming API, as well as Resource Manager to create Streaming Resources.

We'll choose an OCI Compartment, and then a Stream Pool to contain the stream. You can then further define the number of hours to retain messages, as well as the number of partitions to use. So now when we're ready to do the Actions Configuration for an Event Rule after selecting Streaming as the Action Type, we select the OCI Compartment that contains the stream, then choose the appropriate stream within that compartment.

To review the capabilities of Oracle Functions, this is available as a serverless platform running in your OCI tenancy, and it's powered by the Fn Project Open Source Engine. When you deploy a function using the Fn Project CLI, the function is built as a Docker image and pushed to a specified Docker registry. A definition of the function is stored as metadata in the Oracle Function Server, which describe how the function is to be executed, and includes the Docker image to pull when the function is invoked, as well as its maximum execute time per call and the amount of memory that it's allowed to consume.

And of course, since the function service is fully integrated with the OCI Identity and Access Management Service, you can take advantage of Native OCI Identity Functionality when leveraging a wide variety of OCI Services for executing logic that may be required by your Event's massive use case. Oracle Functions uses Fn Project Function Development kits to support popular languages, including Java, Node.js, Python, Go, and Ruby. Especially, an FDK is a set of helper libraries that handles system internals such as protocols, parsing input and output, and logic for function containers.

Functions then are deployed within the scope of an application, which provides for a common context and ability to store configuration variables for all logically group functions within it. An application also ensures runtime isolation for functions. And finally, although not required, for a function to work well as an Events Service Rule Action, the developer should design the function, Trigger Interface, as an HTTP POST method that expects the event JSON message as its payload. From there, they can implement any logic that fulfills the appropriate use case for handling that event.

Again, to learn more about Oracle Functions, please watch those specific lesson recordings in this course. Also, you should review the Online Oracle Documentations, as well as the various blogs and tutorials that are available. So once we have a function deployed and ready to be invoked, we can now complete the Actions Configuration for an Event Rule. After selecting Functions as the Action Type, we select the OCI Compartment that contains the application, choose the application and then the appropriate function.

The OCI Notification Service broadcast messages to distributed components through a publish-subscribe pattern, delivering secure, highly reliable, low latency, and durable messages for applications hosted within your OCI tenancy, as well as external applications. It enables you to set up communication channels for publishing messages using topics. When a message is published to the topic, the message is sent to all of the topics subscriptions. If a subscriber's endpoint does acknowledge the receipt of the message, the Notification Service retries that delivery.

This situation can occur when the endpoint is offline. For example, maybe the email server for an email address may be down. And while there are other use cases for leveraging notifications such as directly publishing a message by way of its API, or configuring alarms in the Monitoring Service, our key focus here is to set up a notification when certain Event Rules are triggered in the Events Service. Once again, since it's beyond the scope of this lesson to fully dissect all the features and capabilities of OCI Notifications, instead I'll-- again, encourage you to learn more about this service by reviewing your Online Oracle Documentation, as well as the various blogs and tutorials that are available.

Of course, before we set up the Notifications Action, we must first create a topic with one or more subscriptions. You can use the OCI Console, the OCI Command Line Interface, REST APIs, or the SDKs to create topics and configure subscriptions. Once the topic is created, we must configure at least one subscription. In other words, where do we want to send those OCI Resource Event Messages? Email, of course, sends an email to one or more addresses each time the event is triggered. The Function option runs the specified function which for our Event Use Cases, we could instead just choose to use the Functions Rule Action option that we talked about earlier.

If you have a particular REST web service that you wish to receive that Event Message, whether it's hosted in OCI or even hosted externally, you can configure the HTTPS option providing the custom URL for that service. A PagerDuty subscription creates a PagerDuty incident by default when the topic receives the Event Message. A Slack subscription is available to be configured to send the event to the specified Slack channel. And finally, while there is an SMS subscription option, this cannot be used directly for receiving Events Messages.

Once we have our topic and it's subscriptions properly configured, we're now ready to edit the Events Rule Action. After selecting Notifications as the Action Type, we select the OCI Compartment and then the appropriate topic. So to wrap up, we learned more about the three options you have when configuring one or more destination actions for an Events Service Rule. I certainly hope this recorded video lesson was useful for you, thanks for watching.

---------------------
Now Playing : Events: Working with Rules




To interact with the OCI Event Service, users create and manage Rules-- simply stated, Rules are the key configuration objects in the Event Service that allow you to select which event types to monitor, which particular resource or resources you're interested in, and then automatically trigger one or more actions when those events occur.

A typical workflow for setting up a rule might follow this pattern. We've already explored this in greater detail in previous lessons, so essentially, you need to set up or identify whatever action resources you need and tend to use with the rule. For example, you might set up a notifications topic, and create descriptions for the DevOps teams, so that they are notified when backups complete. Of course, if a topic already exists, you can use it instead of creating a new topic. In addition, be aware that the destinations you specify for actions do not have to be in the same compartment as where you're configuring the rule.

For planning, you'll need to ensure the resources that you want to monitor emit events to the Event Service and plan your pattern matching strategy. For example, you might want to monitor backups on Autonomous Data Warehouse Instances in a particular compartment. Just ensure that the MW instances emit an event type you can use to create the automation that you are looking for. Review the example, JSON Event, to determine the best way to identify those resources and filters.

And finally, when actually creating the rule, remember that rules apply to events in the compartment in which you create them, and optionally, in a child compartments. Choose the resource you want to monitor, and specify where to deliver matching events. For example, you might create a rule that filters for Autonomous Data Warehouse Backup Events, once again, since the Event Service has no requirement about the location of the Action Resources, you could specify a topic in a different compartment to deliver any matching events.

So at a high level, a rule is simple. To create one, you specify a name for the rule and the compartment where you want it to be created. Next, the trigger condition is the event types that you care about, as well as any other property filters. Of course, you don't have to filter expressions as you can actually subscribe to one or more event types from all the related resources in that compartment. However, you normally filter using tags or some other condition criteria.

For example, any time an object storage bucket resource has been deleted, that has a product don't delete tag. And of course, the response action is what is to be executed once the trigger condition has been met. You can have multiple actions per rule, for example, you may wish to notify the designated responsible individual on a Slack Channel via the Notification Service, but also trigger a function call that will execute backup scripts. The console UI experience provides for both a simple and advanced view for creating rules.

In the upcoming demo, I'll be walking you through the simple mode to create rule conditions as seen here. Essentially, we start with an Event Type Condition selecting the name of the service and one or more of that services event types. Then optionally, we create one or more attribute filter conditions, such as the name of the database as in this example. Or we could define a filter tag condition that is only interested in resources that have a particular tag value. And of course, for actions, as we saw in an earlier lesson, you simply choose the action type and then the appropriate resource.

The advanced mode allows for expert users to type in custom verbose JSON syntax for more complex rules. I'll give you a brief peek at that during the demo that follows this lesson. Once you become more familiar with the event service UI for creating rules, there are some design considerations to consider rules are compartment based. However, they will support nested compartments. So if a customer wants to set up a Tenancy Side Rule, they could create a rule in the root compartment. All rules and actions are checked to ensure that identity and access management permissions are in place.

Users will need the Manage Cloud Events Permissions to be able to define CRUD Event Rules. And before using the service, you'll need to set up a policy to allow the Event Service itself to deliver Event Messages to those designated Action Resources. When events are generated, they also include the tags of the resource that fire the event. So as of best practice, in addition to using resource attributes for filtering a real condition, you should take advantage of filter tags when further refining the rule condition for that event type and resource.

By default, the maximum number of rules that could be created in an OCI Tenancy is 50, although, this limit can be increased. However, keep in mind that each single rule could include multiple conditions or actions. Additionally, the Event Service offers the following guarantees. If an event is ingested, it guarantees that the event will be evaluated at least once against all user rules. If a rule is matched, it guarantees at least one delivery attempt for all actions. Be aware, however, that the events themselves are not guaranteed to be processed or received in order.

| an action target is nonresponsive, the Event Service will retry delivery for up to five hours or until a non retrieval error occurs. Otherwise, a failure metric will be admitted and no further retries will occur. Speaking of metrics, as to monitoring capabilities, OCI Events Metrics helps you measure the success of the rules you create in terms of pattern matching and delivery, and the quality and scope of the emitted events in your tenancy, which are stored for up to 90 days. For each rule, there are three key metrics. The total number of events that were matched by that rule, how many were successfully routed to the corresponding actions, as well as how many failed.

If desired, you can also view these metrics in telemetry dashboards with rich views into how the rules are behaving. And you can also view the total number of events that were emitted for all resources at the scope of an entire compartment. So to wrap up, we've looked at some design considerations and the capabilities you have for selecting the events you wish to process by way of filtering on attributes or tags. In the demonstration that follows this lesson, we'll explore some of the other features available in the OCI Console, such as validating and testing rules. I certainly hope this recorded video lesson was useful for you, thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/cfa6f11d-27ad-4545-befd-0ff316976943)





---------

Now Playing : Events: Use Cases



Exploring some of these Use Cases may also help you to envision any number of additional ways to leverage the Events Service yourself. There are several use cases for Cloud operations teams and developers to consider that make use of OCI Events, here are a few examples. Occasionally, there is a need to execute some scripts, or invoke other services once certain resources are terminated. Such as a provision to Compute Instance, or an Object Storage Bucket.

Or perhaps the need to set up automation for analyzing network logs when certain issues or warnings are detected within the Virtual Cloud Network. Network logs can be uploaded to OCI Object Storage Bucket and then sent to third party tools, such as Splunk for security analysis. Or look to process a file automatically when new files are uploaded to a particular bucket. Maybe there's a need to create a private OCI Object Storage Bucket during new user onboarding that will then be dedicated to store files or other artifacts specifically associated with that new user.

Or perhaps, we have a need to archive all events associated with a specific compartment to a stream that can then be consumed and processed for later analysis. We might wish to publish a notification to certain individuals or other DevOps workflow engines when longer tasks have been completed, such as the completion of an Autonomous Database provisioning request. Or the large number of scenarios in which we might wish to trigger any sort of action when a new resource is created or deleted within a particular compartment, such as an Infrastructure Viability Regression Test.

Let's now overview six separate use cases involving the OCI Events Service that are currently being implemented by our various Oracle customers. This first use case is actually an illustration of one of the examples we just talked about when new or updated log files are placed into Object Storage, that event is processed by an Event Rule, which then triggers a function. The function then retrieves a network access logs that are of interest, and sends them to a customer Splunk for periodic security analysis.

This is an automated Event-Driven Infrastructure-as-Code Use Case that works as outlined here, when a new Compute Instance is provisioned or if one has been terminated, we have a single OCI Event Rule Filter to capture those two event types with a configured action to invoke an Oracle Function. Now depending on which event is set, the function logic will either create a new Private Object Storage Bucket in the same compartment using the name of the new instance for the bucket name-- for the terminated event, it will locate the previously associated bucket, and delete it.

Another Automating Corporate Functions Use Case involves automatically checking to see if all newly provisioned Compute Instances, within the scope of a compartment, comply with all corporate security and isolation policies. The function logic executes one or more checks for compliance. And if any checks fail, the logic terminates the instance since the appropriate notifications and potentially initiates a new provision instance request. This fourth use case provides for invoking an OIC Integration Flow Automatically.

And in this case, as soon as a file is uploaded to OCI Object Storage-- since the Object Storage Service emits events such as this, the Events Service receives it and locates an Event Rule that has been configured for that event type and filters for only that particular OCI bucket. The rule includes an action to send the event to a topic, then OCI Notifications broadcast the event to topic subscribers. Where in this case, the URL for the OIC Integration is configured as an HTTPS subscriber. OIC receives the REST request, which triggers that specific integration flow, where presumably, it would proceed to retrieve and process the file accordingly.

The Oracle Cloud Guard service was released recently and 2020, it helps customers monitor their OCI Resources and maintain a strong security posture. It works by continuously collecting and analyzing configuration and audit logs, as well as other information throughout your tenancy. Then reports its findings as problems based on its detector recipes. However, there are use cases where you may wish to integrate Cloud Guard with external systems. For example, some customers may want to export this data out to their Central SIEM-based System for further analysis and actions.

The SIEM process, which stands for Security Information and Event Management, it refers to a company's strategy towards data security. Well, SIEM-based tools such as Datadog, SolarWinds, and ManageEngine are an important element in that strategy. Of course our customers may prefer to create tickets in their External Service Management Systems for addressing the identified problems. Regardless, the simple answer is to use the OCI Events Service to send a Cloud Guard Events to either the Notification Service or to Oracle Functions as in this example. From there, invoking an API on your external systems.

This final use case is a bit more evolved, but it goes to really illustrate the integration capabilities across a wide spectrum of Oracle Cloud Services. Oracle Business Intelligent Cloud Connector or BICC provides a robust mechanism for performing bulk exports of data from ERP Cloud where exported CSV files can be directed to the museum contained within the ERP Cloud Environment, or as shown here, to an OCI Object Storage Bucket. So now, how do we know when a scheduled job is finished, so we can go fetch and process the file?

This is a common problem that needs to be addressed, and although this example describes a scenario involving ERP Cloud and APEX, this pattern can be reused for any scenario where you need to perform an action when a file is created in an OCI Bucket, but you don't know when the file will be created. So starting with number one. In our example, this file is coming from BICC on ERP Cloud, which allows you to either call a web service to launch an extract job, or to use ERP Cloud to schedule the extract. So in view of this, files could appear in our OCI Bucket at any time.

We need to know when the file is created, so it could be processed right away. Well, as soon as the file is created in our Object Storage Bucket, the event fires, and in our case, a rule is then configured for the Object Create Event Type filtered for that specific bucket. And the real action is to call a notification topic. Here, the topic is being configured as an HTTPS subscriber. And in this example, we are referencing our Oracle REST Data Services-- ORDS Webhook URL. If the service is unavailable when it's called by the notification service, it will retry up to two hours.

In our case, the actual endpoint is an ORDS REST Service running on an Oracle APEX environment, which could be either on-premises or in the Oracle Cloud. This service is designed to receive that event payload, then submit a Database Scheduler Job to fetch and process the file. A synchronous at first, we'll use the OCI REST API to fetch the file from the Object Store Bucket. Now we can parse it using the APEX Data Processor as we deem necessary making that data available for any of our APEX applications.

After seeing those six use case examples, you can begin to understand that there are literally thousands of use cases that can be facilitated using OCI Events because of the extensive number of event types across so many OCI Service Resources. Combine that with the really limitless choices of logic you could implement downstream based on those three Rule Action Trigger options, the OCI Notification, and OCI Streaming Services, as well as Oracle Functions. Here in this slide, we've attempted to summarize these Event-Driven Design Patterns into these APIs general categories.

I'm sure that once you review the OCI documentation to see the list of all the event types, you may very well envision new use cases and implement solutions of your own. So to wrap up, explored a number of different use cases for leveraging the OCI Event Service in this lesson. And in the previous lessons, we covered many of the design and configuration details involved in creating rules, both Rule Conditions and Actions. I certainly hope this recorded video lesson was useful for you, thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/47288aec-baf2-489b-ba38-0590707e6f73)

![image](https://github.com/qriz1452/oci/assets/112246222/afdccfb8-e4d1-4b5c-a137-89b50b32962c)
![image](https://github.com/qriz1452/oci/assets/112246222/f17886e4-4347-4f81-bc8d-c336ad1d3ea9)


------

































