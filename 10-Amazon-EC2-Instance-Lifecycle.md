# Amazon EC2 Instance Lifecycle - Notes

## EC2 Instance Components
When creating an EC2 instance, you must choose specifications for:
- **Instance Type**: Virtual processors (vCPUs), memory, network, storage, and GPUs.
- **Network Configuration**: Default Amazon Virtual Private Cloud (VPC) or custom VPC.
- **Storage Configuration**: Instance store volumes, Amazon Elastic Block Store (EBS).

### Instance Types and Families
EC2 instances are categorized by families based on their optimization:
- **General Purpose**: Balanced compute, memory, and networking (e.g., web servers, containerized microservices).
- **Compute Optimized**: High-performance processors (e.g., scientific modeling, machine learning).
- **Memory Optimized**: Fast performance for large datasets (e.g., high-performance databases).
- **Accelerated Computing**: Hardware accelerators (e.g., 3D rendering, video encoding).
- **Storage Optimized**: High sequential read/write access (e.g., NoSQL databases, data warehousing).

### Availability and High Availability
- **Default VPC**: Public and internet-accessible; not recommended for sensitive data.
- **Custom VPCs**: More control over network configuration and security.
- **Availability Zones**: Design for high availability by using multiple instances across different zones.

### Instance Lifecycle States
1. **Pending**: Instance is preparing to run; billing has not started.
2. **Running**: Instance is active and billing starts.
3. **Reboot**: Equivalent to an OS reboot; maintains IP addresses and data on the instance store.
4. **Stop**: Instance is stopped; may be placed on a new physical server on restart.
5. **Terminate**: Instance is deleted; all data and IP addresses are lost.

### Stop vs. Stop-Hibernate
- **Stop**: Instance stops, RAM data is lost, storage charges apply for EBS volumes.
- **Stop-Hibernate**: RAM data saved to EBS root volume, useful for in-memory applications.

## EC2 Pricing Options
- **On-Demand Instances**: Pay per second without long-term commitments.
- **Reserved Instances (RIs)**: Significant discount for a 1-year or 3-year term commitment; three payment options (All Upfront, Partial Upfront, No Upfront).
- **Spot Instances**: Up to 90% discount, pay based on Spot price, instances may be interrupted.

## EC2 Pricing
- **Instance Pricing**: Cost associated with the instance specifications.
- **Billing**: Per-second basis; prices are often listed per-hour for simplicity.
- **Third-Party AMIs**: May have a minimum billing period.

### Pricing Details
- **On-Demand**: Flexible, pay when instance is running.
- **Reserved**: Discounted, pay for the reserved period even if the instance is stopped.
- **Spot**: Cost-effective but instances can be interrupted.

## Resources for Further Reading
- [AWS: Amazon EC2](https://aws.amazon.com/ec2/)
- [AWS: Default VPC and default subnets](https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html)
- [AWS: AWS Reliability Pillar](https://aws.amazon.com/architecture/well-architected/reliability-pillar/)
- [AWS: Instance lifecycle](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html)
- [AWS: Amazon EC2 pricing](https://aws.amazon.com/ec2/pricing/)
- [AWS: Amazon EC2 On-Demand Pricing](https://aws.amazon.com/ec2/pricing/on-demand/)
- [AWS: Amazon EC2 Spot Instances Pricing](https://aws.amazon.com/ec2/spot/pricing/)
- [AWS: Amazon EC2 Reserved Instances Pricing](https://aws.amazon.com/ec2/pricing/reserved-instances/)

