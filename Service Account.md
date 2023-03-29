There are two type of accounts in Kubernetes, the **User** account and the **Service** account.

**User** accounts are used by humans and **Service** accounts are used by machines.

Example of User accounts: Admin, Developer
Example of Service accounts: Prometheus, Jenkins

> To create a service account refers to [[kubectl#How to create a service account]] .

When creating a service account, a authentication token is created which can be used to access the Kubernetes API. It the automatically creates a [[Secrets]] object and stores this token in there. The secret object is then linked to the service account. (v1.22)

> Since v1.24 creating a service account no longer greates a token. In order to create a token you need to run `kubectl create token [SERVICE_ACCOUNT_NAME]`

> For every namespace created in Kubernetes there is a `default` service account.

Whenever a [[POD]] is created, there default service account and its token are automatically mounted to that POD volume mount.

## Link a service account to a POD

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
    - name: my-kubernenets-dashboard
      image: my-kubernenets-dashboard
  serviceAccountName: dashboard-sa
```

> It's not possible to change a POD service account after it is created. You have to delete it and create it again.

