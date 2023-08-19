 Now Playing : Security Introduction 

 Welcome to this module on OCI security. Let's start with an introduction. So in security, you always hear this term called shared security model. What does this actually mean? Well, in an on-premises environment, you own the whole stack and you are responsible for security end-to-end.

As you move to the Cloud, some of the responsibilities transfer to the Cloud provider, in this case, Oracle, and some are retained by you. So that is what we mean by a shared security model. What does it look like in the Cloud?

Well, in the Cloud, Oracle Cloud Infrastructure is responsible for security of the Cloud, which means things like the physical data center, the physical network, the physical host, even virtualization layer, making sure it's fast and it's up to date. All those are responsibilities of Oracle. So that's basically the security of the Cloud.

You are responsible for security in the Cloud. What does that mean? Well, that means you are responsible for the data, you are responsible for the endpoints, devices, mobile or PCs or your servers of your PCs which are accessing them. And you are responsible for account and access management.

So identities and access management. And there are some other things you are responsible for like if you're using operating systems, you need to make sure they are patched and kept up to date. So this is the model in the Cloud. Some responsibilities shift to the Cloud provider. Some responsibilities are still retained by you.

So let us look at the OCI Security portfolio available currently with-- available currently in OCI. I have put in this slide the use cases and the services, so you really understand not just the services, but you also understand the context in which they operate.

In OCI, security is built in using the defense in-depth methodology, meaning security is built in at various layers of the stack. So a good way to represent this is break down these services by use cases, and then list the OCI Security services that are available for each use case.

So let's start at the very bottom with the infrastructure protection. And here you can see there are several services which are listed. Because this is an introduction lesson, I'm just going to go through these quickly and cover a couple of them at each layer.

So the first one here is a service called web application firewall. It protects applications from malicious and unwanted internet traffic. It can help mitigate layer 7 DDoS attacks. And then there is also a service, which is called network firewall. And that monitors your network for malicious activity. And it can help with intrusion, detection, and prevention.

So this layer is all about infrastructure protection. The layer on top of this is around identity and access management. And it primarily deals with your users who have access to your systems who are the users, and then what kind of level of access do they have? What kind of permissions do they have to your systems?

Then we also have services like multifactor authentication. And MFA or multifactor authentication is a method of authentication that requires the use of more than one factor to verify a user's identity. And then there are a few other services at this layer.

The next layer up is around operating system and workload protection. So like previous layers, this layer also has many services. Let me quickly touch on a couple of them. Shielded instances you see there, they are kind of a virtual machine that offer additional security for customers who need to meet strict compliance and security requirements.

So for example, one of the features in shielded instances is Secure Boot. And what it does is when a VM starts up, it only uses trusted software due to that Secure Boot. So that's one feature, which is there. And there are several other features.

Then we have something like dedicated VM host, which is a bare metal machine single tenant dedicated to you where you can run your VMs. And then we have a service like OS Management, which monitors and manages updates and patches, not just for a single machine, but literally could be thousands of machines, so at scale. So this layer is all about operating system and workload protection.

Then the next layer up is around data protection. This is super critical. The first two components you see here are related to a service, which is called Vault. This service helps you centrally manage the encryption keys that protect your data and the secret credentials like passwords that you use to access resources.

Now we also have a service called certificates, which lets you create and manage certificate authorities, also referred to as CAs and certificates themselves. So this layer all about is about the services that help meet the use cases for data protection.

Finally, we have this layer, which is called detection and remediation. It is also referred to as Cloud security posture management. The whole idea is to improve an organization's security posture. So the services here are continuously monitoring your environment.

And if they notice any kind of misconfiguration or user activities or operator activities, it can notify you. It can actually also automatically remediate the problem. So the first service listed there you see Cloud Guard is a service which does that. It does Cloud security posture management.

Then there's also a service called Security Zones. And think about this as the way it works is you designate your compartments as secure zones. And these comply with Oracle security policies. And you can define these policies like you cannot have public access, resources cannot have public access, encryption is required, et cetera.

And the resources you define in these Security Zones actually will comply with these security policies. So in a nutshell, this is a very high level overview of security services. But I hope that this gives you a good overview of how these security services are categorized based on the use cases. And how it is implemented in this defense in-depth mechanism where you have security built in at different layers of the stack.

