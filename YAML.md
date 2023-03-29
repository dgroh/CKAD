YAML can be used in Kubernetes to define a configuration for Kubernenets.
All of them follow a similar strucrture:

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
    
```

They always container these top level fields. (`apiVersion`, `kind`, `metadata` and `spec`).

## ApiVersion

This is the version of the Kubernenets API to create an object. Depending on what we are creating you must use the right api version.
| Kind       | Version |
| ---------- | ------- |
| Pod        | v1      |
| Service    | v1      |
| ReplicaSet | apps/v1 |
| Deployment | apps/v1 |

## Kind

The kind refers to the type of object.

## Metadata

It's the data about the object, for example, its name, label, etc. 0

> It's a dictionary.

* **name** is a string type. 
* **labels** is also a dictionary and you can defined whatever keys you want

## Spec

The `spec` is the specification of the object we want to deploy. This is for every object different and therefore it's important to always refer to the documentation.

* **containers** is a list.