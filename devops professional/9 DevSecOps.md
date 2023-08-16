DevSecOps Introduction


We all are aware of the typical DevOps workflow. The DevOps workflow using the CI/CD involves integrating continuous integration and continuous delivery or deployment processes to ensure rapid and efficient software delivery. With CI/CD, code changes are automatically built, tested, and deployed to production environments, which enables faster delivery cycles and more reliable software releases.

But what about application security? Security is essential for modern apps that handle sensitive information, such as credit card details and personal data. To protect this information, security teams must conduct comprehensive audits before releasing any production version.

In traditional software development approaches, security practices were often not integrated into the development lifecycle. And security audits were typically carried out towards the end of the development process. This approach could result in security vulnerabilities being missed or introduced during the development process, making it difficult to address them later on.

Let's explore a few potential scenarios that could result in a security breach. These include using outdated or vulnerable third-party libraries or dependencies. Now, many applications rely on third-party libraries or dependencies to function properly. However, if these libraries are outdated or contain known vulnerabilities, they could be exploited by attackers to gain access to sensitive information or execute malicious code.

Leakage of sensitive data. Sensitive data can accidentally leak due to various reasons, such as misconfigured access controls, unencrypted data transmission, and human error. Once data is leaked, it can be used for malicious purpose by attackers. Organizations need to implement proper data security policies and controls to prevent such accidental data leakage.

Next is vulnerability within container images. We all know containerization is a popular method for deploying and managing applications. However, if container images are not properly secured, attackers can exploit vulnerabilities within them to gain unauthorized access. Regular security assessments and vulnerability scanning can help detect and remediate such vulnerabilities.

Lastly, misconfigurations in container orchestration tools. Container orchestration tools like Kubernetes are used to manage and scale containerized applications. However, misconfiguration in these tools can create security vulnerabilities that can be exploited by attackers. It is important to follow security best practices and regularly audit the configuration of these tools to prevent security breaches.

However, these issues can sometimes go unnoticed by developers. And as a result, security teams must conduct thorough scans and analyze any changes made to the code in order to identify potential security issues within the application.

This process can be time-consuming, taking hours, days, or even weeks depending on the complexity of the application. Once the bug has been identified, they must be passed along to the developer to apply fixes in subsequent versions.

However, in the meantime, due to the efficient DevOps workflow, there may be multiple new versions of the applications waiting in the queue for security audits. This can lead to a bottleneck that prevents app releases from entering the production environment for weeks.

So why does security audits take so long? Historically, security has often been treated as a lower priority in software development with more emphasis placed on speed and functionality. Traditional compliance monitoring and security tools were not designed to keep up with the rapid pace of change in our DevOps environment.

As a result, they may not be able to detect vulnerabilities or other security issues that arise from the use of microservices, containers, or cloud-based infrastructure which are often used in DevOps workflow. This can lead to security vulnerabilities going undetected, requiring more time and effort to identify and address, which can slow down the release process.

DevOps teams sometimes see security as an obstacle to development speed and efficiency, leading to less attention being paid to security considerations. This can result in undetected security issues that require more time and effort to fix, slowing down the release process.

Application delivery involves multiple teams, including the development, security, and operations. However, the misalignment of goals between the developer and security teams often leads to issues in the delivery process. Developers wanted to make new things quickly and in creative ways, but security teams cared more about making sure everything was secure and met the rules.

This is where DevSecOps come in as a solution to bridge the gap and ensure a collaborative and secure delivery process. DevSecOps is the logical conclusion to DevOps' missing component, security. Simply put, DevSecOps is a DevOps extension that codifies security as part of the larger goal structure.

To accomplish this, DevSecOps framed security as a shared responsibility where all the teams are working together to find and fix security issues early in the software development process. By collaborating, they can create applications that are safer and of higher quality all while keeping things moving quickly and efficiently.

The idea is to keep development and testing going smoothly without getting held up by security concerns so that, in the end, the application delivered is secure, reliable, and functional.

Delaying the considerations of security concerns in the software development process can lead to an increase in the cost and time required to identify and address security vulnerabilities. However, by implementing a shift left security approach where security is given greater emphasis earlier in the development process, it is possible to reduce these costs and minimize the time needed to fix security-related issues.

The shift left approach involves incorporating security practices such as code analysis, vulnerability scans, and infrastructure security into earlier stages of development lifecycle rather than waiting until just before the deployment. 