So how does this all operate? As you can see in this graphic here, you have an environment where you have some virtual networks. And you are using various security services, whether it's vulnerability scanning, whether it's auditing, whether it's bastion service or the Vault or the identity access management service.

So again, in the next subsequent lesson, we'll get into many of these services in detail. But just keep in mind we have a very broad and extensive set of security services. So just to recap in the Cloud when you move to the Cloud, basically you get this shared security model, and you are responsible for some of the security aspects and the Cloud provider takes care of the other aspects.

And then security is not just one service or an add-on. There's a whole extensive set of services available in different layers of the stack. We went through-- went over some of those. Next lessons, we will look into some of these in greater details. I hope you found this lesson useful. Thanks for watching. 
![image](https://github.com/qriz1452/oci/assets/112246222/2ebeca7e-107c-4913-96b8-40017a416ec0)
![image](https://github.com/qriz1452/oci/assets/112246222/6bac6f10-2a8a-4908-98e1-e701182e672f)
![image](https://github.com/qriz1452/oci/assets/112246222/ff198f05-cffb-42dc-9e74-56778c7ae1bb)


-------
 Now Playing : Cloud Guard 

Welcome back. In this lesson, we are going to look at Oracle Cloud Guard. Oracle Cloud Guard is a very unique feature available within Oracle Cloud Infrastructure.

What is Oracle Cloud Guard? Cloud Guard is a service that falls under the category of security-- Cloud Security posture management. It helps to monitor and identify potential security issues and then remediate them. What is really interesting about Cloud Guard is that it can completely automate the remediation.

As you can see here, the two key aspects-- you detect a problem. And there are a couple of ways you do that. You can check configurations, you can monitor activities, and then you can apply a response. And you can automate this response.

So how does this really work in practice? So the first thing you do is, you specify a target. And a target basically sets the scope of resources to be examined for OCI Compartments can be targeted, and their child compartment can be the target. So target is nothing but resources to be examined.

Then you have detectors. And these detectors are basically identified issues. Detectors are Cloud Guard components that identify issues with resources or user actions and alert when an issue is found. So, as you can see here, if there is a public instance where it should not be, it will flag that. If there's a public bucket, it would flag that, et cetera.

Then you have problems, and problems are potential security issues. So, in a way, talking about problems as being notifications that a configuration or activity is a potential security issue. And, then, finally, we have responders, which provide notification and corrective actions for security problems. So, as you can see here, if the instances public, you could stop that instance. If a bucket is public, you could disable that bucket or make it private and so on and so forth. You could decide what kind of responders you want.

Now, let us look at this in action. So the scenario here is a public bucket, and you don't want this bucket to be public. You want this to be a private bucket because that aligns with your security posture. So, first, what Cloud Guard does, suppose this bucket is living in a compartment, which is monitored by Cloud Guard.

Cloud Guard is running this configuration monitoring. So it's looking at your bucket, and it triggers a flag saying that this particular bucket is public. And it flags that as a critical issue, and a problem gets created. So think of our problem as sort of a ticket. So it gets created saying, bucket is public. And, at the same time, because it assigns a security score, it says it's a critical risk. So it notifies that-- that it's a critical risk.

And, then, there are responders, which look at that. And they say, is my responder enabled on for this kind of issue? And if the answer is yes, it can also have additional functionality-- so things like Cloud Event. It could go to Cloud Event, trigger that as an event, and then you could get notifications out of that.

You could also go to OCI functions, which is our serverless service, and it could do something else. It could slack you or something like that. So it could have some other feature built in. So the responder looks at that, and then it hands it over to a Cloud Guard operator. This is a policy which you write, which says, can I remediate the problem?

Do I have the permission to remediate the problem because one interesting thing about Cloud Guard is, you could automate all this. And if the answer is yes, then it responds. And it makes the bucket private. And that's how you go to that critical risk on, and the situation turns to green again.

So this is sort of an end-to-end workflow on how Cloud Guard works. A lot of this is transparent. You don't see it. And it's a great way to automatically detect issues and fix problems.

Just to recap, Cloud Guard is a service that falls into the category of Cloud Security Posture Management. It helps to monitor and identify potential security issues and then remediate them. You could also automatically remediate these problems. I hope you found this lesson useful. Thanks for watching. 
![image](https://github.com/qriz1452/oci/assets/112246222/406df034-0b9d-4d39-b97e-d947add3e70f)
![image](https://github.com/qriz1452/oci/assets/112246222/fc0d7015-fc30-4104-a423-8ae53866b87b)
![image](https://github.com/qriz1452/oci/assets/112246222/a7d2b506-30bb-45dc-a01d-08f2ef821c81)


----

 Now Playing : Security Zones and Security Advisor 

Welcome to this lesson on Security Zones and Security Advisor. Security Zone is to configure a location in which you cannot disable security. Security Advisor is a service that unifies Security Zone, Cloud Guard, and some other capabilities together in a cohesive whole. In this lesson, we will look into both of these services.

So first, let's look at Security Zones. What are the Security Zones? Well, we talked about that you have resources in your compartments. As you can see here, you have two compartments called compartment A and compartment B. You could designate compartment B as a Security Zone. What does that mean?

Well, that means that this particular compartment, once it's assigned sort of this Security Zone nomenclature has a set of Security Zone recipes. These are nothing but your policies which get enforced here. And any time there's a policy violation, that operation is denied.

So what does that look like? Which services are supported? Well, the core primitives today are supported, including networking, storage, compute, and databases. What does that actually mean? Well, if you specify that subnet always have to be private, if you create a public subnet, that operation will be denied. If the rules says that the customer manage master encryption keys have to be used instead of provider manage encryption keys. And if that is violated, the operation will be denied.

So the idea is you take a portion of your tenancy, think about your own home. You have the most secure items you have, whether it's your passport or documents or jewelry or something else, you could keep that in a secure vault. Make it fire safe, et cetera, so it's protected in case of any kind of a breach or a natural disaster.

So the same idea applies here. You take your tenancy, not everything in your tenancy is super secure but some elements in your tenancy, some portions of it are going to be super secure. You create a Security Zones. Sometimes, it's also referred to as Max Security Zones. And the resources which are kept there have a kind of policies applied to them, recipes applied to them. And those policies cannot be violated.

The simple way to think about for security zones. Security advisor is really a combination service that takes the functionality that's provided by Cloud Guard and Security Zone as well as some of the other security services and bring them together. So in a way, it's our own point of view on how security should be done. The services which are supported today are object storage, files storage, block volume, and virtual machines.

And again, some of the examples we talked about earlier, buckets cannot be public. And that can be enforced by Security Advisor. The Security Advisor will walk you through on how to create a bucket in a Security Zone. And it comes with its own set of requirements.

You have to use a customer manage key and so on and so forth. So Security Advisor would actually go through the steps required to do that. In a demo, we can take a look at how it works. And then you will understand it it a little bit better compared to just going through the slides. 
![image](https://github.com/qriz1452/oci/assets/112246222/d9e8da0e-4fad-4bb0-acd9-8f6eab348bf9)
![image](https://github.com/qriz1452/oci/assets/112246222/c51666c7-0d4f-4064-9c1a-ab43c039bf54)




--------
  Now Playing : Encryption Basics 

  
Welcome to this lesson on encryption basics. In this particular lesson, we are going to look at what encryption is, what different kinds of encryption algorithms exist, what does it mean to have symmetric encryption versus asymmetric encryption, et cetera. So let's start with the basics first.

Encryption is used to transform plain text data into cipher text. What does cipher text mean? Or cipher text is also referred to as encrypted text.

Basically what it means, it's a series of randomized letters and numbers which humans cannot make any sense of. Plain text, you can make sense. Once it's encrypted cipher text, you cannot make sense of that just by looking at it.

Decryption, which is the reverse process, is used to transform the cipher text into plain text. So plain text you take, and then you encrypt it into cipher text. That's the encryption. And the reverse process is decryption.

Now, you also hear this term called key. A key is a piece of information, usually a string of numbers or letters that are stored in a file, which when processed through a cryptographic algorithm-- and we'll look at what these algorithms look like-- can encrypt or decrypt data. So this is the central piece you need in order to encrypt or decrypt any kind of data.

Now, you also hear of this term called key or key pair. Encryption key or key pair is generated for a specific algorithm that can be used for encryption. Or you also hear this term called digital signing. So how does this work if you have to look at it visually?

Well, encryption-- you take the plain text data, and you use the key which is generated for a specific algorithm. So that's what you see here, the key with the specific algorithm here. And that converts into a cipher text, which is a series of randomized letters and numbers. Which, if a hacker gets access to or human gets access to, they cannot make sense of.

And the reverse process is called decryption. You take this series of randomized letters and numbers. You use the key again, which is tied to an algorithm. And then you can get the plain text back. So this is basically how encryption works, encryption or decryption.

Now, you also hear of this term called encryption at rest and encryption in transit. What this means is, data at rest is the data that is stored on a physical device, such as a server, as you can see here. It may be stored in a database or a storage account.

But regardless of where it is stored, encryption of data at rest ensures that the data is unreadable without the keys needed to decrypt it. So if an attacker obtained a hard drive with encrypted data and didn't have access to the encryption keys, they would be unable to read that data. So that's basically what it means by encryption at rest.

Encryption in transit is basically data moving from one location to another, such as across the internet or through a private network. So how this thing works is, you can see the data is moving here. So from the client it goes, let's say, to the server. And you can do in-transit encryption so that the data is secure.

So HTTPS is an example of encryption in transit. Encrypting data in transit basically protects it from outside attackers and provides a mechanism to transmit data while limiting the risk of exposure. So know the difference between encryption for data at rest and encryption for data in transit.

Now let's look at a couple of types of encryption. One called symmetric, one called asymmetric. Now, symmetric-key cryptography is where a single key is used for encryption and decryption.

So if you look, there are two actors here, John and Mike. And John has a message that's as simple as "Hello Mike." And he wants to encrypt it. He makes use of this secret key.

And you can see this series of randomized numbers and letters. This is the cipher text. He encrypts this message, and then he sends it over to Mike. Now, Mike also has access to the secret key. And he takes that, and he uses that to decrypt this message and gets the original plain text message, which is "Hello Mike."

Now, as you can guess, one of the issues with this kind of encryption is everyone has access to the same key. And there are ways to solve around that. This is just a basic kind of encryption, basic lessons, so we're not getting into that. But as you can see, the idea is, both John and Mike, two parties here, they share the same key both for encryption and decryption.

Now, contrary to this, there's another algorithm, which is called asymmetric encryption. Now, asymmetric encryption is where different keys are used for encryption and decryption. So as you can see here, there are two parties again, John and Mike.

And let's say Mike has generated a key pair which has a public key component and a private key component, as shown here on the slide. So each pair consist of a public key, which may be known to others, and a private key, which may not be known to anyone except the owner. So you can see that Mike only has the private key here.

So what happens in asymmetric encryption is, anyone can encrypt messages using a public key. So you see John here. Because public key is public, so he takes this and encrypts the message.

But only the holder of the paired-- this pair here-- private key can decrypt a message. Because only Mike has this key pair here, so he can decrypt the message. If an attacker gets hold of this public key and even this message, because different keys are used for encryption and decryption, they cannot make sense of this cipher text.

So the security of this system depends on the secrecy of the private key, which must not become known to any other party here. So it should only be with Mike because he generated the public and private keys in the first place. So this is what asymmetric encryption is.

Now let's look at some of the-- we looked at encryption, what it is-- transforms plain text into cipher text. Decryption is kind of reverse of that. And key pair is generated or key generated for a specific algorithm to be used for encryption or digital signing.

Now, you also hear these algorithms called AES, Advanced Encryption Standard, where the same key encrypts and decrypts data. Now, AES is pretty advanced, and it's very robust. But the issue around here, as you can imagine, is using the same key for both encryption and decryption.

RSA, on the other hand, is where a public key encrypts and private key decrypts the data. So it has that kind of built in. But there has been discussion on whether to use AES or RSA. Both have their own advantages.

One thing with AES is, it's a symmetric algorithm, absolutely. But it uses the same 128-, 192- or 256-bit key for both encryption and decryption. And so RSA, on the other hand, is computationally more intensive, and it's a bit slower. And there are cases where people use both together. And again, this is basic, so we're not getting into all these details.

ECDSA stands for Elliptic Curve Digital Signature Algorithm. It's one of the more complex public key cryptography encryption algorithms. Keys are generated by elliptic curve cryptography that is smaller than the average keys generated by digital signing algorithms.

So again, basics, we don't have to go into that. But as you can imagine-- we just talked about it-- it's used for digital signing. It's not used for encryption and decryption of data. So that was just a quick primer on encryption basics, looking at the different algorithms, and looking at symmetric versus asymmetric encryption.

Another term which you hear a lot or you would hear in the subsequent lesson is this thing called hardware security module. Think about Hardware Security Module or HSM as a physical computing device that safeguards and manages keys. It performs encryption and decryption functions, also does things like strong authentication and other cryptographic functions.

Now, there are certain characteristics of these HSMs. They are tamper-evident. As we discussed, they are used to manage these digital keys and also perform cryptographic functions.

Now, because the critical role they play in securing applications and infrastructure, HSMs are typically certified to internationally recognized standards, such as Common Criteria or FIPS 140, to provide users with independent assurance that the design and implementation of the product and cryptographic algorithms are sound. So in case of OCI, Oracle Cloud Infrastructure, we have a service called Vault. It uses HSM behind the scenes. And the HSMs it uses meet the FIPS 140-2 Security Level 3 certification. I believe the highest level goes to 4, so 3 is actually pretty high standard.

And it has certain characteristics. Obviously, it's tamper-resistant. It requires identity-based authentication. And if somebody tries to tamper with the device if they get hold of the device, the HSM deletes the key when it detects tampering. So it manages that sort of the superior level of security and independent assurance that it meets certain criteria set in regulatory compliance standards. 

![image](https://github.com/qriz1452/oci/assets/112246222/d855fdeb-1a99-43cf-bdb4-0b43ed02ae52)
![image](https://github.com/qriz1452/oci/assets/112246222/9e648c07-e391-4172-a90c-ae1deece9896)

![image](https://github.com/qriz1452/oci/assets/112246222/60957d98-36d8-4449-a460-90f3752b4be6)
![image](https://github.com/qriz1452/oci/assets/112246222/7b01755e-5566-4a43-a3c3-bc98e2e570c8)
![image](https://github.com/qriz1452/oci/assets/112246222/19702a47-34b6-478c-b7fb-bf303d1c0374)
![image](https://github.com/qriz1452/oci/assets/112246222/40c3b5d6-6114-46c0-ab73-18ced778e3f9)


----------
 Now Playing : Vault 

 
In this lesson, let's look at what is OCI Vault Service. So OCI Vault is a managed service that lets you centrally manage encryption keys and secret credential. Vault removes the need to store encryption keys and secrets in configuration files or in code. So what are these things called keys and secrets?

A key specifies how to transform plaintext into ciphertext during encryption and how to transform ciphertext into plain text during decryption. Secrets are credentials such as passwords, certificates, SSH-keys, or authentication tokens that you can use with Oracle Cloud Infrastructure services. So this particular service lets you centrally manage these encryption keys and credential.

The idea is you don't have to store that in configuration files that are in code, because that can potentially lead to security breaches. So that's the central management aspect of keys and secret credentials. Now, there are two kinds of protection modes for keys. One is called software. One is called hardware security modules. We have hardware security modules in OCI that meets fips 140-2 security level III certification. That's a mouthful.

That's kind of a federal standard for some of these HSM modules. But what's the difference between software and these HSM? The master encryption key protected by an HSM is stored on a hardware security module device and cannot be exported from the HSM. It stays within the HSM.

All the cryptographic operations involving the key also happen on the HSM. Meanwhile, a master encryption key protected by software is stored on a server and therefore can be exported from the server to perform cryptographic operations on the client instead of on the server.

So when I say server here, basically it means your computer host or the storage host where the remote storage or the object storage gets stored. So that's the big difference between HSM and managing the keys in HSM versus managing the keys in software. Now, what all different kinds of algorithms Vault supports? Let's look into them really quickly. So the Vault Service supports AES, RSA, and ECDSA algorithms. What's the difference?

AES is a symmetric algorithm. The same key encrypts and decrypts data. RSA is asymmetric encryption, so the public key encrypts data and the private key decrypts data. ECDSA keys are used in digital signing but they cannot be used to encrypt or decrypt data. So there are various use cases and various both symmetric as well as asymmetric algorithms supported by this particular service.

The keys are integrated with other OCI services. In the next couple of slides, we will look into that. You can rotate your master keys and that way you don't have to do a complete set of encryption again. And one thing which is not listed on the slide here is the service is a regional service and it has a public API endpoint that you can use.

Now, let's look into some of the other basic concepts surrounding using the keys. So in essence, the way the Vault operates is called envelop encryption. Think about this as a two tiered hierarchy for keys. The actual encryption happens with these keys called data encryption keys. They are used to encrypt customer data. And master encryption keys actually encrypt the data keys.

So you can see on the picture here, there is the master key that is used to encrypt the data key. And so you see that out of the middle box where the data is encrypted by the master key, but the actual encryption for storage, let's say, it's block storage or object storage or file storage, is actually done using the data key.

So this two tiered encryption is called envelope encryption. And you can use IM policies to authorize access to master keys. So not everybody has access to those keys, and you could also do audit logs to monitor all key related activities. So you secure your key Vault using those things, like policies and log audit logs. So like I said, this is the envelope encryption.

What are the benefits? It's easier to manage, limits the blast radius, and the fact that you are using master keys, it doesn't generate a complete data re-encryption. Because you could just rotate the master key, you don't have to do the complete encryption here. But one thing to keep in mind is you have to be careful.

If the master key is deleted, then there is no way for anyone to recover the data. So that is why we soft delete the keys with a seven day gap. And you should take requisite backups. The thing to keep in mind is Vault cannot be deleted immediately. You can schedule the deletion by configuring a waiting period, like it stays on the slide, anywhere from 7 to 30 days.

The Vault and all the keys created inside the Vault are deleted at the end of this waiting period. And all the data that was protected by those keys is no longer accessible after the Vault is deleted. Keep in mind, once the Vault is deleted, it cannot be recovered. So that's why that 7 to 30 day period is there by design. Now, let us look at an example of how this works with an OCI service.

So here, you have a key Vault and there is a master key in here. You can write policies to manage who has access to these keys and you could also do audit logs to see who is using these keys. Now, let's look at encryption process and decryption process in the context of object storage.

So let's say you have an object in an object storage bucket. You upload some plaintext data there. First thing the service does and you want to encrypt it. The encryption is actually on by default. You could bring your own keys. If you don't do that, we actually do the encryption by default. So this showing how the process actually works.

So objects storage service calls the Vault service and it asks to generate a data key. And the Vault service returns a data key as well as it returns the data key encrypted with a master key. So that's why you see those two boxes there.

And then the object storage takes those keys, that data key and it does the encryption with the plain text data key. And then it throws away the data key. But in the bucket, it keeps the encrypted object in the bucket. And it also keeps the encrypted data key with it. Right. So you will see why it keeps the encrypted data key.

When at the time of making a request to decrypt this data, the encrypted data key data and encrypted data key are stored as you see that in the bucket. So object storage now makes a request to the Vault and it sends that encrypted data key as part of the request. Vault looks at the encrypted data key. It knows the master key because it is stored inside the Vault. So it strips out the other portion and sends the data key back remember.

This data key is the one which is used for encryption and decryption. Now, once you have the data, you could actually decrypt your plaintext data with this data key. So this is a bit more advanced for a foundational course. But hopefully, you get an idea of how the Vault works, how this envelop encryption, the two tiered encryption works, and why it is useful. Because it limits your blast radius and you don't have to do encryption again in case you rotate your keys. 


![image](https://github.com/qriz1452/oci/assets/112246222/6dade5eb-de16-4efb-ac79-977b2098c371)
![image](https://github.com/qriz1452/oci/assets/112246222/91cca814-a3ab-4e0d-9f8c-533f37a84f84)



------







 










