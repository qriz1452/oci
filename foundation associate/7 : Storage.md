 Now Playing : Storage Introduction 

 Welcome to this module on OCI storage services, what they are and how they work. Before we go and dive deeper into the various storage services available within OCI, let us look at storage requirements because they are many and varied.

So first is when you decide on what kind of storage to use, you want to answer whether you want persistent storage or non-persistent storage. Then you have to answer, what kind of data are you storing? Is it database files? Is it videos? Is it audios, photos, text? What kind of performance do you need? What kind of capacity do you need? How many input/output per second, IOPS? How much is the throughput?

Then you need to decide on durability, how many copies of data you want to maintain. There's a difference between persistence and durability. Persistence basically means you safely store the data. Durability means making multiple copies of the data, replicating the data. So in case you are storing them safely, even if one copy goes bad, you still have other copies to fall back on.

Connectivity is important as well, whether you want local storage or you want network storage. And how does your application access that storage data? And finally, the protocol, because that determines what kind of applications you can build, whether it's block, file, or something as simple as HTTP. Now, these are some storage requirements, and I'm sure there are many more. But you have to wrestle through these before you decide on what storage services to use.

Let us look at the lineup of OCI storage services. And I'm just going to cover some of the few-- the main ones here. There are others, which we will cover in subsequent lessons. So the first thing is local NVMe. Local NVMe means, as you see in the picture here, you have a data center, which we call as "availability domain" within OCI. You have a compute server, and you have a locally-attached storage.

So when you think about local NVMe, think about locally-attached storage. These are NVMe SSDs. Super high performance gives you hundreds of thousands of IOPS. And you could run your most performance-sensitive applications using local NVMe. Then what we do is we take this locally-attached storage, and we move it to a remote server, a network server.

So in this picture, you see there's a compute instance, and it's talking to a storage server, which is on the network. So the advantage here is the storage can be truly persistent and durable and extend beyond the lifetime of the instance itself. This kind of storage is called "block volume." In this case, the storage, the data is managed as fixed-sized blocks. So you create a partition. You create a file system. Then you mount the file system. And that's how your compute instances use the storage service-- so block volume.

File storage is a similar kind of a storage, still in the same availability domain, but it's a shared file storage system. So in this case, you see two compute instances. And then, they have a need to have a shared storage system, where they can read and write, but the storage is shared. So it's very similar to block volume, but the difference here is you manage the storage as files and directories. You don't partition the disk. You still do some of the things like you mount the file system. And that's how your instances use the shared storage. So think shared, think file storage.

And then finally, we have object storage, which is storage for the web. So you have storage-- this is a kind of storage you would use for photos, videos, log files, text file, any kind of files you store on the web. Typically, the way it is accessed is you have an internet client, who accesses this particular-- these objects using simple and familiar HTTP verbs, like PUT and GET-- PUT meaning you create an object, GET meaning you download an object.

And so, these are the main storage services which exist within OCI. Along with that, we have several data migration services. So we have two which are related to data transfer-- data transfer disk and appliance. Disk is, basically, you send us your disks, and we migrate the data. Appliance is you use a much larger appliance to send the data to us. And then finally, we have a service called Storage Gateway, which is a Linux appliance. Sits in your data center, and using that, you can migrate data to OCI.

So that's it-- a bunch of storage services, each suited for a different use cases. In the next few lessons, we are going to dive deeper into each of them. Thanks for watching. 

