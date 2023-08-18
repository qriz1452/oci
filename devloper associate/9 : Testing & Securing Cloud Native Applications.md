----


Now Playing : Cloud Native Testing Overview



Could-native applications run in a different way than the ones deployed on-premises. And testing apps built on could-native also differs from testing applications running at your data center. This is because could-native applications are more dynamic, distributed, built on microservices.

They are shipped at a faster rate often because of CI/CD and DevOps practices. And there are failure modes that are difficult to anticipate and raise. This requires us to adapt to changes and review the traditional testing techniques and include some new and modern ways to detect debug, analyze, and report problems.

These testing techniques will help us in many ways to find and reveal lots of information which will help to increase the overall quality of the could-native applications. Thus, for such applications, testing should be an integral part of all the phases of software development lifecycle, including the pre and post-production. Let's take a look at some of the measures that we need to focus on while coming up with a test plan to test could-native applications.

Scalability. Scalability is the ability to scale the containers or pods based on the real-time requirements. A typical could-native application should scale up or down to resist the fluctuating and dynamic demands without performance degradation. And to maintain this, native apps must be aware of the scalability requirements due to dynamic load patterns and include them in the test strategy.

As a QA, some scenarios that should be covered here are, what happens when the instances are no longer required? How is the service scale? And how is traffic routed when nodes are overloaded?

Resiliency. As you build could-native applications, you should design for failure, but test for recovery. Testing should consider traffic routing during overloading and how does load balancing affect the performance. Also, check how user requests are handled when some features are not available. This also helps in maintaining the impact of the cost associated with the business.

Functionality. One of the main objective of software testing is to confirm that an application is resilient, scalable, and functional enough before bringing it to production. When an application is not performing as expected, you want to be able to identify what's wrong and fix any breach before it causes downtime. Some of the few core functions to check with functional testing are basically page loading, login functionality, input validations, output verifications, and user interfaces.

Robust deployment. For could-native applications, automation is the main factor that brings most impact in terms of speed at which the software is deployed. During testing, focus should not be on large, unmaintainable, or unreliable regression packs that add no value, but on the smart test packs that can simultaneously validate a deployment, and perform a selected set of functional tasks. This type of automated regulation will add a constant value to the development effort and, accordingly, can be expanded or reduced as the product develops.

Resource utilization. In traditional applications, operations team would manage the infrastructure resources allocations manually. This is a tedious job and requires heavy maintenance. In could-native applications, we have a central orchestrating process that dynamically manages and schedules containers for automatic resource utilization. Since this is based on parameters set by DevOps, we need to ensure the balance loads are maintained. Otherwise, it can result in low resource utilization or even increase the response time of your test.



===============
Now Playing : Cloud Native Testing Strategies


So let's get started. Let's now go through some strategies that can be used to effectively test the cloud native applications. Unit testing. In a microservices architectural setup of cloud native application by testing small granular parts of the individual testable service components, it becomes easy to identify the issues early in the software development lifecycle.

These fast, reliable, and automated unit tests will not only ascertain whether the individual units of the service components are working correctly or not, but will also help the developers to observe changes in the unit state and check the interaction between the objects inside them. Component testing. So after all the individual parts of a microservice has been tested, you need to run component level tests on each microservice in isolation.

This is done by testing each microservice individually. Component testing allows you to analyze the performance and functionality of the microservices that makes up your application. This way, you can be sure that every microservice works exactly the way you need it to. Integration testing. Once the service components are integrated, the integration test triggered by the CI servers will help to test the communication path and interaction between the individual service components or between the service components and some external services.

Through integration testing, you can determine whether the services are working together to achieve the larger functional logic. These types of testing can also be used to check whether new features are compatible with the existing applications. End-to-end testing. So end-to-end testing involves checking the entire user flow as well as moving parts of a cloud native application. This ensures that everything is working as expected and that there are no high-level discrepancies.

This level of testing requires evaluating the operations of the cloud native application at the highest level of integration from the user's perspective. This is a time consuming effort, requires heavy resources, and are expensive too. Ideally should be carried out once other testing strategies are completed. Contract testing. Contract testing is required as individual and independent microservices will be involved. The microservices architecture consists of producer-consumer service components.

