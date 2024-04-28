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

3. Custom container deployment.

 The easiest way to deploy example http app is use developer view in web console or cli command.

 Lets start with creaqt new proroject.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/b35d48f6-10e6-447e-92aa-f932abc919f1)

 ![image](https://github.com/kubi79/openshift4/assets/168208701/712bd03c-75fc-42cc-b349-091d03e9eec6)

 Now we will user http oficial image on docker.io.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/5991e3c5-5850-4237-a8c7-37e6c3a657a6)

 ![image](https://github.com/kubi79/openshift4/assets/168208701/46d0bc8f-f285-4892-bca5-7a7ddf1fcb77)

 ![image](https://github.com/kubi79/openshift4/assets/168208701/c15dbf4a-fd3b-4f96-8c32-9feed7b1cf0b)

 We can see that pod is in CrashLoopBackOff status. It is normal becasue the container needs root privilages and we need to make some changes.

 Lets create service account.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/1495edcc-2675-4992-87f4-e769bdc5c2f5)

 Now we need to set scc permission to out created serviceaccount.

 ![image](https://github.com/kubi79/openshift4/assets/168208701/0083a9a4-eda2-4b54-ae87-3a440a8d2af4)

 






 


 


 

 














 






