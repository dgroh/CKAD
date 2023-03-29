Controllers are the brain behind Kubernetes. They are the processes that monitor Kubernetes objects and respond accordingly. 

## Replication Controller

The replication controller helps us run multiple instances as of a single [[POD]] in the Kubernetes cluster providing high availability.

A replication controller is also important in order to load balance [[POD]]s also between multiple nodes.

Replication Controller and [[Replica Set]] have purpose, but they are not the same.

Replication Controller is the older technology that is being replaced by [[Replica Set]] which is the new recommended way to setup replication.

### Defining a Replication Controller

```yaml
apiVersion: v1
kind: ReplicationController
metadata:
  name: myapp-rc
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
```

### Defining a Replica Set

```yaml
apiVersion: apps/v1
kind: ReplicaSet
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

> **Note:** `selector` is the major difference between Replica Set and Replication Controller.