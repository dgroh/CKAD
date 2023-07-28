Kubernetes services enable communication between components within and outside of the application.

In Kubernetes a [[Node (Worker Node)]] has an IP address, the [[POD]] inside the node has another IP address. The internal network of a Cluster can natively only be accessed by components from within the cluster. That is how Services come into place. It enables

There are 3 types of services in Kubernetes: [[NodePort Service]], [[Cluster IP]] and [[Load Balancer]].