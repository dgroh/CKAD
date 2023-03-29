The main goal of node affinity is to ensure that [[POD]]s are deployed to particular [[Worker Node]]s.
Node affinity provides capability of limiting POD placement in particular nodes.

Example:

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
  affinity:
    nodeAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        nodeSelectorTerms:
        - matchExpressions:
          - key: size
            operator: In
            values:
            - Large
```

### Types of Node Affinity

* **requiredDuringSchedulingIgnoredDuringExecution**
* **preferredDuringSchedulingIgnoredDuringExecution**
