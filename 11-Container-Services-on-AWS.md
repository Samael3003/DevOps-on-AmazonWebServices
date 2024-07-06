# Container Services on AWS - Notes

## Introduction to Containers

### What is a Container?
- **Definition**: Standardized unit packaging code and dependencies for consistent operation across platforms.
- **Advantages**: Portability, reliability, isolation.
- **History**: Concept dates to 1970s, modernized through open source evolution.

### Docker
- **Container Runtime**: Simplifies management of OS stack for container isolation (networking, storage).
- **Features**: Easy creation, packaging, deployment, and execution of containers.

### Containers vs. Virtual Machines (VMs)
- **Containers**: Share host OS and kernel, lightweight, quick startup (suitable for scaling).
- **VMs**: Isolated OS per instance, resource-intensive, slower startup.

## Orchestrating Containers

### AWS Container Services
- **Deployment**: Containers run on EC2 instances.
- **Scale and Management**: Orchestration across clusters, handling failures, monitoring deployments.
- **Services**: Amazon ECS (Elastic Container Service) and Amazon EKS (Elastic Kubernetes Service).

### Amazon ECS (Elastic Container Service)
- **Description**: End-to-end orchestration for container management on EC2.
- **Components**: Amazon ECS Container Agent manages cluster, supports Linux and Windows AMIs.
- **Task Definition**: JSON file defining container resources (CPU, memory, ports, images).

### Example Task Definition for Nginx on Amazon ECS
```json
{
   "family": "webserver",
   "containerDefinitions": [
      {
         "name": "web",
         "image": "nginx",
         "memory": "100",
         "cpu": "99"
      }
   ],
   "requiresCompatibilities": ["FARGATE"],
   "networkMode": "awsvpc",
   "memory": "512",
   "cpu": "256"
}
```

### Amazon EKS (Elastic Kubernetes Service)
- **Description**: Managed Kubernetes service on AWS.
- **Features**: Extensible, portable, open-source platform for containerized workload management.
- **Comparison**: Uses Kubernetes concepts (e.g., pods, worker nodes) for orchestration.

## Conclusion
Containers offer flexibility and efficiency in managing workloads, from development to production, on AWS. Choose between Amazon ECS for simplicity and integration with AWS services, or Amazon EKS for Kubernetes compatibility and advanced orchestration capabilities.

### Resources for Further Reading
- [AWS: Containers on AWS](https://aws.amazon.com/containers/)
- [Docker: What Is a Container?](https://www.docker.com/resources/what-container)
- [AWS: Amazon Elastic Container Service](https://aws.amazon.com/ecs/)
- [Github: Amazon ECS Agent](https://github.com/aws/amazon-ecs-agent)
- Coursera Course: Building Containerized Applications on AWS
