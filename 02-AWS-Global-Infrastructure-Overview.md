# AWS Global Infrastructure Overview

## Infrastructure Overview
AWS Global Infrastructure forms the foundation of AWS cloud applications, consisting of physical infrastructure such as data centers and networking connectivity. This infrastructure is organized into Regions and Availability Zones (AZs).

## Regions
AWS Regions are geographic locations worldwide where AWS hosts its data centers. Each Region is independent and identified by a unique geographical name and Region code. Examples include:

- `us-east-1`: Northern Virginia, USA
- `ap-northeast-1`: Tokyo, Japan

### Choosing the Right AWS Region
When selecting an AWS Region for your applications and workloads, consider the following factors:

1. **Latency**: Choose a Region close to your user base to reduce wait times and improve user experience, especially for latency-sensitive applications like gaming and IoT.

2. **Price**: AWS prices vary by Region due to factors like internet connectivity, real estate costs, and local economic conditions.

3. **Service Availability**: Not all AWS services are available in every Region. Check AWS documentation for service availability in your chosen Region.

4. **Data Compliance**: Ensure the Region meets any regulatory requirements for storing customer data in specific geographic locations.

## Availability Zones (AZs)
Inside each Region are clusters of Availability Zones. An AZ consists of one or more data centers with redundant power, networking, and connectivity. AZs are identified by appending a letter to the Region code. Examples include:

- `us-east-1a`: An AZ in the Northern Virginia Region
- `sa-east-1b`: An AZ in the São Paulo Region

AZs are discrete facilities with undisclosed locations and are connected via high-speed, low-latency links.

## Scope of AWS Services
AWS services can be deployed at the AZ, Region, or Global level. The scope of a service affects how you architect your application:

- **Region-scoped services**: Operate across an entire Region. AWS handles actions to increase data durability and availability.
- **AZ-scoped services**: Require specifying an individual AZ for deployment. You are responsible for ensuring data durability and high availability.

## Maintaining Resiliency
To ensure high availability and resiliency of your applications:

- Use Region-scoped, managed services whenever possible, as they come with built-in availability and resiliency features.
- For AZ-scoped services, replicate workloads across multiple AZs. Using at least two AZs ensures that if one AZ fails, your application can continue running in another AZ.

## Conclusion
AWS Global Infrastructure, with its Regions and Availability Zones, provides a robust and flexible foundation for deploying cloud applications. By understanding the structure and scope of AWS services and considering key factors such as latency, price, service availability, and data compliance, you can effectively architect resilient and high-performing applications on AWS.