When a consumer will try to pair with a interface of a provider to use its output, a service contract will get created between them. Automation test suites consisting of these contract tests can be integrated into the integration pipelines, and once run, they will verify whether any change in the provider or the consumer component is meeting the service contract between them or not. Non-functional testing. Testing non-functional quality aspects is very important when the product is being built for the cloud.

Any issue or deviation from the expected behavior in terms of certain server crash or service component goes down or maybe some dependent services become unavailable need to be detected, debugged and fixed as soon as possible. To insure all of this, test the product for performance, usability, load and security, and overcome any potential risk beforehand. Security testing. With cloud native apps, most of your app data are hosted on cloud. This makes security a big concern for the stakeholders.

The main objective of security testing is to stop any threat or malware from accessing, stealing or manipulating any of the sensitive data. It also helps you identify any of the threats and measure their potential vulnerabilities. So far, we have seen testing allows us to detect, debug and fix issues in a cheaper manner than waiting for them to be serviced by a user. But how do we test for things that we are not aware of that can fail? How do we test for the unknown unknowns?

Testing team should bring as much information as possible to the known knowns quadrant, which represents facts about our service. When we change something on our application, previous known knowns are overturned. Testing helps us move from the known unknowns to the known knowns. We can ask questions during the test and get the answers. For example, does this function behave as expected when I provide these specific arguments?

Or does my service returns a 400 when the user sends an invalid data? Or does the UI shows an error message when a user tries to log in with an invalid username and password? Known unknowns are issues that we didn't even they could happen. We can't test for them as by definition, we don't know what can fail until it does. For this case, good observability tool in the production will allow us to debug new issues we couldn't anticipate, but it comes at a high cost.

Once identified, it's always a good idea to write the cheapest test possible for it to avoid regressions and bring it to the known unknowns quadrant for future revision of the software. This will save us time and money. Traditional testing strategies are insufficient for identifying unexpected failures that could occur when an app is deployed. However, the following strategies are helpful for testing unknown unknowns in the cloud native applications. Let's have a look at them one by one.

The first one is Chaos Engineering and Failure Mode Testing. Now, given a microservices-based application, the number of ways the product can fail in production can be unlimited and unpredictable due to the large amount of complexity involved. Chaos engineering is a proactive and a deliberate process of injecting chaos usually in controlled conditions to figure out how a system will respond. That way, you can identify possible flaws before pushing to production.

Failure mode testing helps to identify the cause and effect of failure, and together, it can help us to have a more reliable and resilient product. Next is canary deployments. Gradually rolling out new functionalities or features to a small set of users is a best practice that lets you identify and fix faults before making the app available to a larger audience. Since the new feature is only distributed to a small number of users, its impact is relatively small and changes can be reversed quickly should the new code prove to be buggy.

A/B testing. So while canary releases are a good way to detect problems and regressions, A/B testing is a way to test a hypothesis using variant implementations. A/B testing is a way to compare two versions of something to determine which performs better. In an A/B test, some percentage of your users automatically receives version A and the others receives version B. At the end, the results from two groups, which is a variety of metrics, is compared to determine which version performed better.

Blue/Green deployment. Blue/green deployment is a softer deployment strategy which utilizes two production environments, a blue environment and a green environment. That helps the software deployment process easier and safer. At any time, only one environment is live with the live environment serving all the production traffic. Once you have deployed and fully tested the software in one of these environments, you can switch the router so all the incoming requests now goes to that environment.

This technique helps eliminate downtime due to app deployment. In addition, blue/green deployment reduces risk. If something unexpected happens with your new version on one of the environments, you can immediately roll back to the last version by switching to the older environment. Observability, Monitoring and Log Analysis. One of the approaches which helps us understand the behavior of software in production better is observability. Observability is defined as the approach to understand the ability of the product's internal state by observing its outputs.

