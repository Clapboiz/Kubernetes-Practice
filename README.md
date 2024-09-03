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

# NOTE
In the context of Kubernetes, `---` is used to separate different resources in a YAML file.

# SET UP
Follow these step. 

```
kubectl apply -f mongo-config.yaml
```

```
kubectl apply -f mongo-secret.yaml 
```

```
kubectl apply -f mongo.yaml 
```

```
kubectl apply -f webapp.yaml 
```

```
kubectl get all
```


```
minikube service webapp-service
```
