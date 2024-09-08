# KUBERNETES
Orchestration tools are software tools designed to automate and coordinate the deployment, management, and scaling of applications and services across multiple environments, such as on-premises data centers or cloud platforms. These tools help streamline complex workflows, ensuring that all components of an application work together smoothly and efficiently.

Orchestration tools are essential in environments where there are multiple interdependent services, microservices, or containers, as they help manage the lifecycle of these components, including:

+ Deployment: Automating the deployment of applications or services across multiple environments.
+ Scaling: Adjusting the resources allocated to an application or service based on demand.
+ Monitoring: Continuously monitoring the health and performance of the deployed components.
+ Fault Recovery: Automatically detecting and recovering from failures or crashes.
+ Configuration Management: Managing and maintaining the desired state configuration of infrastructure and applications.

Some popular orchestration tools include:

+ Kubernetes: A container orchestration platform used to automate the deployment, scaling, and operation of containerized applications.
+ Docker Swarm: Description: Docker's orchestration tool for managing Docker containers, providing an easier way to deploy and manage containers.
+ Apache Airflow: An orchestration tool for authoring, scheduling, and monitoring workflows, commonly used in data engineering.
+ Ansible: A tool for IT automation, often used for configuration management and orchestration.
+ Terraform: An infrastructure as code (IaC) tool that allows users to define and provide data center infrastructure using a declarative configuration language.
+ AWS Step Functions: A serverless orchestration service for building distributed applications using AWS services.

