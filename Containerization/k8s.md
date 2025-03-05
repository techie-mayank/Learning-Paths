# Kubernetes Learning Path
## Beginner Level
### 1.1 Introduction to Kubernetes
#### What is Kubernetes?
- **Definition**: Open-source container orchestration platform.
- **Purpose**: Automates deployment, scaling, and management of containerized applications.
- **Use Cases**: Microservices, cloud-native apps, CI/CD pipelines.
#### Key Features
- **Self-healing**: Automatically restarts failed containers.
- **Scaling**: Horizontal scaling based on demand.
- **Rollouts**: Zero-downtime deployments.
#### Kubernetes vs. Docker Swarm
- **Kubernetes**: More feature-rich, complex, enterprise-grade.
- **Docker Swarm**: Simpler, lightweight, easier to set up.

### 1.2 Core Concepts
#### Pods
- **Definition**: Smallest deployable unit in Kubernetes.
- **Lifecycle**: Created, scheduled, terminated.
- **Multi-container Pods**: Shared storage/network, sidecar pattern.
#### Controllers
- **Deployments**: Manage stateless apps, rolling updates.
- **ReplicaSets**: Ensure desired number of pods are running.
- **StatefulSets**: Manage stateful apps (e.g., databases).
- **DaemonSets**: Run one pod per node (e.g., logging agents).
#### Services & Networking
- **ClusterIP**: Internal IP for pod communication.
- **NodePort**: Expose app to external traffic.
- **LoadBalancer**: Cloud-provider load balancer.
#### Storage
- **Persistent Volumes (PVs)**: Cluster-wide storage resource.
- **Persistent Volume Claims (PVCs)**: Request storage by pods.
#### ConfigMaps & Secrets
- **ConfigMaps**: Store non-sensitive configuration data.
- **Secrets**: Store sensitive data (e.g., passwords, tokens).
#### Namespaces
- **Purpose**: Logical separation of resources.
- **Default Namespaces**: `default`, `kube-system`, `kube-public`.

