Config Maps are objects where you can store values for a Kubernetes application in form of key-value pairs.

There are two ways to create a config map. either using the imperative way: `kubctl create configmap` or through a YAML definition:

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_COLOR: blue
  APP_MODE: prod
```

