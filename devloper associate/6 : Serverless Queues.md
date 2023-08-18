Now Playing : Serverless Queues: Introduction

A queue service is a type of middleware solution that allows applications and services to communicate within a cloud computing environment. It provides one or more queues which serve as a lightweight buffer that temporarily but persistently stores messages.

The queue service provides endpoints that allow software components to connect to the queue in order to send and receive messages, thus, decoupling those components from one another. Usually, these messages are small and can be anything from request, replies, and error messages to business transaction details, or just plain operational information, or other application data.

But let's step back for just a moment to better understand the challenges businesses face when using traditional orchestration architecture. Consider a typical e-commerce website as an example.

This application in its most basic form has four features, account-- for sign up, log in, log out, and account details-- inventory, used for displaying the details about one or more of the products, payment, which handles the logic to allow users to make payments, and cart, allowing users to add products to place an order.

In traditional methods, the developer team designs and implements the application with a single code base containing all the code for all the features the application provides. These services, although they have different functions, are very tightly coupled and use the same database.

The issue is that when there is a significant increase in traffic, the application requires quick scaling handled reliably with the least failure situations in case of any error or bug, thus normally requiring the redeployment of the entire application. Since the components are closely coupled and are interdependent to each other, it becomes challenging for the company to grow and scale quickly.

To overcome these challenges and many others, in modern cloud architecture, applications are decoupled into smaller independent building blocks that are easier to develop, deploy, and most importantly, maintain.

Today many websites run as microservices, which means applications are decomposed into loosely coupled components that have various servers working at the back end for every particular service.

As to the benefits, when using a choreography architecture, scalability can be easily achieved because each service is a separate component. You can scale up a single function or service without having to scale the entire application.

Also, your entire application is decentralized and decoupled into services that act as separate entities. Therefore, if any single service goes down, it minimizes the impact of a potential full application failure. This architecture also allows you to deploy an application's components separately when needed based on new requirements or customer demands.

So you see how a decoupled architecture allows software development teams to build, execute, test and debug application modules independently, which are easy to scale, prone to less failures, and allows for open releases.

However this type of architecture does require a communication setup for exchanging messages and data among the components. Unfortunately, with point to point synchronous calls, even a slight change in requirements can render the application ineffective in certain use cases. Therefore, developers seek automated services that can share their load of managing this message based communication.

And that's where the concept of message queues come into place as it allows different parts of a system to communicate and process operations asynchronously. A component known as a producer client adds a message to the queue, then later a consumer client, which is a different component, retrieves and processes the message.

A producer and a consumer can be any element of the application. In fact, a microservice could be both a consumer of one queue then subsequently become a producer to another queue. Again this message exchange pattern is called asynchronous communication, that allows producer and consumer applications or services to communicate with each other indirectly without having to be online or available at the same time.

This then provides three key benefits, zero data loss, systems can continue to function if processes or connections fail, and higher throughput and scalability. Some messages are sent from a producer to a consumer for processing. So the messages are stored in message queues until the consumer application is ready to process them preventing the loss of queued messages.

Also the adoption of asynchronous communications allows developers to keep processes and applications separate. Your sender and receiver applications are decoupled, which allows them to operate independently at different times. And because messages can now be handled in parallel and at different times, asynchronous communication significantly enhances both the reliability and scalability of communication between applications and services.

In such systems, the sender can move on to other tasks without having to wait for the receiver's response. This concept is really similar to text messaging, something all of us I'm sure are familiar with. You can always try to call someone on the phone directly if you need to communicate with them. But that assumes that they are available and have the time to talk to you.

Texting is a more effective method for non-urgent messaging. The recipient's phone puts the message in a queue, then they check it and hopefully respond as soon as they're available.

Now that we better understand how message queues play an important role with enabling decoupling systems and services to communicate, you can now better understand the OCI Queue service which is a fully managed serverless cloud service you can leverage using an on-demand pricing model. That means it can provide message communication between applications or among the various components or microservices within a single application.

OCI queue can support one or more message queues that handle high volume transactional data that may require independently processed messages without loss or duplication. The service supports the ability to scale out transparently and automatically based on the throughput of messages between producers and consumers.

Also, in addition to the provided OCI SDK libraries, OCI Queue also supports open standards, such as REST APIs to support communication from any consumer or producer with minimal effort.

Let's wrap up by reviewing the key benefits of OCI Queue for Oracle customers. Because it is serverless, OCI Queue provides the customer with an asynchronous messaging service that doesn't need any infrastructure management, helping them to innovate more and focus on more important design and implementation decisions.

OCI Queue pay-per use model helps reduce administrative costs, as well as the effort of provisioning and maintaining messaging infrastructures. It also provides customers the tools needed to facilitate monitoring, reporting, support and maintenance.

