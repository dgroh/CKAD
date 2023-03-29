This is known as `kube command` or `kubectl` or `kube control` or `kube cuttle`.
This tool is used to deploy and manage applications on the kubernetes cluster.

The `kubectl run` is used to deploy an application on the cluster
The `kubectl cluster-info` is used to view information about the cluster
The `kubectl get nodes` is used to list all the nodes that are part of the cluster

### How to deploy [[POD]]

`kubectl run`  deploys a docker container creating a [[POD]]. 

For example: `kubectl run nginx --image nginx`.

### How to see deployed [[POD]]s

To see deployed PODs use the `kubectl get pods` command.

### How to see detailed information about the [[POD]]

To see detailed information about the POD, use `kubectl describe pod [POD_NAME]`

### Create a [[POD]] with [[YAML]] definition

`kubectl create -f [POD_DEFINITION.yml]`

### How to see [[POD]] detail

You can use `kubectl describe pod [POD_NAME]` or to see only the image you can use `kubectl get all -o wide` 

### How to see the number of containers in a [[POD]]

The command `kubectl get pods` shows in the **READY** column the number of container in a POD. For example: 
* 1/1 means one running container from a total of one container in the POD. 
* 1/2 means one running containers from a total of two containers in the POD. 

### How to create a base [[POD]] [[YAML]] out of an existing image

You can run `kubectl run [POD_NAME] --image=[IMAGE_NAME] --dry-run=client -o [NAME].yaml` or `kubectl get pod <pod-name> -o yaml > pod-definition.yaml`

This will generate a base Kubernetes YAML template.

### How to reapply a change in the [[POD]] after creation

Use the command `kubectl apply -f [NAME].yaml`

### How to edit an existing [[POD]]

If not via YAML definition, use the command `kubectl edit pod [POD_NAME]`

### How to verify the number of [[Controller#Replication Controller]]

Run `kubectl get replicationcontroller`

### How to verify the number of [[Controller#Defining a Replica Set]]

Run `kubectl get replicaset`

### How to scale [[POD]]s using ReplicaSet

1. `kubectl replace -f replicaset-definition.yaml`
2. `kubectl scale --replicas=6 -f replicaset-definition.yaml`
3. `kubectl scale --replicas=6 replicaset myapp-replicaset`
4. `kubectl edit replicaset/[REPLICA_SET_NAME]`

### How to find out about an API version?

Use the `explain` command. Basically if you also want to know more about some Kubernetes API, you can run `kubectl explain` command to know more about this api, for example like kind and version. 

Example:

`kubectl explain replicaset`

### How to list deployment?

Run `kubectl get deployments`

### How to list [[POD]]s in a namespace?

Run `kubectl get pods --namespace=kube-system`

### How to create [[POD]] in another namespace?

Run `kubectl create -f pod-definition.yml --namespace=dev`

Or use the attribute `namespace` in the `metadata` section of the POD definition.

### How to create a namespace?

Run either `kubectl create -f [NAMESPACE_DEFINITION].yaml` or `kubectl create namespace [NAMESPACE_NAME]`.

### How to list [[POD]]s of all namespaces?

Run `kubectl get pods --all-namespaces` or `kubectl get pods -A`

### How to automatically create a service with exposed port?

Run `kubectl run [POD_NAME] --image [IMAGE_NAME] --port 80 --expose true`

### How to replace an existing POD with new template?

Run `kubectl replace --force -f [DEFINITION].yaml`

>  Replace is a bad practice. Make a backup first of the resource you want to recreate. Replace might happen, that you YAML is currupted for N reasons and then you can't no longer uise the original resource as replace deletes the resource.

### How to check which user is running on a POD

`kubectl exec ubuntu-sleeper -- whoami`

### How to create a [[Service Account]]?

`kubectl create serviceaccount dashboard-sa`

### How to list a service account secrets from a [[POD]]?

`kubectl exec -it my-kubernetes-dashboard -- ls /var/run/secrets/kubernenets.io/serviceaccount`

### How to verify logs form a namespace

`kubectl logs [POD_NAME] -n [NAMESPACE]`

or

`kubectl exec -it [POD_NAME] -n [NAMESPACE] -- cat [LOG_PATH]`
