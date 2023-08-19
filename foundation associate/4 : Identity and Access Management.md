 Now Playing : IAM Introduction 


 Welcome to this lesson on OCI Identity and Access Management. In this particular lesson, we are going to look at very high level overview of OCI IAM. IAM stands for Identity and Access Management service. It's also sometimes referred to as fine-grained access control or role-based access control service.

There are two key aspects to this service. The first one is called authentication, or also referred to as AuthN. And the second aspect is referred to as authorization or also referred to as AuthZ. Authentication has to deal with identity or who someone is, while authorization has to deal with permission or what someone is allowed to do.

So basically what the service ensures is making sure that a person is who they claim to be. And as far as authorization is concerned, what the service does is it allows a user to be assigned one or more pre-determined roles, and each roles comes with a set of permissions. And that's basically what is shown on the screen here for authorization, as what kind of permissions do you have.

Now, there are various concepts which are part of this service or various features which are part of this service, starting with identity domains, principles, groups, dynamic groups, compartments, et cetera. And in subsequent lessons, we are going to cover these in more details.

Now I just want to talk about one such feature here, which is identity domains. Now identity domains is basically, as you see on the picture here, it's a container for your users and groups. So think about this as a construct which represents a user population in OCI and the associated configurations and security settings.

So how does this work in practice? Well, what we do first is we create an identity domain, and then we create users and groups within that identity domain. And then we write policies against those groups, and policies are scoped to a tenancy, an account, or a compartment.

And of course, the resources are available within a compartment. And again, compartment is kind of a logical isolation for resources. So this is how the whole service works. The part which is in a box here is identity domain. And users and the groups, authentication is done by common mechanisms like username and password, and policies is basically where you provide this role-based access control.

So you put these groups in one of the pre-determined roles, and then you assign some permissions against those roles. So this is how the service works in a nutshell. Now one thing which you would see in that previous slide was about these resources.

Now anything you create in the Cloud, all these objects, whether it's a block storage, it's a compute instance, it's a file storage, it's a database, these are all resources. And if these things are resources, there has to be a unique identifier for these resources, is how are you going to operate on these resources?

So what OCI does is it provides its own assigned identifier, which is called Oracle Cloud ID, OCID. You don't have to provide this. We do this automatically for all the resources. And the syntax is as shown on the screen here. So it starts with ocid1, there's a resource type, there is a realm, there is a region, and there is a unique ID here.

So what this means is ocid1 is just the type of resource, realm is basically set of regions that share the same characteristics. So there's a commercial realm, there is a government realm, et cetera. Resource type is kind of the type of the resource. It's a compute instance or it's a block storage device or et cetera.

And then region is basically the region code here. It used to be a three-character code, now it's much longer string. And then there is a unique ID here, which is unique to the resource you create. So what are some of the examples? Well, your account also has an OCID, so you see that here tenancy and you can see the syntax here starting with ocid1.

Now, of course, account is across multiple regions. So you don't have a region identifier here. Its realm is ocid1, and then there is the unique identifier. In case of block volume, you see the region, because block volume is specific to a particular region. So you see the region key here, and then the unique identifier.

So this is hopefully a quick kind of a couple of examples to show you how OCIDs work. If you are working on a management console, you're not going to interact with the OCIDs. But if you are using the CLI or the SDK, you would be using these OCIDs. And remember, Oracle generates these unique identifiers. You don't have to do anything as far as these OCIDs are concerned.

Hopefully this was a quick lesson on OCI IAM. Remember the two key aspects for the service are authentication, basically which deals with identity or who someone is or who someone claims to be, and authorization, which has to do with permissions or what someone is allowed to do.

And in subsequent lessons, we are going to dive deeper into some other concepts like compartments and identity domains and authentication and authorization. I hope you found this lesson useful. Thanks for your time. 

