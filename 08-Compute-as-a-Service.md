# Compute as a Service on AWS - Notes

## Understanding Servers
Servers are essential for hosting applications and handling HTTP requests. They provide CPU, memory, and networking capacity to process user requests and deliver responses. Common HTTP servers include:

- **Windows options**: Internet Information Services (IIS).
- **Linux options**: Apache HTTP Web Server, Nginx, Apache Tomcat.

## AWS Compute Services
To run an HTTP server on AWS, you need to select a compute service from the AWS Management Console. AWS offers various compute options, each suited for different use cases:

### Types of Compute Options
1. **Virtual Machines (VMs)**:
   - Emulates a physical server.
   - Allows installation of HTTP servers to run applications.
   - In AWS, these VMs are called Amazon Elastic Compute Cloud (Amazon EC2).
   - AWS manages the host machines, hypervisor layer, and the guest operating system.

2. **Container Services**:
   - Containerize applications for more efficient resource usage and scalability.
   - Often use virtualization concepts similar to VMs.

3. **Serverless**:
   - Automatically manage the infrastructure for running applications.
   - No need to manage servers; focus on code execution.

### Amazon EC2 (Elastic Compute Cloud)
- A virtual machine service that provides resizable compute capacity.
- Ideal for users familiar with traditional infrastructure.
- AWS handles the underlying infrastructure and management, allowing you to focus on your applications.

## Resources for Further Reading
- [AWS: Compute Services Whitepaper](https://aws.amazon.com/whitepapers/aws-compute-services/)
- [AWS: Compute on AWS](https://aws.amazon.com/products/compute/)
- [AWS: AWS Compute Blog](https://aws.amazon.com/blogs/compute/)
