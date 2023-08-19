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

 Now Playing : AuthN and AuthZ 
 

Welcome back to this lesson on authentication and authorization. Before we get into more specific details, let's look at what is a principal. A principal is an IAM entity that is allowed to interact with OCI resources. There are two kinds of principals primarily in OCI. One is your users. Think about people who are logging on to your console or using your CLI or SDKs users, human beings actually using your cloud resources. And then the resources themselves can be principals.

So a good example of a resource principal is an instance principal, which is actually an instance which becomes a principal, which means that it can make API calls against other OCI services like storage. Also when we talk about principals, we have groups.

And groups are basically collection of users who have the same type of access requirements to resources. So you can have a storage, admin group where you could group all the human beings who are storage administrators and so on and so forth.

So let's look at some of the details starting with authentication. Authentication is sometimes also referred to as AuthN. As we recap from the previous lesson, authentication is basically figuring out, are you who you say you are? And the easiest way to understand this is all of us deal with this on an everyday basis. When you go to a website and you provide your username and password to access some of the content, you are being authenticated.

There are other ways to do authentication. The one common for cloud is API signing keys. So when you are making API calls, whether you're using the SDK or the CLI, you would use the API signing keys which use a public private key pair to sign these APIs calls and authenticate these API calls.

It uses an RSA key pair, as you can see here, with both a public key and a private key. There is also a third way to do authentication and that's based on authentication tokens. And these are Oracle-generated token strings. And the idea here is you can authenticate third-party APIs, which don't support OCI authentication model.

So in this example, we are showing an ADW, calling an ADW, Autonomous Data Warehouse API call where we are using these auth tokens. Still your identity is being followed. These auth tokens can be used for this purpose.

Now let's very quickly look at authorization. So authorization deals with permissions and figuring out what permissions do you have. In OCI, authorization is done through what we call as IAM policies. And policies, think about these as human readable statements to define granular permissions. So you have a couple of examples here. And the policy syntax is always something similar.

In the next slide, I'll talk a little bit more about what this statement means. Remember, policies can be attached to a compartment, or they could be attached to a tenancy. If they're attached to a tenancy, it applies to everything within that tenancy. If it's applied to a compartment, it applies to only the resources within that compartment.

So how is AuthZ done in OCI? We talked about policies. What does the syntax look like? As you can see here, the syntax is always-- always you have to start with an allow. Everything is denied by default. So you don't really have to write a deny statement. So you say Allow group_name.

A group is basically a collection of users. So you cannot try to policy on individual users. You always operate at a group level. To do something, there is a verb. On some resources, there's a resource type. And there's a location. Location can be a tenancy. Location can be a compartment. And you can make these policies really complex with adding conditions. And again, foundations course. So we are not getting into a lot of these complex topic. But you could really write complex policies.

So just to give you an idea of what the verbs might look like, there are four levels of verb. There is a manage. There is a use. There's a read. And there's a inspect. So manage basically means you can manage all resources. Use basically means you can read. But you could not do things like update and delete and so on and so forth. And you can read more on the documentation.

Resource type basically can be all resources, meaning everything in your account, or it could be compute resources, database resources, whatnot, all the resources you have. Now, you could operate at a family level, which is meaning all the entities within that resource family, or you could even go very granular. So you could say that in compute, I just want somebody to operate on the instances but not work on the instance images.

So you could actually do that. So this is how you would write a policy. There are some exceptions to this rule. There are policies you would write for services and such. But again, it's a foundation score, so we're not getting into those advanced details. This is typically how you would do a transition in OCI. 

![image](https://github.com/qriz1452/oci/assets/112246222/c526292c-6c3f-4111-a7ea-273f629d2157)
![image](https://github.com/qriz1452/oci/assets/112246222/4904b79e-2225-4220-a37f-7e36d09f4dba)
![image](https://github.com/qriz1452/oci/assets/112246222/116f800a-d131-4eaa-be40-a6598f9212ee)
![image](https://github.com/qriz1452/oci/assets/112246222/2d0c6d3e-bf3d-471b-8835-e3217721ae7e)
![image](https://github.com/qriz1452/oci/assets/112246222/51882c33-0682-41de-8600-d61e18033a01)


-------------
 Now Playing : Tenancy Setup 

 
Welcome back. In this particular lesson, let's quickly look at how you can set up your tenancy or your account. Well, so until now, we saw that there is a tenancy administrator. This is the person who creates an account and is kind of responsible for day to day operations of this account.

But a best practice is to not have tenancy administrator do kind of day to day operations, but rather have somebody who is an admin for your particular account. And this can be a set of users, not just one person. And you can group all of them under this, like a group such as OCI admin here. And then you write policies for this particular group, and let them operate on their own specific compartments.

So let me talk about some of these things which are shown in the graphic here. So the first thing here, kind of a best practice is what I just said, don't use the tenancy administrator account for day to day operations. You should not be doing that.

The second best practice is to create dedicated compartments to isolate resources as is shown here. So there's a sandbox compartment. It could be a compartment for a production, or development, or a business unit, or it could be a region based compartment, or whichever way you want to isolate your resources.

These compartments are available across all regions. So when I say region based, meaning you could say North America uses this compartment, and Europe uses this compartment, et cetera. So you could isolate your resources in kind of a geographically based on where your users are. But you should have individual compartments. You should not put everything under the root compartment.

And then the third best practice is to enforce the use of multi-factor authentication. And the idea with multi-factor authentication, it's a method for authentication that requires the use of more than one factor to verify a user's identity. So it would be something like a password, something you know, and a device, something you have.

So these are the three best practices you should definitely enforce as you set up your tenancy. So what are the policies you need to write if you have a setup like this where there's a tenancy administrator, but you are not using this account for day to day operations?

So what are some of the policies you need to give to these OCI administrators, so, in fact, they could be a proxy for the tenancy admin, and you could swap out the tenancy admin with the OCI admin?

There are some policies which you absolutely need to provide. So the first thing is you should provide access to manage all resources. I'm showing these policies in tenancy here, but you could scope them to a compartment as well. So you could say compartment ABC. You could have that name here. But you should provide access for the OCI admins to manage all resources, like a tenancy admin would do.

And then there are resource types for the IM service itself, which you need to use in policies so that the admins which are available in the OCI admin groups can use OCI Identity resource types. So for example, in IM, you don't have any aggregate resource type. So you have to use them individually.

So there is a resource type called domains. There's a resource type called users, groups, dynamic groups, policies, compartments. And there are some more identity providers, network sources, tag, defaults, tag namespaces, et cetera. I'm not listing to a whole set of resource types here.

But you have to write these policies, otherwise, OCI admins cannot create users. They cannot create groups. They cannot create policies. So if you have to give them access to manage policies, being able to create users, groups, et cetera, you should actually write these policies.

So this is the least amount of policies you need to write for the OCI admins in order for them to be kind of day to day admins for your tenancy. So hopefully, this is a quick lesson on how you can set up your tenancy following these best practices. I hope you found this lesson useful. Thanks for your time. 

![image](https://github.com/qriz1452/oci/assets/112246222/c879a2aa-8c14-4026-a17c-7cb908f45467)

--------

