![image](https://github.com/qriz1452/oci/assets/112246222/33961e0a-6e0a-49b7-98c9-7c72257f0605)
![image](https://github.com/qriz1452/oci/assets/112246222/2aa98c77-e152-4410-8b76-07ea5666ee8a)
![image](https://github.com/qriz1452/oci/assets/112246222/8a2a9df1-dce4-4d47-9dc3-76c89719e1e0)
![image](https://github.com/qriz1452/oci/assets/112246222/89656842-2d2c-4564-9b4a-8ca936b6244b)

-------------

 Now Playing : Compartments 


Welcome to this lesson on OCI Compartments. Compartments are a unique feature within OCI. And these are really powerful, so let's explore.

So what is a compartment? When you open an account in OCI, you get a tenancy. That's another fancy name for an account. And we also give you a Root Compartment. So think of Root Compartment as this logical construct where you can keep all of your cloud resources. And then what you could do is, you could create your own individual compartments, like you see here.

There is a network compartment. There's a storage compartment. And the idea is, you create these for isolation and controlling access. And you could keep a collection of related resources in specific compartments. So the network resource has-- a network compartment has network resources, and storage compartment has storage resources.

Now, keep in mind, Root Compartment, as I said earlier, can hold all of the cloud resources. So it can be sort of a kitchen sink. You could put everything in there. But the best practice is to create dedicated compartments to isolate resources. You will see why. Let me just explain.

So first thing is, each resource you create belongs to a single compartment. So you create a virtual machine, for example. It goes to Compartment A. It cannot go to Compartment B. Again, you have to move it from Compartment A, or delete, and recreate in Compartment B. Keep in mind, each resource belongs to a single compartment.

The reason why you want to compartmentalize your resources is exactly shown on this slide. Why you use compartments in the first place is for controlling access and isolation. So the way you do that is, you have the resources, let's say in this case a block storage, kept in Compartment A. You don't want those to be used by everyone. You want those to be used only by the compute admins and storage admins.

So you create those admins as users and groups, write these policies, and they can access these resources in this compartment. So it's very important. Do not put all of your resources in the Root Compartment. Create resource-specific compartments, or whichever way you want to divide your tenancies, and put resources accordingly.

Now, how do resources interact if they are in different compartments? Do they all have to be in the same compartment? Absolutely not. As you can see here, resources in one compartment can interact with the resource in another compartment. Here, the Virtual Cloud Network is-- the compute instance uses the Virtual Cloud Network, but these are in two different compartments. So this is absolutely supported. And it keeps your design much cleaner.

Keep in mind that resources can also be moved from one compartment to another. So in this example, Compartment A had a virtual machine. We can move that from Compartment A to Compartment B. Another concept, which is very important to grasp is the compartments are global constructs, like everything in identity. So resources from multiple regions can be in the same compartment. So when you go to Phoenix, you see this compartment existing. You go to Ashburn, you see the same compartment.

Now, you can write policies to prevent users from accessing resources in a specific region. You could do that. But keep in mind, all of the compartments you create are global, and they are available in every region you have access to. Compartments can also be nested. So you have up to six levels nesting provided by compartments. You would do this again because this can mimic your current design, whether it's your organizational design or whether it's your ID hierarchy. You could create nested compartments. It just helps keep your design cleaner.

And then, finally, you could set quotas and budgets on compartments. So you could say that, my particular compartment, you cannot create a bare metal machine. Or you cannot create an Exadata resource. So you could control it like that. And then you could also create budgets on compartments. So you could say that, if the usage in a particular compartment goes beyond $1,000, you'd get flagged, and you get notified. So you could do that.

So that's Compartments for you. It's a very unique feature within OCI. We believe it helps keep your tenancies much better organized. And it really supports your current ID hierarchy and design. Thanks for watching. 
 
![image](https://github.com/qriz1452/oci/assets/112246222/d9d12e50-e5a0-43ab-8b2c-3f95db728e96)
![image](https://github.com/qriz1452/oci/assets/112246222/42c20141-0046-43c2-853f-d7d5aef76543)
![image](https://github.com/qriz1452/oci/assets/112246222/706a7060-b4ba-48f3-aea1-0a624b4712f3)
![image](https://github.com/qriz1452/oci/assets/112246222/d6ac64ca-b6f4-45d6-9843-1cdfd633757b)








----------
