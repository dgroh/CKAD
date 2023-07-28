The service creates a virtual IP inside the cluster to enable communication between different services such as a set of frontend servers and backend servers.

> ClusterIP is the default type of service

Also ClusterIP ist used for internal communication.

## Defining a ClusterIP service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: backend-service
spec:
  type: ClusterIP
  ports:
    - targetPort: 80
      port: 80
  selector:
    app: myapp-service
    type: back-end
```
