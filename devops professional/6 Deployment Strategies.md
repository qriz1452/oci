	 Deployment Strategies-BG Deployment


For any organization, in any environment, it is inevitable that the code and the software will need change or a feature upgrade sometime sooner. Deployment strategies are models and practices that enable modification or upgrade of such applications. They allow DevOps teams to define how applications get deployed to the production environment.

This section highlights two different deployment strategies-- the blue-green strategy and the canary strategy. In this lesson, we will be covering the blue-green strategy, and we will cover the canary strategy in the other lessons. You will find a variety of techniques to deploy new applications or updated versions of the existing ones in the production. So choosing the right strategy is an important decision. This allows the administrators to make the right trade-off between the risk of deploying a new release, the impact of the new release on its users, and the infrastructure overhead needed to implement the strategy.

Let's understand this with an example. Let's visit-- our friend, Tricia, the DevOps engineer. Tricia is working on building a website that sells medicines. The backend of this website is supported by microservices, which handle user authentications, medicines updates, discount programs, and more. Tricia wants to release an update which adds tracking medicine delivery.

Mo, who is the solution architect, is impressed by this feature and asks Tricia about what is the wait for? Tricia doesn't really want to wait until midnight, when the least number of users are active, and then deploy the updated code. She also doesn't want users to experience downtime and lags during the financial transactions.

But with such requirements, how can she ensure uninterrupted uptime and stable transactions? Like always, Mo has a solution and tells Tricia about the blue-green deployment strategy. A blue-green deployment strategy allows DevOps team to release a new version of their application by using two identical environments, where one of them is active at a given time.

The current version of the application is provisioned on the active environment whereas the new version gets deployed to the standby environment. And both these environments are running in the production. Testing of new updates are done in the green environment. After the testing is completed in the green environment, production traffic is gradually transferred from the blue to the green environment, after which testing of new updates are now done in the blue environment, which is also used in case of rollbacks or as a disaster recovery mechanism.

Deploying to the standby environment does not impact the active environment or the user traffic. The DevOps release pipeline can run validation tests against the new version. And once approved, it gets promoted to the production by simply switching the user traffic to the standby environment. This process will repeat for each new version of the application.

Using the blue-green deployment strategy, you can deploy the artifacts to two environments-- one is the container engine for Kubernetes, also known as OKE, and the other environment is the instance group. In the OCI-DevOps service, the blue-green deployment strategy is implemented in four stages, of which two are optional. The first stage is the deployment stage. In this stage, the two environments are selected, along with the artifacts to be deployed.

Now a point to remember here is that the load balancer is selected for the instance group blue-green traffic shape. And for the OKE deployment, an NGINX ingress controller has to be set up for routing the traffic. During the deployment run, the new version of the application is deployed to the standby environment.

The next stage is an optional invoke function stage. Now in this stage, a custom function can be added to the pipeline just to validate the application in the standby environment. In the third stage, which is a manual approval stage, which again is an optional stage, a manual approval step is added to approve the deployment in the standby environment. And that happens before shifting the production traffic.

And finally, we have the blue-green traffic shift stage. And in this stage, after the deployment is validated in the standby environment, 100% of the production traffic is shifted from the current active environment to the standby environment that is running the validated new version of your application.

Let's understand this diagram from end to end. For example, let's say we have a microservices-based application, which is hosted in a blue environment, and there is a new version of that software which is hosted on the green standby environment. The difference between the two environment is the blue is the active environment, which is entertaining the user traffic, whereas the green environment is a standby environment and has no user traffic coming its way.

In the next stage, what can be done is you can use functions to validate the deployments in the standby environment. Once the function validates the software running in the green standby environment, it can be further moved to a manual approval stage, where a manual approval is given to the software running in the green standby environment.

Once all the required approvals are in place, we now need to switch the traffic from the blue active environment to the green environment. So here the load balancer now would point to the green environment, which becomes active, and the blue environment goes into the standby state, which is hosting our old software version whereas the green environment now hosts the new validated software version. So this is how we deploy new applications or updates to the existing one without affecting the existing user traffic.

Let's take a look at the blue-green deployment benefits. The main advantage of this strategy is that it offers near-zero time during the software deployments. Also, if a deployment fails, your users won't even notice that something ever happened. With rollbacks, the reverse process is equally fast because blue-green deployments utilize two parallel production environments. You can quickly switch back to the stable one should any issue arise in your live environment.

Another advantage for blue-green environment is A/B testing. We can load new features onto your idle environment and then split traffic with a feature toggle between your blue and the green systems. We can then collect data from those split user sessions, monitor your key performance indicators, and then if analysis of the new feature looks good in your management system, we can switch traffic over to the updated environment-- no downtime. Blue-green parallel production environments also make load balancing very easy. When the two environments are functionally identical, you can use a load balancer to route traffic to different environments as needed.

Let's also take a look at some of the drawbacks of blue-green deployment strategy. Resource intensive-- it is evident by now to perform a blue-green deployment, you will need duplicate resources. And to maintain two production environments is not an easy task. The cost of this in money and skilled manpower might be too high.

The other drawback is error encountered when changing user routing. So when managing a release between two identical environments, you need to closely monitor both the environments for issues. One issue is that during the initial switch to the new environment, some sessions might fail or users may be asked to re-login into the application. Similarly, when rolling back to the blue environment or the old environment, in case of an error, users logged into the green instance may face service outages.

