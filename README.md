# GitSecure : IBM DevSecOps Toolchain

We are running GitSecure as a Tekton pipeline on IBM DevOps Toolchain. So, GitSecure has following pre-requisites for provisioning DevOps service on IBM Cloud.

### Provisioning DevOps Toolchain on IBM Cloud
References:
<a href ="https://www.ibm.com/cloud/blog/announcements/build-and-deliver-using-tekton-enabled-pipelines">Introduction to IBM DevOps Toolchain</a>
<a href="https://cloud.ibm.com/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines&locale=se">Working with Tekton Pipelines </a>


Please follow these steps to enable IBM DevOps Toolchain using Tekton:

1. Provision a 1 Worker Node IKS cluster. 
```
This is where the private worker will get deployed and your pipeline  will actually run. There was a limitation of running private worker on multi-node IKS cluster.
```

2. Subscribe to Continuous Delivery Service

3. Create a toolchain and select `Build your own toolchain` option.

![Alt text](./media/create-toolchain.png?raw=true "Create Toolchain")
![Alt text](./media/toolchain-type.png?raw=true "Toolchain Type")

3. Create a DevOps toolchain and Select `tekton` as a `Pipeline Type`.

4. Add a `Delivery Pipeline Private Worker` to your toolchain. You can follow the `Getting Started` link from the dashboard to deploy 