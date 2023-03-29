Taints are set on [[Worker Node]] and tolerations are set on [[POD]]s.

To taint a node you can use the command:

`kubectl taint nodes [NODE_NAME] [KEY]=[VALUE]:[TAINT_EFFECT]`

There are three types of taint effects:

* **NoSchedule**
	* The POD will no longer tolerate the taint
* PreferNoSchedule
	* PODs might or not tolerate the taint
* NoExecute
	* Only new PODs will not tolerate the taint, existing one remains as they were

Example:

`kubectl taint nodes node1 app=blue:NoSchedule`

## Example on POD

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
    - name: nginx-container
      image: nginx
  tolerations:
    - key: "app"
      operator: "Equal"
      value: "blue"
      effect: "NoSchedule"
```

> Tolerantions and Taints have no relationship with [[Node Affinity]]

> **IMPORTANT:** The [[Master Node]] is automatically tainted on Kubernetes setup, so that no PODs can be deployed there.

