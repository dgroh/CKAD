Kubernetes does not deploy containers directly in the [[Worker Node]]. The containers are encapsulated into a kubernetes object known as **POD**.

A POD is a single instance of an application. The POD is the smallest object you can create in kubernetes.

It's possible to add more PODs to de node to share load or even to add other nodes to the cluster.

POD has a one-to-one relationship with a container. To scale up, you create new POD, to scale down, you delete an existing POD.

It's possible to have multiple containers within the same POD. For example a helper container. In this case both containers can communicate with each other via localhost as they share the same network.