# Introduction to Amazon VPC

## What is a VPC?

A Virtual Private Cloud (VPC) is an isolated network you create within the AWS cloud, similar to a traditional network in a data center.

### Key Components to Create a VPC

1. **VPC Name:** Choose a name for your VPC.
2. **Region:** Select a region for your VPC. Each VPC spans multiple Availability Zones (AZs) within the chosen region.
3. **IP Range:** Specify an IP range in CIDR notation for your VPC. Each VPC can have up to four /16 IP ranges.

Using this information, AWS provisions a network and IP addresses for that network.

## Creating a Subnet

After creating a VPC, you need to create subnets within this network. Subnets are smaller networks inside your base network, similar to virtual area networks (VLANs) in traditional on-premises networks.

### Key Components to Create a Subnet

1. **VPC Association:** Choose the VPC where your subnet will reside (e.g., VPC 10.0.0.0/16).
2. **Availability Zone:** Select the Availability Zone for your subnet (e.g., AZ1).
3. **CIDR Block:** Specify a CIDR block for your subnet, which must be a subset of the VPC CIDR block (e.g., 10.0.0.0/24).

When you launch an EC2 instance, it will reside within a subnet located inside the chosen Availability Zone.

## High Availability with a VPC

To maintain redundancy and fault tolerance, create at least two subnets in different Availability Zones. This ensures that if one AZ fails, resources in the other AZ are available as a backup.

## Reserved IPs

AWS reserves five IP addresses in each subnet for routing, DNS, and network management purposes.

For example:
- VPC with IP range 10.0.0.0/22 includes 1,024 total IP addresses.
- Divided into four subnets, each with /24 IP range (256 IP addresses).
- Only 251 IP addresses are usable per subnet due to the reserved five IP addresses.

A common practice is to create a VPC with a /16 IP range and subnets with a /24 IP range to ensure ample IP addresses.

## Gateways

### Internet Gateway

To enable internet connectivity for your VPC, create an internet gateway. This connects your VPC to the internet, similar to how a modem connects your home network to the internet. Internet gateways are highly available and scalable. After creation, attach it to your VPC.

### Virtual Private Gateway

A virtual private gateway (VGW) connects your AWS VPC to another private network. Once attached to a VPC, it acts as an anchor on the AWS side of the connection. You'll need a customer gateway (CGW) on the other side, which can be a physical device or software application. Once both gateways are in place, establish an encrypted VPN connection between them.

## Resources

- [AWS: VPC with public and private subnets (NAT)](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Scenario2.html)
- [AWS: Custom route tables](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Route_Tables.html)
- [Customer Gateway](https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html)
- [AWS: What Is Amazon VPC?](https://aws.amazon.com/vpc/)
- [AWS: VPCs and subnets](https://docs.aws.amazon.com/vpc/latest/userguide/VPC_Subnets.html)
