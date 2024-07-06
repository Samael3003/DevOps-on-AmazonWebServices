# Introduction to Amazon Elastic Compute Cloud (EC2) - Notes

## What Is Amazon EC2?
Amazon EC2 (Elastic Compute Cloud) is a web service that provides secure, resizable compute capacity in the cloud. It allows users to provision virtual servers called EC2 instances. You can create and manage these instances through:

- AWS Management Console
- AWS Command Line Interface (CLI)
- AWS Software Development Kits (SDKs)
- Automation tools and infrastructure orchestration services

## Defining an EC2 Instance
To create an EC2 instance, you need to define:

- **Hardware Specifications**: CPU, memory, network, and storage.
- **Logical Configurations**: Networking location, firewall rules, authentication, and the operating system.

### Amazon Machine Image (AMI)
The first step in launching an EC2 instance is selecting an Amazon Machine Image (AMI). An AMI includes:

- The operating system
- Storage mappings
- Architecture type (32-bit, 64-bit, 64-bit ARM)
- Additional software installed

### Relationship Between AMIs and EC2 Instances
An AMI is like a blueprint, while an EC2 instance is a live instantiation of that blueprint. When you launch an instance:

1. AWS allocates a virtual machine that runs on a hypervisor.
2. The selected AMI is copied to the root device volume, which contains the image used to boot the instance.
3. You get a server you can connect to and install packages and additional software, like a web server.

### Advantages of Using AMIs
- **Reusability**: You can create an AMI from your running instance and use it to launch new instances with the same configurations, reducing time and minimizing human error.

### Finding AMIs
You can select an AMI from various categories:

1. **Quick Start AMIs**: Premade by AWS for quick startup.
2. **AWS Marketplace AMIs**: Popular open source and commercial software from third-party vendors.
3. **My AMIs**: Created from your EC2 instances.
4. **Community AMIs**: Provided by the AWS user community.
5. **Custom Images**: Built with EC2 Image Builder.

Each AMI in the AWS Management Console has a unique AMI ID, which is region-specific.

## Resources for Further Reading
- [AWS: Amazon EC2](https://aws.amazon.com/ec2/)
- [AWS: Amazon Machine Images (AMI)](https://aws.amazon.com/ec2/amis/)
- [AWS: Creating an Amazon EBS-backed Linux AMI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/creating-an-ami-ebs.html)
- [AWS: What Is EC2 Image Builder
