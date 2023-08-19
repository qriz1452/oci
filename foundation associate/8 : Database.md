 Now Playing : Database Introduction 

 Hello and welcome. In this lesson, let us look at the various database services available in Oracle Cloud Infrastructure. So as you can see here on the slide, we have the Oracle Public Cloud which is Oracle Cloud Infrastructure. And as part of Oracle Cloud Infrastructure, there are three main categories of database services which are available.

So the first category is what we refer to as Base Database Service. And in here, you create databases on virtual machines with a choice of compute shapes, a single node or two nodes, and block volume storage capacity. The service provides built-in automation for common database lifecycle management tasks, such as backups.

Now if you need to provision a DB system-- these are called DB systems-- for development or testing purposes, a special, fast provisioning single-node VM system is also available as part of this offering. The second offering we have is called the Exadata Database Service on Dedicated Infrastructure, what you see here.

Now this is a combination of hardware and software that provides you an infrastructure which is solely for running Oracle database. And now what you see with these two database services is this term called Co-Managed. What we refer to by Co-Managed is you as customers manage the database, but the infrastructure is managed by Oracle. So that's what we mean by Co-Managed.

And then the final database category we have available in OCI is the Autonomous Database. Now Autonomous Database is the world's first autonomous data management service in the cloud which delivers automated patching, upgrades, and tuning while the system is running, without any human intervention. So this database is self-managing, self-securing, and self-repairing, which helps to eliminate manual database management and human errors.

So as part of that, you see this autonomous description here. It comes from the fact that it's self-managing, self-securing, and self-repairing. Now this database-- and we have a lesson on this later on in this module-- comes in two flavors-- Shared and Dedicated Exadata Infrastructure, as you can see here.

Now Shared Exadata Infrastructure, with this option, you provision and manage only the autonomous database, while Oracle deploys and manages all the underlying infrastructure. On the other hand, the Dedicated Exadata Infrastructure, what we do is we give you a completely dedicated compute, storage, network, and database service just for you, just for a single benefit. So that is the difference between Shared Exadata Infrastructure and Dedicated Exadata Infrastructure.

Now if you wish to have all these capabilities running in your own data center, then we have an offering, which is called Cloud@Customer. And here you would use Cloud@Customer because it enables you to meet your company's demanding regulatory requirements, data residency requirements, and application latency requirements, while at the same time, you can leverage all the benefits of database services running in OCI Public Cloud.

