# Amazon VPC Routing and Security

## The Main Route Table

When you create a VPC, AWS automatically creates a route table called the main route table. A route table contains a set of rules (routes) that determine where network traffic is directed. By default, the main route table allows traffic to flow between all subnets in the local network.

### Components of a Route Table

- **Destination:** The range of IP addresses where you want your traffic to go.
- **Target:** The connection through which to send the traffic.

## Custom Route Tables

While the main route table controls routing for your VPC, you can create custom route tables to manage traffic for specific subnets. Custom route tables allow for more granular control, such as separating frontend and backend resources.

- Custom route tables still allow communication between all resources and subnets within the VPC by default.

## Secure Your Subnets with Network ACLs

Network ACLs (Access Control Lists) act as a firewall at the subnet level, controlling the traffic allowed to enter or leave your subnet.

### Default Network ACL

By default, the network ACL allows all traffic in and out of your subnet:

#### Inbound Rules

| Rule # | Type            | Protocol | Port Range | Source    | Allow/Deny |
|--------|-----------------|----------|------------|-----------|------------|
| 100    | All IPv4 traffic | All      | All        | 0.0.0.0/0 | ALLOW      |
| *      | All IPv4 traffic | All      | All        | 0.0.0.0/0 | DENY       |

#### Outbound Rules

| Rule # | Type            | Protocol | Port Range | Source    | Allow/Deny |
|--------|-----------------|----------|------------|-----------|------------|
| 100    | All IPv4 traffic | All      | All        | 0.0.0.0/0 | ALLOW      |
| *      | All IPv4 traffic | All      | All        | 0.0.0.0/0 | DENY       |

### Custom Network ACL Example

#### Inbound Rules

| Rule # | Source IP    | Protocol | Port | Allow/Deny | Comments                                                  |
|--------|--------------|----------|------|------------|-----------------------------------------------------------|
| 100    | All IPv4 traffic | TCP      | 443  | ALLOW      | Allows inbound HTTPS traffic from anywhere                 |
| 130    | 192.0.2.0/24 | TCP      | 3389 | ALLOW      | Allows inbound RDP traffic to the web servers from your home network’s public IP address range |
| *      | All IPv4 traffic | All      | All  | DENY       | Denies all inbound traffic not already handled by a preceding rule |

#### Outbound Rules

| Rule # | Destination IP | Protocol | Port Range  | Allow/Deny | Comments                                                               |
|--------|----------------|----------|-------------|------------|------------------------------------------------------------------------|
| 120    | 0.0.0.0/0      | TCP      | 1025-65535  | ALLOW      | Allows outbound responses to clients on the internet (serving people visiting the web servers in the subnet) |
| *      | 0.0.0.0/0      | All      | All         | DENY       | Denies all outbound traffic not already handled by a preceding rule    |

Network ACLs are stateless, meaning you need to include both inbound and outbound ports for the protocol. 

## Secure Your EC2 Instances with Security Groups

Security groups act as a firewall at the instance level. By default, security groups block all inbound traffic and allow all outbound traffic.

### Stateful Nature of Security Groups

Security groups are stateful, meaning they remember the state of the connection and allow responses without needing additional rules.

### Custom Security Group Example

#### Inbound Rules

| Type     | Protocol | Port Range | Source    |
|----------|----------|------------|-----------|
| HTTP (80)  | TCP      | 80         | 0.0.0.0/0  |
| HTTP (80)  | TCP      | 80         | ::/0       |
| HTTPS (443) | TCP      | 443       | 0.0.0.0/0  |
| HTTPS (443) | TCP      | 443       | ::/0       |

### Design Pattern for Security Groups

A common design pattern is to organize resources into different groups and create security groups for each, controlling network communication between them.

- **Web Tier:** Only allow internet traffic over HTTPS.
- **Application Tier:** Only allow Web Tier traffic over HTTP.
- **Database Tier:** Only allow Application Tier traffic over MySQL.

This approach allows for isolation and security without relying on network configuration.

## Resources

- [AWS: Route tables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html)
- [AWS: Example routing options](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Example_Routing.html)
- [AWS: Working with routing tables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html#VPC_Route_Tables_WorkingWith)
- [AWS: Network ACLs](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_ACLs.html)
- [AWS: Security groups for your VPC](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_SecurityGroups.html)
- [AWS: How to allow users to connect on HTTP (80) or HTTPS (443)](https://aws.amazon.com/premiumsupport/knowledge-center/ec2-connect-http-https/)
