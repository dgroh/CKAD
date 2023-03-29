Each **[[Worker Node]]** has a set of CPU, Memory and Disk resources available. When a **[[POD]]** is consumed by a node, it consumes resources available on that node. The [[Components#Scheduler]] considers also when assigning PODs to a node the available resources.

If node has no sufficient resources the scheduler avoids placing the POD on that node.

By default Kubernetes assumes that **a container within the POD requires 0.5 CPU and 256 Mi of memory** and this is known as a resource request for a container - the minimum amount of CPU or memory requested by the container. This can by achieved by creating a [[Limit Range]] resource in a specific namespace.

In Resources, **0.1** can be expressed as **100m**, where **m** stands for **milie**. You can go lower to **1m** but not lower than that.

1 CPU is equal to:
* 1 AWS vCPU
* 1 GCP Core
* 1 Azure Core
* 1 Hyperthread

Similar to memory, you can specify 256 **Mi**, where **Mi** stands for Mebibyte (1 Mi = 1.048.576 bytes).

Allowed values for memory:

* G (Gigabyte)    = 1.000.000.000 bytes
* M (Megabyte) = 1.000.000 bytes
* K (Kilobyte)     = 1.000 bytes

* Gi (Gibibyte)    = 1.073.741.824 bytes
* Mi (Mebibyte) = 1.048.576 bytes
* Ki (Kibibyte)     = 1.024 bytes

> In the docker world, the container will use as much resource as it can suffocating the process of the node it's runing on. Hower in Kubernetes you can set limit of resources on the PODs by adding **limits** section under **resources** section on the **container** section.

```yaml
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
      resources:
        requests:
          memory: "1Gi"
          cpu: 1
        limits:
          memory: "2Gi"
          cpu: 2
```

> **limits**  and **requests** are set for each container whithin the POD.
> 
> **In case of CPU** going beyond the limit, Kubernetes throtles the CPU so that it does not go beyond the specified limit. A container can not use more CPU resources than its limit.
> 
> However a container can use more **memory** resources than its limit. If a POD tries to consume more memory than its limit, the POD is terminated.