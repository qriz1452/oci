 Now Playing : Pricing 

 Welcome to this module on governance and administration. As part of this module, the first lesson we are going to look at is around pricing. Now pricing is a complex topic. A lot of pricing with a lot of Cloud providers is complex. Oracle's pricing is simple. It's transparent. And it's lower pricing than our competitors. So let's look at some of these in this particular lesson.

The first thing is what kind of pricing models do we support? So we definitely support pay as you go pricing where you charge only for the resources you consume. There is no upfront commitment. There is no minimum service period. And the usage is metered for. This is Pay as you go for most of the resources.

But for some resources like our managed serverless platform called Functions, it takes you to the next level. So you have this concept of consumption based pricing, where you are charged only when you consume the resource which is different than pay as you go, because you have to pay for the VMs, even though you might not be using them or they might be running idle.

So we support pay as you go and consumption based pricing and all sorts of models in between. And then the second model we support is called Annual Universal Credits. And the idea here is you commit to an annual pool of funds. In return because of this commitment, you get significant savings. But the thing is you have to use these credits within 12 months.

If you end up with more resource usage, then you pay for them on a pay as you go basis. And the discounts here vary based on the size of the deal and term of the deal. There's also something called Monthly Universal Credit. And you should read more about that on our website.

And the last option is bring your own licenses. This is for customers who are running on-premises licenses if they want to reuse that in the Cloud. Why would you do it? It reduces your overall cost, and you could reuse those licenses in the Cloud.

Now let's look at factors that impact pricing. The first factor which impacts pricing is the size of the resource. So bigger resources are going to cost you more. That's just natural, because the service pricing is based on consumption and the type of resource you use. So the bigger resources will cost you more.

Data transfer is a big part of the pricing. And we'll talk about some of that on the next slide. The resource type you choose also determines your pricing. So virtual machines versus bare metal have a different price points versus serverless has a different price point. If you bring in your own licenses, they have a completely different pricing model. So keep all that in mind.

One thing to keep in mind with OCI is we have the same pricing across the world. So all the OCI regions have the same pricing. This is very different than the typical traditional Cloud model where the pricing is very local. So you pay a different place in the US. You pay a different place outside the US in different countries where the Cloud regions operate.

Let's look at the data transfer cost and why it is so important. Well, the thing is data transfer can be up to one fourth of your bill or even higher. And the reason is your applications are always communicating, whether they are communicating to the end users or they are communicating internally.

So to give an example, if you look at the OCI Region 1, we have 2 availability domains. You have an application which might be running in a high availability mode across two availability domains. Now in case of OCI, you don't really pay for any data transfer happening between these two ADs as you can see on the graphic here. In case of some other Cloud providers, they charge you for data transfer between ADs.

In a way, this is penalizing customers for achieving high availability, which is one of the goals of Cloud computing. So it doesn't make a lot of sense that way. Also with Oracle, incoming traffic is free as it's the industry standard. But outgoing traffic is 10 times lower than some of the other Cloud providers. And you heard me right. It's 10 times lower. It's not 10% lower. It's nearly 10 times lower.

So you save a lot of money, particularly if you have applications which have high data transfer usage. You end up saving significantly by using OCI. And that's it. We wanted to keep it very high level, very simple-- the three pricing models we support.

And then the highlight of our pricing is it's simple. It's transparent. And some of the elements like data transfer cost you 10 times lower. So it's definitely a lot cheaper than some of the traditional Cloud pricing out there. Thanks for watching. 

