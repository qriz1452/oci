Now Playing : API Gateway Introduction


Hi. Before we began learning about API management with the lessons in this module, it's useful to put this topic into context. Recall, once again, the learning path overview video where I mentioned the case study workshop which uses this VisionStays cloud native reference architecture.

After the Application microservices and functions for third party aggregators have all been implemented, an API Gateway is added. Thus, the scope of this module is to learn more about the capabilities, features, and use cases for configuring API deployments with the OCI API Gateway.

In the hands-on workshop, we abstract and secure access to the two functions, as well as the three microservices. This is achieved by implementing an API Gateway deployment with specific routing rules for each backend service. Once again, as a reminder, after you've watched the videos in this module, you'll want to look at the API Gateway solution in the workshop to learn even more.

![image](https://github.com/qriz1452/oci/assets/112246222/d1549285-490f-4c37-8d87-649604818cc2)


-------
Now Playing : API Gateway : Introduction to API Management


Welcome to course on API management. This is a level 100 course. My name is Robert Wonderlich. I'm a product manager with Oracle Cloud Infrastructure. In this course, we will discuss API and API gateway. We will walk through the steps to prepare a tenancy for API gateway. And we'll create some API. We will explore how we can use API gateway to create a protected HTTPS endpoint for API and how the gateway can apply policies that validate API requests, enforce authorization, work with runtime context, and transform API requests between our clients and our backend implementation. We will finish up with monitoring and managing API through logging and metrics.

Let's get started. So what is an API and API gateway? The term API or application programming interface has been around for a very long time. Developers use them in many of the popular programming languages such as Java. Rather than implement everything from scratch, developers make use of libraries to accelerate their development simply by importing the libraries that they need.

The developer interacts with the pre-built capabilities via well defined API. We can refer to this as a local execution because the developer imports the necessary libraries into her project. But it is encapsulated, as the developer does not need to deal with the internal implementation of the API. Web services share the fundamental principles of encapsulating the implementation but have some distinct differences.

Like their name indicates, they are typically available over the web. They are highly decoupled meaning that a client application invokes the web service over the wire. And the code for the web service does not typically run in the same context as the application that is using it. As a matter of fact, the web service is often written in a wholly different language than the client that is using it.

As we've come to refer to web services as API throughout this course, whenever we say API, we are talking about web services because we were talking about what is the API. We have clients. And those clients need to use functionality on a server. So they connect to the server over the wire or the web service, which is a well-defined contract that we'll talk about in a moment. We need to be able to protect that endpoint because if that web services available to the world wide web, anybody, not just the client we intend, could try to get to it.

So we use an API gateway. And that API gateway provides an interface for the clients to be able to use. And it connects to the backend web services. So the client is not aware of the implementation of the backend web service. The client just interacts with the API gateway. Let's delve into the elements of an API.

An API comprises a description, a set of policies, and then implementation. So beginning with the description-- the description is a contract between the consumer and the provider. It describes the functionality of the API. And there's a wide range of tools available for creating API description. You can use Postman, Stoplight, Swagger Editor, Code Editor, and many more.

Description is typically written in a format such as OpenAPI, which is an implementation agnostic way to describe the behavior. And it's well recognized and the industry. When our API is being made available, that endpoint needs to be protected. And so we use the API gateway. The API gateway applies policy to enforce protection such as authorization. It also performs validation, transformation, and routing.

Another benefit of using an API gateway is it can add metrics, alarms, and logging for that endpoint. When implementing the actual functionality of the API, the choices are endless. You can implement on Oracle Kubernetes Engine. You can use Helidon. You could have custom code running and Compute.

You could create modern serverless APIs using Oracle Functions. You could work against the Autonomous Database and Oracle REST Data Services. You could work against a wide range of SaaS applications. You can connect to just about anything with integration. Or you can use any other technology.

So the API gateway is a network attach device. And it connects between the client and the backend server. So the clients from the outside connect through the gateway to the backend services. And of course, those services can be running in OCI or through OCI connected to your data center. The API gateway provides security, mediation, and monitoring.

So the Oracle Cloud Infrastructure API gateway is a serverless policy enforcement point. It adds authorization, rate limiting, and routing. It performance request validation. It also performs request and response transformation. To help ease the load on your backend services, it includes response caching.

You can create both public and private endpoints. So you can have internal APIs running that are not accessible to the internet. And you can also have public API. You can also set up custom domains so that you can have APIs under your own host names. The gateway also includes integrated logging and metrics. And you can also use advanced logging analytics with API gateway.

As you're designing your APIs in open API 2 and 3, you can load those into the gateway. And you can quickly create API deployments that have built in mock-testing. As you deploy your APIs and make those available for developers to create applications and use them, you can generate SDK so the developers can work with your APIs in the language of their choice.

![image](https://github.com/qriz1452/oci/assets/112246222/9c740d60-15a9-4e81-9da8-736184f80253)
![image](https://github.com/qriz1452/oci/assets/112246222/abb71072-afb5-4ccd-82fe-71abda98dd1a)
![image](https://github.com/qriz1452/oci/assets/112246222/633a8f38-68c1-491d-9a88-e7c585309123)


--------
Now Playing : API Gateway : Networking and Security Policies

Let's set up our tenancy for using API Gateway. API gateway is a network attach device. So if we do not yet have a virtual network, we need to first create one. The virtual Cloud network, or VCN, contains multiple resources, for example subnets. Our subnets can be both public and private. API gateway appears as a network device on the subnet of your choosing. API gateway is fully managed by Oracle. And it has built in failover capabilities.

Therefore, when creating a gateway, you will always use a regional subnet. When you create a gateway, the API gateway service automatically provisions your gateway with an active and failover instance. And a region with multiple availability domains, the instances are created in separate availability domains. If there is ever an interruption to the service and the availability domain, the active instances running in, the service will automatically failover to the backup domain.

In the case of a single AD region, the gateway will be provisioned across two fault domains. All of this is transparent to the user. As you set up your network, you will need to ensure that the traffic and ingress into and egress from the gateway. Oracle Cloud Infrastructure is secure by design and follows the principle of least privilege. This means that the appropriate ingress rules need to be added to the Security list.

And depending on your chosen network topology, you may need to add appropriate routes to your route tables. Continuing the principle of least privilege, access is never assumed. And policies have to be added to explicitly allow access. It is best practice to set up a well defined groups and OCI identity management. And then, add the appropriate policies for the access needed. Users are not directly granted access to resources.

Rather policies are created to grant access to groups. And users are then added to those groups. When a new user is created, that user has no resource access until that user is assigned to a group. When enabling your teams to develop APIs, they will need to be granted the appropriate permissions for group membership. Resource to resource access is also controlled through policies.

For example, if you want to create a serverless API with API gateway and functions, you must add a policy to allow API gateway to invoke the functions. Here we are in the OCI Console. As we talked about before, we need to set up the network and also security policies before we use our first API gateway. OK, so the first thing we want to do is go ahead and create a network. So I'll go ahead and go into networking. And I will select Virtual Cloud networks.

Super important is to make sure that you have the appropriate compartment. Here I have L100 development check. And that's what I want. So I'm going to go ahead and create a virtual Cloud network. Now what I can do is I can create a VCN. Or I can start the VCN wizard. So here, I'll give my VCN a name. Again, I'm ensuring that I am in the appropriate development compartment, L100 development.

My site or blogs are automatically filled out for me. I'll go ahead and leave those as is. And everything looks good. So I'm going to go ahead and create my VCN. The wizard will go through all of the necessary resources for my VCN, fairly quick. OK, so my new VCN is created. Let's go ahead and do it. In my VCN, I have a number of resources. I have a private subnet and a public subnet.

API gateway can work on either private or public subnets for different use cases. I also have a number of other resources created, such as my that gateway, my service gateway, DHCP options, my security list. As a matter of fact, security lists are super important. And this is something that will trip a new user up for API gateway. The example is I go in and create my VCN. Then I'll ultimately create my gateway, create an API. And I'll want to test it.

And as I go to invoke it from my test client from the internet, I will be confused in that I won't be able to get a response. My gateway will appear to me that it is not working. And what it is, is the security list has not been properly configured. So in this case, what I'm going to do is I'm going to go to my default security list for the L100 API management VCN. And I'm going to add an increased role. Notice here, there's a default ingress rule of port 22, which is SSH.

And that's all you get when you set up a network. OCI is secure by design. So there's no assumptions made as to what type of resources you're going to run and all of your security lives are totally locked down and you have to actively open up the appropriate ports. So I'm going to add an ingress rule. But what I'm going to do is I'm going to say 0.0.0.0/0, essentially, everything from the internet.

The IP protocol is TCP. And I'm just going to say 443. API gateway only allows HTTPS traffic in at this point. So what I'll say is HTTPS traffic for API gateway. This is an optional description. But just as I go back and I looking at a later point, if I'm wondering why I have that open, I have a description telling me why. So super important step, like I said, a lot of people, what happens is they get into trying things out, then at the gateway, wondering why they can't connect to it.

Simple thing, we just need to go ahead and allow, open the gate, so to speak, to allow that traffic to come into the gateway. So as far as networking is concerned, we're all set. Let's go ahead and create some policies. So I'm going to go to Identity and Security. And I'm going to select Policies. Here I'll create a policy. I give my policy a name.

Well, API gateway, call functions, this is in my development compartment. I'm going to go ahead and select the Manual Editor. This is a little more complex policy. But once we go through it, it'll make sense. So I have this already copied just for time. And I'll go ahead and paste this in. All right, so what does this tell us? We're going to allow any user to use functions family in the compartment development where it meets our condition.

All, the requests principal type, is API gateway. And then request resource compartment ID is this compartment ID. This is the compartment development compartment ID. My gateway will happen to be in the same compartment as my functions. But I could have those in separate. So I could have a policy that is defining for functions in a separate compartment altogether. Different users are working on those.

And I need to allow the gateway to be able to invoke those functions at runtime. This is for creating serverless APIs. And so we want to give API gateway the resource principle access to be able to invoke functions. So that policy's created. I could add a few more policies. But I'm going to go into another compartment just to show those examples.

So if I look in this compartment, I have a set of policies for my API developers, and set up a number of groups of API developers, API managers, gateway managers, and so forth. So my API developers can manage the API gateway. They can manage the network, functions, everything within the development gateway-- development compartment rather. They can work. They're free to do what they need to do to build their APIs.

Just for context and a little bit of an example, let's go ahead and take a look at the QA compartment. So here I have access control for developers and testers for QA UAT. When I take a look at this, I can see that I have a group, API testers. And they can manage the API gateway and QA compartment, functions family. They can work with that. And if we look down the line, we can see developers can view those resources. But they can't change the resources.

And that's as the API progresses through the development lifecycle, we do not want developers making changes directly and QA. We would want to limit that. So we have a testers group. And this is how we give rights to users to be able to work at development time and configuration time. We add those users to groups. So we assign the rights to the groups. And then, we go ahead and create the appropriate policies to allow the appropriate access.

But, again, at runtime, that policy I created for the gateway is a dynamic policy of sorts. Because any gateway I create in that compartment would have access. So I can add and change and take away gateways. I don't have to add each one into a specific group to solve that. So that covers what we need for networking and also policy. Let's go ahead and go create a gateway. So I'm going to go back to my menu. I'm going to select Developer services.

And under API Management, I'm going to select Gateways. I'm going to ensure that I'm in the correct compartment. So I'm going to select L100 and Development. Now go ahead and create a gateway. Give my gateway a name. This one I'll make a public gateway. You can make a public or private gateway. And this one will make public because I want to have a publicly accessible address so I can create APIs and test against it.

It's in the correct compartment, L100 development. I'm going to go ahead and select my VCN that I created, which is my L100 API management. And you notice, we have regional sunets, here, private and public. I'm going to go ahead and select Public. Then I'll go ahead and create my gateway. OK, my gateway has now been created. And I'm ready to go to start creating APIs and deploying them.
![image](https://github.com/qriz1452/oci/assets/112246222/d94d70a4-4908-4503-a07c-14b421c75be1)
![image](https://github.com/qriz1452/oci/assets/112246222/dbf20546-583f-4a5b-9be9-908f9e70942e)

-------
Now Playing : API Gateway : Creating an API


 The key element of creating an API is to be able to prototype that API. So we can create a description of the API. Ultimately, we're going to implement that API by creating a web service.

However, that web service may not immediately be available after we've designed our API. Oftentimes, the team has to come and implement that web service on the back end in parallel with the team that's using the API on the front end. So what we can do is use the API gateway. By loading our description into API gateway, we can very quickly create a stock response deployment in API Gateway.

API gateway will serve the API. It will return the example response for clients invoking that API. This is also useful to be able to test that API to validate that it is meeting the requirements for the project. Once the backend web services are implemented, then that can be connected in API gateway to serve the ultimate request. So to create a prototype in API, you create an open API description. And you can use any tool that you wish.

You can load this into your API gateway. Then you can deploy the API. And API gateway will automatically define it as a stock response and use your example in your open API description. Then you can test it out with your client. Let's go going into API gateway. We'll build an API description, load it into API gateway, deploy it as a stock response, and test it out. Here we are in the OCI Console. We'll navigate over to API gateway under developer services, API management.

And we'll choose APIs. APIs represent a repository of API descriptions. I'm going to go into an existing compartment. And we can see some of that we already have loaded. We can support both open API 2.0 and open API 3.0 definitions. So this is an example of one such definition that we have loaded. What I'm going to do is go ahead and work on one of these APIs or show how we might be able to edit one of these APIs.

Very simple, there's many tools on the market. One such tool is Swagger Editor. I pulled this up in my web browser. And I have an API definition, which you can see here this is a Field Service API, the sample ticketing system. So in this API, we have a definition of services, such as, to get tickets. It includes information about the required parameters for the service. It also includes some example data that can be used for generating samples.

So what we're going to do is we're going to deploy this or load this into API gateway. So within the API gateway, I'm going to choose my compartment that I want to work with, not work with my own L100 compartment. I go to my development compartment. So what I'm going to do is I'm going to go ahead and create an API. And I'll call this, Field Service. And what I'm going to do is I'm going to choose my file.

So here's a copy of my AP description. This was written with a file name of Swagger.eml. Swagger is old name that we used to call, Open API Definitions. There's still Swagger Tools that we work with. And that's what Swagger now stands for today, as Swagger Tools. Open APIs is the new term. So if it's Open API 2.0, that's what was formerly called, Swagger. And if it's open API 3.0, that's the next format of open API.

API gateway does support both. In this particular file, I have open APIs 2.0. So I uploaded this into API gateway. And a couple of things are happening. One is the API gateway is validating the file that uploaded to make sure that it is semantically correct. And then, what it will do is it will create a predefined deployment object that can be used to quickly create API definitions for this API. So it's validated. And now the deployment specification is generated.

So I'll go ahead and deploy this to a gateway. So I can choose deploy. And I can go ahead and choose my gateway. This is my L100 training gateway that I created. So I'll use that. I'll call this, Field Service. And I'll give this a path prefix. So I'll just call this fs/v1. I can call it whatever I want. Now, what I have here is a number of policies. So we'll get into detail with the different policies that we're going to be using.

But what I'm going to do is I'm going to go ahead and add one necessary rule for a test client that I'm going to use in a moment. And I'll explain that shortly. So what I'm going to do is I'm going to go ahead and say, I want to allow all origins. I want to allow all methods. And I'm going to allow header of X-API-Key. This is a header that is included with that API definition. So I'm including that.

This is to make a test client work that I'm going to use. There's many different test clients, many different ways. And I'll explain that as we go through. I'm going to go ahead and apply that change. When I go to my next screen, what we can see here is there's a stock response that's automatically pre-populated for us. This was the example that was within that definition. So when I load this into the gateway, it automatically creates or repopulates my route for me.

This is the method that I have defined, which is just to get. And, of course, this is a stock response. This can go against Oracle Functions. Or it can also go against HTP backends. So I'm going to go ahead and create my API. This will take roughly about 30 seconds on average, 30 seconds or less to go ahead and create the deployment. And we'll go ahead and test it. So in this case, what I'm going to do is I'm going to copy the deployment.

And I'm going to go into my test client while it's deploying. So I can come back here to Swagger Editor. There's two elements here that I've left not populated. And I'll go and start populating these. I'm just going to paste the end the point that I have and go ahead and make some changes. So here, we have the host value. And then, we have the base path value, which I'll go ahead and take these. And I'll put these in place in my file. And I'll go ahead and uncomment these.

I'll take out to do. And I'll also take out the to do here, base path. OK, so I have this created. So what I can see here is, in Swagger Editor, I have my code or my Swagger file, which is written in YAML, could also be written in JSON. And then, I have on my right hand side, dynamically generated documentation. That includes a tester. So what I can do is go ahead and select this. And I'm just going to give this an API key.

I'm not doing anything with API right now. I'm just using it to satisfy the request. So what we see here is I've made the request. It's called the service. And I've got the response. Now there's no back end service implemented. It's just within the gateway. The gateway is returning a response. So what I can do is work with team. And I can work with my front end developers and my back end developers. And we can make sure that this API definition is doing what we want.

And as long as we're all comfortable with what's happening and the kind of behavior, then what we can do is send the front end developer teams off to go build the front end apps, the back end developer teams can work on the back end developer apps. And then they can go ahead and tie the API gateway to the actual back end when implemented. That's just one example. I'm going to go ahead and copy the syntax here. And we'll go ahead and open up a terminal window.

And if I were to paste this, what we should see, of course, is a return, make this a little bit nicer. Let me see if I can get this, as well. I'll just go ahead and paste this. There you go. So I get that nice formatted so that we can see here the response. So this is a live service, where you can go ahead and call this, start writing, run in applications and work against the API. Now, this is one tool that I've shown in Swagger Editor.

You can use multiple tools. So for example, we can go into Stoplight. We have this service here that we're working with. And it's the same thing. All we're doing is just taking the file, the Swagger file or the open API definition. We're just loading it into our OCI API gateway. Another example just to call out real quick to kind of show how open everything is and how you can use different tools is we can go ahead and take this and point here.

And we could go over to another popular tool called, Postman. So here I'm in Postman. And so, what I can go ahead and do is create a new request. I can go ahead and call the request here. Now, which you'll notice, is I'm not really doing anything with that API key. I'm not validating that API yet. This is just a stock response. It's giving me that response. So with this, I've created an API description.

I have loaded that API description, the API gateway. And I've gone ahead and created a deployment of my stock response and tested it within my clients. So that's the demo.



-----
Now Playing : API Gateway : Validating API Requests



In this module, we will talk about validating API requests, which is a core component of an API gateway, including rate limiting and validation of other elements of the request. So let's take a look at a basic API that is called, /pets. And it has multiple backends for /cat, /dog, and /fish. If the front end client were to make a request to /pet, /cat, then the gateway would route to the cat back end.

A resource also may include a path parameter. These are dynamic elements passed from the front end client to the back end service. So in this case, if the user were to try to get pets, dogs, and the ID of 1234, API gateway would route to pets /dog and pass 1234 from the front end to the back end. Let's say that same user tried to issue a put request to /pet, /dog, slash 1234 to make a change to that record.

API gateway is also designed to protect that back end to only allow the appropriate operations. And in this case, it only allows a get request to that back end. So API gateway would validate and reject that request. Path parameters can get pretty dynamic. So for example, you may have a get for pet and dog and 1234. But you also may have a route save for the vaccinations for the dog.

And that would route to a different back end for the vaccination system. You can also add wild cards. So for example, if you have a back end request of /pets, /dogs, slash, 1234 /back, /locations. Locations, if you did not have the asterisk on the parameter, it would reject the request because there are elements that are coming after that ID. So by adding an asterisk to that, that is where you are allowing a wide range of different back end requests.

This is very powerful. But you also need to be very careful that you understand how you are defining your APIs to only allow valid requests to your backends. Now let's take a look at validating API request with API Gateway. OK, here we are in the console. And I'm going to go ahead and go to one of my existing APIs that I created in a previous module. It's under Developer Services, I'll go ahead and select under API Management, Gateways, my L100 training gateway.

And what we see here is I have a deployment there for Field Service that I created before. In this particular deployment, it was originally created with a stock response back end. I'm going to go ahead and switch this to a HTTP to be backend. And in practice this, we would be doing this when we've created our backend implementation. But I'm going to do it here with this, as I have a echo service that I've written in a function.

And I'm going to go ahead and use that as my backend. So what we'll do is we'll go ahead and just point to that. So that's my actual backend echo service. And I'm receiving it totally hosted on another gateway that I have running. That's invoking the function. But from this gateway, I'll call the other one. That's going to serve as the kind of a method where it will echo the request that it receives.

So as we're working through our lab, we'll be able to observe the behavior as we're changing values coming into the gateway and going out and what not. We can see actually what's sent to the backend, as well as, deploying. We're going to copy this. And I'll go ahead and put that over in my test client. We'll wait for that to deploy. OK, that's deployed. So I'll go ahead and switch back to my test client, test it out.

So what we see is a return request. And this one, we're making this request to this gateway ending in TPQ. And you can see here I have a different host because that's the actual gateway, c6y, that this echo service is running on. This gives me some other information about my request. But a couple of things to call out here is, when we're invoking a function or function from a gateway, it's being executed not as a specific user, but as a resource because it's a gateway that's making the request.

Now the more important part of this for our test is this request body query string, the methods, things like that. This is the information the headers that we see here, as well. We'll be able to see that as it goes through. So we're going to talk about validating API requests. So we have a live end point, so to speak, with an API. So we'll go ahead and test that. So let's come back into our API definition.

And what we'll do is we'll go ahead and make some changes. So first, let's go and add rate limiting. If I were to come in here and say, I want to limit this, I could do this either by total. So I'm protecting a backend that cannot handle a certain number of requests. I can limit. Or if I want to ensure that not one API client is over consuming over all the others, I can do for client IP. I've set this rate limit really low. It's one request per second.

And that's so that we can just kind of test that capability as the gateway, To go ahead and rate limit. So what I'm going to do is I'm going to copy this. And I'm going to come over to another window. And we'll go ahead and run a tester. So what I'll do is I'll go ahead and put this as a certain level of verbosity, say 10 requests. So this is kind of ungoverned, meaning that the client is going to send the request without any timing or any limitation.

It's just going to fire all the requests very quickly. So what we'll see is the gateway handle the requests and the requests start to throttle requests. OK, the deployment has completed. So we'll go ahead and fire off the tests. So there's a lot of text flying across the screen. And we will just take a look at this. So if I were to scroll up, what I should see is a payload coming through here. So you can see here is a request that went through successfully.

It's not formatted. But this is that payload that we were looking at before with the various headers. As we scroll down this test, what we should see is also some 49. So here you see in methods, there's a 49. That you have there. So we could do the same thing with our test client manually. So we can copy this. We could go over to our test client. We could put this in here. We can fire our requests. And then, of course, we could try firing it.

We might get it to trip. We're doing it through the UI and test client setting up. It may not allow it. So there was a 49 that popped through there. So the test client, AV test client, was a little bit better because it was sending a lot of requests all at once. All right, so API gateway also handles routing. And we're going to route all through the same backend. We can route different backends. But we can also validate.

So let's say, for example, I want to send data to this. So I'm going to go ahead and come in here. I'm going to edit this. And I am going to go to next. And what we can see is I have a ticket and I have a POST method here, which is just kind of giving me a status. OK, this was my sample that I had here. I'm going to go ahead and clear that. I'll just removed that, will go ahead, and save my changes.

And then, I'm going to get ready and test this with my test client. So in this case, what I'm going to do is I'm going to set this up for POST. And I'll go ahead and set a body here. And we'll go ahead and just set this up as a JSON, we'll just say, and put-- maybe a basic response is fine. And I'll go ahead and set a content type, a content type of application just tell the gateway what I'm sending to it.

So simple things, simple POST, stuff like that, and it looks like it is deployed. So go back to my test client. Now, go ahead and issue my POST request. Now what you see is I get a 405. And that's because this method is not allowed. I'm only allowing a get request coming into this. So let's say I wanted to issue another request. I wanted to say tickets/foo this way. And I wanted to clarify that request.

I would get a 404. And that's because I do not have tickets/foo defined. So what if I were actually trying to get a ticket number? So let's just go ahead and switch this back, and say, get requests. And I were to say, I want to do, a get 1234. I don't have this defined. So the gateway will automatically lock it down, won't allow that request. So I don't have to worry about that request going to the backend server.

Let's say, for a moment though, we want to go ahead and allow that because to get the specific ticket I want to be able to provide the ticket ID. And I want to put it in, what we call, a path parameter. So what I can do is go ahead and update my definition. And I'll do that. OK, so I'm going to edit this API. And what we're going to do is we're going to add an additional group. So I'm going to add for tickets that I have.

I'm going to add a path parameter. And I'm going to call it, path parameter ID. So we'll go ahead and make that a get request. I'm just going to use the same endpoint that I had before. And what I want to do is I'm going to use that path parameter. So I'm going to say, request dot path and the name of the path parameter. So now, if I just do a get and I don't pass a path parameter, API gateway will select it as endpoint.

But if I do a get and I use a path parameter, it will select this endpoint. So we'll go ahead and update our API. OK, our API is updated. So let me go ahead and go back into my test client. And I have my get 1, 2, 3, 4. And so, when I make the request, it returns a result. Now something to kind of notice is, if I go to my backend end point, or the endpoint that's been passed through, you can see tickets 1, 2, 3, 4 that has been passed. And, of course, this is a get request.

Let's say that my API requires some query string, such as, maybe a tenant ID, something that I need a front end client to be able to pass in. And, of course, if they don't, I don't want to allow the request. Then come back into my API definition. And I can go ahead and start to apply some other validations. So if I expand my request policies, I have a number of policies that I can go in and label.

What I'm going to do is I'm going to go ahead and add a query parameter validation. So this is for a query string. OK, we'll add this as the tenant ID. And we'll go ahead and say that this is required. We'll add that validation. We'll go ahead and redeploy our API. OK, API is deployed. So we'll go ahead and go into our test client. And we'll send the request.

And so, what we see is there's a bad request because the query parameter tenant ID was not passed in. So what we can do is go ahead pass that query string in. Now bearing in mind, this is something to validate for the backends who are not doing anything with the query parameter. It's something the backend requires, we'll say tenant-id. And we'll just give it a tenant-id and send that in.

So what we see is we have a request that went through because it did satisfy the requirement, tenant-id. We can see there's a query string now that has been sent through to the backend. Let's say tenant-id equals 31. We can do the same thing with headers, as well, within the deployment.

![image](https://github.com/qriz1452/oci/assets/112246222/8ff95174-3266-476e-bdc6-07b5e4d39473)

![image](https://github.com/qriz1452/oci/assets/112246222/b90e99ec-77ad-4617-91d0-f83e6964c727)

![image](https://github.com/qriz1452/oci/assets/112246222/8b0c4aef-7c9d-438e-bea5-47cc3a3aa369)

![image](https://github.com/qriz1452/oci/assets/112246222/91b66adb-a2dd-4c64-92af-297a67663b91)


---------
Now Playing : API Gateway : Authorizing Requests




In this module, we're going to talk about authorizing requests and how we can use OAuth and the JSON web token validation. As we begin, let's talk about a typical OAuth flow. The user uses an application. This is the client.

The client will request an authorization token from an authorization server. This takes multiple forms. Sometimes the client is just requesting the token based on its own authorization credentials, and sometimes the client is redirecting the user to a login. You might have seen this in some cases when you log in using your favorite social network. The client requests a token from the authorization server, and as long as the client is properly authorized, the authorization server will return a proper access token, then the client uses the access token with the API request to the resource server. In this case, it's the API gateway.

The API gateway will validate the token based on the authorization server, and if it's valid and contains the appropriate scopes, it will process the request, forwarding to the back end service and returning the response to the client. This is how this works within API Gateway. API Gateway validates the JOT or the JWT. So the client will go through the CI network into API Gateway, and API Gateway will validate that token using the JSON web keys of the identity management server of your choice to validate that the token is legitimate, has not been tampered with, and then it will validate the appropriate scopes. And if those scopes match up, it will go ahead and forward the request to the back end service and return the result to the user.

Let's go ahead and test this out. In this lab, we're going to add authorization to our API. So I'm going to go to API Management under Developer Services. I'll choose Gateways, and I'll choose my L100 training gateway in my deployments.

I have my Field Service deployment that I created in a previous module. We'll choose that, and I'll go ahead and edit it. Part of the API request policies are authentication. I'll go ahead and select this, and I have two types of authentication I can perform. We have a native JWT, JSON web token, or JOT validation policy, or you can use a custom function, which will use Oracle functions, and you can validate any type of token you need to.

In this case, we're going to do a standard JWT or JOT. So what we're going to do is we're going to define that our JOT is going to come through a header, and it's going to be our authorization header, which is a pretty standard form. And this is a bearer token that we'll be receiving. Now, when we get to the issuer, there's some settings that we have here. We need to select an authorization server that we can use. API Gateway will support any standard OAuth-compliant authorization server. So whether it's Auth0, Okta, Oracle Identity Cloud, or IDCS, we can use any one.

For this one, I'll go ahead and use Oracle Identity Cloud, IDCS. So I have IDCS opened up in another session just to take a look at kind of an app configuration, and I've pre-configured the app, and we'll walk through that. So I have this Field Service API defined as an application in IDCS, and in this I can configure both what we call the client and the resource. In my configuration, I have a client configuration, and in this case I'm just working with client credentials. There's all different types of models that we can use to go ahead and get our access token, but for this one, just to be simple, I'm just going to go ahead and go with client credentials.

So I have my client configured, and essentially this client has access to a Field Service API resource of a scope of fieldservice:read. So we're basically reading tickets. I could have multiple scopes here to read and write, update, delete, whatever I want to do with tickets, but in this case we'll just go ahead and choose to read tickets. So this is fine. In this scenario, what I'll do is I'll go ahead and take a look at what a token would look like.

If I go to my test client, what I can look at-- and I have this in another window. I have a token here, and I'll go ahead and reissue the request just to refresh that, and we'll go ahead and take a look at what an access token includes. Interesting tool that we can use, which is nice. There's a number of tools out there by various identity management providers, but we can work with Auth0 to do that, or you can use curity.io.

In this case, I'm in jwt.io, which is a free site. So I can paste my token, and what we have here is some identity information in my token. So what we're going to do is we are going to get some information from this. First is I have my issuer or my ISS claim, and I'm going to select this. What's really important to know is when you're selecting one of these values, all of these values are in quotes. So while this looks like a URL, this is technically not a URL in the same way that you would see in your web browser.

You need to make sure that you have everything in between the quotes. So what I'm going to do is I'm going to take this issuer, and I'm going to switch over to my API, and I'm just going to put that in the allowed issuer. Now, audiences is important, audience and scope, and in this case it's going to be fieldservice. That's what I set as the audience, and I'm going to switch over to my app in IDCS, and we can kind of take a look at that.

So what you see here in the client configuration is where you had this fieldservice:read, but what we're really looking at is if we switch into the resource element we can see that the primary audience here is fieldservice. Another area where we can see this is if we go back to the token that I generated from the app itself. What I could see is there's an aud, or AUD claim or audience, which is fieldservice, so I've matched that up.

Now what we can do is come back into our definition of our OAuth policy that we've configured here in-- our JWT policy, rather, that we've configured in the gateway, and there's one other thing that we need to do. This token that I was able to take from IDCS to be able to paste into jwt.io was not encrypted, but it is signed, and this is super important. We don't want somebody to be able to take a token and manipulate it and be able to have that in there. So this is signed with a JSON web keys.

You can do a static key if you want to load them, or you can do the remote, and most identity management providers actually provide a remote endpoint. So if I go over to my Postman client again, we can see here's an example of the sign-in certificate from IDCS that we have there. So it's really convenient if I take that URL and I go ahead and put that into my end point for my public keys. The gateway will automatically retrieve the sign-in certificate and will use that to make sure that the token it received legitimately came from IDCS.

So, again, somebody cannot go and manipulate or tamper with that token, and change it, and get rights that they wouldn't otherwise have. So that's pretty much a simple way to kind of set up the authentication policy here. Essentially, what we have is bearer token, the issuer that's coming from the audience defined for this app, and then of course the public keys. So we're going to go ahead and apply that. OK.

So we have that in place, which is well and good. Now, the next thing we're going to do is we're going to go in under Tickets to get tickets. We're going to go ahead and go into the route request policy, and what we're going to see is an authorization field has shown up here. So we can select the authorization type.

There's a couple of different things we could do. One is we could go ahead and say this is anonymous. There's another setting. If you had multiple endpoints but one of your endpoints you didn't want to do authorization-- maybe it was a health check or a public endpoint-- you could do authentication only, just basically saying, look. I want to make sure that the user's logged in, that it's a valid token, but we don't need to check any specific rights, or what you can do is you can define scope. So, any of the allowed scopes.

In this case, I'm going to add read in here because that was the scope that I was using with this. So this means that this user-- if anybody calls, they have to have this specific token-- or scope, rather. An application can have multiple scopes and different users. Different client apps may have different scopes that they have access to. For example, with this particular API I could read tickets, but I also could update tickets, and I might have a write scope on there. And if the client calls and tries to call an update without the appropriate scope, the gateway would reject that request.

So even know that client has authenticated and they received a token, they don't have the complete scope that they need to be able to invoke that. Now what we're going to do is they're going to copy the endpoint here, and I'm going to go ahead and go back into my test client. The other thing I'm going to do is I'm going to go ahead and duplicate this, just so that we can kind of see the difference in behavior. This one, what I'll do is I'll go and say No Auth. So in this scenario, what I should see is a value that basically says make sure I got my tokens.

I just want to make sure I got that right. OK, so No Auth. If I go ahead and send my request, I get a 401 unauthorized. I don't have appropriate scope. This one, I don't have my bearer token yet, so I got a 401 unauthorized, but what I can do is go ahead and get a new access token. So this basically gave me the new access token that I have here, so I'll go ahead and use that token and send my request, and now I have the return.

So this just basically validated my authorization that I have there. Let's just say I went to do a post, of course, and this API does not allow the post, so of course it'll tell me the method's not allowed. I could add the post. I could add a different scope to be able to go ahead and validate that.

So that's the JWT validation. Really simple to set up that relationship with your authorization server. The clients can go ahead and set up their access tokens and be able to do that. If you have different token types such as basic auth or anything else that you want to do with that, you can use the custom functions. So you can write your own function, let that validate your token in the gateway, and be able to return a result. That is the authorization.

![image](https://github.com/qriz1452/oci/assets/112246222/6ff400b9-401d-4636-8af8-5e0cd29406ce)


![image](https://github.com/qriz1452/oci/assets/112246222/5a28eeba-1040-426d-8f18-64fc6d4e1222)



-------
Now Playing : API Gateway : Using Context Variable




In this module, we're going to talk about using context variables-- from headers, query strings, path parameters, and the auth context. When we talk about auth context, we have a number of runtime variables defined when a request comes into the gateway.

When the client calls the API, there is a resource path, and that is captured in a request.path. If the client were to submit query strings, then that would be contained in request.query. The request can include one or more headers, and that is included in request.headers. If the authorizer is used, the authorizer can Express claims from the token in a request.auth. All of these can be used at different points in the API execution.

Let's go ahead and take a look at this in the Gateway. OK, now we're going to set some context variables in our API. We've actually worked with these in a prior module. We'll point that out along the way. So let's go ahead and go back into API Gateway, under Developer Services, API Management, and Gateway. I'm going to go to my L100 Training. Now what we'll do is go into Deployments. I'll go into my Field Service Deployment.

So we've already looked at context variables. We have this Route 1, which is /tickets. It's to get the whole list of tickets. But in an earlier module, we added a route two, and we added a path parameter. This is this request.path in the name of the path parameter that we're referencing. So let's display around and add another one. And we'll just add a header.

This actually delves into a later model, as far as required transformations, but we'll go ahead and take a look at that now. So we'll use a header transformation, and I'll go ahead and add the header. So we will go ahead and Add. And I'm going to set this header. We'll get into more details about transformations in a later session.

Let's say, I'm going to set header called app-name. And I already know that, in my authorization token, my access token, I have an element called the client_name. So we'll go ahead and use that. So that is going to be a request.auth client_name. And we will go ahead and just Apply that.

So when a request comes in, and this request is validated, then I go ahead and get a request.auth client_name out of that. So go ahead and say Next and Save Changes. OK, my API is deployed. Let me go back over to my test client, and we'll go ahead and make a request with my token in place. And what I see is I have an app name header now that's been added. And it's my Field Service API. This is the authorization token that I received and that I had in my request, and so I pass that through.

That's the context. And of course, I can do any manner of transformations. And we'll get into that in the next module.

![image](https://github.com/qriz1452/oci/assets/112246222/250fa888-f67c-4836-86bf-cb7cb67eb71b)

-------
Now Playing : API Gateway : Transforming API Requests and Responses



In this module, we will talk about transforming API requests and responses, specifically setting, filtering, and copying headers and query strings. An API request may include multiple headers or query strings in the request. And using API gateway, we can control how those headers or query strings go from the client to the backend server. We can add headers and query strings, we can drop headers and query strings, and we can even rename headers and query strings.

When we set these values, we can set them to a static value or to one of the context variables in the request. Transforming responses are very similar to transforming requests with the exception of query strings. A response does not include a query string. So there's no action to happen there. However, we can set headers, rename headers, and we can drop headers.

Now, let's go ahead and look at transforming request and responses with API gateway. OK, now what we'll do is we'll transform some requests from our API requests to our responses. And we can actually transform responses as well. Let's go ahead and just take a look and see how some of this works.

So again, I want to go on to Developer Services, API Management, and Gateways. And then, of course, go into my API that I've been working with my L100 training gateway, and Field Service. We'll go and edit that API.

So let's go ahead and take a look at transformation. So this is in both the request and the response policies. You can see here, I have a number of transformations, header transformations and query string or query parameter transformations.

I also have this in the response, but I only have header transformations. As we talked about before, when a backend returns a response, it doesn't set query strings. That's only in the request can only transform that in the response.

So let's go ahead and take a look and see some of the things that we can do here. One of the things is interesting, and this is a good way to modernize a backend application. So let's just say for a moment that we have our tickets, KPI. This is all well and good. And then, of course, we go down to our tickets that we have here.

And here, we had mapped this to a request path ID. But what happens if we can't do that because our backend doesn't do a path parameter, but it actually requires a query string, and it actually wants something different? So how can we work with that?

Now, a little more modern, some people would say a little more modern way, is this RESTful model is to say, I want to have this as a path parameter, not necessarily a query string. That's probably set the date back and forth, but let's just say for our purposes, the way we want our API to operate is as a resource with the ID. But the backend doesn't match the same way.

Well, what we can do is we can go ahead and transform the request. So in this case, what I'm going to do is I'm going to go to my query parameter transformations, and I'm going to add a transformation. And so what we'll do is we'll call this ticket ID.

Now, what we'll do is we'll go ahead and do that path parameter. So we'll do request path ID because that's what was being passed in on the frontend. And now while we're here, let's go ahead and talk about some other things we can do. Because we have only been sitting elements, this actually allows us-- we can do a number of things.

One of the things we can do is we can rename. So if we have an existing query parameter that's coming in on a request but is different, meaning the frontend might just say ID but the backend is ticket ID, and we just needed to rename that, we can go and rename it. Or if we want to go ahead and filter to basically remove and only allow certain query parameters to come through, we can also set that. So that's a way that we can protect our backend systems by only allowing the appropriate parameters to go back.

They also have another behavior here that we can set whether we overwrite, skip, or append. So, for example, if the requester, the client, passes and ticket ID, we're just going to override it. It doesn't matter if they tried passing it, we're going to override it in this case. Or what we could do is we could skip.

So this is kind of a set default value. If they did not pass it, then we'll go ahead and set it. Or we could append to it. Maybe we have a query string or even a header that has multiple values, and we need to add to it. So we can set that behavior.

So we'll go and apply the changes. And we'll go ahead and deploy our API. OK, our API is now deployed, so we'll go ahead and test this. OK, so we've made our request.

Now, the backend is different in what we'll see. Is our request URL, instead of having the path parameter, now has this query string ticketID=1234, which you can see for the frontend, I've actually passed this is a path parameter. So this is a way we can reshape or transform the request that's coming in to the API gateway for the requirements for the backend that we need. And that's essentially request response transformation.

If the response had different headers and we want to change those, so, for example, if we have the headers that come back to us, there's a number of values that we have here and we needed to set something, we could do that as well on the response. So is basically with every need that you have, the gateway in between can go ahead and set, append, or can drop as needed. And that's the request response transformation.
![image](https://github.com/qriz1452/oci/assets/112246222/573ceda3-3f75-47a0-bd7c-912b8b7fe2c9)

------

Now Playing : API gateway: Dynamic Authentication


Welcome. In this lesson, we'll take a look at an important API Gateway feature designed to support multi-tenant architectures, in this case, dynamically selecting the authentication provider based on client information.

Before we dive in, let's review first a basic pattern used with API Gateway to enforce proper authentication and authorization of a client. In step 1, the client authenticates with an identity provider, such as OCI Identity and Access Management, Microsoft Active Directory, or Okta. If successfully authenticated, the client receives a token that provides authorization.

In step 2, the client invokes the API exposed by the gateway with that token. And in step 3, the API Gateway validates the token to ensure that the client is authorized to make the request. Now, if the client is authorized, the gateway routes to the appropriate backend service to fulfill the request and returns a response to the client.

Now, notice that in step 3, there is a trust relationship between the gateway and the identity provider. For the OCI API Gateway, this trust relationship is configured in the API deployment, which means each deployment has a specific single provider.

Now, for most use cases, this works well as all clients are provisioned using one identity provider per API deployment. However, how do you handle an API that needs to support multitenant clients where each tenant could have a separate identity provider?

Well, the answer is dynamic authentication where the gateway can choose the appropriate provider at runtime based on the client request. Here's how it works. The client authenticates with and receives a token from its chosen identity provider.

So just as before in step 2, it invokes the API using that token. What's different is that when the gateway receives the request with the token, it performs a lookup based on an element of the request to determine at runtime which identity provider to use.

Options include a request header, such as X-Tenant-ID, the host or subdomain that the client used to invoke the API, a path parameter, or even a claim in the authorization token. Then, of course, if authorization is successfully validated, the gateway routes the request to the backend and returns a response to the client.

Dynamic authentication also allows the API provider to choose how the token is validated for each tenant. Some tenants can use a JSON web token validation, and others can use an authorization function.

This example describes multi-tenant clients. But this capability also applies to other use cases, such as trial or developer users that are stored in one identity provider and then moved to another provider when they upgrade to a paid account. With dynamic authentication, the API Gateway can decide with each call which provider to use to validate the authorization at runtime.

Let's now visit the OCI Console to take a look at how these options are configured. I'll start by looking at a deployment here in my demo gateway that has no authentication defined. In this particular deployment, if I go to the authentication page, I see I have now two options-- either defining a single authentication provider or perhaps using a dynamic authentication approach.

First, looking at single as a review, notice that you define the authentication type, whether it's going to be a JSON web token or an authorizer function. In that example, you would simply choose the function application and the appropriate function and then define which arguments should be sent from the request to the function, such as request headers or some path or query parameter or some value in the body of the request.

In the case of a JSON web token, of course, you're defining where the token location is, either a header location or a query parameter location name, I should say. And then below that, you're defining one or more issuers and audiences as well as the way to validate the Java web token with public verification keys.

Going to be a static key that you define or a remote key using a URI. But static, of course, in your defining the key definition format, whether it's JSON, a web key, or whether it's a PEM-encoded public key.

All right. So that's what happens when you use a single authentication approach. Everything is being defined by that JSON web token or authorizer function approach. And, of course, you can also choose to enable or disable anonymous access.

In the case of dynamic authentication based upon multiple providers, notice you're selecting that first, and then you're defining one or more authentication policies based upon some selector value. So it could be an authorization token claim name, or it could be a header.

For example, in our lecture, we talked about maybe it could be based upon, say, a tenant ID or could be a subdomain value or a query parameter or a path parameter or even a host name.

In that example, then you would simply define one or more policies. So I would provide a name for that policy and then maybe one or more values, comma-separated list of names that might have-- in this case, host names have been used by the client to make the request.

Now, notice that once you define each policy-- you can have more than one-- you're now presented with those same options, either a JSON web token as we saw a moment ago or an authorizer function. And, of course, regardless of which one you choose, then you're also allowed to choose whether or not you want to enable anonymous access based upon that.

Now, I have an example. Let me cancel out of here. That has already been done. So you can kind of see what that might look like with multiple policies or go to this other deployment. And if we look at it, we can now see that I did choose multi-authentication.

I used host as my selector. And I've got four authentication policies, as you can see here, depending upon the host name being used by the client with these options here. And we define either the JSON web token or the authorizer function we're going to employ dynamically for that particular client.

And that's it for this lesson on selecting identity providers dynamically with API Gateway deployments. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/7a2bf20d-09f2-4245-8a69-d8709be05f7a)
![image](https://github.com/qriz1452/oci/assets/112246222/03507666-4bbe-489e-b9b5-9d08fb6434b2)

------
Now Playing : API Gateway: Dynamic Routing





Welcome. In this lesson, we'll take a look at an important API gateway feature which allows for routing to multiple backends using dynamic criteria. Part of the responsibility of an API gateway is to route API client request to the appropriate backend service. For a deployment configuration, you have the option to define one or more routes to each specific backend service. But what is the same path route needs to be routed to different backends based on dynamic information sent from the client?

For those use cases, you configure the API route to have multiple back ends, where the selector criteria chooses the appropriate back end at runtime based on the client request. So the gateway chooses the route based on the client request such as /sales, shown in step two, but in step three, s further examines the request to determine which backend service receives the request. You configure a selector to tell the gateway which part of the request is used to perform a lookup to map to the appropriate backend service.

This selector can be defined based on a header value, query parameter, host or subdomain name, a path parameter, authorization token claim, or a specific usage plan. Dynamically selecting the backend enables you to present a single facade to different API consumers and shield them from the complexity of multiple backend systems.

Let's now visit the OCI Console to take a look at these selector options. Here in my demo gateway, I've created a deployment where I've set up some example configurations and that we can take a look at. So let me jump down here and I'll show you the first one. In this one, I defined a use case where the path is /sales, and here are the appropriate methods. So notice I've checked the Edit added multiple backends. That's where the configuration started.

From there, I'm going to be defining one or more backends based upon some selector. And notice the options I have, I can define a claim name, and an authentication token. I can base it upon some header value, for example, that could have been the tenant ID, the host name, a path or a query parameter, a subdomain name, or maybe the OCID of a usage plan.

In this particular example, I defined it based upon the expression for a host. So we simply click onto define, in this case, two backends. One would be if the host provided by the client was cars@example.com, we would now route to this particular HTTP backend, and you can kind of see how that configuration would be done. In this case, it's this particular URL. And the other case, if they provide minivans.example cloud.com, or trucks.example.com, in either case, that's going to go to this particular Oracle function, that's going to be the backend to invoke for that request.

Let's go take a look at some other examples in route-- in this one example, I set up multiple backends based upon a subdomain. So here's the domain mask, and again, based upon that domain mask, I defined one of these two backends that we're going to route to. In this example, for route 3, I've again defined multiple backends, this time the selector as a subdomain was using simply example.com of the domain mask, and as case, we match cars or hatchbacks.

In this fourth example, I've just set up a based upon headers looking for the Accept header name. If the header is JSON, we're going to go to one backend, if it's XML, we're going to go to a different backend. The assumption here is those particular backend services are able to handle that particular kind of response.

Here's another example where we will base it upon an authentication claim. In this case, the name of the claim is tenant, in the authentication token, and if the expression is tenant cars, we go to one service. If it's tenant trucks, it goes to another one. Notice we can also define a default path. In this example, I set up a query parameter use case, where I'm looking for a vehicle type parameter and the query string. And if it's car, we go to 1, if it's minivan or truck, we go to the other.

And finally, in this last example, we set up a use case based on the Oracle Cloud identifier. And I set up a-- in fact, two usage plans. And we're implying here one might provide for premium service, and one might be a free service, and we have two different usage plans associated with those.

And that's it for this lesson on using dynamic routing options with API Gateway deployments. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/acde2cd5-17a9-4e76-80ef-bad68ce08100)


------

Now Playing : API Gateway : Monitoring APIs


In this module, we will talk about monitoring API through metrics and logging. With API Gateway, you automatically have metrics for your APIs. You can also use the public logging service to get access and execution log, and for more advanced cases, you can also use logging analytics. Let's take a look at how metrics and logging work with API Gateway.

OK. We've been working with our APIs for a while now, but one of the most important parts of an API Gateway is logging and monitoring. We need to be able to understand what's going on, so let's go ahead and take a look at that. If I go back into my API gateway under Developer Services, API Management, and Gateways-- and I'll go ahead and select my L100 gateway. We'll see as all along as we've been sending requests, we're getting metrics that are coming through.

So there's a couple of levels here. One is we can go ahead and look at metrics. We can look at it at the gateway level. We can also look at it at the deployment level. So if we had multiple deployments, we could look at each separate deployment that they're doing. API Gateway is a core component of the platform of Oracle Cloud Infrastructure, and so like all of the other services with Oracle Cloud Infrastructure, it uses a common metrics system.

In this case, we have these charts that are here, but we can go in and we can actually look at in the Metrics Explorer, and we can run a number of different reports that we would with others or taking a look at that. But another element that we'd want to look at is logging, how do you log information, and so for that we can enable logging. In this case, what we'll do is we'll go ahead and use the public logging service, and we'll go ahead and select Logging.

Default, it's fine. So we'll go ahead and enable logging, and in this case what we'll do is do both access and execution logging. Access and execution logging in slightly different. Access logging is essentially just when a client has requested access to the API. So it's just kind of your front end request. Execution gives a little more detail about how the request went to a back end and what kind of response that I got there.

OK, so now both of my access and execution logs are active, and so calls to the API will be logged. So what I'm going to do is go ahead and send some traffic to the API so that we can go ahead and see what comes into the log. So I will switch over into my terminal, and I'll run kind of the batch testing client, and I'm going to just send a number of requests.

So what it's doing is this is sending traffic. We're hitting rate limits. We're getting some requests through. We're just sending traffic through, so we'll just go ahead fire these requests then for a little bit. And then what we'll do is go ahead and go in and take a look at what shows up in the logs.

OK, so we have a pretty good amount of volume at to start taking a look at. So let's go ahead and take a look at the access log. We'll go to Field Service Access. This will switch us over into the public logging service we used for API Gateway. It also can be used for all kinds of traffic, right? So you can have all different types of systems.

So what you see here this is kind of like a web access. So this is what's come in, the request, the remote address. All the requests get tagged in with a request ID that can be correlated, and of course we can kind of see what's going on, that these are all these get requests that have come in here. We should see there's a status 429. So you can even do some searching, right?

So if we were to explore with log search, we can come in here. We can say, OK, let's go ahead and go data.status equals-- you know, how many 429s did we get? Right?

So we can start to see, and we can start to do kind of research to see what happened there as we're getting that. So this is not just looking a raw log file. This is also using all of the searching mechanisms that we have that we can work with that.

So let's go ahead and go back to our logs, and we can look at the execution log just to see what was coming in there. So here what we can see is we had some requests. There was a missing authorization token.

In the tester, I wasn't using the authorization token. So when the requests came in, it essentially said no. You know, the gateway is rejecting the request that we're seeing there. So we were going 401s and 429s pretty consistently. So that's access and execution logging that comes right out of the box with API Gateway and using the public logging service.

So let's take a look over at logging analytics, and to do that I'm going to go over into another tenancy where I have logging analytics set up. OK. So we've switched over into another tenancy where we have some different kind of traffic and some different use cases set up. And we'll just take a look real quick. So if we look in Developer Services, API Management, and Gateways-- which we'll see as I have a different gateway that I have set up here-- and we can see that I just started to send some traffic through this gateway showing in this test.

If we were to go look at this traffic a little bit more-- we can delve into this with the Metrics Explores-- what we can see is there's a good amount of requests going along through this. So we can see a number of different services that we have, all kinds of different operations that are running through here. So let me go ahead and go over into Logging Analytics. So we'll go into to Dashboards. What we'll do is we'll pick one of our dashboards that's in our root compartment here, and what we'll be able to see is not just API Gateway but also a bunch of other services that we're executing. So you can see we have-- well, we're invoking functions. This is through API Gateway, but where we're using functions and we can kind of see what's going on there.

We can do a fair amount of analysis. So some of the things we can do here is we can see the different statuses of what's going on. So you can see we may have a 202 here, and we can actually kind of sort and search this. For example, I can take all of these out and say I want to know where my rate limits happen. It looks like rate limiting is not happening too much, and it is happening in Field Service, though, out of these three APIs.

Field Service, help desk, and insurance. I'm seeing that. What about 405s? That's happening. You know, wrong method. Something's going on in insurance, and I could go and delve into those as well. You know, 201s, different things, so I can actually analyze the data as we're going through here.

Another thing I of course can do is I can go into the Log Explorer, and here I can do all manner of analysis. For example, if I want, I can go in and start to expand out my other fields. For example, instead of doing this by a log source, I can go and group this by status. Go ahead and apply that, then what I can see is all the different statuses, and of course I can change this the way this goes.

So let's just say I want to put this into a tree map. What I can see is I have a number of statuses. Some are records, because I think this would be functions. It may not report that or other services, rather. Would not report the kind of status that we're using here. But I can see this with a gateway. So if I start to see something start to grow, then I can get into that and take a look at that. For example, what's happened in the 429s?

I can go and delve into those loans and analyze this. So this really provides a really good way to build rich dashboards, and monitoring and managing API gateway, but this is the same platform that can be used for things like BCN, flow logs, all kinds of other services, whether you're running just different databases, or middlewares, or anything. There's a whole wide range of log parsers that are available for logging analytics that you can use along with API Gateway to build holistic dashboards to monitor and manage your technology portfolio. And that's monitoring and management with API Gateway.



------





































