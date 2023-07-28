Kubernetes per default wants your application to live forever. 
If you want to change this behaviour, you can change the value of the attribute `restartPolicy` on the Pod.

Example:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: math-add
spec:
  containers:
    - name: math-add
      image: ubuntu
	  command: ['expr', '3','+','2']
  restartPolicy: Never