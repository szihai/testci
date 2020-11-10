# KubeVela github action demo

## The demo

This demo showcases the CI process using KubeVela. Assume you have provisioned a K8s cluster, with KubeVela installed. Now you have just merged some code. And that's the context when it begins.

The building and deploying instructions are all in the `vela.yaml` Appfile. In this demo, it builds an image and deploys the application to your K8s cluster just like a Docker Compose file. Of course you don't have to have building step. The idea is the Appfile provides the same experience when you are deploying locally or in the github action.

## How to use the example

### Prerequisite

* Have a K8s cluster > 1.16 provisioned. 
* Have KubeVela installed on the cluster.

### Steps to use the example

* Fork this repo.   
* In your github repo, create three secrets: KUBECONFIG, DOCKERUSER, DOCKERPWD.
You need to use base64 encoded secret for KUBECONFIG:
`cat ~/.kube/config | base64 `   
* Change the docker repository in the `vela.yaml`, where it specifies the image to match the docker credential you provide.
* Merge your change, and it will trigger the github action.

## The workflow

The workflow is under `.github/workflows/main.yml`. It fairly straightforward: Download the vela binary, and run `vela up` command.   
There are two github actions used in the workflow. One is the common checkout. The other one is the vela github action, which simply downloads vela binary and runs your Appfile.