There are also monitoring techniques and tools using which we can collect, store, maintain, and query information related to the application state, behavior, interaction between the services in production. We can interpret and display them using metrics and logs. These logs and metrics can be analyzed further to gain valuable insights or to evaluate and debug issues quickly. OCI provides the features and tools to help with these activities.

![image](https://github.com/qriz1452/oci/assets/112246222/f1afd309-0f1f-41e5-bee4-04c0a4e3177f)
![image](https://github.com/qriz1452/oci/assets/112246222/369e4d28-94dd-4afb-a7df-f32a353e1820)

--------
Now Playing : OCI Vault: Overview

OCI Vault is an Oracle-managed service that allows you to centrally manage your encryption keys and secret credentials. It currently supports three encryption algorithms-- AES, RSA, and ECDSA. In addition to leveraging the encryption of password credentials to use with any external application. The Vault service integrates with OCI SDK, CLI, or API clients as well as integrating directly with several OCI services under the covers.

The main elements include the vaults themselves, keys, and secrets. I'll be covering each of these as we progress further in our training. Essentially, the Vault service removes the need for you to have to store these encryption keys and secrets in configuration files or in code. As a best practice, DevOps engineers should use Vault to help improve the overall security posture for their application and service deployments.

To use the Vault service, you start off with creating one or more vaults. Each vault serves as a logical container where you leverage the service to create an durably store your keys and secrets. When creating a vault, you choose one of two types. The first one is called a virtual private vault, which will essentially be a dedicated, isolated partition in a hardware security module. With this option, you can store up to 1,000 key versions, and you have better isolation, of course, because it's dedicated to you.

Another advantage is, you can back up the vault and the keys you have created to an OCI Object Storage bucket, which supports disaster recovery scenarios and cross-region replication requirements. So consider this option to be the more advanced version of the product. And of course, it comes with a higher cost.

The default option is to provision your vault in a shared partition. While it is still totally secure, you share that HSM partition with other Oracle customers. As such, you don't get some of the advanced features. For example, you can't back up to object storage. However, it has a lower cost because you only get charged for the actual number of keys, key versions, and secrets which are stored.

So now, what are keys? Well, these are logical entities that are used to represent one or more versions of cryptographic material which is generated for a specific algorithm. You can create and use AES symmetric keys or RSA asymmetric keys for encryption and decryption. And you can use RSA or ECDSA asymmetric keys for signing digital messages. In the Vault service, conceptually, there are three types of keys-- master encryption keys, data encryption keys, and wrapping keys. Let's take a closer look at each of these.

To better understand, master encryption keys are the keys that you actually create or import into your vault. You select the encryption algorithm and key shape, either the number of bits for AES and RSA, or Elliptic Curve ID for ECDSA. In addition, there is this concept of data encryption keys which are generated by a master encryption key. Data encryption keys themselves are encrypted dynamically with a master key. This is known as envelope encryption.

You see, OCI services, such as block or file storage, either use Oracle-managed keys, or you can specify a custom master key from your vault for specific use cases, for example, one or more object storage buckets or specific block volume.

As noted earlier, when you create a new master encryption key, you decide on one of two protection modes. The first one, HSM, is when your key is backed by a highly available and durable hardware security module, and all cryptographic operations take place inside the HSM. However, with this option, the key cannot be exported to an external client. Now, this is the most secure option. However, it is slightly more restrictive.

The second option, software, where the master encryption key will be stored on an internal server, in this case, it can be exported to perform cryptographic operations on a client instead of just the server. However, these keys are fully protected while at REST, since they are encrypted by a root key on the vault's HSM partition. Be aware, there are different pricing models depending on which protection mode you choose to use.

The third kind of key, which is-- Vault service uses as a wrapping key. It's automatically included with each vault. You use the public portion of the wrapping key pair when you need to import an external key into your vault. Since the vault has access to the private wrapping key, it can unwrap it so it can be imported as another master encryption key. So instead of letting the vault generating your master keys itself, you might wish to leverage this BYOK strategy for various reasons.

You may need to use keys that have been generated by some other tool or source based on your requirements. Or you might wish to use the same keys that you're already using in other cloud environments or in private, on-premise systems. Some choose to simply leverage the Vault service for the management of their external keys, such as storage, expiration, and deletion. Or perhaps you wish to own and handle your keys outside of OCI for additional durability and recovery use cases.

Finally, let's talk about rotating these master keys. As I mentioned earlier, each key is automatically assigned a key version when you create a key for the first time. Well, when you rotate a key, a new key version is automatically generated. Or you can choose to import another key. As a best practice, periodically rotating a master encryption key will limit the amount of data that is encrypted or signed by just one version of the key, which can significantly reduce risk to data integrity if a key is ever compromised.

Now, you might be wondering, if we rotate the key, how does the Vault service figure out how to handle decryption, for example, if encryption was done with version, but now we're using version two? Well, behind the scenes, the vault leverages the unique Oracle Cloud Identifier of the older key version as needed. And while older versions can't be used for encryption anymore, fortunately, they will still be available and used to decrypt data which was encrypted earlier with a previous version



---------
Now Playing : OCI Vault: Integration with OCI Services



As I mentioned in the vault introduction lesson, there are several OCI services which can integrate directly with a vault for handling data encryption. Here's the current list-- Object Storage Buckets, file storage, boot and block volumes, streams within a stream pool, Kubernetes secrets used in an OKE cluster, and Autonomous Container Databases. This list of services will be expanding in the future, so you should always check our online documentation. As you can see here, the scope for all these services is regional which means you'll be designating master keys from vaults located in the region in which the OCI service resides.

However, before we discuss integrating the vault service, let's review how Oracle Cloud manages data encryption in those other OCI services. By default, we'll handle data encryption and decryption by using an Oracle-managed master encryption key. Assuming you have selected that option, as you see here in this example, when you're provisioning those resources, such as a block volume, or an object storage bucket, or an OKE cluster.

Therefore, even if you're not leveraging the vault service, stored data in those OCI services, often referred to as data at rest, is always encrypted. You can't turn it off, which is an important point to keep in mind. So then Oracle-managed keys means that we use a master encryption key from an internal Oracle-managed vault which will generate a data encryption key to retrieve and handle the respective services for encrypting data.

However, when you decide not to use Oracle-managed keys, this is where you are choosing to leverage the OCI vault service by selecting a master encryption key from your own vault. As you can see here, you locate your vault then choose the key you wish to use. There are various security reasons why you might choose to do this. However, the most common use case is when you're provisioning resources in a designated security zone compartment. In that case, for example, buckets are not allowed to use an encryption key managed by Oracle. You must use a master encryption key from your own vault.

Keep in mind the customer-managed keys selection we see here is not the same as the bring your own key option I discussed in the introduction lesson. Customer-managed keys simply means a key that is maintained within your vault. Therefore, it could be a key that you previously imported into your vault or it could be a key that was generated by the vault service when you created it. Either way, that key belongs to you. You manage rotating key versions and you are responsible for the lifecycle of the key.

So now let's take a look at how all of this works under the covers from a visual perspective, because this is an important concept you need to understand. Here's your vault backed by hardware security module, which is FIPS 140-2 Level 3 compliant. And within the vault service itself it leverages the identity and access management service. You then identify and define authorization policies to decide which services and which users have access to your vault or even down to a specific particular key or a secret.

Now in this example someone is adding some plain text data. For example, a log file, into an object storage bucket. Before it can be stored of course, it needs to be encrypted. Let's see how this process works. The object storage service requests a data encryption key along with a copy of the key encrypted with a master encryption key from the vault service.

Next, the object storage service users the plain data key to encrypt the log file data. But more importantly, it immediately removes that key from the memory as soon as it's used. Now the encrypted log data file and the encrypted data key are stored in the bucket, so later on even if somebody, let's say, gets access to those two artifacts they still cannot make any sense of the data, because the data key itself is encrypted. Therefore, data remains fully protected. Only a system or entity that has access to your vault to request a decrypted plain data key will be able to decrypt the data file.

So now let's reverse the process. Since the encrypted data key is stored in the bucket, when the object storage service needs to decrypt the data, the first thing it does is send that encrypted data key back to the vault, because the service needs a plain data key. The vault service uses the appropriate master encryption key to remove the envelope encryption and then sends the decrypted data key back. Now, object storage can use the key to decrypt the file, the ciphertext, back to plain text which was our log file. Once again, the service immediately removes the plain data key from memory as soon as that process is over.

So this is how it all works end-to-end. Keep in mind the object storage service or for that matter any other service which integrates with vault has no access to the plain data key until it is retrieved each time from the vault. Therefore, your data at rest is always protected. And although we used object storage for this example, a similar process is followed for all the other integrated OCI services, such as block volumes, OKE clusters, or the file storage service.


-------
Now Playing : OCI Vault: Secrets Overview


OCI Vault-- Secrets. As you should recall from my introduction lesson on OCI Vault, I discussed the elements of the Vault service, which included the Vault itself, backed by a FIPS 140-2 Level 3 hardware security module that is either a shared or private HSM as well as the master encryption keys you can create or import into your Vault.

Until now, we haven't really discussed the third important element, secrets. Secrets are credentials, such as passwords or tokens or any other confidential data that you need to use with other Oracle Cloud Infrastructure services or perhaps even with other external applications or systems. Storing secrets in a Vault provides greater security than you might achieve storing them elsewhere, such as in code or configuration files. And you can retrieve secrets from the Vault service when you need them to access resources or other services.

You can create secrets by using the OCI Console UI, as shown here, or programmatically in code or from scripts using the OCI SDK, CLI, or REST API. In addition, each secret is automatically assigned a version. So when you rotate a secret, you provide new secret contents to the Vault service to generate a new secret version.

Periodically rotating secrets reduces the impact in case a secret is exposed. The secret's unique Oracle-assigned identifier called an Oracle Cloud ID remains the same across rotations allowing the Vault service to rotate secret contents to meet any rules or compliance requirements you might have, while programmatic access remains the same.

Optionally, there are rules you can apply to specific secrets preventing the re-use of secret contents to limit the scope of affected resources in the event of a security breach is the first one. You can deprecate a secret version and then delete it if you find out it can no longer be safely used. And you can choose whether secret re-use rules apply even to deleted secret versions.

You can also configure an expiry rule to specify a time interval for how long a secret version can exist. The longer that a set of credentials are used, the more time an attacker has to try to access or decipher them. As a best practice, frequently updating a secret with new contents helps keep credentials safer from users with malicious intent or, at the very least, makes shorter the period of time during which compromised credentials can unknowingly be used or disseminated.

You can configure a secret version to expire anywhere from 1 to 90 days. However, the secret can also have an absolute expiration date and time, ranging from day to one year after its creation date. You can configure either of these values or both. And you can decide whether the secret contents are blocked past the expiration date.

In order to gain a better understanding for using secrets, let's first take a quick look at the OCI Console UI. So here I am in my console on the Vault's page, under Identity and Security. You can see I've already created a Vault called Demo. And inside the Vault, I have a few master encryption keys that can be used to include those that are software or HSM or those that are using the AES algorithm and so forth.

What I want to focus on now is the secrets. I've already created one secret here called ADB-username. And I just do that for sake of time here. I can view the current secret details. Right now we only have one version. So if I want to see the contents, I can click in there. By default, it shows the Base64. I can show the clear text. As you can see, this is the username for the database, which, in this case, is the admin user.

So for demonstration purposes, what we're to do is go back, and we're going to create ourselves a new secret that I'll use for the database user's password. So I'll come in here, give it a name. Optionally, I'll provide a description, which will be handy for anyone else reviewing this. And of course, we need to select an encryption key. I'll choose this one. And then we need to provide some contents.

Now, for this demonstration, of course, I just have a demonstration password. And I can create that secret. I can also see what that looks like in a Base64 conversion. Now, it'll take just a few moments to create that secret. While that's being created, I want to point out what we're going to need in order to use these secrets programmatically or from a script.

So I'll go back to our ADB-username to show you that, when you click on a secret, there is a unique OCI ID. And I could just copy it. Of course, for demonstration, I'll just show you what that looks like. And that's the OCID value that I'll need to have available to my developers.

Now, what's interesting is, once they have this OCID, that's going to remain the same regardless of how many times we rotate or update the secret contents. This will always be, in this case, associated with the ADB-username. And of course, they'll also need the OCID of the password, which has now been created. And it too would have a unique OCID that we would use in our environment.

And by the way, as a reminder, for automating security requirements, the DevOps engineer can manage all of these same configurations programmatically using the Vault CLI or API and scripts or code instead of manually doing what I just did in the OCI Console to include obtaining the secret's Oracle Cloud ID. So now that we have the OCID of each secret, in this Kubernetes examples, I've added two new Vault variables in the YAML build file, which is used to build the code, create a container image, and then deploy to an OKE cluster.

The Maven Build command will reference those variables, in this case, the database username and password. In this Oracle functions example, instead of defining hard-coded variables used to connect to the OCI container registry within this YAML configuration file, I replace them with Vault variables, which are set to the Oracle Cloud IDs of those two secrets in my Vault.

And for any other use case that doesn't necessarily involve Microservices deployed within OKE cluster or Oracle functions, you can still dynamically retrieve the secret credential using the OCI Vault API or CLI, programmatically, using that same secret OCID. For more detailed information on leveraging the Vault CLI, API, or SDK functions, be sure to review our online documentation and tutorials.




----

Now Playing : Security for OKE: Image Security


For compliance and security reasons, system administrators often want to deploy software into production system only when they are satisfied that the software comes from a trusted source and the software has not been modified since it was published, thus compromising its integrity.

Container image signature verification ensures the authenticity and integrity of container images and ensures that the image used at runtime is the same image that was published and hasn't been tampered with. So it helps prevent potential man-in-the-middle attacks. Container images are signed in the OCI Registry using an asymmetric master encryption key from the OCI Vault, then the signatures are viewed and verified ensuring that the integrity of the image isn't compromised.

To further enhance security, you can configure clusters you've created with OKE to only allow the deployment of images from the OCI Registry that have been signed by a specific master encryption key. To make this happen, administrators define policies that will require image signature verification.

This is done by first adding policies to allow the cluster to access the OCI Vault as well as the images in the Registry. You then enable signature verification at the OKE Cluster level, under Resources, we click Image Verification, then click Enable, then select the Vault and the master encryption key used to sign the images.

This signature verification policy will permit the use of images for deployed pods signed with only this master encryption key, although the policy can be updated to add additional keys if needed. Developers easily sign the container images as part of their build process. After they push the image to the registry, they execute this OCI command to sign the image once they've obtained the image ID.

OKE then enforces these policies by validating that the image is appropriately signed prior to being used in a pod deployment. From now on, the cluster will only allow the pooling of images from the registry that have been signed using the master encryption keys included in the image verification policy.

Now while we're discussing images, an additional consideration and best practice, because image tags are mutable, we recommend that you only pull your Container Docker images using the image digests and not pull images using tags. Image digests are the SHA-256 digests of your image, which allows Docker to verify the image it downloaded is what you expected. As a reminder, of course, you can always retrieve the actual image digest IDs by executing the Docker images command when needed.

To further assist your security policy for images to be used in OKE Cluster deployments, you can also leverage the OCI Registry to enable scanning of container image repositories and to view scan results. When repository scanning is enabled, the OCI vulnerability scanning service scans the images pushed into the repository for security vulnerabilities published in the Common Vulnerabilities and Exposures, or CVE database.

In addition, these images are automatically rescanned when new vulnerabilities are added to the list of threats. So to access the scanning information, just navigate to the image in the repository, then in the scan results, you can see a list of potential vulnerabilities identified with the vulnerability description, risk level, and a link to the CVE database.



--------

Now Playing : Function Container Permissions

When a function you deployed is invoked, it runs inside a Docker container. The operations that a container can perform are determined by the user ID and group ID specified when the container is started. So in order to protect against the container running as the root user, which would be the default if a UID and GID are not specified, Oracle functions always specifies a user and group named fn using 1000 as the UID and GID. No privileges are granted to UID and GID 1000. Therefore, the container and the function running inside it cannot acquire root capabilities, as defined in the Docker documentation.

In addition, the container is prevented from gaining privileges. So as a result, you cannot create and deploy functions that depend on any capabilities that are unavailable or depend on privilege elevation, such as a sudo command. Also, be aware if you're using your own Docker file, you must include this command to add that user and group yourself.

![image](https://github.com/qriz1452/oci/assets/112246222/6f9e5521-24ff-42f6-8843-cd3b838f3d0d)


--------
Now Playing : API Gateway: OCI Certificates Integration

Welcome back. The API gateway Service now uses the OCI Certificate Service to manage certificates and certificate authorities. This means that, when creating or updating a gateway that is receiving a request for a custom DNS hostname, you will select the corresponding TLS certificate from the OCI Certificate Service. Let's now take a quick peek as to how this looks in the OCI Console.

So first of all, let's navigate over Developer Services, API Management, and Gateways. And let's just take a look and remind yourself, when you create a new API gateway, since it is TLS-enabled, it requires that you specify a certificate issued by a certificate authority. So you have two choices. Of course, there's the default option where it's a certificate provided by the gateway using an Oracle-designated certificate authority as you see here.

Or if you're using a custom DNS configuration, and you must choose a certificate that's been previously added to the Certificate Service in your tenancy. So then since we cover the Certificate Service. In other lessons and demos, let us quickly show you those options here in the console. Identity and Security, heading over to Certificates, and of course, you can upload a certificate bundle, if necessary, a PIM file.

You can also, if you need to, create a new certificate authority, either a root certificate authority or a subordinate certificate authority, and, of course, adding certificates by specifying either an imported certificate that's issued by a third party that you're going to manage here in the Certificate Service or one that's issued by an internal CA where you're going to manage it either in Certificate Service or manage it externally.

Anyway, let's head on back to our creating our gateway. So once you've decided on your certificate, of course, then under Advanced Options is where you have the opportunity then to add one or more certificate authorities or certificate authority bundles if needed in your setup. OK, that's it for this lesson on OCI Certificate Service integration with API gateway. Thanks for watching.



-------
Now Playing : API Gateway: Customize Trust Store


Welcome back. The gateways you create with the API Gateway service verify TLS certificates presented to them using a trust store. Let's learn more about how that store can be customized. Your gateways trust store can contain certificate authority root certificates and CA bundles of root and intermediate certificates.

And when you first create a new gateway, a default CA bundle is added automatically, containing certificates of well-known public CAs, such as IdenTrust and DigiCert, which enables the gateway to verify TLS certificates presented by backend services. In addition to the default CA bundle, you can add the root certificates of other custom certificate authorities and other ca bundles to the trust store after you've added them as resources within the OCI Certificates service.

Now, any TLS connection to your gateway, including from backends and from the response cache, will all be verified using both the default CA bundle and the custom CAs and CA bundles you've added to the store.

By the way, this is also necessary for those use cases when you need to specify mutual TLS support while configuring an API deployment, as the gateway will use only the custom CAs and custom CA bundles to verify gateway client certificates. The default CA bundle is not used to verify client certificates during a mutual TLS handshake. We cover this aspect in more detail in another lesson.

Let's now take a quick look as to how this all works in the OCI Console. Let's start by navigating over from Developer Services to Gateways. I already have a test gateway we can use for this demonstration. And as you can see down here on the left-hand side, there is a link for Certificate Authorities where we can add one or more. Now, in order to do that, I have to have them. So over in the Certificates service-- we'll go there from Identity and Security over to Certificates.

For this demonstration, I did two things. I added, first, a certificate authority for this example organization. We'll take a quick look at it. Again, it's a self-signed root certificate, and it's just got basic information. And I've added this to this Certificates service. Also in the Certificates services, I uploaded and brought in a ca bundle called Demo. And if you wanted to see the contents, you could. You'll notice that it's just a PEM file with a bundle of a couple of certificate authorities.

Now that those two resources are available in the Certificates service available to me, let's go back over to our test gateway. I simply click on adding them with this button. And there are two types, certificate authorities and bundles. We'll do the certificate authority first. And since I'm looking in that compartment, it only sees one. On the Certificates service, I can add that. And then I can click here to add that bundle right here and select the bundle. And it's as simple as that. We click on Add Certificate Authorities and wait for it to be updated.

Now that those updates have been made and the authorities and bundles have been added, we can see them listed here. If we navigate back over to the Certificates service and I look at each of them, I can see their associations, now, will be present.

If I click on my certificate authority, I can go down to associations and I can see that it's actually associated with my API gateway. The same is true for the bundle. I can click on that bundle and we can see it also associated with my API gateway. OK, that's it for this lesson on Customizing the API Gateway Trust Store. Thanks for watching.

![image](https://github.com/qriz1452/oci/assets/112246222/572ea909-be1b-4cb9-987e-fa6ffe3c5f88)


-------
Now Playing : API Gateway: Mutual TLS Support


Welcome back. In this lesson, we discuss adding mutual TLS support for your API deployments in the API Gateway service. First, a quick review. In mutual TLS authentication, sometimes referred to as two-way SSL, both the client and server-- in this case, your gateway-- authenticate each other by providing their digital certificates so that both parties are assured of the other's identity.

In this aspect, there are handshake messages used to establish the encrypted channel prior to actually exchanging data. The client initiates the handshake by sending a hello message to the server. The message will include which TLS version and cipher suites they support, along with some other information. In reply to the client, the gateway sends a message containing the gateway server certificate, the chosen cipher suite, and some other encryption information, along with a request for the client to send their certificate.

The client then validates the gateway certificate using one of the certificate authorities contained in their trust store. Then they send their certificate to the gateway server, along with the session key information that is encrypted with the server's public key. Now, API Gateway will validate the client's TLS certificate to verify the client's identity using one of the custom certificate authorities in its trust store. Then finally, it sends a finished message completing the handshake. At this point, the API request and response can be processed securely on the encrypted channel.

How is this configured in API Gateway? Well, you simply add a request policy in the API deployment specification to add mutual TLS support to an API. The mTLS request policy applies globally to all routes in that API deployment specification. Now, for extra control, you can also specify that certificates presented must contain particular values in the certificate's email address, URL, or domain name fields. In that case, the gateway will reject requests from client certificates that do not contain them.

If you don't specify values for these fields, API gateway will accept all requests, as long as the certificate is valid. Also, be aware that, in a mutual TLS handshake, the API Gateway only uses custom certificate authorities and custom CA bundles to verify client certificates. So before you click to enable mTLS as an API request policy, you must first add the custom CA or CA bundle to your gateway's trust store. We discuss more on that topic in another lesson.

Let's now take a quick peek as to how this is done in the OCI Console. Let's navigate to Developer Services, API Management, and Gateways. Here, I already have a gateway created that we can use for this demo. And one of the requirements, before I edit a deployment policy, is to make sure that I have one or more custom certificate authorities, or a CA bundle. And as you can see here, I indeed do. So this will work.

Let's go over to our deployments. I have a deployment that I created earlier, which is a simple doorway into a demo function that can be called. And we're going to update its configuration to add that mutual TLS request policy. It's as simple as clicking Enable.

And then if I left it there, then it would accept all certificates from anyone, as long as it's valid. But we could limit this to one or more domains. In this case, I'm going to add example.com and maybe example2.com. I could add another one. Maybe it's example.org, depending on what the use case is. You can actually add up to 10 of these if you need to.

From there, I simply click on Next and Next. Since I've already configured the configuration, I can show those filters that I've set for this and then save those changes. This will then update the API deployment in this gateway. And that completes the demo. That's it for this lesson on adding mutual TLS support for API deployments. Thanks for watching.
![image](https://github.com/qriz1452/oci/assets/112246222/a34d9910-ab8f-4946-8796-6ab152c705d7)


---------




































