
## Components

The core component of Kubernetes is the Control Plane. It's the responsible for coordinating everything in a Kubernetes cluster.
Its key components are:

- API Server: it exposes a Rest API for clients to talk to the Control Plane for actions such as creating a pod or update a deployment.
- etcd: the cluster's memory. It's a NoSQL database, a distributed key-value storage that holds the cluster's state.
- Scheduler: It's responsible for deciding which node is the best host for a pod to be deployed based on resources and capacity
- Controller Manager: Ensures everything runs as it should, maintaining the desired state of resources.