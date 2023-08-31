 Now Playing : OCI Overview 

 
To keep things simple, let us break them down into seven major categories. Core infrastructure, database services data and AI, analytics, governance and administration, developer services, and application services. But first, the foundation of any cloud platform is the global footprint of regions. We have many generally available regions in the world, along with multicloud support with Microsoft Azure and a differentiated hybrid offering called Dedicated Region Cloud@Customer.

We have building blocks on top of this global footprint-- the seven categories we just mentioned. At the very bottom, we have the core primitives, compute, storage, and networking. Compute services cover virtual machines, bare metal servers, containers, a managed Kubernetes service, and a managed VMware service.

These services are primarily for performing calculations, executing logic, and running applications. Cloud storage includes disks attached to virtual machines, file storage, object storage, archive storage, and data migration services. OCI offers a complete range of storage services for you to store, access govern, and analyze your structured or unstructured data.

Networking features let you set up software-defined private networks in Oracle Cloud. OCI provides the broadest and deepest set of networking services with the highest reliability, most security features, and highest performance. Then we have database services. We have multiple flavors of database services, both Oracle and open source.

We are the only cloud that runs autonomous databases and multiple flavors of it, including OLTP, OLAP, and JSON. And then you can run databases in virtual machines, bare metal servers, or even Exadata in the cloud. You can also run open source databases such as MySQL and NoSQL in the Oracle Cloud Infrastructure.

Data and AI services. **We have a managed Apache Spark service called data flow**, a **managed service for tracking data artifacts across OCI called data catalog** and a **managed service for data ingestion and ETL called data integration**. We also have a managed data science platform for machine learning models and training. We also have a managed Apache Kafka service for event streaming use cases.

Then we have governance and administration services. These services include security, identity, and observability and management. We have unique features like **compartments that make it operationally easier to manage large and complex environments.**

Security is integrated into every aspect of OCI, whether it's automatic detection or remediation, what we typically refer to as cloud security posture management, robust network protection, or encryption by default. We have an integrated observability and management platform with features like logging, logging analytics, and application performance management, and much more.

Then we have a bunch of developer services. We have a managed local service called APEX, several other developer services, and a **managed Terraform service called resource manager.** For analytics, we have a **managed analytics service called Oracle Analytics Cloud** that integrates with various third-party solutions.

Under application services, we have a managed serverless offering called functions, and API Gateway, and an event service to help you create microservices and event-driven architectures. We have a comprehensive connected SaaS suite across your entire business, finance, human resources, supply chain, manufacturing, advertising, sales, customer service, and marketing, all running on OCI.

That's a long list. And these seven categories and the services mentioned represent just a small fraction of more than 80 services currently available in OCI. Fortunately, it is quick and easy to try out a new service using our industry-leading free tier account. We are the first Cloud to offer a server for just a penny per core hour.

Whether you are starting with Oracle Cloud Infrastructure or migrating your entire data center to it, we can support you in your journey to the cloud. That's it. OCI, a broad and deep cloud platform. Thanks for watching. 