![image](https://github.com/qriz1452/oci/assets/112246222/7313cc1c-ce25-4683-9cbe-f42bab5762df)


-------

 Now Playing : Cost Management 


Welcome to this lesson on Cost Management. Let's look at what tools OCI provides to you to manage your costs. So the first option you have are these things called OCI Budgets. You can use budgets to track costs in your tenancy. After creating a budget for a compartment, you can set up alerts that will notify you if a budget is forecast to be exceeded or if spending surpasses a certain amount.

As you can see here on the screen, we have two kinds of budgets set, one for $1,000, one for $100. And you could look at the forecast and other things and get notified if you are close to exceeding that or if you have exceeded it. It's an important way for you to manage your cost and be notified if the cost surpasses your forecast or your plans.

The second tool, which is available to you, is around cost analysis. And this, as the name indicates, you could analyze your cost after you have spent it, but it's a nice way to look at your past cost and then make changes for the future. If there are elements you want to change, this is a great way to do that.

There are also usage reports. Today, currently the usage reports get downloaded in form of these CSV files, and these are generated daily. And they show usage data for each resource in your tenancy. The CSV files are stored in an object storage bucket that is accessible using a cross-tenancy policy, so you could look across not just your tenancy, you could look across multiple tenancies if there are multiple tenancies being used.

Now, a couple of other tools in this area include service limits, the tool to set your limits, quota, and usage. So as with any Cloud, we limit how many resources you can run in a traditional tenancy to prevent things like fraud and misuse. But you can always-- for legitimate cases, you can always change your limits for a particular service, and there is a way to look at your current limits and change it. And you could submit a support request to do that, but that tool provides you at a glance what kind of limits you have broken down by things like your availability domain so you can dive deeper and get more details here.

Then, finally, as we talked about, compartments are these logical entities, which you can use to isolate resources and have better access to these resources, so if you are using these compartments, you have ability to set up compartment quotas. And the way it works is you have these different policies you could write, where you could set the maximum number of Cloud resources that can be used for a compartment. So you could say that, in this particular compartment, you can only use, let's say, 10 virtual machines. You could unset that and go back to the default service limits, or you could zero it out. So as an example, here, you could say, this particular compartment should not have any Exadata resources. And you could do that to prevent misuse and also save on your cost.



---------

 Now Playing : Tagging 

 Welcome to this lesson on tagging. Tagging is a very, very important capability within OCI, and you should definitely leverage it. Let's talk more about it. So at the core, what is tagging? Tags are basically these key value pairs, which you could use to better organize your resources.

So as you can see here, this particular instance, I have put two different tags. So there is a tag which is environment with a value of production. And there's another tag which is project and has value of alpha. And I could do multiple tags. You should always check service limits as to how many tags I could put on a particular Cloud object. But in this case, I'm putting two tags here.

And these again, just to recap, are simple key value pairs or name value pairs where the key is the key for the tag, and then the value is the value you want to assign. So the idea here is you are going to run hundreds or thousands of Cloud resources. And as you are creating applications, you're creating this complex architectures, you could tag them. And you could identify your applications, your resources by using these tags.

So that's the first reason why you would use your tags, because your accounts and your resources-- you're going to use many, many resources. And tags is a very easy mechanism to better organize your resources.

The second reason you would use tags would be for cost management. Now imagine all these resources you're tagging, you could pull them up by the tag. And you could find out what is the cost usage for those resources. And that's a very important way to figure out how much your application is consuming.

Remember Cloud is all about pay as you go pricing. And you could pinpoint it down to a particular set of resources as to what kind of cost you are incurring. So second reason why you would use tags are cost management.

You could also do this thing called Tag based access control. So you could control the access based on the tags for the resources, not the users and the groups. So in a way by using tags, it becomes even more powerful, the ability to do write policies based on tags. So those are some of the use cases. And there are many, many more. But those are some of the reasons why you would use tags.

So as we talked about in OCI, there are two kinds of tag. There is free form tags. And there is defined tags. So first let's look at the free form tags. As you can see on the graphic here, there is a key and a value. So for this particular tag, the key is environment. The value is production. It's a very simple key value payer. There's no defined schema. Or there is no kind of access restriction.

Then we have defined tags. And these have more features and control. And the first thing to note here, as you can see on the graphic, is these tags now are contained within this thing called a namespace. So you specify a namespace saying, in this case, it's operations. And then you can put as many tags as you want in those namespaces. So you are defining a schema.

And other thing you could do it also supports policies. So defined tag support policies to allow you to control who can apply your defined tags. So not everybody could just use these defined tags. You could write that in the policy. And the tag namespace is the entity to which you apply this policy. So you could say a particular group of operations admin can only apply this particular tag, because the namespace has operations in that. So you could write a policy against that.

So how does it really look in practice? So as an example here, there is a namespace which is operations. And within, that I'm defining a key value pair. So the key is environment, and the value is production. And you could take it to the next level. So as you can see here, operations is the namespace. Environment is the key. And production is the value.

Now as we talked about, namespace is a container for a set of tags with tag key definitions. Tag key definitions specifies the key like it is here. And you could also specify the type of values allowed. You could say the type is a string. And it allows any value, or it is blank. Or you could set a specific set of values. And when the users come to apply this particular tag, they can only choose from those particular values.

So it is another way for you could first determine who applies the tag by writing the policies. And then you can also specify what kind of values are allowed. So this is really is that defined schema along with policy makes the resources even more better organized.

One thing to keep in mind is tag namespace once you define, cannot be deleted. But you can always retire them, and you don't have to use it. This is more for governance purposes. So whatever namespaces you have, you can keep an audit of the namespaces you had in your account. So that's it.

Tagging-- a very important feature, useful feature in Cloud. And in OCI, we take tagging to the next level using these defined tags. I hope you get to use defined tags. Thank you for watching. 
![image](https://github.com/qriz1452/oci/assets/112246222/d236766f-f106-47ad-8eef-6593ff17f2fb)
![image](https://github.com/qriz1452/oci/assets/112246222/367dd628-5cc9-44d6-a904-1dc5e31c8821)


------------




 

