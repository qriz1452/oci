Automation Overview


Recall that one of our main goals with DevOps is to be able to continuously make changes. That means constantly pushing new versions of the application as well as adjusting the infrastructure itself. In order for that to work, our infrastructure needs to be both consistent and flexible. And to do that, we need to leverage infrastructure automation.

Specifically, we'll address two types of automation, configuration management and infrastructure as code. Configuration Management, or CM, automates how every resource is configured. For example, it ensures that every machine that hosts the application has all the same dependencies installed and with the same version. Or when it's time to update a dependency, it'll roll that out to every machine in the group. This way, we know that every machine is configured correctly, and we can make changes on the fly.

Infrastructure As Code, or IAC, automates what resources are even provisioned. So for instance, it lets you specify that you want three VMs in a private subnet with a public load balancer. Then you can deploy that exact set of resources again and again, and it will be the same every time. Or you can say that you now want five VMs, and changing that should be as easy as changing a three to five and saying go to the automation program.

This way, we know that every environment is consistent in terms of what resources it has and again, we can make changes on the fly. So infrastructure's code asks, what resources are there? And configuration management asks, how are they configured?

There are lots of tools out there for both of these, but in this course, we're going to use Ansible for configuration management and Terraform for infrastructure as code. It can get confusing which to use when, so let's take a look at some of the key differences. First, Ansible is all about mutable infrastructure, while Terraform is about immutable infrastructure. This means that Ansible likes to make changes to resources once they're provisioned, while Terraform prefers to destroy and reprovision instead.

For example, suppose you have a VM with an old version of Docker installed and you want to update it. Ansible would be able to update Docker within that machine, while Terraform would just destroy it and reprovision with an image with newer Docker. Mutable infrastructure gives you more flexibility, while immutable infrastructure gives you more consistency. This reflects that Ansible works via SSH, while Terraform works via API calls.

So in that previous example where we'd want to update Docker, Ansible would SSH into the machine to execute commands, while Terraform would hit the infrastructure provider with API calls to destroy and reprovision. Finally, Ansible uses a procedural language, while Terraform uses a declarative one. This means that for Ansible, you define series of steps that you want it to take, while for Terraform, you just define what the infrastructure should look like, and it'll figure it out from there.

Now, strictly speaking, there's a huge overlap in what each of these tools can accomplish. For example, you can use Terraform with initialization scripts to install software and machines, or you can use Ansible to provision infrastructure. But the way we're going to recommend is to use Terraform for provisioning and deprovisioning and Ansible for configuration, patching, deployment, and maintenance.

And just as a final side note, both of these tools are open-sourced on GitHub. So in this video, we introduced two forms of infrastructure automation, configuration management and infrastructure as code. And we introduced the respective tools we'll be using for them, Ansible and Terraform. In the next video, we're going to start diving into configuration management in a little more detail. See you there. 

