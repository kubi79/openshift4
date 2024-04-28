# openshift4
Deploy the openshift cluster.

In below example I have installed Openshift Single Node (SNO) because it don't have resources to install full node cluster in private resources. I was using Openshift Assisted Installer method.
That method is the fastest way to get full functional one node cluster and doesn't need high resources.

Minimum resource requirements:
- 8 vCPU cores
- 16 GB of RAM
- 120 GB of storage

Other requirements:
- internet access
- api/api-int/apps dns in domain ocp4.openshift.local
  in my example I run dnsmasq service in small linux vm:
  
 ![image](https://github.com/kubi79/openshift4/assets/168208701/666a9212-5980-47dc-b8c0-f0d2ce277577)

 Install Openshift SNO steps:
 We enter the console.redhat.com to start the wizzard:

 ![Screenshot 2024-04-26 170221](https://github.com/kubi79/openshift4/assets/168208701/4d176c2d-8439-47d6-89e1-0d44fd315826)

 ![Screenshot 2024-04-26 170314](https://github.com/kubi79/openshift4/assets/168208701/1d519f4a-a5fd-404f-ada4-f4c16f72037f)



 






