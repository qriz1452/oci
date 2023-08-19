 Now Playing : Oracle's Data Management Strategy 

 This is the Oracle University module on Oracle Data Management strategy. I'm going to explain Oracle's Data Management strategy to you. We're going to talk about what it means to be simply complete and completely simple. It's a fun play on words, right? So I'm not going to waste any of your time. Let's dive right in.

App development paradigms are in a rapid state of transformation. Modern app development is simplifying and accelerating how you deploy applications. Also simplifying how data models and data analytics are used. Oracle data management embraces modern app development and transformations that go beyond technology changes. It presents a simply complete solution that is completely simple. Immediately you can see benefits of the easiest and most productive platform for developing and running modern app and analytics.

Let's start by looking at how Oracle Data Management is easy and most productive for development of our modern applications. Oracle Database is a converged database that provides best of breed support for all different data models and workloads that you need. When you have converged support for application development, you eliminate data fragmentation. You can perform unique queries and transactions that span any data and create value across all data types and build into your applications. This also includes structured and unstructured data. The Oracle converged database has the best of breed for JSON, graph, and text while including other data types, relations, blockchain, spatial, and others.

Now that we have the ability to access any data type, we have various workloads and converge data management that supports all modern transactional and analytical workloads. We have the unique ability to run any combination of workloads on any combination of data. Simply complete for analytics means the ability to include all of the transactions, including key value, IoT, or Internet of Things, along with operational data warehouse and lake and machine learning.

Oracle's decentralized database architecture makes decentralized apps simple to deploy and operate. This architecture makes it simple to use decentralized app development techniques like coding events, data events, API driven development, low code, and geo distribution. Autonomous Database or ADB now supports the Mongo database API adding more tools for architectural support.

Autonomous Database or ADB has a set of automated tools to manage, provision, tune, and patch. It provides solutions for difficult database engineering with auto indexing and partitioning and is elastic. You can automatically scale up or down based on the workload. Autonomous Database is also very productive. It allows for focus on the data for solving business problems. ADB has self-service tools for analytics, data access, and it simplifies these difficult data engineering architectures.

Now that we discovered how development is easier and most productive, let's look at running modern apps and analytics. Running applications means thinking about all the operational concerns and solving how to support mission critical applications. Traditionally this is where Oracle excels with high availability, security, operational solutions that have been proven over the years.

Now having developer tools and the ability to scale and reduce risk simplifies the development process without having to use complex sharding and data protection. Mission critical capabilities that are needed for the applications are already provided in the functionality of the Oracle Data Management architecture. Disaster recovery, replication, backups, and security are all part of the Oracle Autonomous Database.

Even complex business critical applications are supported by the operational security and availability of Oracle ADB. Transparently, it provides automated solutions for minimizing risk, dealing with complexity, and availability for all applications. Oracle's big picture data management strategy is simply complete and completely simple with the converged database, data management tools, and the best platform.

It is focused on providing a platform that allows for modern app development across all data types, workloads, and development styles. It is completely scalable, available, and secure, leveraging the database technologies developed over several years. And it's available consistently across the environment. It is the simplest to use because of the available tools and running completely mission critical applications.

Simply complete and completely simple. Easy to remember and easy to incorporate into your existing architectures. Thanks for watching and don't forget to get your free Cloud account if you haven't signed up yet. Take care. 