![image](https://github.com/qriz1452/oci/assets/112246222/ba805f2d-f503-4be4-97a4-e14ddeae80c4)



----------

Configuration Management - Overview



Recall that DevOps is all about continuous changes and continuous improvements. Configuration Management, often abbreviated CM, supports this kind of high-velocity workflow by automating several key aspects of infrastructure. These include testing, documenting, versioning, and deployment.

So if you want to migrate Docker versions, it'll unit-test the application with the new version, it'll document that change, it'll publish it as a new version of the infrastructure, and it'll roll out that change to the target environment. This way, we not only minimize time in manual labor, but we also ensure consistency in performance, function, design, and implementation. For software developers, this should sound familiar. It echoes how DevOps will approach software development in later modules.

The key idea here is that we want to do this with hardware. We want to treat the infrastructure with exactly as much rigor and automation as we would treat an application. We're not quite there yet, but know how this foreshadows infrastructure as code in later lessons. In fact, we can implement configuration management within a CI/CD pipeline. But that's getting ahead of ourselves. Let's slow down and take a look at the tools available for CM.

While there are many, two that stand out for official OCI support are Ansible and Chef. Puppet is another good one to be aware of, but as of right now, winter 2022, OCI doesn't have an official plugin, so integration would be a little more manual. I encourage you to look into all of them. But for this course, we'll dive into Ansible.

To call Ansible a configuration management tool is a little unfair, as it aims to be a general purpose IT automation platform. It handles tasks from configuration management to infrastructure provisioning to container orchestration, et cetera. But we're only going to look at its configuration management abilities and use other tools for the other tasks. OK, so how exactly does Ansible work its magic?

Ansible follows an agentless architecture, meaning that it doesn't need an agent running on every target machine. Instead, it just has one control machine that SSHes into all of the target servers to manage them. By default, Ansible will try to use native OpenSSH for remote communication. This enables ControlPersist, a performance feature, Kerberos, and SSH options, such as jump host setup.

However, when using Enterprise Linux 6 operating systems as the control machine, like Red Hat Enterprise Linux and derivatives, such as CentOS. The version of OpenSSH may be too old to support ControlPersist. On these operating systems, Ansible will fall back into using a high-quality Python implementation of OpenSSH called Paramiko.

If you want to use features like Kerberized SSH, then OSs like Fedora, Mac OS, or Ubuntu would be better choices. Through this connection, you can run an ad-hoc command on this machine, and it will roll that out to every target machine. For example, you could run one command to update HTTPD, and the control machine will execute it on every node. These commands can be grouped into plays, which are, in turn, grouped into play books that are used to define consistent configuration sets for deployment, management, and orchestration.

For example, if you had 50 Apache servers and wanted to ensure a consistent set of configuration parameters within http.conf, you could generate a playbook with all the requisite values defined. When executing the playbook against the group of web servers, Ansible would connect to each server and apply the same set of configurations. These nodes that the playbooks or commands or run against are called the inventory and are defined in a simple text file.

OK, so let's review Ansible's vocabulary. An inventory defines different groups of nodes to be managed. A task is a call to an Ansible module. It's an atomic command to execute. Plays are a series of Ansible tasks or roles mapped to groups of hosts in the inventory, executed in order. Playbooks are a series of plays that explain what to run and are written in YAML. And a role is a standard directory structure for specifying tasks and variables. Playbooks can be broken up into roles for modularity and reuse.

Let's take a look at a couple of examples of ad-hoc commands. First, you can run basic shell commands, like touch, in this case. Second, you can perform package management like with yum. And for our third example, you can manage the running surfaces like the HTTP daemon. As always, memorizing the syntax here isn't that important, but knowing what you can and cannot do is.

Ad-hoc commands are great for one-off tasks. But for reusability, let's look at an example Ansible playbook. You can see that these are written and YAML for human readability and are essentially a list of tasks. This one does two simple tasks, installing and starting an Apache server on a host of a web servers. 

![image](https://github.com/qriz1452/oci/assets/112246222/de8f5caf-34de-4788-924b-a15e9fc70834)

![image](https://github.com/qriz1452/oci/assets/112246222/c9c3090f-a162-4f92-af55-482e5f859c75)
![image](https://github.com/qriz1452/oci/assets/112246222/c8287845-4322-4ed0-bcd5-6fa411849c42)
![image](https://github.com/qriz1452/oci/assets/112246222/596e4965-3c37-44f4-9c69-0de177058f99)



------

: Intro to Terraform


Terraform is composed of two main parts. The first is a declarative language that lets you codify infrastructure stacks. Don't worry about the details quite yet, but here we can see a portion of Terraform code that declares a compute instance in OCI.

The second main part of Terraform is an engine that uses Terraform configurations to create a plan for making real-world infrastructure look like what is specified in the code. Again, don't worry about the details. But for example, if we give Terraform the config from before, it generates this plan to create a compute instance.

It can then take this plan and convert it into API calls to any infrastructure provider. This includes not only IaaS like OCI, but also PaaS like Kubernetes and custom on-premise solutions. When using Terraform, we can think of infrastructure management in three parts-- initial provisioning, maintenance and evolution, and eventual decommissioning.

At the start, you write your Terraform code, feed it to the Terraform engine, and it provisions the infrastructure. Then as your needs change over time, you can modify the Terraform code, and the Terraform engine will compare it to the existing infrastructure to then reconcile the two.

Once it comes time to decommission the environment, one command allows Terraform to clean up all of the resources that it's provisioned. This workflow is what infrastructure as code is all about. And it has myriad advantages.

You can reproduce stacks across environments, parameterize and version control infrastructure, create reusable hardware modules, and basically get all of the tools and techniques currently available for software development for hardware.

Easing into the details, Terraform does this through a very simple CLI. There are three main commands that you'll ever need to execute. Plan, apply, and destroy. We're already kind of familiar with Terraform apply. It takes a configuration file and provisions the infrastructure.

However, it also writes a file called the state that represents Terraform's view of the world. After thinking about this for a while, you might ask, what about if the infrastructure changes without Terraform? Perhaps someone logs into the OCI console and provisions a new machine.

For this, Terraform has an action called refresh that looks at the real-world infrastructure and refreshes the state file based on it. By default, this command is implicitly executed before any of the core actions. But in more complex implementations, it might be turned off.

Before you run apply, however, it's best to run a Terraform plan. This compares the configuration to the state and generates a plan for getting the state to match the configuration, often called the diff. You can look at the diff to confirm that your Terraform code does what you think it will.

By default, Terraform apply runs a Terraform plan and asks for your confirmation. But again in more complex implementations, this might be turned off, and Terraform apply will require an explicit Terraform plan. The last command is Terraform destroy which, as the name suggests, destroys all of the infrastructure that was under Terraform's purview.

Before we get too much into the weeds, let's go through a quick example of using Terraform to provision a VCN and a compute instance. First, we'll head over to VCNs. We'll click the menu, Networking, Virtual Cloud Networks, and select our compartment.

We can see that there's nothing here. So let's take a look at some Terraform code that will add a VCN with one subnet. Don't get caught up in any of this in text just yet. We'll discuss that later. All we want to note is that we have one block that configures a VCN named Terraform VCN, and one block that configures a subnet named example subnet. We can head to the terminal and run Terraform plan.

You can see that it outputs a list of changes that it'll make. Now let's go ahead and run Terraform apply. It outputs the same list of changes, and asks us whether we want to proceed. We'll say yes, and it'll go ahead and start creating the networking resources. Now if we head back over to the OCI console, we can see that we have our VCN. We'll click on its details. And it has that subnet.

Now let's see if we can modify the Terraform code to include a compute instance. First, let's navigate to compute instances just to see what I have. We can see that I just have a terminated instance from a test I ran earlier. Now let's head back over to the Terraform code where I've added two blocks.

The first one just selects an availability domain. But the second one configures an instance in the network we just provisioned. Now if we run Terraform apply, it creates a plan, promises as before, and goes ahead with creating the instance. You might want to take a second and stand up and stretch your legs here.

OK, it's done. And we can see that the console now shows our new instance in the running state. To wrap up, let's run Terraform destroy. It'll ask for confirmation, and it'll destroy the subnet, the compute instance, and the VCN.

Now that it's done, it'll show the instances terminated, and the VCN that we created will be gone. So that wraps up our intro to Terraform. In the next video,

![image](https://github.com/qriz1452/oci/assets/112246222/0a9fa2d4-4b95-4c6a-a21e-bcc12b00e483)
![image](https://github.com/qriz1452/oci/assets/112246222/6863f201-41f1-4262-a3a6-5ff287f8a392)

![image](https://github.com/qriz1452/oci/assets/112246222/2fbb3f1e-c2bb-42ce-8a28-8954f8c175f1)
![image](https://github.com/qriz1452/oci/assets/112246222/4472a609-834e-4fe0-800a-a291889834b6)
![image](https://github.com/qriz1452/oci/assets/112246222/a4e96440-2676-4405-a48f-12eb2f006640)
![image](https://github.com/qriz1452/oci/assets/112246222/4bb70989-b620-4635-bfdc-e9dd6c040884)


--------

 Terraform Configurations


 In order for Terraform to do anything, it has a key concept called Providers.

Recall that we have this model of Terraform being all about the interplay between configuration, state, and diff, and the real world infrastructure. And as mentioned before, Terraform can manage infrastructure across multiple platforms, including custom ones.

But this brings up the question, how can Terraform actually be platform-agnostic? To figure that out, we have to take a closer look at the internals of the Terraform engine. There are two main parts of the engine, the Terraform core and plug-ins called Providers.

The core figures out everything in a platform-agnostic way. Then, the providers translate that into the platform's language. To be a little more specific, Providers are Go language executables that translate between Terraform's diff, refresh, and apply functions, and the target platforms' CRUD API. HashiCorp maintains a registry of official, verified, and community providers that you can install. The official ones will install automatically if they're specified in the Terraform configuration.

OK. Now we can get into the real meat and potatoes of Terraform, the language itself. The big thing to know is that Terraform is declarative. That means that, for the most part, it consists only of blocks that declare resources, labels for those resources, and parameters that can figure that resource. To get a sense of the language, let's read over a very simple example together.

First, we have a block that configures Terraform itself. In that block, we have another block that lists the providers that are used. In this example we only listed OCI, but we could specify more as needed here. Next, we have one configuration block for each provider, in this case one for OCI. Any of the official or verified providers will have docs on the Terraform registry for what arguments are needed. So here we can see that we chose a region, method of authorization, and a user profile.

Finally, we have a resource block. This one declares that we have a VCN named Example. When you write these, you basically search the docs for the resource you want to create and fill in the attributes that it asks for. In this example, we fill in a DNS label, a CIDR block, a compartment OCID, and a display name.

If we wanted to improve this configuration, we would first notice that we have some hardcoded values like region and compartment OCID. We can factor these out by declaring them as variables and defining them all together. This way we can parameterize the Terraform configuration to be reusable in many different forms.

So if you look at this example Terraform code available on GitHub, you can see that they wrote it using a bunch of variables. A couple of interesting ones include num_instances, where you can change the amount of instances that you provisioned with just a number, and changing the instance shape, as well as the OCUPs and the memory. These kinds of variables are very useful in creating configurable reusable chunks of code.

To improve our code even further, Terraform has a concept of code reuse called modules. To illustrate that, suppose we have a Terraform configuration for a VCN and related resources. You could then use that VCN configuration as what's called a module and embed it inside of another configuration.

So in this example, we're calling the VCN module twice to provision it twice. This way, you could reuse the VCN module in different configurations to construct a Hub and Spoke network topology for example. You could then use the Hub and Spoke configuration as a module in an even larger application, and so on.

HashiCorp maintains a registry of modules and examples. In practice when writing Terraform you want to use these as much as possible. Admittedly, Terraform goes way deeper than is within the scope of this course. For that, HashiCorp maintains very well done tutorials and documentation that I highly recommend perusing.

For this course, like with Ansible, we're only looking to get a sense of the workflow so that when you decide you want to implement infrastructure automation, you know where to start. So that's all we have for general Terraform knowledge. In the next video, we'll talk about the tools available in OCI to facilitate Terraform usage. 
 
![image](https://github.com/qriz1452/oci/assets/112246222/a616a74f-61cc-480f-8a3d-b5ef096cd775)
![image](https://github.com/qriz1452/oci/assets/112246222/def8e1f2-b40f-46d1-8b0b-f172b32d1b3c)
![image](https://github.com/qriz1452/oci/assets/112246222/c7ccb627-87e5-44e1-8bd8-598a4d092232)


--------

 OCI Resource Manager Basics


 In our first model for Terraform, you draft configurations on your local machine, run Terraform on your local machine, and it reaches out to cloud providers like OCI to manage infrastructure. It's great for experimenting, but there are two obvious problems with this approach.

The first is lack of version control. You need to keep track of various versions of the code for things like rolling back and branching for features. The second is in collaboration. You have to centralize the configurations and plan outputs to make sure everyone is on the same page. This leads us to storing the configuration and plan outputs in a centralized version control repo.

So now we have this model where everyone can collaborate. Note, the state isn't uploaded because it can contain sensitive info, like OCIDs and IPs. Contributors then write configs and test plans on their local machines before merging changes together. One pulls from the latest version in the shared repo before running Apply. OK, this is a great improvement, but there are still a couple of problems.

To understand those problems, we need a quick tangent on Terraform Apply, Plan, and Refresh. When you call Apply, it calls Plan, which calls Refresh to update the state, which is used to generate a diff, which is executed to provision the infrastructure. The flow for Plan is the same, except the diff isn't executed.

This works well for small stacks, but for larger, more complex ones, Refresh becomes an expensive operation, especially because it relies on API calls to the Infrastructure. Similarly, actually computing Plan becomes very expensive on more complicated stacks. To deal with these problems, we get rid of the automatically cascading invocations and replace them with manual invocations, almost. Technically, explicit invocation of Refresh is deprecated and is done with an option when calling Plan.

OK, now that we have our more sophisticated workflow, what does that get us? Let's look at the diagram again. First, the state file isn't centralized, so different configuration authors could be working with different state files while calling test plans. Second, the actual diff that is executed against the infrastructure isn't centralized, so there's no guarantee that what happens is what everyone agreed on.

These bring us to our third model for Terraform usage. If we actually run Terraform from within the cloud, we can guarantee that we're using the latest version of state or diff files. In this workflow, we draft configurations locally, sync them with a centralized repository, and execute Plans and Applys in a centralized manner.

This brings us to a really important tool to get familiar with, OCI Resource Manager. You can think of it as a cloud-based Terraform host for centralized source control, state management, and job queuing, plus some Terraform-based automation, like resource discovery and drift detection. We'll go over each of those in detail later, but for now let's dive into this workflow with a demo.

To start, we have Terraform in a GitHub repo. Let's look at the main.tf file. It configures Terraform, and it configures the OCI provider. And this code provisions the VCN and two subnets within it. Now let's go to the variables file. Here, we only have two variables-- compartment_id and region.

The next step is to create what's called a stack in Resource Manager. A stack is a set of resources to manage infrastructure. For our demo, we'll mirror our GitHub repo. We'll start at the home page of the OCI console. Navigate to the menu, Developer Services, and Resource Manager. Here, we can select Stacks. And let's go ahead and create one.

You can upload Terraform configuration files directly, use an OCI-provided template, mirror from GitHub or GitLab, or create one based on an existing compartment. We'll mirror from GitHub.

Here, you select a configuration source provider, which is just a connection to GitHub or GitLab with an authentication token. I'll select the connection I made to GitHub earlier. I'll select the repository I just showed, and I'll select the main branch.

Here, we can name the stack, select its compartment, Terraform version. And let's go to the variables. Right now, this part just reads the variables file and provides us fields for each variable. We'll grab a compartment ID, and select Phoenix for the region. We can review. And let's Create.

Now we've created our stack, but we haven't run any Terraform. For that, we'll have to hit the Plan or Apply buttons. So now we have a stack with a configuration. And since we selected to not provision immediately, we also have a state file that just states that nothing is provisioned.

We can also hide the local machine and GitLab from the picture for now. Next, we want to run a plan. For every stack, there is a queue of jobs, commands that will be run. We'll add a plan to the job queue, which will lock the state file, get passed to the Terraform host, which executes it and generates a diff. Once that's done, the state file will unlock.

Let's go ahead and hit Plan now. Let's name our plan, and hit go. It will take a second to run, but here you can download the Terraform configuration as well as cancel the job. You can view all of its details here, and it will show all of its outputs down here. So you can see that it finished, and it created a plan down here.

Finally, we'll add an apply to the queue that will lock the state file and execute the diff to provision the infrastructure. We're going to go ahead and hit Apply. Name the job. And then we can choose either using an existing plan or running a new one. We'll choose an existing one. And we'll hit go.

And you can see that it succeeded, and the logs are down here. Now let's go back over to VCNs to see what it created. You can see it created the example VCN, and it should have two subnets. So that's the basics of using Resource Manager for Terraform. In the next video, we'll go over how to handle when Infrastructure and Resource Manager are out of sync. See you there. 


![image](https://github.com/qriz1452/oci/assets/112246222/8e0e9d6c-d62e-4193-8860-83ea6ccdfc5c)
![image](https://github.com/qriz1452/oci/assets/112246222/c561299a-1b63-45c0-bbf6-154f34f44676)
![image](https://github.com/qriz1452/oci/assets/112246222/1acf87e0-44ef-48e6-af5b-c52b57ddbffc)




==========

Syncing Resource Manager and Infrastructure


Welcome back. In the previous lesson, we introduced Resource Manager to provision and manage infrastructure. However, we assumed a perfectly linear workflow where all changes made to the infrastructure are made through Terraform, which is not totally realistic. To mimic this, I made two changes to the VCN. First, I added a new subnet. Second, I added another CIDR block.

This is called drift, the process of real infrastructure slowly diverging from what was configured. For this, Resource Manager can run what's called Drift Detection to compare the configuration and the infrastructure to generate detailed drift reports for each resource. To do this, we'll go to our Stack in the Console, and click More Actions, Run Drift Detection, and Confirm.

We now have a Drift Detection work request down here. It'll take about a minute to run. Now that it's done, we can go back to More Actions, View Drift Detection Report, and we'll see that it's detected a modification on the VCM, specifically, a new CIDR block.

We'll minimize those. And we'll see that, while it did detect the new CIDR block, it didn't detect the extra subnet. This is because Drift Detection only reports on resources that Terraform knew about already. We can address this, but to do that, we'll take a quick tangent.

Another problem with our idealized workflow is that it's not realistic to always draft the Terraform first and then provision a stack for it. Sometimes it's easier to just mess around in the console and provision the infrastructure first. For this, Resource Manager can take all of the infrastructure in a compartment and generate the stack and configuration based on it.

To do this, we'll go to our Stacks and Create a new one. We'll select Existing Compartment. Pick the compartment we want to scan. And select the services that we care about, in this case, core services. We'll name our stack. And go ahead and Create it. It'll take about a minute to run.

And now we have a stack based on the existing resources in a compartment. You can download the Terraform configuration right here. If we open up the Terraform, we can now see how we can address that extra subnet that Drift Detection didn't catch. We can take the Terraform from here, paste it into our Terraform configuration, and update the state using Terraform CLI. We can also update the VCN's Terraform with the new CIDR block captured here.

Now, we can not only use Terraform and Resource Manager to provision infrastructure, but we can also use Drift Detection to find changes and Resource Discovery to write Terraform for us. This way, we can support a more nonlineat workflow that's representative of the real world. In the next video, we'll talk about extending the console to support our stacks more seamlessly. See you there. 


-----------

Extending the Console


Welcome back. In the last few videos, we talked about using Terraform with Resource Manager. Now, we'll discuss some final touches streamlining Terraform usage with OCI. So far, we've talked about using Terraform as an input to Resource Manager to provision the infrastructure, as well as using Resource Manager to write Terraform based on existing infrastructure.

This picture should be a little more complex, though, because we'll often use the same configuration to provision multiple stacks. For example, we might have a development, a QA, and a production environment. Also in a microservices-based application, as we'll talk about in later modules, an application can be broken up into multiple, loosely coupled pieces.

Finally, one of the big parts of DevOps is that it's not only traditional ops people that manage infrastructure, but also traditional developers that aren't necessarily experts on Terraform. The way Resource Manager makes it easy for DevOps personnel to manage infrastructure is by allowing you to hide the Terraform a way into what are called templates.

To make a template, we can just upload our Terraform configuration here. It'll also need a schema document, but we'll address that later in this video. To use the template, we'll go to the stack creation form and select to use the template. Here we can select between Oracle provided templates and our custom ones. Then we just need to go through and fill in all the variables.

A template consists of two pieces-- a Terraform configuration and a schema document. You should be familiar with Terraform configurations, but schema documents are probably new. These are YAML documents that list the variables in the code, the constraints on those variables, and what variables to show on the stacks page in the web console. These allow the web console to render forms for provisioning these stacks.

Let's run through an overview of the syntax before showing an example. The fundamental thing that is specified in the schema document is a list of all of the variables. In this example, we specify a variable named functions app name that takes a string. The field is titled application name, and has the description do not use spaces. It ends up getting rendered like this.

The other main thing that is specified is how variables are grouped. To specify a variable group, we just give it a title and the list of variable names. Each variable group renders as a box of fields to fill in. For this example, let's walk through some simple Terraform.

The first block configures Terraform, the second block configures the OCI provider, the third configures a VCN, the fourth configures a subnet in that VCN, and the fifth declares a compute instance in that subnet. Note how he factored all the parameters out into variables.

Now let's take a look at the variables file. Here we declare everything, but we skipped specifying anything about the variables because we'll do that in the schema document. If you intend on also using the Terraform CLI with these configurations, you should fill this in too.

Onto the schema document. The first block gives the template a title, description, and quick blurb. This is displayed when selecting between templates. You could also add a thumbnail here, but it's optional. The next main block that we have is for variable grouping. Here we have a group for hidden auto-populated variables. In this case, just region.

And then we have a block each for the VCN variables, the subnet variables, and the compute variables. The VCN variables just include the compartment, the display name, the DNS label, and the CIDR block. The subnet has the same variables, just with different names.

The compute has compartment OCID, display name, shape, image, and availability domain. Here's where we actually specify the metadata on each variable. First, let's look at region. Type is the most important thing to specify. The OCI docs have a list of allowed types. By specifying that it's a region, OCI can then just auto populate this variable. Next, we give it a title and say it's required.

Now let's look at the VCN variables. By giving compartment ID its respective type, it tells OCI to provide a dropdown of all the available compartments. This way, you don't have to go searching for OCIDs anymore. Then we just say it's required, and give it a title and description.

String-based variables like display name are largely boilerplate. However, some string-based variables like CIDR block are best given a regex pattern for input validation. For DNS label, we gave it a maximum character length of 15. The subnet variables are identical, so we'll skip that.

Onto compute variables. Compartment ID has the same configuration as before. Display name is also very straightforward. Shape is more interesting, because by specifying its respective type, OCI will give us a dropdown of possible shapes.

By saying it depends on the compartment ID, it will also filter by the shapes that are available in the selected compartment. Likewise for image, it gives us a dropdown that we can filter by the compartment and by the compute shape chosen above. Finally, for the availability domain, it can get a dropdown with the 80 names that are specific to our tenancy.

Now we can take a look at how this renders when provisioning the stack. We'll start off by hitting Create Stack. Then we'll upload our configuration. This is the one that I just showed. Here's where it shows the title, info, and thumbnail. We'll name our stack, and we'll see that the description was pre-populated.

Now here's what the schema document does all the heavy lifting. We'll use this dropdown to choose our compartment. We'll name the VCN. Give it a DNS label. And give it a CIDR block. Now we can do the same for the subnet.

We'll select our compute instances compartment, give it a name, and now notice how compute shape filled in with a default, and the dropdown is populated by available shapes in the compartment. The dropdown for image then is filtered by compartment and by compute shape. Finally, we'll pick our availability domain.

Now let's create the stack. And we'll hit Apply. This will take a few minutes to run. But I'll cut that. Now that it's done, we'll go ahead and look at our resources. Go to the Menu, Networking, Virtual Cloud Networks, and we'll see our VCN. Now let's go back to the menu, hit Compute Instances, and we'll see our example instance.

And that wraps up our module on infrastructure automation. We first went over configuration management with Ansible, and demonstrated how to configure multiple machines with Ansible plays in playbooks. Then we gave a brief introduction to infrastructure as code with Terraform, and using it with Resource Manager. Then we went over detecting changes with drift detection, and using resource discovery to write Terraform for us.

Finally, we went over using templates and schema documents to neatly package a Terraform configuration for easy reuse. We went over a lot, and all of this stuff goes pretty deep. But what's important is that you should have a feel for managing infrastructure in this way, and would be able to dive deeper on your own when needed.

For the certification, I highly, highly recommend that you write some Terraform and play with it in Resource Manager. You could do a lot with just the free tier. With infrastructure automation in our tool belt, we can start to think about the application that sits on top of it.

How can we structure the software in such a way that it's conducive to the fast-paced DevOps lifecycle? For that, I'll pass the floor to my colleague Mohenjo Mehra to dive into microservices and orchestration. See you there. 

![image](https://github.com/qriz1452/oci/assets/112246222/d72ee84e-edb4-4f6c-bcd5-9861529ecef9)














 






























