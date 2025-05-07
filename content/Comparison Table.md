# Karmada 
Karmada is a kubernetes management system that enables to run cloud-native applications across multiple Kubernetes and Clouds, with no changes to the applications. It speaks Kubernetes-native APIs and provides advanced scheduling capabilities.

## Service Discovery and Binding
In Karamada service discovery is supported using the ServiceImport and ServiceExport CRDs.

To connect the two clusters the remote cluster need to expose a service which can be deployed using the native Kubernetes API. This service is exported by the remote cluster and imported by the local one.

The remote cluster is seen in the local cluster as **derived service** which can be accessed to perform operation and control the status of the control plane on the remote cluster. The request for connection is performed using a request pod.

This process can be simplified using the MultiClusterIngress API provided in Karmada to import external traffic to services in the member clusters.

In karmada is possible to peer the cluster using both push and pull mode, but with pull mode each modification is effective because the cluster is actually receiving directives from the cluster local.
# Liqo

Liqo is an open source project that enables dynamic and seamless kubernetes multi-cluster topologies.
## Virtual Node
Liqo leverage the virtual node concept. The virtual node abstraction is implemented using an extended version of the _Virtual Kublet Project_.

Kubelet is the primary node agent and it is responsible for registering the node with the control plane and handling the lifecycle of the pods.

The virtual kubelet replaces a traditional kubelet when the controlled entity is not a physical node, allowing to control arbitrary objects through standard kubernetes APIs.

# Open Cluster Management
OCM is a powerful, modular, extensible platform.
In OCM the approach which is used is the Hub-agent architecture. This architecture is identical to the hub-kubelet from kubernetes.
In this architecture the kubelet is the primary agent node that runs on each node. It can register the node with the apiserver using one of the primary address of the node.

In OCM the function performed by the kubelet are done by the **Klusterlet**
which is also called "managed cluster" or "spoke cluster". The Klusterlet actively pulls the prescription from the hub cluster and reconcile the phsycal Kubernetes clusters.
