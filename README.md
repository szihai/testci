# KubeVela github action demo

## Use case

Assume you have provisioned a K8s cluster, with KubeVela installed. Now you have just merged some code, it will trigger the workflow.

The github action will use your Appfile to build and deploy your application to the K8s cluster.

## Prerequisite

* Have a K8s cluster > 1.16 provisioned. 
* Have KubeVela installed on the cluster.



## Steps to use the example

Fork this repo.   
In your github repo, create three secrets: KUBECONFIG, DOCKERUSER, DOCKERPWD.
Here is an example of how to create the base64 encoded secret:
`cat ~/.kube/config | base64 `   
All three of them have to be encoded.
Change the docker repository in the `vela.yaml`, where it specifies the image to match the docker credential you provide.

merge your change, and it will trigger the github action.

## The workflow

The workflow is under `.github/workflows/main.yml`. It fairly straightforward: Download the vela binary, and run `vela up` command.

The building and deploying instructions are all in the `vela.yaml` Appfile. In this demo, it builds an image and deploys the application to your K8s cluster. 
