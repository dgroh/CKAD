To define security context for instance **in a [[POD]]**, add a field called `securityContext` to the [[YAML]] definition under the `spec` section.

For example:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
    type: front-end
spec:
  securityContext:
    runAsUser: 1000
  containers:
    - name: nginx-container
      image: nginx
      command: ["sleep", "3600"]
```

To define security context on container level move the field  `securityContext` to the [[YAML]] definition under the `container` section.

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
      command: ["sleep", "3600"]
      securityContext:
	    runAsUser: 1000
```

To add capabilities, use the field `capabilities` under the container level:

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
      command: ["sleep", "3600"]
      securityContext:
	    runAsUser: 1000
	    capabilities:
	      add: ["MAC_ADMIN"]
```

> Capabilities are only supported at the container level and not at the POD level.
