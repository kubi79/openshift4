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
  in my example I run dnsmasq service in small linux vm
  ![image](https://github.com/kubi79/openshift4/assets/168208701/e6e7e202-4235-4ed8-8205-08c8dd325944)





