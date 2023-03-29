In Kubernetes, namespaces provides a mechanism for isolating groups of resources within a single cluster. You can provide for each namespace certain rules and policies so that you can restrict for example its access, amount of space, etc.

Kubernetes already brings already 3 namespaces , those are:

### kube-system

Contains internal resources for necessary for Kubernetes to run like networkin solutioins, DNS services, etc.

### kube-node-lease

This namespace holds Lease objects associated with each node. Node leases allow the kubelet to send heartbeats so that the control plane can detect node failure.

### default

This is the default namespace which can be used for all user. Every object create per default will land here.

### kube-public

Here is where resources created for all users are available.

## Communication between namespace resources

It's possible to let resources from a specific namespace communicate with resources from another namespace by simply using the syntax: `[SERVICE_NAME].[NAMESPACE].[SERVICE].[DOMAIN]` where per default service is **svc** and domain is **cluster.local**, therefore: `[SERVICE_NAME].[NAMESPACE].svc.cluster.local`.

## Create a namespace

A namespace is also a Kubernenets object. That means, you can create it via YAML definition and it looks like this:

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: dev
```
