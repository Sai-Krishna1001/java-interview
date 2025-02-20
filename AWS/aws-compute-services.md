### 1. What is Amazon Elastic Compute Cloud (EC2) and what are its key features?
Amazon EC2 is a web service that provides scalable computing capacity in the cloud. Key features include:
- On-demand virtual servers
- Multiple instance types
- Auto-scaling capabilities
- Security with VPC integration
- Pay-as-you-go pricing

### 2. Describe the different EC2 instance types and their use cases.
- **General Purpose (e.g., t3, m5):** Balanced compute, memory, and networking.
- **Compute Optimized (e.g., c5):** Ideal for CPU-intensive workloads.
- **Memory Optimized (e.g., r5, x1):** Designed for applications requiring high memory.
- **Storage Optimized (e.g., i3, d2):** Suitable for high-speed storage operations.
- **Accelerated Computing (e.g., p4, g4):** Used for machine learning and graphics workloads.

### 3. What is Amazon Elastic Container Service (ECS) and how does it work?
Amazon ECS is a fully managed container orchestration service that allows users to run, manage, and scale containerized applications using Docker. It supports:
- Fargate (serverless execution)
- EC2-backed clusters
- Load balancing and auto-scaling

### 4. Explain the difference between Amazon EC2 and AWS Lambda.
- **EC2:** Provides full control over virtual machines with flexible configurations.
- **Lambda:** Serverless computing that runs code in response to events without provisioning servers.

### 5. What is AWS Elastic Beanstalk, and when would you use it?
AWS Elastic Beanstalk is a Platform as a Service (PaaS) that automatically handles application deployment, scaling, monitoring, and maintenance. It is ideal for developers who want to focus on coding without managing infrastructure.

### 6. How does auto-scaling work in AWS?
Auto-scaling dynamically adjusts the number of instances based on traffic demand. It ensures high availability and cost efficiency by scaling up during peak loads and scaling down during idle periods.

### 7. What is Amazon Elastic Kubernetes Service (EKS) and its benefits?
Amazon EKS is a managed Kubernetes service that simplifies deploying, scaling, and managing containerized applications. Benefits include:
- Automatic scaling
- Integration with AWS services
- High availability and security

### 8. Describe the concept of spot instances in AWS.
Spot instances allow users to bid for unused EC2 capacity at lower prices. They are cost-effective but can be terminated by AWS when demand rises.

### 9. What is AWS Fargate and how does it differ from Amazon ECS?
AWS Fargate is a serverless compute engine for containers. Unlike ECS, it eliminates the need to manage EC2 instances, allowing users to run containers without provisioning infrastructure.

### 10. Explain the purpose of Amazon EC2 Container Registry (ECR).
Amazon ECR is a managed container registry that allows users to store, manage, and deploy Docker container images securely. It integrates seamlessly with ECS and EKS for streamlined containerized application management.

