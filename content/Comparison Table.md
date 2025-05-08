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

****
# Comparison Table

## Networking
## Workload Scheduling
## Overhead
## High Affidability


[1]https://karmada.io/
[2]https://karmada.io/docs/userguide/clustermanager/cluster-registration