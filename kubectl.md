This is known as `kube command` or `kubectl` or `kube control` or `kube cuttle`.
This tool is used to deploy and manage applications on the kubernetes cluster.

The `kubectl run` is used to deploy an application on the cluster
The `kubectl cluster-info` is used to view information about the cluster
The `kubectl get nodes` is used to list all the nodes that are part of the cluster

## How to deploy [[POD]]

`kubectl run`  deploys a docker container creating a [[POD]]. 

For example: `kubectl run nginx --image nginx`.

## How to see deployed [[POD]]s

To see deployed PODs use the `kubectl get pods` command.

## How to see detailed information about the [[POD]]

To see detailed information about the POD, use `kubectl describe pod [POD_NAME]`

## Create a [[POD]] with [[YAML]] definition

`kubectl create -f [POD_DEFINITION.yml]`