Orchestration tools are key components in DevOps and cloud-native environments, helping teams to efficiently manage complex, distributed systems.
## KUBECTL
![image](https://github.com/user-attachments/assets/6455d829-66e8-4fd7-98a2-07c8feeb4861)

# NOTE
In the context of Kubernetes, `---` is used to separate different resources in a YAML file.

Deployment and service in 1 file because they belong together

ETCD is the `cluster brain`.

Application data `is not` stored in etcd!

# Kubernetes Components
## 1. Pod
- **Purpose**: A Pod is the smallest deployable unit in Kubernetes. It represents one or more containers that share the same network and storage.
- **When to Use**: All applications in Kubernetes run inside Pods, but they are often managed through higher-level controllers like Deployment or StatefulSet.

## 2. Deployment
- **Purpose**: Manages the deployment and scaling of Pods. Ensures the desired number of replicas are running and handles updates to the Pods.
- **When to Use**: For stateless applications or when you need to manage multiple replicas of a service.

## 3. StatefulSet
- **Purpose**: Like a Deployment, but designed for stateful applications. Ensures that each Pod has a unique identity and stable storage.
- **When to Use**: When deploying stateful applications, such as databases, that require stable, unique Pod identities.

## 4. ConfigMap
- **Purpose**: Stores non-sensitive configuration data in key-value pairs, which can be consumed by Pods.
- **When to Use**: When you want to provide dynamic configuration to your applications, separating config from code.

## 5. Secret
- **Purpose**: Stores sensitive data, such as passwords or API keys, in an encrypted format.
- **When to Use**: To securely pass sensitive information to your application without exposing it in the source code.

## 6. Service
- **Purpose**: Provides stable networking to access Pods, even if individual Pod IPs change. Services expose Pods inside or outside the Kubernetes cluster.
- **When to Use**: Anytime your application needs to communicate with other services or external users.

## 7. Ingress
- **Purpose**: Manages external access to services within a Kubernetes cluster, typically via HTTP/HTTPS, and provides features like load balancing and SSL termination.
- **When to Use**: When you need to expose your application to the internet or route traffic between services based on domain names.

## 8. PersistentVolume (PV) and PersistentVolumeClaim (PVC)
- **Purpose**: PersistentVolumes are storage resources in Kubernetes, and PersistentVolumeClaims are requests for that storage.
- **When to Use**: When you need long-term, stable storage for your applications, especially stateful ones like databases.

## 9. Horizontal Pod Autoscaler (HPA)
- **Purpose**: Automatically adjusts the number of Pod replicas based on resource utilization (e.g., CPU, memory).
- **When to Use**: To automatically scale your application based on the system load.

## 10. Job and CronJob
- **Purpose**: Jobs manage the execution of short-lived tasks and ensure they complete successfully, while CronJobs schedule Jobs to run at specific times.
- **When to Use**: Use Jobs for one-time tasks and CronJobs for scheduled, recurring tasks.

# Core Kubernetes Namespaces

In Kubernetes, there are four core namespaces that are created by default when a cluster is initialized. These namespaces provide logical separation and resource organization within the cluster.

## 1. default
- **Description**: This is the default namespace where resources (Pods, Services, etc.) are created if no specific namespace is specified.
- **When to Use**: If you don’t require namespace segmentation or are working on simple test applications, resources will be created in the `default` namespace.

## 2. kube-system
- **Description**: This namespace contains resources related to Kubernetes control components, including critical services like `kube-dns`, `scheduler`, and `controller-manager`.
- **When to Use**: You will rarely interact directly with this namespace, but it is essential as it houses the core components of the Kubernetes cluster.

## 3. kube-public
- **Description**: This namespace is publicly readable by all users, including unauthenticated users.
- **When to Use**: It's typically used for storing publicly accessible information in the cluster, such as a default ConfigMap that holds cluster information.

## 4. kube-node-lease
- **Description**: This namespace contains "lease" objects associated with each node. These leases are used to track node health and improve the performance of node heartbeat detection.
- **When to Use**: This is a system namespace that Kubernetes manages automatically for tracking nodes, and you won’t need to interact with it directly.

---

## Custom Namespaces
In addition to these core namespaces, you can create custom namespaces to logically separate applications, environments (like `dev`, `staging`, `prod`), or teams. This helps in better resource management and isolation.

# Comparison of Ingress, External Service, and Internal Service in Kubernetes

In Kubernetes, **Ingress**, **External Service**, and **Internal Service** are mechanisms to handle traffic between services within the cluster and from outside the cluster. Each serves a different purpose and use case. Below is a detailed comparison of the three.

## 1. Internal Service (Type: ClusterIP)

An **Internal Service** (default service type: **ClusterIP**) is used for **internal communication** within the Kubernetes cluster. It is not exposed outside the cluster and is accessible only by other services or Pods within the cluster.

### Key Features of Internal Service:
- **Cluster-only access**: Accessible only within the Kubernetes cluster via a cluster IP.
- **Service discovery**: Pods within the cluster can use the service name to communicate.
- **Load balancing**: Automatically balances traffic between Pods tied to the service.
- **No external access**: Ensures internal services remain private and inaccessible from outside the cluster.

### When to Use Internal Service:
- For backend services, databases, or APIs that only need to communicate with other services inside the cluster.
- When privacy and isolation of services are critical.
- For internal-only microservices communication.

---

## 2. External Service (Type: NodePort or LoadBalancer)

An **External Service** is a type of service that allows access from outside the Kubernetes cluster. It can be used to expose services via a node port or a cloud provider's load balancer.

### Key Features of External Service:
- **NodePort**: Opens a port on each node in the cluster, allowing external access via `<NodeIP>:<NodePort>`.
- **LoadBalancer**: Utilizes a cloud provider's load balancer (like AWS ELB, GCP Load Balancer) to route external traffic into the cluster.
- **Direct external access**: Simplifies public access to a service from outside the cluster.
- **Load balancing**: Handles load balancing at the cloud provider level (for LoadBalancer) or at the node level (for NodePort).

### When to Use External Service:
- When you need to expose a service publicly to the internet without complex routing.
- For simple applications that require direct access from external users.
- **NodePort** is useful for development or testing environments.
- **LoadBalancer** is ideal when using cloud providers for production applications.

---

## 3. Ingress

**Ingress** is a Kubernetes resource that provides external access to multiple services within the cluster through defined HTTP/HTTPS routing rules. It acts as a single entry point to the cluster and routes requests to the appropriate services.

### Key Features of Ingress:
- **Routing**: Supports routing traffic based on **URL paths** or **hostnames** to different services.
- **Single access point**: Consolidates access to multiple services through one external IP or DNS name.
- **SSL/TLS termination**: Supports HTTPS access and termination of SSL/TLS connections at the Ingress level.
- **Advanced load balancing**: Can use advanced load-balancing algorithms and rules via an Ingress controller.

### When to Use Ingress:
- When you have multiple services that need to be exposed externally and require HTTP/HTTPS routing.
- When you need features like **path-based routing**, **host-based routing**, or **SSL termination**.
- For complex applications where you want to centralize and manage external access through a single entry point.

---

## Detailed Comparison Table

| **Feature**               | **Internal Service (ClusterIP)**           | **External Service (NodePort/LoadBalancer)**      | **Ingress**                                        |
|---------------------------|--------------------------------------------|--------------------------------------------------|---------------------------------------------------|
| **Access Scope**           | Internal (only within the cluster)         | External (accessible from outside the cluster)    | External (accessible from outside the cluster)     |
| **Traffic Type**           | Any protocol (TCP/UDP)                     | Any protocol (TCP/UDP)                           | Primarily HTTP/HTTPS                              |
| **Routing**                | No routing, direct access via service name | No advanced routing; exposes entire service       | Supports path and host-based routing              |
| **SSL/TLS**                | No SSL/TLS support                        | No built-in SSL/TLS support                      | Built-in SSL/TLS termination                      |
| **Load Balancing**         | Internal, simple load balancing            | Cloud provider (LoadBalancer) or node-level (NodePort) load balancing | Advanced load balancing with custom routing rules |
| **Complexity**             | Simple, default service type               | Easy to set up, especially with cloud providers   | More complex, requires an Ingress controller      |
| **Use Case**               | Internal services that do not need public exposure | Exposing services directly to external users      | Managing access to multiple services via a single entry point |
| **Cloud Usage**            | No specific cloud provider integration     | LoadBalancer is cloud provider-specific           | Requires deploying Ingress controller             |

---

## Summary:

- **Internal Service (ClusterIP)**: Used for communication between services **within the cluster**. It's private and ideal for backend services, databases, and internal APIs.
  
- **External Service (NodePort/LoadBalancer)**: Exposes a service **directly to the external world**. Suitable for simpler applications that don't need complex routing or advanced configurations. **NodePort** is more appropriate for development environments, while **LoadBalancer** is ideal for cloud providers in production.

- **Ingress**: Provides **external access** to multiple services within the cluster, using **HTTP/HTTPS routing rules**. It acts as a **single entry point** for managing traffic to various services and supports SSL termination, making it perfect for more complex setups that require routing flexibility and security.
