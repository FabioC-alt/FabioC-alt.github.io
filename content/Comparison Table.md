# Karmada
Karmada is a Kubernetes management system that makes possible to run a cloud-native application managing multiple clusters which runs Kubernetes, so by speaking Kubernetes-native API and providing advanced solutions for scheduling capabilities. [1]

### Core functioning and Components
Karmada control plane can manages the clusters using two different methods depending on the Cluster Registration Mode.

Karmada supports both `Push` and `Pull` mode to manage the member clusters. The main differences between `Push` and `Pull` modes is the way they access member clusters when deploying manifests.[2]

In `Push` mode the Karmanda control plane will access member cluster's `kube-apiserver` directly to get cluster status and deploy manifests, while in `Pull` mode the Karmada control plane will not access member cluster but delegate it to an extra component named `karmada-agent`.

Each `karmada-agent` serves a cluster and takes responsibility for:
- Registering cluster to Karmada
- Maintaining cluster status and reporting to Karmada
- Watching manifests from Karmada execution space and deploying the watched resources to the cluster the agent serves.

The Karamada `Pull` mode manages the cluster using the hub-spoke pattern, while the `Push` mode uses the master-slave approach to the cluster management.
# Liqo

Liqo is an open source project that enables **dynamic and seamless kubernetes** multi-cluster topologies.[3]

## Virtual Node
Liqo leverage the virtual node concept. The virtual node abstraction is implemented using an extended version of the _Virtual Kublet 
Project_.[4]

The virtual kubelet replaces a traditional kubelet when the controlled entity is not a physical node, allowing to control arbitrary objects through standard kubernetes APIs.

Liqo's particular feature is the **peering** method. In Liqo,**peering** as a unidirectional resource and service consumption relationship between two Kubernetes clusters, with one cluster (i.e., the **consumer**) granted the capability to offload tasks (_pods_) and propagate resources (_volumes_, _secrets_, etc.) to a remote cluster (i.e., the **provider**), but not vice versa.[5]

This configuration allows for maximum flexibility in asymmetric setups, while transparently supporting bidirectional peerings through their combination. Additionally, the same cluster can play the role of provider and consumer in multiple peerings.

Liqo follows the pattern **peer-to-peer** previously examined.

****
# Comparison Table

## Networking
## Workload Scheduling
## Overhead
## High Affidability


[1]https://karmada.io/
[2]https://karmada.io/docs/userguide/clustermanager/cluster-registration
[3]https://docs.liqo.io/en/v1.0.0/
[4]https://docs.liqo.io/en/v1.0.0/features/offloading.html#virtual-node
[5]https://docs.liqo.io/en/v1.0.0/features/peering.html