And finally, Oracle manages the allocation of resources such as servers and storage automatically along with other housekeeping activities traditionally associated with deploying other messaging solutions such as WebLogic JMS or Apache Kafka systems.

OK then. We've now learned a little more about message queuing, the OCI Queue service, as well as some of the benefits of leveraging asynchronous messaging architectures. But there is more to learn. We'll see you in the next lesson.

![image](https://github.com/qriz1452/oci/assets/112246222/ab2999e4-b4ff-48e6-9f0f-e9cb4352cd42)
![image](https://github.com/qriz1452/oci/assets/112246222/df466160-11a5-45bb-8585-1e72e3fc1c19)
![image](https://github.com/qriz1452/oci/assets/112246222/760c1714-c98b-414b-b458-16f53f3e3c30)
![image](https://github.com/qriz1452/oci/assets/112246222/9e49b421-113c-446b-b5cf-20557f6e82d1)
![image](https://github.com/qriz1452/oci/assets/112246222/4bede5ad-890f-4997-a42f-ec7a411f77a2)
![image](https://github.com/qriz1452/oci/assets/112246222/ec138783-5886-412b-9c7e-eced8d3fbc7d)
![image](https://github.com/qriz1452/oci/assets/112246222/e82a8bb8-c742-43d8-a722-b7fddcce2c3b)
![image](https://github.com/qriz1452/oci/assets/112246222/5c25ce9e-fb47-4dd7-96ac-e791a93425cb)
![image](https://github.com/qriz1452/oci/assets/112246222/cb88ea35-d479-40ad-a96a-6835e3987319)


---------

Now Playing : OCI Queue Features




 in this lesson, we'll take a closer look at the features of OCI Queue. Starting with encryption OCI Queue provides end-to-end message encryption. So whether the message contents are at rest or the message is in transit, the information is always secured.

When a producer sends a message to OCI Queue, the message is first encrypted using TLS before it is transmitted over the network. This encryption ensures that the message cannot be intercepted and read by a third party. Likewise, when a consumer retrieves a message from the Queue, the service will also use TLS encryption to ensure the message is secure in transit.

Transport layer security uses a combination of symmetric and asymmetric encryption. So when the client and OCI service first establish a connection, they negotiate a set of encryption algorithms and keys to use for the communication. This negotiation process ensures that both are using the strongest encryption possible.

As to the data at rest, when the OCI Queue service receives each message, it stores the data securely using advanced encryption security known as AES with a key that is 128 bits long. This is a widely used encryption algorithm that provides strong protection for stored data. The key point to remember is that all of this is fully managed by Oracle, which means that both at rest and in transit encryption is a default feature that cannot be disabled by you or anyone else.

OCI Queue is fully integrated with OCI Identity and Access Management for both authentication as well as IAM authorization policies. This allows you to have complete control over authenticating the identity and setting permissions of those seeking access to OCI Queues. Connecting to a queue will require one of OCI authentication mechanisms, such as an API signing key pair or OAuth 2 token credentials.

OCI IAM policies allow for fine grained access control from queue creation and updates to producing or consuming messages to the queue. Let's look at some examples of IAM policies related to OCI Queue. This policy provides for full administrative privileges to users which allow for creating, updating, or deleting queues using the manage verb.

Then there are more fine-grained policies that can be used to allow specific groups of users to either produce messages to a queue using the queue push resource type or to consume messages from a queue using the queue pull resource type. And in this example, we have a policy that limits permissions to only viewing messages on queues using the read verb.

OCI Queue allows you to design decoupled applications and systems by using asynchronous messaging. Decoupling ensures that individual application components can scale independently, and that as new application components get built, they can produce to or consume from a particular queue. Decoupling also ensures that the entire application does not necessarily go down when there is a temporary failure of one of the components or microservices.

Since it is serverless, OCI Queue scales its capacity automatically to accommodate hikes in traffic. Oracle simply provisions more infrastructure resources as needed. OCI queue can also ingest a significant volume of messages over a very short period up to 10 megabytes per second. Even if you have limited consumers, which allows the messages to be processed based on consumer's availability and their bandwidth.

As a fully managed service, you don't need to worry about service availability or scaling to meet demands because the OCI queue service provides for an unlimited number of messages per queue. Next, some features for reliable message processing. A message is guaranteed to be delivered to the consumer at least once unless the message has expired.

Also, OCI Queue protects against message delivery issues and ensures that messages are never lost even if the consumer becomes unavailable. Additionally, you can define the number of attempts for delivering the same message based on your business requirements. Ultimately, if a message can't be consumed successfully because that maximum number of attempts have been made, the message is sent to a dead letter queue. From there, you can inspect the message and perhaps redeliver it to the consumer after fixing the message or otherwise, resolving the issue.

To access an OCI Queue the most common approach for developers of microservices is to use the OCI provided software development kit for their favorite programming language, where they can produce or consume messages from a queue. However, OCI Queue also allows you to communicate using its REST API with all those operations and payloads defined through an open API specification. This diagram illustrates the security best practice of abstracting remote clients on the web by using an API Gateway deployment, but that certainly isn't required.

Another powerful feature of OCI Queue is the ability to send and receive messages using the simple text-oriented messaging protocol or STOMP. STOMP is an open protocol designed for messaging that can boost efficiency because authentication is done only once per connection instead of on every single request, as it is handled with REST access over HTTP.


![image](https://github.com/qriz1452/oci/assets/112246222/188d3fae-228c-42c0-b7a0-082f38ba7905)
![image](https://github.com/qriz1452/oci/assets/112246222/8796f9be-faea-4b12-9d10-d17d2b3df4cd)
![image](https://github.com/qriz1452/oci/assets/112246222/104bcbf1-b2f6-441f-b644-a1c72eac2968)
![image](https://github.com/qriz1452/oci/assets/112246222/e64be001-aa3b-4356-854e-14c360b72a41)
![image](https://github.com/qriz1452/oci/assets/112246222/4c119df1-80a9-44de-8f63-9cf586517f82)


------

Now Playing : OCI Queue Fundametals

To get started, here are some key concepts associated with an OCI queue, starting with the message itself.

It can be any string representing a request, reply, or some information required for interprocess communication. Every message is processed independently, although they can be sent or received in a batch. A producer is any service or client application that serves as the source of a message.

A producer publishes one or more messages to a specific queue, which then gets immediately persisted. Consumers also connect to a specific queue, where they can receive a copy of one or more messages, then process the message, and finally, delete messages from the queue once they have completed processing.

The maximum retention period will be defined for each specific queue. Ideally, the consumer deletes the message when they're done processing. But what about those situations where the consumer fails to delete it? Well, the OCI queue service will not allow messages to live forever in the queue.

Instead, messages will be automatically deleted by the system once this retention period has been reached. By default, that is 24 hours. However, you can configure this parameter to be anywhere from 10 seconds to seven days.

The delivery count is associated with each specific message. It is simply the number of times that message has been sent to a consumer. You see, the OCI queue service keeps track of this number because of this maximum delivery attempts parameter.

This parameter is defined for each specific queue which is configurable from 1 to 20. And once that number of delivery attempts have been made for a particular message, it will then be sent to the dead letter queue. We'll talk more about that a bit later.

A default polling timeout parameter is also configured for each queue. However, a consumer can choose a different timeout when requesting messages, anywhere up to 30 seconds, which is the default. Essentially, if a queue is empty, this is how long the consumer will block to wait for one or more messages to arrive on the queue.

So for those consumers that are in a continuous loop polling for messages, this will logically define their polling interval. This visibility timeout parameter-- by default, 30 seconds-- is also configured for each queue and can be any value from one second all the way up to 12 hours.

But once again, a consumer can set a different timeout when requesting messages. This is needed to help ensure that a message that is being processed is only done by one consumer, because once they receive a message, that message will not be visible to other consumers until that time has elapsed, which now helps you understand inflight messages.

These are the messages that have been delivered to a consumer, but that consumer has not yet deleted them from the queue. Again, these in-flight messages are not visible to other consumers. And if the consumer that received the message fails to delete it, it is not available for redelivery until that visibility timeout has passed.

And finally, in order for a queue to produce or consume messages, they'll need to have that specific queue's message endpoint. This can be found on the Queue Details page and the OCI Console, which uses this general syntax.

To better understand how this all works, let's look at an example. First, a producer sends a message to the queue with the default message retention time, then immediately gets a confirmation that the queue service has indeed received and stored the message. Consumer A connects to the queue to get the message. He receives it, knowing that he's supposed to process the message within the visibility timeout.

Meanwhile, consumer B connects and tries to get a message. He receives nothing, since the only available message was already consumed by consumer A and is no longer visible. Now it seems that consumer A needs more time to process the message, so he decides to update that message to extend its visibility timeout.

Consumer B tries to get a message again, but as before, he receives nothing, since that message is still in flight, because the visibility timeout was extended. However, for this use case, let's assume that consumer A has failed to process the message. Therefore, they did not delete it. And now the extended visibility timeout has elapsed.

Consumer B tries to get a message for the third time. He now receives the message and knows it is supposed to be processed within a new visibility timeout. Consumer A tries to get a message but receives nothing, again, because that message has been locked by consumer B.

At this point, consumer A can no longer extend the message's visibility timeout, nor can he delete the message. Essentially, the message is no longer visible, because it was delivered to consumer B. And finally, consumer B is able to process the message successfully and now deletes the message from the queue, where he receives confirmation that the message was permanently deleted, so that that message can no longer be delivered to any other consumer.

Earlier I mentioned this concept. When we create a queue, a corresponding dead letter queue is automatically made available. The purpose is to isolate problematic messages, allowing time to maybe help troubleshoot why those messages are failing. But what do we mean by an unsuccessful consumption of a message?

To review, once a message has been sent to the queue, it becomes available to be consumed. If the consumer fails to process the message after the visibility timeout, it will be made available to other consumers. So then only if and when the unsuccessful delivery count becomes greater than the maximum delivery attempts parameter-- which was three here, in our example-- will the message now move to the dead letter queue.

To review, each unsuccessful delivery attempt means that the consumer couldn't process it. And as a result, they did not delete the message from the queue within the visibility timeout. Also the maximum delivery attempts per message was globally defined while creating the queue, a value from 1 to 20.

Be aware that the OCI queue service will still ultimately delete the message from the dead letter queue once that maximum retention period has expired. Of course, this can be configured to be up to seven days. Again, during that period of time is when you could retrieve messages from the DLQ to examine and perhaps troubleshoot why they failed. And that wraps up this lesson on OCI queue fundamental concepts. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/da15af25-97fc-4957-8ad6-1a0d64858994)

![image](https://github.com/qriz1452/oci/assets/112246222/5f7d54e8-1016-4596-9884-ee1874b44b44)

![image](https://github.com/qriz1452/oci/assets/112246222/0238d82e-c607-4ba0-9be7-9cd4bbdcc883)

![image](https://github.com/qriz1452/oci/assets/112246222/28f997b2-3750-4c42-8301-d8b9288ad13e)


---------

Now Playing : OCI Queue Operations


Starting with queue management, the service endpoint provides access to the control plane for the OCI Queue service which is unique for each region, as in this example for the US Phoenix region. To create, read, update or delete queues, one option is to use the OCI Console. To create a queue, for example, the UI shows your configuration options for queue parameters.

If you need to automate with administrative scripts, you could use the OCI CLI. For example, to create a queue, you provide the compartment ID and a unique display name. Other operations, such as update, delete, and get, require you to provide the queue ID.

You can also use the QueueAdminClient class programmatically leveraging the OCI SDKs or REST API. There are quite a number of operations that are available for managing queues.

Once the queue has been created, message management is handled by client applications and services that can access the queue to perform the key message operations, publish, consume, update, and delete. So a producer client will publish messages to the queue which later can be processed by another application or perhaps a particular microservice.

The PutMessages operation allows you to send one or more messages up to 20. Optionally, you can override the retention and visibility timeouts for the messages being sent in that request. After a successful publish, the queue service returns the ID for each message.

Instead of using the API or SDK, you can also use the CLI providing the queue ID, the array of messages in JSON, again up to 20 messages. You also need to know the message endpoint used by the queue in order to publish. You can find it on the queue details page in the OCI Console or by using the GetQueue request.

As a reminder from the previous lesson, the endpoint for the queue will be in this general URL format. Speaking of SDK clients, here's a Java code example where we build the request, then use the PutMessages method to send the batch of messages. Of course, it will be a consumer client that processes messages previously published to the queue.

A GetMessages request will return an array of up to 20 messages. And in addition to their contents, it returns each message ID, its expiration time, visibility timeout, the delivery count, and a receipt. Consumers will need that receipt later in order to delete or update the message.

Now if there are no messages on the queue, the call just returns after the timeout. While processing a message, as a reminder, the message is locked to prevent another consumer from retrieving it. However, if the consumer is unable to process the message within the visibility timeout, the message is then once again made visible in the queue. So it can be processed later or by another consumer.

Every time a message is retrieved, its delivery count is incremented. If that count exceeds the maximum delivery attempts configured for the queue, the message is moved to the dead letter queue. Here is the syntax for a CLI command to consume messages from a queue providing the queue ID and message endpoint.

In this example, we have a Java client again that is continually polling for messages in a while loop using the GetMessages method to retrieve the next batch of messages that are visible on the queue.

The update message operation extends or reduces the lock which is the visibility timeout of the message for the current consumer process. Consider a queue with different kinds of messages, and perhaps the consumer needs more time to process a certain type of message. In such a case, you might want to extend those visibility timeouts.

Do keep in mind that the visibility timeout cannot be extended beyond the maximum retention period parameter that was configured for that particular queue. The UpdateMessage call requires the receipt of the message which was provided in a response to a previous GetMessages request.

Again, here is the CLI syntax used to update a message, providing the message receipt string, the queue ID, and of course, the new visibility timeout value. To update a batch of messages with just one request, you can use the UpdateMessages operation.

Here's how the UpdateMessage call looks. Again, we're showing a Java example. But as a reminder, you can also choose other programming language SDKs to include Python, TypeScript, Go, .NET, or Ruby.

Once a delivered message is successfully processed by the consumer, they should delete the message from the queue to ensure it doesn't get processed by another consumer after the lock has expired.

You can either delete just one message using a DeleteMessage request or DeleteMessages for a batch of messages. As a reminder, these requests, similar to UpdateMessage, requires the receipt of the message which was provided in response to the previous GetMessages request.

Another alternative for deleting messages can be executed by clients with administrative permissions. However, PurgeQueue deletes all messages that are on the queue at the time it is invoked.

Let's look at the CLI syntax for those three APIs. The delete message operation has you provide the message receipt along with the queue ID. To delete a batch of messages, this command will expect a JSON file that contains all of the message receipts to be deleted.

And finally, here's the syntax for using the purge command, which indicates one of three purge type options, NORMAL which purges just the primary queue, DLQ queue which purges the dead letter queue, or BOTH, which purges both queues.

And here, once again, is a Java code example of using the DeleteMessage request in some sample code. Let's now recap the OCI Queue service guarantees. The queue will send an acknowledgment to the producer when a message is successfully published, and that message is guaranteed to remain persisted until it's either deleted by the consumer or the maximum message retention period configured for that queue has passed.

A message with a visibility timeout will not be delivered or made visible to other consumers until the timeout expires. If the timeout has expired and the consumer is not able to process the message successfully, the message is then made visible again to the queue for other consumers.

The other guarantee is that while the message is in the retention period, the queue service will not delete it. Only a consumer can process and delete a message within the queue's retention period.

And finally, an overview of the service limits. The OCI Queue service allows you to provision up to 10 queues per region in your tenancy. Producers can batch up to 20 messages as long as the total request doesn't exceed 512 kilobytes. When consumers request messages, they can choose to receive up to 20 messages as long as they don't exceed 2 megabytes.

And the maximum size for any single message produced to a queue cannot exceed 128 kilobytes. Now these limits might potentially increase with later version updates to the OCI Queue service. So check the documentation for the latest information.

And that wraps up this lesson on OCI Queue management and messaging operations. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/37e86e8c-099b-4af4-813c-ca97f45a1d85)

![image](https://github.com/qriz1452/oci/assets/112246222/5a16b653-a51b-45e2-a37f-55b8fc4bf51b)
![image](https://github.com/qriz1452/oci/assets/112246222/9ccbf313-79bf-42e1-8826-18fae479cf17)
![image](https://github.com/qriz1452/oci/assets/112246222/c3793320-de53-451a-8d3b-41dc378c5ebb)

![image](https://github.com/qriz1452/oci/assets/112246222/ec6035ae-6a23-4bae-80d2-d6af89e528d2)

![image](https://github.com/qriz1452/oci/assets/112246222/f68d60ff-0921-411b-aba0-28122eff6659)

![image](https://github.com/qriz1452/oci/assets/112246222/1e0f53af-ff61-48fa-9d72-1fe976dd581a)


------------
Now Playing : OCI Queue Use Cases


 let's consider a media processing application. And within the code base of the application, there is a producer component that serves as a media manager containing the logic to send asynchronous work request to various OCI queues using the Put Messages API.

In this example, there is a resizing microservice that retrieves messages from QA using the Get Messages API. Another microservice that handles media compression retrieving from queue B and another encoding microservice that processes requests from queue C.

By using a different queue for each service, each back end consumer can work independently and may even be configured to scale their capacity depending upon the workload to achieve a higher overall throughput. Here's an example highlighting a parallel processing use case. When an order request is received, the Create Order Logic of the shop service is triggered.

That service then publishes two copies of an order message which contains relevant data about the request to both the pay queue, as well as the report queue. From there, each of the two sets of consumer microservices, payment and reporting, retrieve messages from their respective queues in order to execute their own business logic, make payments, and recording purchase data, which can be achieved by invoking downstream services.

In this example, we're making a payment. And in parallel, creating a separate record capturing data for each product ordered per user to generate real time product analytics. If you extend the previous example, the payment service publishes the payment details to the verify queue.

From here, multiple verify payment microservices will check the details received during the transaction by forwarding them to the respective customers bank for verification. And since all of this processing must happen before the transaction can be cleared, while the customer is waiting, this architecture allows for scaling more verify payment services as required.

Or maybe more payment microservices, depending upon where the extra processing resources are needed. So to recap, any parallel processing scenario with a single queue, you may have a single producer or perhaps multiple producers publishing messages to the queue. But here, the key idea is to have multiple consumers processing the messages from the queue in parallel.

Also, in case there is a sudden spike in producer traffic, the queue itself can scale seamlessly to accommodate the increase in messages. Or you can configure the consumers to scale, which is called horizontal scaling in Kubernetes deployments.

Let's consider another scenario where the producer is publishing messages to a queue. But then the consumer that is processing those messages suddenly becomes unavailable. These are the use cases where reliable messaging is essential because the message remains persistent, and will not be lost or discarded until the retention period configured for the queue has ended, which, again, can be up to seven days.

That provides plenty of time for that consumer to become visible again or perhaps another consumer can be deployed to resume the processing. Consider scenarios where companies use email services for a variety of purposes, running marketing campaigns, delivering weekly or monthly newsletters to their customers, resetting customer accounts and new customer signups.

None of these actions indicate the need for urgent processing. Certainly, delays in email delivery won't interfere with the essential operation of the applications. But we do need to ensure that they are sent.

So implement a single consumer microservice dedicated to email delivery functions and totally independent of the sources of the email. So to do that, we configure an email queue. Then the multiple producer services place these email elements into the queue.

The service reads messages from the queue one at a time and sends the emails accordingly. Again, reliability is provided by the queue service itself, which persists the email messages, until they can be processed and sent.

Another situation could be that the consumer is unable to process a message because there is an issue with the message itself. So depending on the configured visibility time out and maximum delivery attempts parameter, soon, the unprocessed message will be moved to the dead letter queue.

So then while other messages can continue to be processed normally, this pattern allows for a queue administrator to sign in to the OCI console, to look at the message, and troubleshoot. Or you could even deploy an automated process to parse messages in the dead letter queue.

This way, you ensure that the queue is not blocked by a message which is corrupt or just unreadable by the consumer, which makes the queue more resilient. So clearly, we're not finished. After messages have been sent to a dead letter queue, let's consider five common error handling options, first.

Obviously, some messages in the deal queue will need to be reprocessed. However, the message would need to be fixed, first. The solution can be an automated script or human interaction to edit the message or even returning the correct message to the producer, asking them to resend a corrected message.

Secondly, some use cases might expect a certain percentage of bad messages. And perhaps, they can just be dropped. However, before deleting, a business process should examine them.

For instance, a dashboard app could consume the error messages and perhaps visualize them. Or how about using advanced analytics? Instead of processing each message in the DLL queue, a third option is to analyze the incoming data for real time insights or issues.

For example, a simple application could apply processing for calculations, such as the average number of error messages per hour or any other insights that help to inform you as to the errors in your producer applications. The fourth option is to interrupt processing.

You might need to stop the upstream workflow from one or more producers if bad messages are rarely expected. The consequences of continuing to receive those messages might be impacting the overall business process. So an interrupt action can either be automated or perhaps decided by someone responsible for handling manual troubleshooting and intervention.

And finally, while this might sound like the worst option, just let the dead letter queue fill up and do nothing. This may be perfectly appropriate in certain use cases, especially with transitory messages. The queue service will simply delete once the maximum retention period for messages has expired.

![image](https://github.com/qriz1452/oci/assets/112246222/051c4467-b716-4bbd-8816-eb59cec0ddf6)
![image](https://github.com/qriz1452/oci/assets/112246222/edf98e91-c72e-4526-b099-ff57bbb7f565)

![image](https://github.com/qriz1452/oci/assets/112246222/9141ef40-a651-4079-8f9b-978116e826e7)

![image](https://github.com/qriz1452/oci/assets/112246222/f731f57e-2472-4ee9-b860-e6b993c8259d)

![image](https://github.com/qriz1452/oci/assets/112246222/b40c086b-a370-4a6e-a983-8b4156ecb6e6)

![image](https://github.com/qriz1452/oci/assets/112246222/038e4dbd-8e81-43d3-acf6-80589fe8b7ed)





-----------
Now Playing : Which Messaging Solution Part1


we'll look at the evaluation factors for selecting an appropriate messaging solution that aligns with your business needs. Oracle Cloud Infrastructure provides a choice of technologies to support asynchronous communications and messaging. Of course, different services offer different benefits.

The OCI Notification service broadcasts messages to distributed components through a published subscribe pattern delivering secure, highly reliable, low latency, and durable messages for applications hosted on OCI. Oracle Integration Cloud is a fully managed service that allows you to integrate data and orchestrate business logic involving one or more Cloud-based SaaS applications, as well as on-premise apps.

As we learned in this module, OCI Queue provides a scalable system to process messages while handling complex management tasks such as guaranteed at least once processing tracking and client isolation using visibility timeouts.

OCI Streaming provides a fully managed scalable and durable storage solution for ingesting continuous, high-volume streams of data that you can consume and process in real-time. And Oracle's transactional event queues and advanced queuing are robust and feature-rich services that are integrated within Oracle databases providing for both basic queuing capabilities as well as multiple event streams per queue. And while it would be awesome to contrast all five of these service options, now is at the time is that simply is beyond the scope of this lesson.

Instead, when it comes to considering the most likely services to be used by cloud native and microservices developers, it generally boils down to using either OCI Queue or OCI Streaming, which we covered in the previous module. So which one should you choose?

Well, it really depends on the use case. So in the next few slides, we'll briefly take a look at each of these six considerations to help you determine which service would be the best choice for any particular business requirement, starting with the number of consumers.

Whether you require messages to be processed by a single consumer or multiple consumers is an important consideration. Now while both Queues and Streams allow for multiple concurrent consumers, the difference is that with Queues, each message is delivered to only one consumer at a time. On the other hand, Streams allow for every message to be read by multiple consumers.

In this OCI Queue example, we have an inventory microservice sending messages to a queue with three cart microservices consuming and processing those messages. However, each specific message will be consumed in process by just one of those cart services because once consumed, the message is deleted.

By contrast, in this streaming example, the payment microservice is sending data to a stream, but then OCI Streaming is allowing the same data to be distributed to three different consumers at the same time. Object storage is serving as a temporary staging area for an Apache Spark application. For example, a Spark job could process data to do error analysis. And an Autonomous Data Warehouse may store the data for long time reporting and other analytics jobs, such as website performance and a custom-built application could use the data for other downstream processing or to perform data transformations.

Next, for our second factor, let's consider the payment models impacting the cost for your application solution. OCI Queue uses a model that charges for each API request to the queue both when producing or consuming the messages. You get a million requests per month for free. Then the cost is 0.22 cents per 1 million requests.

Again, a request is considered to be an 8 kilobyte messages with larger messages or batches of messages counting as multiple requests. However, even though messages are always deleted once they have been successfully consumed, there is still no charge for the storage of messages that have not been consumed, which can be up to seven days to include the dead letter queue.

On the other hand, OCI Streaming charges for both throughput and storage. The charge for moving data into a stream or retreating data from the stream costs 2 and 1/2 cents per gigabyte. In addition, since all data is stored persistently in the stream until it has reached its expiration period, OCI Streaming charges $0.02 for each 100 gigabytes of data per hour.

Fortunately, however, there is no charge for all those use cases involving the movement of data directly into other OCI services, such as object storage or an Autonomous Database. And so we'll pause our lesson here. Please watch the part 2 video to learn about these other four considerations.

![image](https://github.com/qriz1452/oci/assets/112246222/bd2d0669-ed30-484a-ae4a-7b22ee4bf783)

![image](https://github.com/qriz1452/oci/assets/112246222/32bed480-f71b-44a4-a892-ee78d8f08a5b)
![image](https://github.com/qriz1452/oci/assets/112246222/7ab2bc22-062a-4bf1-83d9-490bf373f1e2)
![image](https://github.com/qriz1452/oci/assets/112246222/d9237119-5bda-4dbd-8b06-3cba0baa6f4f)

------
Now Playing : Which Messaging Solution Part2



Let's continue now with the next consideration factors, message size and messaging volume. These factors are an important design consideration for your solution depending on the use case. For example, consider a share trading application that will receive messages when stock share prices change.

Each message would be small in size, but message volume will be high due to the frequency of those updates. Therefore, the messaging system would need to be able to handle that high throughput. Whereas a system that supports larger messages, but has a lower throughput, may not be able to support this use case.

So let's first look at the throughput capabilities. When contrasting the total maximum rate for producing message data, the queue service provides for an unlimited number of messages supporting a data rate of up to 10 megabytes per second. For OCI Streaming, each partition is limited to a data rate of 1 megabyte per second, although you can create up to five partitions per stream.

For consumption, the queue can scale up to 1,000 concurrent consumers with each consumer allowed up to 1,000 requests per second, which could total up to a million requests per second. However, there is a limit for the maximum data consumption rate of 10 megabytes per second.

By contrast, OCI Streaming allows for up to 50 consumer groups per stream, each with a limit of five GET requests per second per partition. So if all of them were consuming from the same partition, that would provide for a total of up to 250 concurrent requests per second limited to a maximum read rate of 2 megabytes per second.

So clearly for message data throughput, OCI Queue can handle more volume. However, when looking at the maximum size for any one message as the situation becomes reversed, OCI Queue limits each message to no larger than 128 kilobytes, while the streaming service allows up to 1 megabyte for a single data message.

So then obviously if you need to process messages larger than 128 kilobytes, you'll be using streams instead of queues. The next factor to consider is message retention. While both OCI Queue and OCI Streaming can retain messages for up to seven days, a queue will only keep the message stored until it has been successfully consumed.

Now, technically it is the consuming client that's responsible for deleting the message, otherwise the message becomes visible to be retrieved again. By contrast, the very nature of a stream is to store all produced messages until their retention period has expired. It doesn't matter whether or not they've been read. The messages remain available to be read again by the same consumer or other consumers later on.

But of course, this comes at additional cost that I mentioned earlier, since you pay for the amount of storage that will be used. The next factor to consider is whether or not you need guaranteed ordering, which simply means that the messaging system will deliver the messages in the order in which they were produced.

Now while this is not always a requirement, sometimes it is very important. Take, for example, a use case in which a message is sent indicating that a new product has been added to a customer shopping cart, which is then followed by a message that the order has been placed and should now be executed. But then let's say that the order needs to be canceled. Perhaps the customer has changed their mind.

Well, it's critical that these messages are delivered in the order that they were sent. Now without guaranteed ordering, however, imagine that after the product and cart message was delivered, the next delivered message is order canceled. But then there was no order placed so there's nothing to cancel.

Next the order placed message is delivered, and the order is processed without being canceled. Obviously, that becomes a major problem for the logic of this application. So then the difference between queues and streaming is how they support guaranteed ordering.

The OCI Queue service supports standard queues which guarantees a best effort ordering. Messages are delivered to the consumers in the same sequence that they were received from the producer. However, occasionally messages could be delivered in a different order to avoid adding latency for order correction.

The queue generally as a best effort maintains the order when only one producer is adding messages. However, once additional producers are added to the scenario, this best effort becomes a bit more difficult. If this occurs, the order can shift. As you can see in this example, the queue allows them to be delivered regardless of which order might have been intended by the producers.

On the other hand, the OCI Streaming service can better handle multiple producers or consumers by providing for partitions and keys. Messages that have the same key will be stored on a single partition. And when they are consumed, the same ordering is guaranteed.

However a partition can also be configured to accept messages from multiple different keys as shown here. So to summarize, messages within a stream per partition are guaranteed to be delivered in the same order that they were produced regardless of how many producers are involved. Bottom line, streaming provides more capabilities over queues for guaranteed ordering.

Our last factor to consider is access support. Using industry standard formats and protocols to send and receive messages increases your flexibility for supporting multiple types of clients. Fortunately, both queue and streaming provide REST-based APIs, which allows for any HTTP client to produce or consume messages.

In addition, they both support the same list of software development kits for popular programming languages, which are all open source and available on GitHub. OCI also provides a command line interface reference for both services, which allows for quick access and full functionality without the need for programming.

The real difference here is that only OCI Queue supports the STOMP messaging protocol, while only OCI Streaming allows you to configure support for Apache Kafka clients with Kafka APIs or by leveraging Kafka connect configurations.

And with that is we have seen there is plenty of similarity and overlap of capabilities with queue and streaming services. But let's quickly review and revisit those six consideration factors with regard to their differences.

You're going to prefer a queue when you need to ensure that only one consumer will process a message, where streams work better for parallel processing from multiple consumers. Queue charges for each API request while streaming will also incur storage costs. While both queue and streaming support high throughputs, queues have more message bandwidth while streaming supports larger messages.

Queues are designed to deliver messages to one consumer, then they are deleted, while streaming retains all messages even after they are read. OCI Queue provides a best effort quality of service for message ordering, where streaming can guarantee message ordering within the scope of a partition.

And finally, while both services provide many of the same options for client access, only queue supports clients using the STOMP protocol, while only streaming supports Kafka APIs.

And that wraps up this lesson on comparing OCI Queue and OCI Streaming. Thanks for watching.
![image](https://github.com/qriz1452/oci/assets/112246222/058c471e-7ef7-44aa-bb0e-28b8a5f2d801)

![image](https://github.com/qriz1452/oci/assets/112246222/4d6e49a7-11f0-4703-a4f2-2a23117cca76)
![image](https://github.com/qriz1452/oci/assets/112246222/5b9be12b-b7c5-4065-bf9e-ef1143795fe6)
![image](https://github.com/qriz1452/oci/assets/112246222/7f4cc23c-1008-4ef2-b17e-79a70e087748)


--------
























