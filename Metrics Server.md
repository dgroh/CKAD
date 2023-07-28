You can have one metrics server pro [[Cluster]] . It retrieves metrics from each [[Node (Worker Node)]] and [[Kubernetes/Pod|Pod]]s, aggregates them and store them in memory.

> The kubernetes metrics server is In-Memory solution and does not persist the metrics anywhere.

[[cAdvisor]] is responsible for retrieving performance metrics from PODs and exposing them through the [[Kubelet]] API to make the metrics available for the metrics server.

To view the metrics use the following commands:

**For nodes:**

`kubectl top node`

**For pods:**

`kubectl top pod`