Managing database dependencies between deployments can be complicated. It's because the process of maintaining two clones of production and pushing only one of them live can cause all kinds of database problems. For instance, what if the database schema is going to be changed as part of the new release in the blue environment? The green environment with old code will not function with that database anymore. 



![image](https://github.com/qriz1452/oci/assets/112246222/d10f6a4a-8da2-44e0-b5cf-55563941e3a4)0

![image](https://github.com/qriz1452/oci/assets/112246222/69f8c965-54df-4504-ae93-e14c301afabf)

![image](https://github.com/qriz1452/oci/assets/112246222/3d93042f-2b36-4333-8d6f-24c222bb4c4a)

![image](https://github.com/qriz1452/oci/assets/112246222/4a9d72c9-eada-447e-adee-b1e94d3e119e)

![image](https://github.com/qriz1452/oci/assets/112246222/03af35d8-4ab4-4f35-8519-fd08395faec2)

![image](https://github.com/qriz1452/oci/assets/112246222/4f901f1e-9555-423e-834b-47284469adf1)


-----------------------

 Deployment Strategies-Canary Deployment

Canary deployment is a technique to reduce the risk of introducing a software update in the production by slowly rolling out the change to a small subset of users before making it available to everybody.

Initially, the new version gets deployed to a canary environment with no user traffic. The DevOps release pipeline can run validation test against the new version, and once ready, route only a subset of users to the canary environment. This technique allows the DevOps team to evaluate the new application version against real user traffic, gradually increasing the user traffic to the new software version deployed in the canary environment.

They can compare the two application versions side by side before rolling out the new version to a larger user base. It also offers risk mitigation because the new version is only enabled for a small subset of users. These users can easily switch back to the previous version if any issue arise. You can deploy artifacts using canary release strategy for Container Engine for Kubernetes, also known as OKE, and instance group deployment.

In the OCI DevOps service, the canary deployment strategy is implemented in five stages, of which one is optional. Stages are individual actions that take place during a run of a pipeline. Let's take a look at the stages for the canary deployment.

The first stage is the canary deployment stage. In this stage, a canary environment, which can be an instance group or an OKE, is selected along with the artifacts to be deployed. Remember, load balancer is selected for the instance group canary traffic shift. And for OKE deployment, NGINX Ingress Controller has to be set up for routing the traffic. During the deployment run, the new version of the application is deployed to the canary environment.

Next stage is the invoke function stage, which, again, is an optional stage. In this stage, a custom function can be added to the pipeline to validate the deployment in the canary environment. The invoked function tests the new version before moving to the production environment.

The third stage is the traffic shift stage. In this stage, part of the production traffic is shifted to the canary environment. The stage is the manual approval stage. In this stage, a manual approval step is added to approve the deployment in the canary environment before deploying the application in the production environment.

And finally, we have the production stage. In this stage, a production environment-- it can be an OKE or an instance group-- is selected. And the application that is validated in the canary environment is deployed to the production environment during the deployment run.

Let's understand this diagram from one end to another. Let's assume you already have a software application posted on one of the environments on the OCI platform. Now you wish to update that software to a newer version. For that, you must first have a canary environment created. It can be either in the Container Engine for Kubernetes, or it can be an instance group.

You deploy your new software version in one of these environments. You can optionally choose to have a custom function, which can validate the new software version. And once validated, you move on to the traffic shift stage, where you shift some of the user traffic to the canary environment where you have deployed the latest validated new software version.

Now, based on the users' reception of your new software version, you can also have a manual approval stage, where you can decide whether the deployment in your canary environment should be moved to the production environment. And once that approval has been received, your load balancer now can move all the traffic from the original environment towards the canary environment, where you have the latest updated version of your software running.

Let's take a look at some of the canary deployment benefits. One of the benefits it offers is real-world testing. Canary deployment allows organizations to conduct small-scale real-world testing in production with real users and use cases and compare different service versions side by side.

Another advantage is rollback. It is fast and safe to trigger a rollback to the previous version of an application. In case of any issues with the working version of the application, we users are rerouted to the stable version, and the canary nodes are rolled back to the previous code state. And lastly, there is zero downtime while updating or releasing the new feature.

Let's also look at some of the drawbacks of canary deployment. One of the drawbacks of canary deployment is more overhead. Canary deployments share the same complexities as blue/green deployments-- having many production machines, migrating users between the production systems, and monitoring the new system. These are all complicated tasks.

Another drawback is slow rollout. Scripting a canary release can be complex. Manual verifications or testing with limited real-world users can take time.

Observability-- testing and validating a new release at scale can be complex. The monitoring and feedback systems for the infrastructure should be modified to monitor the canary deployment separately, which may involve additional research.

Users are still exposed to software issues. While the whole point of a canary deployment is to expose only limited users to a new feature, you will still expose end users to the less-tested code. Remember, the first group using the canary will find the worst bugs, leading to poor user experience. 


![image](https://github.com/qriz1452/oci/assets/112246222/d58557be-df10-43ce-ae90-d5714406b4b5)


 ![image](https://github.com/qriz1452/oci/assets/112246222/0b1516ef-51fd-403b-8b00-12eccfd00f1f)

![image](https://github.com/qriz1452/oci/assets/112246222/f9b3c12b-8e67-488b-9871-4a2126e9f62b)

![image](https://github.com/qriz1452/oci/assets/112246222/ff5e369f-17f4-4a88-af83-16ab0f4ab199)


![image](https://github.com/qriz1452/oci/assets/112246222/5562222f-4deb-40c7-bebc-b0dc5f9b0286)


---------