![image](https://github.com/qriz1452/oci/assets/112246222/5f50cd1a-e9f0-4ba1-8e0e-dbbcd88e111f)
![image](https://github.com/qriz1452/oci/assets/112246222/498c7708-43bc-46c8-b4c2-d48b0b06032f)
![image](https://github.com/qriz1452/oci/assets/112246222/ec1268c2-5996-44f9-acce-140561567d31)




----------
 Now Playing : OCI Architecture 

 
Welcome to this lesson on OCI architecture. In this lesson, we will cover the core constructs of OCI's physical architecture, starting with regions. Region is a localized geographic area comprising of one or more availability domains. Availability domains are one or more fault-tolerant data centers located within a region but connected to each other by a low latency, high bandwidth network.

Fault domains is a grouping of hardware and infrastructure within an availability domain to provide antiaffinity. So think about these as logical data centers. We looked at it in the previous lesson. Today, OCI has a massive geographic footprint around the world with multiple regions across the world. And we also have a multicloud partnership with Microsoft Azure. And we have a differentiated hybrid cloud offering called Dedicated Region Cloud@Customer.

But before we dive into the physical architecture, let us look at how do you choose a region. First thing is choosing a region, you choose a region closest to your users for lowest latency and highest performance. So that's a key criteria.

The second key criteria is data residency and compliance requirements. Many countries have strict data residency requirements. And you have to comply to them. And so you choose a region based on these compliance requirements.

The third key criteria is service availability. New cloud services are made available based on regional demand, at times regulatory compliance reasons, and resource availability, and several other factors. Keep these three criterias in mind when choosing a region.

So let's look at each of these in a little bit more detail. Availability domain. Availability domains are isolated from each other, fault tolerant, and very unlikely to fail simultaneously. Because availability domains do not share physical infrastructure, such as power or cooling or the internal network, a failure that impacts one availability domain is unlikely to impact the availability of others.

So as you can see in this graphic here, a particular region has three availability domains. One availability domain has some kind of an outage is not available. But the other two availability domains are still up and running.

We talked about fault domains a little bit earlier. What are fault domains? Think about each availability domain has three fault domains. So think about fault domains as logical data centers within availability domain. So as you can see in the picture here, we have three availability domains. And each of them has three fault domains.

So the idea is, you put the resources in different fault domains. And they don't share a single point of hardware failure, like physical servers, physical rack, top-of-rack switches, or power distribution units. You can get high availability by leveraging fault domains.

We also leverage fault domains for our own services. So in any region, resources in that most one fault domain are being actively changed at any point in time. This means that availability problems caused by change procedures are isolated at the fault domain level. And moreover, you can control the placement of your computer database instances to far domain at instance launch time. So you can specify which fault domain you want to use.

So what is the general guidance? The general guidance is we have these constructs, like fault domains and availability domains, to help you avoid single points of failure. We do that on our own. So we make sure that the servers, the top-of-rack switch, all are redundant. So you don't have hardware failures. So we try to minimize those hardware failures as much as possible.

You need to do the same when you are designing your own architecture. So let's look at an example. You have a region. You have an availability domain. And as we said, one AD has three fault domains. So you see those fault domains here.

So first thing you do is when you create an application, you create this software-defined virtual network. And then let's say it's a very simple application. You have an application tier. You have a database tier. So first thing you could do is you could run multiple copies of your application.

So you have an application tier, which is replicated across all domains. And then you have a database, which is also replicated across fault domains. Why do you do that? Well, it gives you that extra layer of redundancy. So something happens to a fault domain, your application is still up and running.

Now, to take it to the next step, you could replicate the same design in another availability domain. So you could have two copies of your application running. And you can have two copies of your database running. Now, one thing which will come up is, how do you make sure your data is synchronized between these copies?

And so you could use various technologies, like Oracle Data Guard, to make sure that your primary and standby the data is kept in sync here. And so you can design your application your architectures like these to avoid single points of failure. Even for regions where we have a single availability domain, you could still leverage fault domain construct to achieve higher visibility and avoid single points of failure.

Let's summarize what we learned in this lesson. So we looked at region. Region comprises of availability domains. Availability domains comprise of fault domains. So let's look at the inside-out view. So first let's start with fault domain. Fault domain provide protection against failure within an availability domain. Availability domain themselves provide protection from entire availability domain failures, particularly in a multi-AD region.

And then you have this concept of region pair where in every country we operate on, most of the countries we operate, we have at least two data centers. So you could use the second data center for disaster recovery or backup, or it also helps you with to comply with data residency and compliance requirements. And then not only this, we also have SLAs on availability, management, and performance. 

![image](https://github.com/qriz1452/oci/assets/112246222/c6435318-2842-4b8a-a527-fff0d3cd0b6d)
![image](https://github.com/qriz1452/oci/assets/112246222/39c90d3c-3ad1-4e76-94d9-0b4d392ab1f4)
![image](https://github.com/qriz1452/oci/assets/112246222/e03d8d45-7976-4a6c-a95c-a127cf7dceb4)
![image](https://github.com/qriz1452/oci/assets/112246222/c6a4379a-9134-436e-a865-fd4cbc8cf82a)
![image](https://github.com/qriz1452/oci/assets/112246222/e19ec057-329e-46fa-90eb-e40d586e6dee)
![image](https://github.com/qriz1452/oci/assets/112246222/501226a7-4335-4edc-8699-76b601d35f24)


---------
 Now Playing : OCI - Distributed Cloud 

 


Hello, and welcome. Let us look at OCI Distributed Cloud in this lesson. A unique aspect of Oracle Cloud is the fact that it's distributed, which means customers can get Oracle Cloud Services lots of different ways. It gives exceptional flexibility and choice.

Customers can get our services through our public cloud regions-- more than 41 plus global regions across the world with all the security, reliability, and scalability benefits. They can also get cloud services and cloud capabilities on premises through our hybrid offerings like Exadata Cloud@Customer, and they can get the whole portfolio of cloud services through our Dedicated Region and dedicated cloud.

Finally, we understand that most customers use more than one cloud provider, and customers can leverage the best of cloud services through our multicloud offerings. In this lesson, we will look at hybrid and multicloud in a lot more-- in a lot more details.

So let's look at first our hybrid cloud services. The first offering we have is the Dedicated Region Cloud@Customer, which is our air-gapped private isolated regions. We'll look into more details in the next slide.

Then we have a service, which is called Oracle Cloud VMware Solution. And here what we do is we provide a VMware-based environment in OCI using which you can migrate on premises VMs to the cloud in a seamless fashion. So the use case here would be disaster recovery. It would be your whole data center migration.

Then we have Autonomous DB on Exadata Cloud@Customer. And the idea here is all the advanced Autonomous DB capabilities are available in your own on-premises environment. And finally, we have a offering called Roving Edge Infrastructure, which is basically a dense, portable, compute and storage optimized server that has been ruggedized to operate in remote and austere environments. And this is good for use cases where you want to process data and compute at the edge in a remote disconnected fashion. So these are some of the hybrid cloud services we offer.

Let's look at Dedicated Region Cloud@Customer in a little bit more detail. Well, this offering provides all the OCIs 100-plus public cloud services in a self-contained independent cloud region in a physical location that you choose. So in your own data center of choice. And this is an air gap offering, meaning that this region can be fully disconnected from the outside network. Customers can start small, and they can scale all the way to 450-plus racks very quickly.

Oracle will install, operate, support, and upgrade each Dedicated Region in the same way we maintain public cloud regions worldwide. So the use case here-- basically, there are two use cases. One is for data residency to meet your governance, regulatory compliance and data privacy requirements for sensitive data. And it can also be used to run latency sensitive applications. So these are some of our hybrid cloud offerings, including the Dedicated Region Cloud@Customer.

Let us change gear and let us look at some of our multicloud offerings. So the first thing here is this OCI Azure Interconnect which was launched in 2019. So the idea here as you can see on the slide is Oracle and Microsoft have a private interconnect running between them. And today, we have 12 regions worldwide, as you can see on this slide, where this interconnect is available.

And if-- this is a private interconnect, meaning that the latency is very low, less than 2 millisecond latency. And the pricing for this offering is solely based on the ports and the circuits you provision on both sides, and there is no charge for the bandwidth-- inbound or outbound bandwidth consumed. So the use case here would be running database on Oracle, running application here on Azure, and running them in a seamless fashion because of this low private latency to the private interconnect.

Then, in 2022, we took this offering one notch higher and we created this Oracle database-- launched this Oracle Database Service for Azure. And the idea here is it's an Oracle-managed service for Azure customers to provision access and operate Oracle Database Services-- Database Services in OCI with a familiar Azure-like experience.

So just in a few clicks, customers can connect their Azure subscription to the OCI tenancy and the service automatically configures everything required to link the two cloud environments. So the main difference between this, and OCI Azure interconnect is, as you can see here, the interconnect portion, you don't have to manually deploy that. The service actually automates it. So this takes like a service-based approach as compared to like a manual approach of configuring the interconnect.

And finally, the service also sends metrics, logs, and events for the OCI Database you provision to the Azure tooling. So you get this unified telemetry and monitoring where you can see all the dashboards and you can see all the services which are available. And like the OCI Azure Interconnect, there is no additional cost to operate this service. So these are two notable offerings we have for multicloud-- OCI Azure Interconnect and Oracle Database Service for Azure.

So that's a quick introduction on OCI Distributed Cloud and the combination of public cloud, dedicated cloud, and our multicloud offerings. I hope you found this lesson useful. Thanks for your time. 

![image](https://github.com/qriz1452/oci/assets/112246222/fd2ca14d-8d91-4a19-95f4-31fc0845d730)

![image](https://github.com/qriz1452/oci/assets/112246222/526e793f-97f4-4ebe-ba7f-e464ec6a4a95)
![image](https://github.com/qriz1452/oci/assets/112246222/e1a6d1bd-6a65-4366-8946-41958b2920c3)
![image](https://github.com/qriz1452/oci/assets/112246222/57a39450-070f-4815-a545-7eba39b01403)
![image](https://github.com/qriz1452/oci/assets/112246222/8c23785f-4798-4273-9ff9-e008622f288a)








--------