So like the OCI Cloud, you get Exadata Database Service which runs on Cloud@Customer. And you also get Autonomous Database running on Exadata Cloud@Customer. And again, it's either co-managed or it's autonomous. So that's it. This gives you a good overview of what database services are available in OCI as well as your on-premises environment to Cloud@Customer capability. I hope you found this lesson useful. Thanks for your time. 
![image](https://github.com/qriz1452/oci/assets/112246222/73ccbd97-9939-4b7a-9e36-f26a3e9ae21d)


-----


 Now Playing : Autonomous DB 


Welcome to this lesson on Autonomous Databases, which summarize what Autonomous Databases are in the intro lesson. But let's look into them in a little bit more detail here. So the key idea with Autonomous Database. Autonomous Database is a cloud database that uses machine learning to automate database tuning, security, backups, updates, and other routine management tasks, traditionally performed by DBAs.

So the idea is all database and infrastructure management, monitoring, and tuning processes are automated. And DBAs can now focus on more important tasks. That's the key idea behind Autonomous Databases. So that's what is being shown here. It's a complete infrastructure automation. It's a complete database automation. And it's automated data center operations and machine learning.

So the idea is, as much as you can automate and let your users focus on differentiated higher level tasks, the better it is because they don't have to get involved with a lot of manual tasks and repetitive tasks. They don't have to do these because some of these tasks are also error prone. So using technologies like machine learning, we can take that out from the equation, let them focus on the value, additive, higher level differentiated tasks.

So what kind of options and flavors are supported in OCI today? So there are two options which are supported. One is called shared. One is called dedicated. As the name specifies, dedicated basically means you have exclusive use of the Exadata hardware. Underline Exadata hardware. This is where you have Autonomous Database and the Exadata completely dedicated to you. In

The shared model, you provision and manage only the Autonomous Database, while Oracle handles Exadata infrastructure deployment and management. It is, again, supported for both these models. What are these two models? Within Exadata, you have two database types which are supported.

One is called Autonomous Transaction Processing. This is for your OLTP. So think about transactions. And the second one is Autonomous Data Warehouse. This is for your online analytical processing. So these are two distinct database types, model supported, workloads supported. And these are supported both for the shared option as well as the dedicated option.

And again, as we said many times, autonomous itself, irrespective of whether you are running shared or dedicated or ATP or ADW, those are the nomenclature for transaction processing and data warehousing. Some of these tasks listed on the slide are all automated. So things like backup, things like patching, upgrade, database tuning, these are all automated for you.

In the previous slide, we looked at Autonomous Database and the two workload types around Autonomous Data Warehouse and Autonomous Transaction Processing. But there are two other workload types we didn't discuss in the previous slide. And these are Autonomous JSON Database and the APEX Service. Let's look at them really quickly.

So Oracle Autonomous JSON Database is Oracle Autonomous Transaction Processing but designed for developing NoSQL-style applications that use the JSON documents. JSON stands for JavaScript Object Notation document. So this is optimized for NoSQL style applications.

Well, on the other hand, Oracle APEX Service is a feature scoped and significantly lower priced workload type of Autonomous Database that enables developers to rapidly build and deploy low code APEX applications. So this workload type is geared towards developers who are building low code APEX applications.

Again, just this kind of team keeps coming back again and again. It's a complete automation. That's a big focus for autonomous. So things like scaling up, scaling out, tuning, security, patching, all these are supported. And the key idea is the idea of self securing so that we have capabilities to protect against both external attacks and malicious internal users, self repairing, meaning self tuning, so meaning we can prevent downtime, including unplanned maintenance.

And self driving, meaning a lot of these repetitive manual tasks are automated. So users can focus on differentiated higher level, value additive tasks. And you can see that even though we do all this, none of the database goodness, things like RAC, Data Guard, Database Vault, all these features, we don't sacrifice. And all of these are still supported in this Autonomous Database model.

So folks, that's Autonomous Database. Next time you think about doing that repetitive database task, don't do it. Just go adopt Autonomous databases. And you can see the difference for yourself. Thank you for watching. 

![image](https://github.com/qriz1452/oci/assets/112246222/da4c99bc-d854-44a1-8e46-d93d83a06aa6)

![image](https://github.com/qriz1452/oci/assets/112246222/11e97c12-c9e5-4580-83b9-e02dde82de5d)
![image](https://github.com/qriz1452/oci/assets/112246222/aa0633a0-6060-4582-aa7c-203d6c47e7ac)
![image](https://github.com/qriz1452/oci/assets/112246222/5819aaa6-1b30-4f28-8e8e-84faf360ae75)

--------
 Now Playing : MySQL 

 
Welcome to this lesson on MySQL Cloud Service. Sometimes also referred to as MySQL Database Cloud Service. Let's look into all the capabilities of this particular service. And we'll hone on two key concepts or two key features of this particular service.

So some of the generic features you could host MySQL databases in the Cloud through the service. You could rapidly provision them. You could apply patches, rollback, do all those things, all elastic compute. So you could increase or decrease resources, whether it's compute or storage. You could do replications. And you have all sorts of security features available.

And then it reduces your cost of ownership. Because now, you're using MySQL as a Cloud Service instead of running it on your own. The two features I really want to highlight in this particular lesson are high availability and HeatWave. So what is high availability? High availability basically gives you that fault tolerance. It has a lot of benefits like automatic failover, increased uptime, zero data loss. So you could create a standalone MySQL database in OCI. Or you could create this high availability database.

Now, what does these actually mean? With a standalone option, you get a single instance MySQL DB systems back ended by the resilient and secure OCI block volume. This option is good for dev and test and development environment. But if you're running in production, you really want to go with the high availability option. This option enables applications to meet higher uptime requirements and the zero data loss tolerance.

When you select the high availability option, MySQL DB system with three instances is provisioned across different availability domains or different fault domains. The data is replicated among the instances. Now, your application connects to the single endpoint to read and write data to the database in case of a failure.

If an availability domain is not available or a fault domain is not available, the MySQL Database Service will automatically failover within minutes to a secondary instance without any data loss and without requiring to reconfigure the application. So next time you are running MySQL in production, definitely think about using the high availability option because of all the benefits it provides.

The second key feature I want to talk about is the MySQL Database Service with HeatWave. So what is HeatWave? HeatWave is a new integrated high performance in memory query accelerator for MySQL Database Service that accelerates MySQL performance by order of magnitude for analytics and transaction queries. HeatWave scales out to thousands of course.

MySQL Database Service with HeatWave is the only service available in the market that enables database admins and app developers to run both OLTP and OLAP workloads directly from their MySQL database. This eliminates the need for complex, time consuming, and expensive data movement, and integration with a separate analytics database. And also, the thing to keep in mind that this service is optimized for and exclusively available in Oracle Cloud Infrastructure.

Again, it's a very new feature. Give it a shot. It definitely adds a lot of value compared to the traditional approach of using MySQL only for OLTP purposes. 
![image](https://github.com/qriz1452/oci/assets/112246222/19b0b36d-6363-48ed-bb01-ee238e3465d4)

![image](https://github.com/qriz1452/oci/assets/112246222/15305d02-8014-4988-8e8c-f2f7c9363964)
![image](https://github.com/qriz1452/oci/assets/112246222/b0801b80-0f43-4f94-9582-5ecc7617fac6)


----------
 Now Playing : NoSQL 

Welcome to this lesson on Oracle NoSQL Database Cloud Service. This is going to be a short lesson. Let us look at some of the key capabilities provided by this particular service. So some of the defining characteristics of this service are listed on this particular slide. It's sort of a long list.

The service is fully managed. It's elastic. It has high performance. And the number to look therefore is predictable single digit millisecond latencies with high workloads, with high bandwidth. You have data model flexibilities. So using the same database, you could-- its database supports document, fixed schema, key value models. And there's a single application interface. And it supports all these models.

You get enterprise grade security. You can manage all kinds of access. It's a low operating cost, because you're running in the Cloud. Of course, NoSQL database is used a lot by developers. So it's developer friendly. It has these Rest APIs. It's always available. So it leverages all the high availability features of Oracle Cloud Infrastructure. And then it also runs on-premises.

So I know this is sort of a long list of features. But some of the key features to keep in mind here is the data model flexibility, supporting document, fixed schema, key value payers, high performance, single digit millisecond latencies, and the fact that it's available both in the Cloud as well as on-premises. And it works seamlessly the same both places. Those are the top features to consider for this particular service.

What are some of the top use cases for the NoSQL Database Cloud Service is well, lot of these modern applications, whether it's mobile applications, IoT, a lot of these online advertising applications, all of these applications where there's a huge amount of volume, the key thing which is common between all these applications-- huge amount of volume you would use on NoSQL Database Cloud Service.

Again this is supposed to be a very short lesson. The idea is to give you just a quick introduction on what Oracle NoSQL Database Cloud Service is. I hope you found this quick intro useful. Thank you for watching. 
![image](https://github.com/qriz1452/oci/assets/112246222/b578b9ad-fee5-47e4-afe5-bc69c77df589)
![image](https://github.com/qriz1452/oci/assets/112246222/e5b5d97c-c773-44e0-bd11-637b13c78a01)





------
 




 




-----
