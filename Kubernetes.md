## Pod
 - the smallest unit of a kubernetes deployment, and serves as an abstraction layer over a container, encapsulating one or more closely related containers within a single unit

## Node
 - a virtual machine running multiple pods
 
## Deployment
 - blueprint of the application pod and specify the number of replicas we want to run
 
---
## Services

### ClusterIP
- **Purpose**: Exposes the service **internally** to the Kubernetes cluster.
- **How it works**: When you create a `ClusterIP` service, Kubernetes assigns a virtual IP address (ClusterIP) that is only accessible within the cluster. It cannot be reached from outside the cluster.
- **Use case**: This is used for internal communication between different microservices or applications running within the same cluster. For example, an internal database or a backend service that only needs to be accessed by other services in the cluster.
### NodePort
- **Purpose**: Exposes the service on each node’s IP at a specific port (between 30000 and 32767).
- **How it works**: When you create a `NodePort` service, Kubernetes opens a specific port on all nodes of the cluster, and traffic that hits the node on that port is forwarded to the service. This means the service is accessible externally via `<NodeIP>:<NodePort>`.
- **Use case**: Typically used for development, testing, or cases where external access to the service is needed but without a full load balancer. It is more basic than a load balancer.

### LoadBalancer
- **Purpose**: Exposes the service externally using a cloud provider’s **load balancer**.
- **How it works**: When you create a `LoadBalancer` service, Kubernetes automatically provisions an external load balancer (such as AWS ELB, GCP Load Balancer, etc.) and routes external traffic to the service through the load balancer. This service type builds upon `NodePort` and `ClusterIP`, routing external traffic into the cluster.
- **Use case**: Ideal for production environments where external, public access to the service is needed with the built-in support for high availability, automatic scaling, and failover provided by cloud load balancers.
----
## ReplicaSet
- **Purpose**: Ensures a specified number of **replicas** of a pod are running at any given time.
- **How it works**: If a pod crashes or is deleted, the ReplicaSet will automatically replace it with a new one. Conversely, if too many pods are running, it will terminate the excess ones.
- **Use case**: Useful for **stateless** applications where individual pod identity doesn’t matter (e.g., web servers, APIs, microservices).
- **Scaling**: Can easily scale up or down the number of pods.
## StatefulSet
- **Purpose**: Manages **stateful** applications where the identity, storage, or network configuration of each pod is important.
- **How it works**: Pods created by a StatefulSet are given unique, stable names and persist across rescheduling or restarts. Each pod gets its own **Persistent Volume Claim (PVC)** to store its data. StatefulSets ensure that the ordering (i.e., the sequence in which pods are created, scaled, or terminated) is maintained.
- **Use case**: Essential for **stateful applications** like databases (e.g., PostgreSQL, Cassandra) where each pod needs its own storage or maintains data between restarts.
## DaemonSet
- **Purpose**: Ensures that a **single instance** of a pod is running on **every node** (or specific nodes) in the Kubernetes cluster.
- **How it works**: DaemonSet runs one pod on each node. When a new node is added to the cluster, the DaemonSet will automatically schedule a pod on that node. When a node is removed, the DaemonSet cleans up the pod running on it.
- **Use case**: Ideal for running **system-level services** on each node, like log collection, monitoring, or security agents. (Prometheus node exporter)
---
## Volumes

### emptyDir
- **Purpose**: Temporary storage for a pod that lasts as long as the pod is running.
- **Use case**: Caching, temporary files, or sharing data between containers within the same pod.

### hostPath
- **Purpose**: Mounts a file or directory from the **node’s filesystem** into the pod.
- **Use case**: Accessing specific host resources like logs or Docker sockets.

### PersistentVolume (PV) and PersistentVolumeClaim (PVC)
- **Purpose**: Provides **persistent storage** that outlives the pod's lifecycle.
- **Use case**: For stateful applications that require persistent storage, such as databases (e.g., PostgreSQL, MySQL).

### configMap
- **Purpose**: Provides configuration data to the application.
- **Use case**: Storing and injecting non-sensitive configuration files or environment variables into a pod.

### secret
- **Purpose**: Stores **sensitive information** like passwords, tokens, or certificates.
- **Use case**: Injecting sensitive data securely into a pod without hardcoding it.

### awsElasticBlockStore / gcePersistentDisk
- **Purpose**: Provides **persistent cloud-based block storage** (e.g., AWS EBS or GCP Persistent Disk).
- **Use case**: For cloud-based applications that require persistent storage across pod restarts or failures.
---
[EXAMPLE USAGE OF SERVICES AND DEPLOYMENTS](https://github.com/kodekloudhub/example-voting-app-kubernetes)
