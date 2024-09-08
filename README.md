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