Environment variables in Kubernenets can be set by using the attribute `env` in the YAML definition file:

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
      env:
        - name: APP_COLOR
          value: PINK
```

Environment variables can also be set using files, for example for [[Config Map]] or [[Secrets]]:

```yaml
envFrom:
- configMapRef: 
	name: app-configs
```

```yaml
envFrom:
- secretRef: 
	name: app-secrets
```