### 1.3 Cluster Architecture
#### Master Components
- **API Server**: Front-end for Kubernetes control plane.
- **etcd**: Key-value store for cluster data.
- **Scheduler**: Assigns pods to nodes.
#### Node Components
- **kubelet**: Ensures containers are running in pods.
- **kube-proxy**: Manages network rules on nodes.
- **Container Runtime**: Runs containers (e.g., Docker, containerd).
#### Image Link
- [Kubernetes Cluster Diagram](https://example.com/k8s-arch.png)

### 1.4 Installation & Setup
#### Minikube
- **Purpose**: Local Kubernetes cluster for development.
- **Setup**: `minikube start`, `minikube stop`.
#### kubeadm
- **Purpose**: Bootstrap production-ready clusters.
- **Steps**: `kubeadm init`, `kubeadm join`.
#### Managed Services
- **EKS**: Amazon Elastic Kubernetes Service.
- **GKE**: Google Kubernetes Engine.
- **AKS**: Azure Kubernetes Service.
#### Basic kubectl Commands
- **get**: List resources (e.g., `kubectl get pods`).
- **describe**: Detailed info about a resource.
- **logs**: Fetch logs from a pod.

## Intermediate Level
### 2.1 Application Deployment
#### YAML Manifests
- **Structure**: `apiVersion`, `kind`, `metadata`, `spec`.
- **Best Practices**: Use labels, avoid hardcoding values.
#### Multi-Container Pods
- **Sidecar Pattern**: Helper container for main app.
- **Adapter Pattern**: Normalize data for main app.
#### Probes
- **Liveness Probe**: Is the app running?
- **Readiness Probe**: Is the app ready to serve traffic?
- **Startup Probe**: Is the app initialized?

### 2.2 Networking Deep Dive
#### CNI Plugins
- **Calico**: Network policy enforcement.
- **Flannel**: Simple overlay network.
#### Ingress Controllers
- **Nginx**: Popular, highly configurable.
- **Traefik**: Dynamic, supports multiple backends.
#### Network Policies
- **Purpose**: Define pod communication rules.
- **Example**: Allow traffic only from specific namespaces.

### 2.3 Scaling Applications
#### Horizontal Pod Autoscaler (HPA)
- **Purpose**: Scale pods based on CPU/memory usage.
- **Example**: `kubectl autoscale deployment <name> --min=2 --max=10`.
#### Cluster Autoscaler
- **Purpose**: Scale nodes in cloud environments.
- **Example**: Automatically add nodes when pods are pending.

### 2.4 Monitoring & Logging
#### Prometheus + Grafana
- **Prometheus**: Collects and stores metrics.
- **Grafana**: Visualizes metrics with dashboards.
#### EFK Stack
- **Elasticsearch**: Stores logs.
- **Fluentd**: Collects and forwards logs.
- **Kibana**: Visualizes logs.

### 2.5 Security
#### RBAC
- **Roles**: Define permissions within a namespace.
- **RoleBindings**: Bind roles to users/groups.
#### Pod Security Policies
- **Purpose**: Restrict pod behavior (e.g., privileged mode).
#### TLS Certificates
- **cert-manager**: Automates certificate management.

## Advanced Level
### 3.1 Advanced Scheduling
#### Node Affinity/Anti-Affinity
- **Affinity**: Schedule pods on specific nodes.
- **Anti-Affinity**: Avoid scheduling pods on the same node.
#### Taints & Tolerations
- **Taints**: Prevent pods from being scheduled on nodes.
- **Tolerations**: Allow pods to ignore taints.
#### Custom Schedulers
- **Purpose**: Implement custom scheduling logic.

### 3.2 Operators & CRDs
#### Operator Framework
- **Purpose**: Automate application management.
- **Example**: etcd Operator.
#### Custom Resources (CRDs)
- **Purpose**: Extend Kubernetes API.
- **Example**: Define a `Database` resource.

### 3.3 Stateful Applications
#### StatefulSets
- **Purpose**: Manage stateful apps with stable network identities.
- **Example**: MySQL cluster.
#### Volume Snapshots/Cloning
- **Purpose**: Backup and restore persistent data.

### 3.4 CI/CD Integration
#### GitOps with Argo CD
- **Purpose**: Declarative CD using Git.
- **Workflow**: Git repo -> Argo CD -> Kubernetes.
#### Jenkins Pipelines
- **Purpose**: Automate build/test/deploy workflows.
#### Image Link
- [CI/CD Pipeline](https://example.com/cicd-flow.png)

### 3.5 Advanced Networking
#### Service Mesh
- **Istio**: Traffic management, security, observability.
- **Linkerd**: Lightweight, focused on simplicity.
#### DNS Policies
- **CoreDNS**: Customize DNS resolution for pods.

## Real-World Scenarios
### Blue/Green Deployments
- **Purpose**: Zero-downtime deployments.
- **Workflow**: Deploy new version alongside old, switch traffic.
### Canary Releases
- **Purpose**: Gradually roll out changes.
- **Workflow**: Deploy to small subset of users first.
### Multi-Cloud Clusters
- **Anthos**: Google’s multi-cloud platform.
- **Azure Arc**: Manage Kubernetes clusters across clouds.
### Troubleshooting
- **Network Issues**: Check CNI config, DNS resolution.
- **CrashLoopBackOff**: Investigate pod logs, resource limits.

## Certifications & Resources
### CKA (Certified Kubernetes Administrator)
- **Exam Focus**: Cluster management, troubleshooting.
### CKAD (Certified Kubernetes Application Developer)
- **Exam Focus**: Application deployment, debugging.
### Books
- **"Kubernetes Up & Running"**: Comprehensive guide.
- **"The DevOps Handbook"**: Best practices for DevOps.
### Labs
- **Katacoda**: Interactive Kubernetes tutorials.
- **Play with Kubernetes**: Free online Kubernetes playground.
