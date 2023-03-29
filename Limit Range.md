A LimitRange is a policy to constrain the resource allocations (limits and requests) that you can specify for each applicable object kind (such as Pod or [PersistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims)) in a namespace.

A _LimitRange_ provides constraints that can:

-   Enforce minimum and maximum compute resources usage per Pod or Container in a namespace.
-   Enforce minimum and maximum storage request per [PersistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#persistentvolumeclaims) in a namespace.
-   Enforce a ratio between request and limit for a resource in a namespace.
-   Set default request/limit for compute resources in a namespace and automatically inject them to Containers at runtime.

A LimitRange is enforced in a particular namespace when there is a LimitRange object in that namespace.

The name of a LimitRange object must be a valid [DNS subdomain name](https://kubernetes.io/docs/concepts/overview/working-with-objects/names#dns-subdomain-names).