![image](https://github.com/qriz1452/oci/assets/112246222/86ff2dc8-2cad-45c6-9ff4-f8874bfa75f9)


---------

 Now Playing : Object Storage 

 Welcome back to the lesson on OCI Object Storage. What is OCI Object Storage? Well, it's an internet-scale, high-performance storage platform. In here, data is managed as objects. Irrespective of the kind of data you store, they are all managed as objects.

It's ideal for unstructured data, like your logs, your videos, your pictures, your text files. It's a regional service. It's a public service. There are multiple storage tiers. And we'll look into each of them. You can still have private access from OCI resources like your compute instances. So even though it's a public service, you could still have private access and several other mechanisms to do that.

And then there are lots of advanced capabilities. This is a foundational course. So we're not going to go into those features. But it's a very rich-- feature rich service. So what are the scenarios in which you would use an OCI Object Storage? Well, you use it as a content repository. Like I said, you can use it for structured and semi-structured data. You could use for big data scenarios. And very importantly, you could use it for archive and backup purposes.

So how does object storage work? Let's look into this. What are the key resources here? So the first thing is object itself. Anything you store in object storage is referenced as object. Think about object as key value pairs or name value pairs, name being the name of the file your storing and the value being the actual value of the file. And then objects can also have object metadata. And you could define your own metadata there.

Objects are stored in a bucket as you can see on the graphic here. And the buckets have your unique name within the tenancy. Important thing to keep in mind is there is a flat hierarchy. And anytime you see a folder structure, that's simulated by the object storage service by using something called prefixes.

So remember all the objects you store just go in a flat hierarchy within the service. There's also something called a namespace. Namespace is a logical entity. It's a top-level container for all buckets object. And it has to have a globally unique name.

So let us look at an example of how this works. You can see here, I have this URL, which is the API endpoint for object storage. That's how you access these objects. Remember, this is public service. You access them using a public API endpoint. And that's-- API endpoint is, one of the examples is shown here.

So in this case, let's start from the bottom. You have an object which has a notation /O and anything beyond that-- after that is the object name. So here I'm storing object, which is log.zip. It goes into a bucket, which is called development.

And that's denoted by the /B. And then there's a namespace, which is the account name. And you can see that there. So that's how the API is constructed. And the first few things part there are the object storage service name. And it's a regional service, so you see a region there, US San Jose 1.

So let's look at some of the tiers. We talked about object storage tiers. So the first tier in object storage is called the standard tier. It's also referred to as the hot tier. What it means is this you keep all the critical data, which you want to retrieve instantaneously, you keep it here.

The retrieval is instantaneous. And it's also strongly consistent. So any time you update the data, we give you the most recent copy of that data. There is a second tier, which is called infrequent access. What it means is you still have critical data, but this is a long-term critical data. You don't need it right away.

So think about backups. You would keep them in infrequent access. There are some restrictions here. The data has to be stored for a minimum of 31 days. And there is a retrieval fees when you get the data back. What is the upside? It's 60% cheaper than the standard tier. And there is a retrieval fee, but it's significantly cheaper than the standard tier.

And then there's a third tier, which is called the archive tier. This is for your data, which you don't need right away. You rarely access this data. So think about tape storage. It's basically tape storage in the Cloud, but much easier and much more feature-rich.

So there's a minimum retention requirement of 90 days. And there is a process where objects need to be restored and then downloaded. So when you put data in archive storage, you'll need to restore it. The minimum time required to restore is an hour. And then you need to download. And you get 24 hours, which you can extend to 40 hours. But you need to download that data to standard tier, and then you can access from the standard tier.

But that's not all. There is a feature called auto-tiering, and what it does is it looks at your access pattern. And let's say you have unknown access pattern or your data access pattern keeps changing, it can move the data from standard tier to infrequent access tier and vise versa. And it can move back to standard if your objects start getting used again.

The idea here is this is intelligence given by the service. There is no retrieval fees. There is no pro-rated storage fees. And using this feature, you can significantly reduce your cost because you can go from standard to infrequent access, 60% cheaper, and then move back if your objects start getting used.

That's not it. There are lots of other features. One feature, which is really important is lifecycle management. And as you can see here, it helps you transition the data from higher cost tiers to the lower cost tiers. So you could say after 30 days, move my data from standard tiers to archive tiers, and delete them after 180 days. And you write a rule. And the service takes care of that.

You can also do versioning because as you are storing your data, you can have multiple versions of that data. And these objects are automatically versioned. You just specify that on the bucket and we take care of that.

So data encryption. It's very important because you're storing sensitive data in the Cloud. You want it to be safe. So we give you data encryption by default. You cannot turn this off. You can always bring your own keys for very stringent requirements. You have that option.

How do you access all this data? You access all this data using a simple API call. Like I showed you in the beginning, you call that API, use familiar HTTP verbs, and you can access this data. So that's it folks. Object storage, a very feature-rich service. Next time you're taking that picture, chances are it is stored in an object storage. Thanks for watching. 

![image](https://github.com/qriz1452/oci/assets/112246222/0f1ef711-05f8-4ad1-9326-bfd158307d9f)
![image](https://github.com/qriz1452/oci/assets/112246222/cc609a38-0ef2-4552-9198-beadbbcaca74)


-------

 Now Playing : Block Volume 



 Welcome back. Let's look at OCI Block Volume service. At the very core, the Block Volume service provides persistent and durable storage to compute instances. As you can see on this graphic here, there's a compute instance which is talking to disks, persistent and durable disks, which are sitting on a network server.

So the core idea here is to get the persistent and durable storage. What does that actually mean? Well, if you look at the same picture again, your compute instance talking to a block storage disk. You can create and attach these disks to the compute instances. You can detach and delete the disks. And most importantly, you can keep the data even after you delete the instance.

So the data is stored independently of the instance lifecycle. And that is the number one reason why you would use a Block Volume service to provide that persistent and durable storage, persistent meaning it's a safe storage. It stays beyond the lifecycle of the compute instances itself. Compute instance gets terminated is still safe. And durable means we make multiple copies. So even if we lose one copy, we have other copies of the data available in the data center.

Let's look at the Block Volume tiers. We start with a tier which is called lower cost. This is good for large sequential I/O workloads like streaming data warehousing. Then you have a balanced tier, which is a balanced choice for random I/O, things like your boot disks. Then we have a higher performance tier, which is for the most I/O demanding workloads.

And then we have ultra high performance tier, which is for the highest I/O-demanding workloads. So things like your relational databases. And you can see the characteristics down below starting with two IOPS per gig, going all the way to 225 IOPS per gig.

And then we also have this feature, which is called auto-tune performance. And what it does, it changes the volume performance to lower cost when the volume is detached. When the volume is reattached, the volume performance is automatically adjusted to the previous setting. Why would you do it? Well, it helps you save on the costs.

So with Block Volumes or data in general, you want that data to be safely stored. So we have encryption turned on by default. You cannot turn this off. And you can bring your own keys. And we also have encryption for data at REST.

And we also have encryption in transit, meaning when your virtual machine is talking to the block storage service, the traffic is encrypted in transit between the virtual machine and the block service. Block service also has this feature called read/write shareable where a single disk can be shared with multiple VMs. And these VMs can read and write to the single block volume.

We also have this capability of resizing Block Volumes. And what this means is you could do online resizing or offline resizing. With online resizing, you can expand the volume size without detaching the volume from an instance. So it keeps your applications up and running. And you can still change the size of your Block Volumes.

We also have a feature which is called replication of Block Volumes. And as you can see in this graphic here, the Block Volumes are being replicated from one region to another region. Why would you do that? You would do that for disaster recovery. You would do it for migration. Or if you are expanding your business, you would leverage this feature. The idea here is to replicate the data to multiple regions. And keep in mind this replication is asynchronous.

And then finally, we have this feature called volume groups. Block Volume service provides you with the capability to group together multiple volumes in what we call as a volume group. This simplifies the process to create time consistent backups of running applications that span multiple volumes across multiple instances. And the idea here is then you can-- once you create a volume group, you can restore an entire group of volumes from a volume group backup. So folks, that's it. That's Block Volume Thanks for watching. 

![image](https://github.com/qriz1452/oci/assets/112246222/0cacdc9f-9184-4c39-a8f0-4ce04e932046)

![image](https://github.com/qriz1452/oci/assets/112246222/384a3080-6c4d-489a-a3e5-9868d7fbc9f3)
![image](https://github.com/qriz1452/oci/assets/112246222/95ab4b5b-5db3-48bb-b3ea-254ae21690b7)

-------

 Now Playing : File Storage 

Welcome back. Let's look at OCI File Storage Service. Before we dive deeper into the service, let us first look at what is file storage. Very simply, file storage is hierarchical collection of documents organized into name directories. All of us are familiar with it. Whether you are using Linux machines or you're using Windows machines, you are familiar with how you organize your files into folders and directories and several of them.

Now, the differences in the cloud, we have distributed file systems. These are not local to your machine. And the two most common ones we use are NFS for Linux, network file system, and server messaging block, SMB, for Windows. Both the protocols and the standards are supported by Unix and Windows. And there are lots of details around operating systems and hypervisors which support these.

So what are the use cases for file storage? Well, the first use case are, many of the enterprise applications, Oracle has applications like EBS, E-Business Suite, which really needs shared files storage. So that is provided by the file storage service.

There are general purpose file systems. All of us have used corporate directories where we have shared folders, where we keep our content. So that's an example of a general purpose file system. Microservices and containers actually are typically stateless.

And if you think about how we create these architectures, there has to be a place where you maintain the state for these microservices and containers. Many times, customers would use shared file system to manage that state. And there are several other use cases like HPCs, scale-out applications, analytics, and many more where you would use file storage service. So in a nutshell, how does file storage work?

As you can see in the picture here, you have a single data center in an OCI region. You have a couple of compute instances. They are all talking to the shared file system. And that's your OCI File Storage Service. So it's shared storage for compute instances.

Today, currently, we support NFSv3 as a distributed file system standard. You can take backup of the file system, what we call as snapshots. So that provides you protection. If your folders or directories get deleted, you can always take backups called snapshots.

And then we take security really seriously. So you have data at REST encryption. And you also have in-transit encryption, meaning when your compute instances are talking to the shared file system, that traffic is encrypted. Since this is a foundational course, we are not going deep into how you create a file system and the amount points and all the details. But the basic idea is you create a file system.

And then you mount it to the compute instances. And then you start using them. Many instances can share the same file system. And they can read and write from that file system. So that's it. File system, next time you're thinking about directories and folders and general purpose file system, think about using OCI file storage service. Thanks for watching. 

![image](https://github.com/qriz1452/oci/assets/112246222/2f827411-f6f2-4b28-8ac8-4772ba45c3e6)
![image](https://github.com/qriz1452/oci/assets/112246222/7763f4a2-4683-4ce4-8810-8eb1d3a1345d)
![image](https://github.com/qriz1452/oci/assets/112246222/db0b7750-ba62-4ed6-8d11-69ae34ca6e3e)
![image](https://github.com/qriz1452/oci/assets/112246222/93dd56ed-da6d-4c71-abb0-76ce22b21d5a)


-------
























