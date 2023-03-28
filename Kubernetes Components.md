## API Server

The frontend for kubernetes for communication with the cluster

## etcd

key-value store for the cluster

## kubelet

The agent that runs on each node in the cluster. It ensures that the containers are running on the nodes as expected.

## Container Runtime

The underline software to run the container, for examploe: `docker` 

## Controller

Brain behind orchestration. Responsible for noticing and responding when node containers or endpoints go down. 

## Scheduler

Responsible for distributing work across the nodes and assigning them to the nodes