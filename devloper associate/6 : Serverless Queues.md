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












