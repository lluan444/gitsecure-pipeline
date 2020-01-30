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

4. Add a `Delivery Pipeline Private Worker` to your toolchain. You can follow the `Getting Started` link from the dashboard to deploy private worker on your IKS cluster.

![Alt text](./media/worker-agent.png?raw=true "Deploy Worker Agent")

5. Add your repository that you want to scan with GitSecure to the toolchain. 
`NOTE: First time users, will be asked to permit IBM Cloud to access your Git Account`

6. Add this `gitsecure-pipeline` repository to your toolchain. This repository contains the Tekton Pipeline Definitions to run all GitSecure Analytics tasks.

7. Add `Deliver Pipeline` tool to your toolchain and select `Tekton` as `Pipeline Type`.

8. Then Click on `Configure Pipeline` to configure tekton, worker agent, trigger events and properties.
```
NOTE: Currently, we support only Git Events as Trigger
```
![Alt text](./media/Gitsecure-Definitions.png?raw=true "Definition Tab")
![Alt text](./media/Gitsecure-Trigger.png?raw=true "Trigger Tab")

9. Under Environment Properties you need to specify a property named `apikey` and this is an IBM Cloud API key you need to provide. This key is used to retrieve the Git Token for your git repo by GitSecure tasks to perform actions like `Open an Issue`, `Comment on PR`, `Create Auto-remediation PR`.
![Alt text](./media/Gitsecure-Properties.png?raw=true "Properties Tab")

10. Once pipeline is configured properly, you can go ahead and create a PR on your repository and monitor a GitSecure Pipeline getting triggered on the Toolchain.

