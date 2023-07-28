Deployment in Kubenetes is a higher hierarchie which manages ReplicaSets  and provides declarative updates to [[POD]]s along with a lot of other useful features.

A deployment is also a type of object in Kubernetes and has its own kind named Deployment. It's identical to the ReplicaSet configuration, except for its kind.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp-replicaset
  labels:
    app: myapp
    type: front-end
spec:
  template:
	metadata:
	  name: myapp-pod
	  labels:
		app: myapp
		type: front-end
	spec:
	  containers:
		- name: nginx-container
		  image: nginx
  replicas: 3
  selector: 
    matchLabels:
      type: front-end
```

The main difference between ReplicaSet and Deployment

>   A ReplicaSet ensures that a number of Pods is created in a cluster. The pods are called replicas and are the mechanism of availability in Kubernetes. But changing the ReplicaSet will not take effect on existing Pods, so it is not possible to easily change, for example, the image version. 
>   
>   A deployment is a higher abstraction that manages one or more ReplicaSets to provide a controlled rollout of a new version. When the image version is changed in the Deployment, a new ReplicaSet for this version will be created with initially zero replicas. Then it will be scaled to one replica, after that is running, the old ReplicaSet will be scaled down. (The number of newly created pods, the step size so to speak, can be tuned.)
>   
>   As long as you don't have a rollout in progress, a deployment will result in a single replicaset with the replication factor managed by the deployment.
>   
>   Always use a Deployment and not a bare ReplicaSet.

### Rollback

It is possible to rollback a Deployment to an earlier revision by running the following command:

```bash
kubectl rollout undo deployment/my-deployment-name
```

#### Useful deployment commands

```
kubectl create -f deployment-definition.yaml
kubectl get deployments
kubectl apply -f deployment-definition.yaml
kubectl set image deployment/myapp-deployment nginx=nginx:1.9.1
kubectl rollout status deployment/my-deployment-name
kubectl rollout history deployment/my-deployment-name
kubectl rollout undo deployment/my-deployment-name
```