![image](https://github.com/qriz1452/oci/assets/112246222/51455d40-22c0-403e-b86f-83dbc3073224)
![image](https://github.com/qriz1452/oci/assets/112246222/87811291-b4e0-4cc4-9286-5139015dca5d)
![image](https://github.com/qriz1452/oci/assets/112246222/d0eeda94-8d1f-4d3e-a585-de4cc34c6262)
![image](https://github.com/qriz1452/oci/assets/112246222/fc8fabc9-cf7a-4bae-8726-80faa24f5943)



------------

 Now Playing : Oracle Database Offerings 


 Hey there. Kay Malcom here. I'm going to talk about the different Oracle Database offerings we have at our back and the ways you can actually use them, if you have ever wondered about on-premise, DBCS, ADP, Exadata, or third-party cloud. So let's talk about this a little bit more.

Let's compare Autonomous Database to how you ran the database on premise. How you ran the database on the cloud using our earlier Cloud Services, Database Cloud Services, and Oracle Exadata Cloud Service. The key thing to understand is Autonomous Database, or ADB, is a fully managed service. We fully manage the infrastructure. We fully manage the database for you.

In on premise, you manage everything-- the infrastructure, the database, everything. We also have a service in between that that we call a co-managed service. Here we manage the infrastructure, and you manage the database. That service is important for customers who are not yet up to 19c. Or they might be running a packaged application like E-Business Suite. But for the rest of you, ADB is really the place you want to go.

And why do you want to do that? Well, because it's fully managed and, because it's fully managed, is a much, much lower cost way to go. So when you talk to your boss about why he wants to move to ADB, they often care about the bottom line. They want to know like, am I going to lower my costs?

And with ADB, because we take care of a lot of the tedious chores that DBAs normally have to do and because we take care of best practices, configurations, we can do things at a really low cost. We have some analyst reports now that have looked at this cost of ownership around ADB.

In particular, on this slide, we have Wikibon Research. And they analyzed the costs of running Autonomous Transaction Processing versus running it on prem, running Oracle Database on Amazon using their RDS-managed service, and then ATP. What they found was very interesting. You've heard a lot of noise about-- yeah, you know. Amazon is actually pretty expensive. And this research sort of confirms it.

If you run an Oracle database on RDS for Amazon, they found that the cost was either about the same as on prem or even higher. If you want to use disaster recovery, any kind of configuration like that, multizone configuration, the cost was actually about 50% higher to use Amazon versus on prem.

But with ATP, they found the cost was almost half of what you could do on prem. And so it's a really nice report. I recommend you go take a look at it.

Now, you know, you may have heard that moving to Autonomous Database requires some extra work. And there is some element of truth there. So what did we do? We've got a tool that helps you look at your current database on prem. This tool will analyze what features you're using and let you know, hey, you know you're doing something that's not supported for ADB, for example.

If you're running some release before 19c, we don't support it. If you're doing stuff like putting database tables in the system or sys schema, we don't support it. There are a few things that very few customers do that we don't support. And this tool will flag those for you.

And then the next step, it's pretty simple. You just use our Data Pump import/export tool to move your data out of your database on prem into the object store on the Cloud. And then you simply import-- you know how to use Data Pump to import-- the data off the file and the object store into the database. Then you're done. Pretty simple process.

If you've already tuned this application on prem for years and years, there's no need to use the autotuning capabilities of ADB, if you don't want to. Your DBAs can sort of preserve all the existing tuning they did-- all the existing indexes on the database. DBAs have a really important role here to make sure your database continues to run well, your existing database.

Now, we more recently have come out with a new service on our Cloud called the Database Migration Service. This service automates those steps we just talked about on the previous slide. With Autonomous Database Migration Service, you can just point us at your source database on prem or even on some other cloud. Whatever it is, we will take care of everything from there and move that, go through all the steps I talked about on the previous slide for you, and move your database to ADB on the Cloud.

Even better, we now are working with our Applications customers to make it really easy for them to move their packaged applications to Autonomous Database. The Oracle development teams that built JD Edwards, PeopleSoft, Siebel have now all certified that those packaged applications can run with Autonomous Database no problem. Our EBS team is working on it. And that'll be coming soon, sometime next year.

And once you do that, we have a fully managed service available on our Cloud that lets you take your entire application stack on the middle tier and the database tier, move it to our Cloud. Move the database part to Autonomous Database. And they will also manage your middle tier for you.

And then we're working with third parties also to certify their applications with Autonomous Database. We list a few here-- MESTEC, MineSense, NEC, Zebra. And then we're also working, of course, with all the tools' vendors who have tools that run against the Oracle Database, people like Tableau, BusinessObjects, and more. And we've got all of these guys and gals certified. And if you have more questions about whether your tech stack is certified on ADB, there's a link at the bottom of the slide that lets you look them up there.

And then, of course, we have lots of real customers who have moved on-prem databases to ADB. TaylorMade is a pretty well-known golf club manufacturer. They had a big Oracle data warehouse on prem. They have successfully moved that to Autonomous Data Warehouse a couple of years ago. They are getting much lower cost of ownership around doing this. They're getting much better performance. And basically, the vision of Autonomous Data Warehouse is playing out very well for them.

I mentioned earlier that we have this great tool called APEX, or Application Express. We have a version of Autonomous Database just for any APEX application. And just to review, what is APEX again?

Well, APEX is a low-code tool. It is our low-code tool that lets you rapidly build data-driven applications where the data is in the Oracle Database, really easy and really rapidly. We estimate at least 10 times faster than doing traditional coding to build your applications. What we're seeing is much, much higher productivity than that. Sometimes 40, even 50 times faster coding.

Out of the box, it comes with really nice tools for building things-- your classical forms and reporting kinds of workloads. It gives you things like faceted search and capabilities to do things like see on an e-commerce website where you get to choose things like dimensions, like I want a product where the cost is in this range. And it might have some other attributes. And it can very quickly filter that data for you and return the best results.

And it's a really nice tool for iterating. Now, if your user interface doesn't look quite right, it's very easy to tweak colors and backgrounds and themes. Another reason it's so productive is that the whole middle tier part of your application is fully automated for you. You don't have to do anything about connection management or state management. You don't have to worry about mapping data types from some other 3GL programming language to data types. All of that is done for you.

And we've got millions of APEX apps, including live labs out there in the market. 3,000 or so are being built pretty much every single day. So the bottom line is if you're still doing traditional coding to build your database applications, you really should rethink things. That should be the exception. Do something quick. Do something fast. You should be using a low-code tool like APEX for building pretty much all your database-related apps.

And here's an example of a customer. Wilson Truck Lines, they're using a combination of ADB and APEX to build an application for their business. And their story is really kind of interesting. They actually originally built an application on Amazon. And they used traditional coding methods, recommended by Amazon, which is like lots of code.

They were able to redevelop an application that took them three months to code on Amazon in two days using APEX. This is that 45 times productivity I was talking about. And like I said, this is actually pretty typical with APEX. And so this application gave them great performance and great interactive response times. And they're very happy with it. The combination of ADB and APEX really rocks.

Here I just want to show you a little bigger picture of what we're doing here. We're not just talking about a data warehouse on the cloud that does massively parallel query really fast. This is what the original first generation data warehouse on the cloud did. It's much more than that.

So beyond this, we've built a collection of self-service tools that would make your analysts and your data scientists really productive. I mean, you don't need an engineer to get data from your data sources and transform it. You don't need them to build the OLAP models. We've got self-service tools that do the data loading for you in this drag-and-drop fashion.

We have ETL transformation tools. Again, they let you specify transformations in a drag-and-drop fashion on the screen. We have all sorts of other tools and, in the service, the full power of the converged analytic technologies, things like graph analytics, spatial analytics, machine learning. All of this is built into this new platform.

Now, a big, new capability around machine learning is something that we call AutoML. That lets any data scientists give us a data set, tell us what the key feature is that they want to analyze, and what the predictions are. And we will come up with a machine learning model for them out of the box. Really that easy. Plus, we have the low-code tool APEX that I mentioned earlier.

So this environment is really powerful for doing more than traditional data warehouses. We can build data lakes. We are integrated with the object stores on Oracle Cloud and also on other clouds. And we can do massively parallel querying of data in the core database itself and the data lake.

And of course, we support all third-party popular analytic tools. And here's an example. Seattle Sounders Football Club is a customer using Autonomous Data Warehouse, or ADW. They were able to build a very powerful analytic environment to analyze their sports statistics. And as you ladies and gents know, sports are becoming really focused on analytics, all different kinds of sports.

They were able to build an ML model quickly to detect things around various models to help them figure out, you guessed it, how to score more goals. That's the objective in soccer, right? And of course, the pay-per-use model of the cloud lets them lower cost quite a bit. And beyond the Seattle Sounders, we're also working with the English Premier League. They are using Autonomous Data Warehouse technology for their environment.

Now, just to start closing things out, beyond the database technology, there is the business side. We want to make your path to ADB really easy from a business standpoint, a decision-making standpoint as well.

So if you're an existing Oracle customer, you have an existing Oracle Database license you're using on prem, we have something called BYOL, Bring Your Own License, to OCI. We have the Cloud Lift Service. This huge cloud engineering team across all regions of the world will help you move your existing on-prem database to ADB for free.

And then, finally, we announced fairly recently something called the Support Rewards Program. This is something our customers are really excited about. It lets them translate their spending on OCI to a reduction in their support bill. So if you're a customer using OCI, you get a $0.25 to $0.33 reward for every dollar you spend on Oracle's Cloud.

You can then take that money from your rewards and apply it to your bill for customer support, for your technology support even, like the database. And this is exactly what customers want as they move their investment to the cloud. They want to lower the costs of paying for their on-prem support.

And so just to summarize what we talked about today, my big focus here was ADB. And we first talked about our converged database architecture for software that, of course, we deliver with ADB.

And the big thing is ADB and the fact that it's a fully managed cloud service. It manages the Exadata infrastructure. It manages fully the database software on top of it. It gives you "out of the box," best-practice configurations for security, for availability, and for performance. You avoid all the problems you might run into on prem when you miss one of those best practices. It automatically patches and tunes the database for you as well.

Now, we've talked about money. This lowers costs greatly. So ADB has lots of value. But the big thing I think to think about is really that it lowers costs. It lowers that cost via automation, higher productivity, less downtime, all sorts of areas. We showed you some TCO studies from Wikibon Research and from IDC to support those claims. We're not making them up.

And finally, we talked a lot about how it's really quite easy now, as most of you have now moved a lot of your databases up to 19c. ADB is a great place to go. Take those existing Oracle Databases you have. Move and modernize them to a modern cloud infrastructure that's going to give you all the benefits of cloud, including agility and lower cost.

And finally, we really want to make it easy for you to adopt this technology. So on our Cloud, we have something called the Always Free Autonomous Database Service. This service lets you get your hands on ADB. Try it out for yourself. You don't have to believe what we claim about how great this technology is.

And we have other technologies like Live Labs that you can find on developer.oracle.com/livelabs that lets you do all kinds of exercises on this Always Free ADB infrastructure. Really get your hands dirty. And see for yourself how productive it can be. Thanks for watching. 

![image](https://github.com/qriz1452/oci/assets/112246222/ef7e57b6-0a6e-4e19-be26-307e8622e430)
![image](https://github.com/qriz1452/oci/assets/112246222/7528aadd-e296-447e-8a82-e6bb132c6a8b)
![image](https://github.com/qriz1452/oci/assets/112246222/1b01f41a-3bf6-404d-a4b1-c8062a6ea608)
![image](https://github.com/qriz1452/oci/assets/112246222/4a444cd6-7c15-4858-8f90-d76d50449809)
![image](https://github.com/qriz1452/oci/assets/112246222/d83f4d39-47d2-4f07-bf58-0fbb52647a2b)
![image](https://github.com/qriz1452/oci/assets/112246222/8594c24c-bd81-4b9b-a012-277abc326c46)
![image](https://github.com/qriz1452/oci/assets/112246222/56f0619a-c507-45b4-b5c1-f698fdd92fea)
![image](https://github.com/qriz1452/oci/assets/112246222/d9fe5c5d-2ea0-40e0-bc88-77f44784c308)
![image](https://github.com/qriz1452/oci/assets/112246222/a1a5e0c2-11f9-45a9-8941-b7ac68d0cc72)










