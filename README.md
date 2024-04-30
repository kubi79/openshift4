# openshift4
1. Deploy the openshift cluster.

In below example I have installed Openshift Single Node (SNO) because it don't have resources to install full node cluster on private resources. I was using Openshift Assisted Installer method.
That method is the fastest way to get full functional one node cluster and doesn't need high resources.

Minimum resource requirements:
- 8 vCPU cores
- 16 GB of RAM
- 120 GB of storage

Other requirements:
- internet access
- dhcpd server
- api/api-int/apps dns in domain ocp4.openshift.local
  in my example I run dnsmasq service in small linux vm inside network 192.168.3.0/24
  
 ![image](https://github.com/kubi79/openshift4/assets/168208701/666a9212-5980-47dc-b8c0-f0d2ce277577)

 Install Openshift SNO steps:
 
 We enter the console.redhat.com to start the wizzard:

 ![Screenshot 2024-04-26 170221](https://github.com/kubi79/openshift4/assets/168208701/4d176c2d-8439-47d6-89e1-0d44fd315826)

 ![Screenshot 2024-04-26 170314](https://github.com/kubi79/openshift4/assets/168208701/1d519f4a-a5fd-404f-ada4-f4c16f72037f)

 ![Screenshot 2024-04-26 170416](https://github.com/kubi79/openshift4/assets/168208701/bd498817-2d9e-4667-93dc-838110274b07)

 ![Screenshot 2024-04-26 170517](https://github.com/kubi79/openshift4/assets/168208701/6ba353ff-49ca-4cf4-9f18-abb7e91a087a)

 ![Screenshot 2024-04-26 170536](https://github.com/kubi79/openshift4/assets/168208701/9d1a1744-5ed3-4036-bbf6-4aab6634cb39)

 ![Screenshot 2024-04-26 170558](https://github.com/kubi79/openshift4/assets/168208701/a1b6145d-75ca-41b1-aea1-920cfec22d4a)

 ![Screenshot 2024-04-26 170644](https://github.com/kubi79/openshift4/assets/168208701/9eefaaa5-33f3-472b-abf7-54cd9c960f49)

 ![Screenshot 2024-04-26 173510](https://github.com/kubi79/openshift4/assets/168208701/e3a5daf9-a756-4303-8741-534279b7567f)

 ![Screenshot 2024-04-26 173538](https://github.com/kubi79/openshift4/assets/168208701/9453d2a3-decc-49b2-97bd-8e57308463fc)

 ![Screenshot 2024-04-26 173604](https://github.com/kubi79/openshift4/assets/168208701/d11a2755-6479-47b7-b8b9-7eb0938314e9)

 ![Screenshot 2024-04-26 173622](https://github.com/kubi79/openshift4/assets/168208701/2e9bee43-1322-4f01-8f4c-fb6108957399)

 ![Screenshot 2024-04-26 175930](https://github.com/kubi79/openshift4/assets/168208701/f9eeb1de-9444-499c-b363-5be5738b36ab)

 ![Screenshot 2024-04-26 181752](https://github.com/kubi79/openshift4/assets/168208701/4cdcbd32-4dbd-4e54-b64a-ad9339a2c96e)

 ![image](https://github.com/kubi79/openshift4/assets/168208701/44e6407c-2823-4bd4-bb25-d0cde0a81361)

 Our Openshift Single Node Cluster has been installed.

2. Application Deployment and Management
As a first step I forked application https://github.com/nordcloud/openshift-assignment/ to my git on https://github.com/kubi79/openshift-assignment
to make some changes in structure. I added manifests folder wit definitions for deployment service and route.

![image](https://github.com/kubi79/openshift4/assets/168208701/5e4eed1f-7768-40f3-8fbe-24e1463600b8)

![image](https://github.com/kubi79/openshift4/assets/168208701/5257aabc-06ad-43c3-9ce1-5ce06bc2afd1)

![image](https://github.com/kubi79/openshift4/assets/168208701/09bbfeb2-9932-4782-a087-a50648416ecc)

![image](https://github.com/kubi79/openshift4/assets/168208701/25576dce-5c63-44df-812d-4f168d6d145b)

Becasue I have no registry configured in SNO Openshift I decided to create image from your docker file and push it to docker.io registry.

![image](https://github.com/kubi79/openshift4/assets/168208701/e1b84bf1-d54d-4b00-991f-a1b94282b4fa)

After created image I needed to tag it and push to the docker.io

![image](https://github.com/kubi79/openshift4/assets/168208701/fb1197d2-4dd4-416d-be11-9da330c858e7)

I have deployed Red Hat OpenShift GitOps Operator - fastest way. It works out of the box. I needed only add some cluster permisions to argocd service accounts.

![image](https://github.com/kubi79/openshift4/assets/168208701/c3ed32cf-3b31-4d5f-8290-5f5be591e341)

For deployments production and testing purposes I have added second branch to git. Main branch will be used for production purposes and branch testing
for second deployment means testing. I also need to change route url in branch testing for ohb-tessting.apps.ocp4.openshift.local to avoid have the same route name after deployment.

![image](https://github.com/kubi79/openshift4/assets/168208701/3e7ca05d-047c-46d4-8570-79b181802d8e)

![image](https://github.com/kubi79/openshift4/assets/168208701/3ab2c2be-10c7-4037-a9fe-9eb36df7afcf)

Lets create first deployment for prod from branch main.

![image](https://github.com/kubi79/openshift4/assets/168208701/06f231a1-23ea-466e-84b3-2bc5573e86ad)

![image](https://github.com/kubi79/openshift4/assets/168208701/d09aa530-4c85-4666-b3d5-09ffb668cb9b)

![image](https://github.com/kubi79/openshift4/assets/168208701/30fe8c62-31fc-466f-96e8-d15193ddfb37)

After sync we can see:

![image](https://github.com/kubi79/openshift4/assets/168208701/4f3c39ea-a830-41cb-ac74-a6fc0f72d91d)

Lets create second deployment for testing purposes from branch testing.

![image](https://github.com/kubi79/openshift4/assets/168208701/316aaa88-67b1-4e5c-8528-68844375ffe9)

After sync we see:

![image](https://github.com/kubi79/openshift4/assets/168208701/a9e11807-558f-4af2-952b-2305d43cbb8c)

Both deployment are deployed and apps are working.

![image](https://github.com/kubi79/openshift4/assets/168208701/fe41afa1-4781-454a-aaef-4c44424b5ce7)


3. Custom container deployment.

 The easiest way to deploy example http app is use developer view in web console or cli command.

 Lets create new proroject.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/b35d48f6-10e6-447e-92aa-f932abc919f1)

 ![image](https://github.com/kubi79/openshift4/assets/168208701/712bd03c-75fc-42cc-b349-091d03e9eec6)

 Now we will user http oficial image on docker.io.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/5991e3c5-5850-4237-a8c7-37e6c3a657a6)

 ![image](https://github.com/kubi79/openshift4/assets/168208701/46d0bc8f-f285-4892-bca5-7a7ddf1fcb77)

 ![image](https://github.com/kubi79/openshift4/assets/168208701/c15dbf4a-fd3b-4f96-8c32-9feed7b1cf0b)

 We can see that pod is in CrashLoopBackOff status. It is normal becasue the container needs root privilages and we need to make some changes.

 Lets create serviceaccount.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/1495edcc-2675-4992-87f4-e769bdc5c2f5)

 Now we need to add scc permission to our created serviceaccount.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/0083a9a4-eda2-4b54-ae87-3a440a8d2af4)

 The next step will be add settings for serviceaccount to our http deployment.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/c9246647-ed82-49da-b263-39c2095959fd)

 After that the pod will be restarted and start properly.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/6b9ffc62-89c1-427f-9fbc-b5dda80906ea)

 ![image](https://github.com/kubi79/openshift4/assets/168208701/f531fe82-1464-440c-9740-76942be96fcd)

 When we open default route deployed with deployment we will see that http service is up and running.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/51a3947c-fe3c-4367-9b19-5c6502c882d1)

 The next step would be change index.html page inside the container. The easiest and afastest way will be create configmap.

 Lets create our new index.html default file on our SNO node.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/00087ebc-cf27-4a2a-9d81-e6cf4139ced5)

 And configmap from index.html file.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/67ef78e2-42f7-4f82-92b3-724738b32b9a)

 Now we need to set our config map as volume in our deployment/http and mount as specific folder where original index.html is placed inside http container.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/3c0c909c-07f4-44c9-92c9-d11de39334a5)

 Now our configmap is changing index.html file during the deployment.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/365afa1c-a9de-4ebe-8a2c-070ecb27bcc6)

 The http deployment proces has finished.

 4. Advanced Deployment Strategies

The primary steps to have blue-green deployment strategy is have two separate deployments. First old version of the application
and second the new version of the application.
For prepare some showcase we use http application deployed in point3.

![image](https://github.com/kubi79/openshift4/assets/168208701/3faeec4a-1fb1-4827-92ce-d80fb5d9f83d)

Lets create second http deployment named http2.

![image](https://github.com/kubi79/openshift4/assets/168208701/4e7ffbdf-8f63-4432-815c-db6b2e2dc1af)

And fix root permission issue:

![image](https://github.com/kubi79/openshift4/assets/168208701/0ab9df5d-125a-4687-a6f6-480aa04f0fe7)

Now we have two different deployment with two routes lets remove route for http2:

![image](https://github.com/kubi79/openshift4/assets/168208701/9aafb4bf-8471-401e-834b-3fcddc1cb2f1)

Existing route is pointing to old app:

![image](https://github.com/kubi79/openshift4/assets/168208701/08c67288-760e-419e-a1ca-86f1e7cf1731)

Lets modify orginal route to point to our new application.

![image](https://github.com/kubi79/openshift4/assets/168208701/d0607b76-dcd7-4435-b982-a8c6179f07f5)

We can modify route between two deployments:

![image](https://github.com/kubi79/openshift4/assets/168208701/02caf4ae-1c5c-4f18-b5cd-40a5dccb6474)

I that case one deployment second is exposed to access and first deployment is not.

![image](https://github.com/kubi79/openshift4/assets/168208701/0a189690-1918-438c-a88e-51bf5ca5ffcb)













 


 



 




 



 






 


 


 

 














 






