# Serverless and AWS Lambda

## Remove the Undifferentiated Heavy Lifting

When running code on Amazon EC2, AWS handles the physical hardware, but you manage the logical controls such as:
- Guest operating system
- Security and patching
- Networking
- Scaling

For containers on Amazon ECS and EKS, AWS manages more of the container management, but you still maintain the underlying EC2 instances. To avoid managing EC2 instances entirely, you can use AWS serverless compute options.

## Go Serverless

Key aspects of serverless:
1. No servers to provision or manage.
2. Scales with usage.
3. No payment for idle resources.
4. Built-in availability and fault tolerance.

With serverless, focus on differentiating your application rather than managing servers. AWS offers several serverless compute options, including AWS Fargate and AWS Lambda.

## Explore Serverless Containers with AWS Fargate

Amazon ECS and Amazon EKS run in two modes:
- Amazon EC2 mode
- AWS Fargate mode

AWS Fargate is a serverless compute engine for containers that:
- Manages infrastructure and scales automatically.
- Eliminates the need to manage EC2 instances and cluster capacity.
- Supports ECS and EKS architecture.
- Provides workload isolation and improved security.

Fargate integrates with AWS Identity and Access Management (IAM) and Amazon Virtual Private Cloud (VPC), allowing you to launch Fargate containers within your network.

## Run Your Code on AWS Lambda

AWS Lambda allows you to run code without provisioning or managing servers or containers. It supports a variety of applications, including:
- Data processing
- Real-time stream processing
- Machine learning
- WebSockets
- IoT backends
- Mobile backends
- Web apps

### How Lambda Works

Lambda functions consist of:
1. **Code**: The source code that describes what the Lambda function should run.
    - Create from scratch
    - Use AWS blueprints
    - Use code from AWS Serverless Application Repository

2. **Configuration**: Information describing how the function should run, including:
    - Network placement
    - Environment variables
    - Memory
    - Invocation type
    - Permission sets

3. **Triggers**: Describe when the Lambda function should run, integrating with other AWS services to respond to events.

### AWS Lambda Function Handler

The function handler in your code processes events. The general syntax for a Python handler is:
```python
def handler_name(event, context):
    ...
    return some_value
```
Naming the handler:
- File name: `lambda_function.py`
- Default handler name: `lambda_handler`

If you choose a different handler name, update it in the Lambda console's Runtime settings.

### Billing Granularity

AWS Lambda charges are based on:
- Number of times the code is triggered (requests).
- Duration of code execution, rounded up to the nearest millisecond.

This pricing model is cost-effective for functions with short execution times, such as low latency APIs.

## References

- [AWS: Serverless](https://aws.amazon.com/serverless/)
- [Building Modern Python Applications on AWS (Coursera)](https://www.coursera.org/learn/building-modern-python-applications-on-aws)
- [AWS Serverless resources](https://aws.amazon.com/serverless/resources/)
- [Building Applications with Serverless Architectures](https://aws.amazon.com/serverless/architectures/)
- [Best practices for organizing larger serverless applications](https://aws.amazon.com/blogs/compute/best-practices-for-organizing-larger-serverless-applications/)
- [Managing AWS Lambda functions](https://docs.aws.amazon.com/lambda/latest/dg/lambda-introduction.html)
- [10 Things Serverless Architects Should Know](https://aws.amazon.com/blogs/compute/10-things-serverless-architects-should-know/)
- [AWS Alien Attack! A Serverless Adventure](https://aws.amazon.com/blogs/compute/aws-alien-attack-a-serverless-adventure/)
