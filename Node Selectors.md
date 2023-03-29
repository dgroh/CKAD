Node selectors are a way to determine which [[POD]] can be deployed to which [[Worker Node]], for example, assuming the following POD configuration:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
    type: front-end
spec:
  containers:
  - name: nginx-container
    image: nginx
  nodeSelector:
    size: Large
```

Prior to creating a POD with such a definition it's important to have a node labeled with `size: Large`.

To label a node you can run:

`kubectl label nodes [NODE_NAME] [KEY]=[VALUE]`

For example:

`kubectl label nodes node01 size=Large`

> Node selectors are not flexible enough to accept more than  one criteria, for example, if we want a POD to be deployed to eiter a Medium or Large. To solve this, we can use [[Node Affinity]]