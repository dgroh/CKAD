The service listens to a port on a [[Node (Worker Node)]] and forward requests to the [[POD]]s.

Here we have 3 ports involved:

1. The port on the pod where a web server for example runs is 80 (known as Target Port, because that is the port the the service forward the requests to)
2. The port on the service (80)
3. The port on the node (30008) which we will use to access the web server externally and that is known as the NodePort
	> node the port on the node (30008) which is part of the node allowed port range which can be from 3000 to 32767
	
## NodePort Defnition

This is an example of a definition of a service of type node port.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  type: NodePort
  ports:
  - name: 80-30008
    targetPort: 80
    port: 80
    nodePort: 30008
  selector:
    app: myapp
    type: front-end
```