![image](https://github.com/qriz1452/oci/assets/112246222/ee278252-c916-4240-a03f-8200fca5b72b)


------------------



 Applying DevSecOps in OCI

 In today's digital landscape, security is more important than ever. And integrating it into your DevOps workflow is crucial for ensuring the safety of your applications and data.

In this session, we'll explore the various security options available when working on DevOps projects with the help of this diagram. When a developer commits code to a repository, they must follow certain policies and permissions when using DevOps code repositories. To integrate with third party code repositories, such as GitHub or GitLab, developers need to create a personal access token to obtain permissions to access the code.

Now, to ensure the security of these tokens, they are stored in an OCI Vault. It provides a saved and reliable method for storing sensitive data. Once the code is committed to a code repository, it can trigger a CI/CD pipeline. When we use a CI/CD tool to build our applications, we have access to some powerful capabilities.

For example, we can use a service called application dependency management to help identify security weaknesses in our software applications by checking their dependencies. This service relies on scores provided by the Common Vulnerability Scoring System, which is an open framework used to communicate the severity of software vulnerabilities. In order to use this service, we need to configure it during the manage build stage of our DevOps pipeline.

We can also use third party tools like sonatype, sonaqube, or overops to analyze our code for security defects or bugs in code quality. These tools helps us make sure that our code is as secure and reliable as possible.

Once we have built our container image, we can push it to an Oracle Cloud Infrastructure Registry repository with scanning capability enabled. The CI/CD tool then uses the Vulnerability Scanning REST API to obtain the results of image scan. Now, based on the results of the scan, the CI/CD tool can decide whether to move the image to the next stage in the lifecycle or not.

This is an important step in ensuring that our applications are secure and reliable. Once the code analysis and image scanning process have been completed successfully, the CI/CD tool moves on to automated testing. During this stage, we typically conduct security, API integration, and user interface testing to ensure that our applications and code are working as intended.

If the tests pass, it's a good idea to add a control stage approval within the deployment pipeline. This involves pausing the deployment for a specified period and notifying an approver of the deployment. The approver will then manually provide approval before the deployment can proceed. This is an important control measure that helps us ensure that our deployments are secure and reliable.

Once the deployment pipeline has been approved, the application and code are deployed to the production environment of the OCI platform. The deployment can be done on various OCI platforms, such as compute instances. Now, this includes both virtual machines and bare metal instances.

To ensure that our deployments to compute instances, container engine for Kubernetes, also known as OKE and OCI functions are secure, we can take several steps. For example, we can use security list and network security groups to control inbound and outbound traffic to our compute instances. We can also use compartmentalization and identity and access management policies to restrict access to our resources and limit the action that can be taken on them. You can also deploy to a serverless function platform called OCI Functions.

Similarly, when deploying to OCI Functions, we can use identity and access management policies to control access to our functions and protect them from unauthorized access. We can also use encryption and key management to secure our data and protect it from potential attackers. When deploying to OKE, we can use Kubernetes security features, such as role-based access control, and network policies to ensure that only authorized users and services can access our applications and services.

We can also use secrets management to securely store and manage sensitive information, such as passwords, API keys, and other credentials. Continuous monitoring of our applications environment is essential for identifying security issues. We can use OCI's monitoring tools such as APM, monitoring, and logging, configure them to use OCI's native functions like notification for quick response to security threats.

We can also integrate logs with ServiceNow or third party SIEM systems to streamline security issue resolution. To wrap up, we've learned about implementing DevSecOps in OCI DevOps project and utilizing its security services to secure your DevOps environment.

![image](https://github.com/qriz1452/oci/assets/112246222/157274e6-f3cd-4b48-9a52-e61a078f217f)



------------

DevSecOps Best Practices


How do you ensure the security of your application in a fast-paced DevOps environment? Let's explore the best practices and tools for implementing DevSecOps in Oracle Cloud Infrastructure so you can confidently deliver secure and reliable software to your customers.

Enforcing policy and governance is the foundation of a strong DevSecOps process. It ensures that security is built into the development lifecycle from the very beginning, and helps reduce the risk of security breaches. Identity and Access Management is a critical part of policy and governance in DevSecOps. It involves managing user identities, roles, and permissions to ensure that only authorized personnels have access to sensitive resources.

Privileged Access Management involves controlling and monitoring privileged access to critical systems and data to prevent unauthorized access or misuse. To enforce policy and governance in DevSecOps, it is important to define roles and responsibilities for everyone involved in the development process, from developers to operations teams to security personnels. Training and education are crucial for effective implementation of security controls in DevSecOps.

Staying updated with the latest safety techniques and best practices is equally essential to keep pace with the evolving threat landscapes. Automating DevOps security processes and tools is essential to reduce the risk of human errors and security incidents. By leveraging efficient tools and automation, organizations can streamline their DevOps security processes, resulting in faster and more resilient applications.

Oracle Cloud Infrastructure provides a range of security tools for DevOps teams to use, including code analysis, configuration management, patching, and vulnerability management tools, like OS Management, and Oracle Vulnerability Scanning Service. Additionally, privileged credentials and secrets management is offered through OCI's Vault Service.

To ensure the security of your OCI assets, it is crucial to perform comprehensive discovery of all devices, tools, and accounts in your environment. This process helps ensure that all assets are validated and monitored continuously in accordance with your security policy. By doing so, you can align your assets to adopt a zero trust security model, where no user or device is trusted by default. This approach can help mitigate the risk of potential security breaches, and ensure that your security policies are consistently enforced across all assets.

You must make sure to regularly scan for vulnerabilities in your applications and systems, and prioritize fixing them based on their severity. It is also important to follow established security guidelines, such as the OWASP DevSecOps Guideline during the development and testing process. This helps ensure that security is built into the application from the start, and reduces the risk of security incidents in production.

In a DevOps environment, managing credentials and identity accounts in code is critical to ensure secure access. Utilizing a secrets management tool like Vault can help prioritize security and effectively manage the lifecycle of secrets.

In order to ensure secure access to your infrastructure, it is important to implement Privileged Access Management policies. With the help of Oracle Cloud Infrastructure services, such as IAM, DevOps IAM policies, logging, and monitoring, you can effectively control, monitor, and audit access to your resources. This helps to prevent unauthorized access and protect against security threats.

When implementing DevOps processes, it is important to segment networks to reduce the attack surface and isolate different work environments, such as production and development or test environments. This helps ensure that security risks in one environment do not impact others, and provides better control over access and security policies. 


---------------


 OCI Vault: Overview

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

Now, you might be wondering, if we rotate the key, how does the Vault service figure out how to handle decryption, for example, if encryption was done with version, but now we're using version two? Well, behind the scenes, the vault leverages the unique Oracle Cloud Identifier of the older key version as needed. And while older versions can't be used for encryption anymore, fortunately, they will still be available and used to decrypt data which was encrypted earlier with a previous version. 


![image](https://github.com/qriz1452/oci/assets/112246222/bc15d6ac-d31c-4782-a9bb-9de2ded6ca97)



-------------

 OCI Vault: Integration with OCI Services


As I mentioned in the vault introduction lesson, there are several OCI services which can integrate directly with a vault for handling data encryption. Here's the current list-- Object Storage Buckets, file storage, boot and block volumes, streams within a stream pool, Kubernetes secrets used in an OKE cluster, and Autonomous Container Databases. This list of services will be expanding in the future, so you should always check our online documentation. As you can see here, the scope for all these services is regional which means you'll be designating master keys from vaults located in the region in which the OCI service resides.

However, before we discuss integrating the vault service, let's review how Oracle Cloud manages data encryption in those other OCI services. By default, we'll handle data encryption and decryption by using an Oracle-managed master encryption key. Assuming you have selected that option, as you see here in this example, when you're provisioning those resources, such as a block volume, or an object storage bucket, or an OKE cluster.

Therefore, even if you're not leveraging the vault service, stored data in those OCI services, often referred to as data at rest, is always encrypted. You can't turn it off, which is an important point to keep in mind. So then Oracle-managed keys means that we use a master encryption key from an internal Oracle-managed vault which will generate a data encryption key to retrieve and handle the respective services for encrypting data.

However, when you decide not to use Oracle-managed keys, this is where you are choosing to leverage the OCI vault service by selecting a master encryption key from your own vault. As you can see here, you locate your vault then choose the key you wish to use. There are various security reasons why you might choose to do this. However, the most common use case is when you're provisioning resources in a designated security zone compartment. In that case, for example, buckets are not allowed to use an encryption key managed by Oracle. You must use a master encryption key from your own vault.

Keep in mind the customer-managed keys selection we see here is not the same as the bring your own key option I discussed in the introduction lesson. Customer-managed keys simply means a key that is maintained within your vault. Therefore, it could be a key that you previously imported into your vault or it could be a key that was generated by the vault service when you created it. Either way, that key belongs to you. You manage rotating key versions and you are responsible for the lifecycle of the key.

So now let's take a look at how all of this works under the covers from a visual perspective, because this is an important concept you need to understand. Here's your vault backed by hardware security module, which is FIPS 140-2 Level 3 compliant. And within the vault service itself it leverages the identity and access management service. You then identify and define authorization policies to decide which services and which users have access to your vault or even down to a specific particular key or a secret.

Now in this example someone is adding some plain text data. For example, a log file, into an object storage bucket. Before it can be stored of course, it needs to be encrypted. Let's see how this process works. The object storage service requests a data encryption key along with a copy of the key encrypted with a master encryption key from the vault service.

Next, the object storage service users the plain data key to encrypt the log file data. But more importantly, it immediately removes that key from the memory as soon as it's used. Now the encrypted log data file and the encrypted data key are stored in the bucket, so later on even if somebody, let's say, gets access to those two artifacts they still cannot make any sense of the data, because the data key itself is encrypted. Therefore, data remains fully protected. Only a system or entity that has access to your vault to request a decrypted plain data key will be able to decrypt the data file.

So now let's reverse the process. Since the encrypted data key is stored in the bucket, when the object storage service needs to decrypt the data, the first thing it does is send that encrypted data key back to the vault, because the service needs a plain data key. The vault service uses the appropriate master encryption key to remove the envelope encryption and then sends the decrypted data key back. Now, object storage can use the key to decrypt the file, the ciphertext, back to plain text which was our log file. Once again, the service immediately removes the plain data key from memory as soon as that process is over.

So this is how it all works end-to-end. Keep in mind the object storage service or for that matter any other service which integrates with vault has no access to the plain data key until it is retrieved each time from the vault. Therefore, your data at rest is always protected. And although we used object storage for this example, a similar process is followed for all the other integrated OCI services, such as block volumes, OKE clusters, or the file storage service


![image](https://github.com/qriz1452/oci/assets/112246222/75313eb3-42da-4322-ae91-425399df00e4)



----------








 









 









