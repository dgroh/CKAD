Secrets are similar to [[ConfigMap]] except that they store sensitive data in a encoded format.

There are two ways to create a config map. either using the imperative way: `kubctl create secret generic` or through a YAML definition:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: app-secret
data:
  DB_Host: mysql
  DB_User: root
  DB_Password: Password
```

A secret can be encoded by using `echo -n 'MY_SECRET' | base64` and to decode simply use `echo -n 'MY_SECRET' | base64 --decode`

## Injecting Secrets in [[POD]]s

There are 3 ways of injecting secrets in PODs. 

### 1. Environment variables configuration with `envFrom`

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
    - envFrom:
      - secretRef:
          name: app-secret
    - name: nginx-container
      image: nginx
```

### 2. Single environment variables configuration with `env`

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
    - env:
	  - name: DB_Password
	    valueFrom: 
	      secretKeyRef:
            name: app-secret
            key: app-secret
    - name: nginx-container
      image: nginx
```

### 3. Via `volumes`

```
apiVersion: v1
kind: Pod
metadata:
  name: myapp-pod
  labels:
    app: myapp
    type: front-end
spec:
  containers:
    - volumes:
      - name: app-secret-volume
        secret:
          secretName: app-secret
    - name: nginx-container
      image: nginx
```


## Notes

> Secrets are not Encrypted. Only encoded.

> Do not push secret objects to SCM along with code

> Secrets are not encrypted in ETCD
> 	Consider ecrypting data at rest (EncryptionConfiguration)

> Anyone able to create pods/deployments in the same namespace can access the secrets
> 	Configure least-priviled access to Secrets - RBAC

> Consider third-party secrets store providders like AWS, Azure, GCP and Vault (Handled in Certified Kubernetes Security Specialist course)

