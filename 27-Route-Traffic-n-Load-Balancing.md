## Route Traffic with Amazon Elastic Load Balancing

### Understanding Load Balancing

Load balancing is essential for distributing incoming application traffic across multiple resources, such as EC2 instances, to ensure optimal performance and reliability.

#### Elastic Load Balancing (ELB) Overview

**Features and Benefits of ELB:**

1. **Managed Service:** ELB eliminates the need for managing and operating your own load balancing solution. AWS handles scaling, maintenance, and operational tasks.
   
2. **Availability:** ELB is designed to be highly available by default. It distributes traffic across multiple Availability Zones (AZs), ensuring resilience against failures.

3. **Scalability:** Automatically scales to handle varying levels of incoming traffic without intervention. This capability is crucial for maintaining application performance during traffic spikes.

4. **Health Checks:** ELB performs health checks to ensure that traffic is only routed to healthy instances. Health checks can be configured to verify various aspects of application health, such as database connectivity and service availability.

#### ELB Components

ELB consists of three primary components:

- **Listeners:** Define how traffic is forwarded to backend instances based on protocol and port. Supports HTTP, HTTPS, TCP, and UDP protocols.
  
- **Target Groups:** Define groups of resources (e.g., EC2 instances, IP addresses, AWS Lambda functions) that receive traffic from a specific listener. Each target group requires a health check configuration.
  
- **Rules:** Associate target groups with listeners based on routing conditions such as URL path, host header, HTTP method, and query string.

### Application Load Balancer (ALB)

**Key Features of ALB:**

- **Routing Based on Request Data:** Routes traffic based on HTTP request attributes such as URL path, host, headers, and methods, allowing for flexible routing to different target groups.
  
- **TLS Offloading:** Supports HTTPS traffic and manages SSL/TLS certificates, offloading encryption and decryption workload from backend servers.
  
- **Authentication:** Integrates with authentication protocols like OpenID Connect and supports user authentication before traffic reaches backend applications.
  
- **Sticky Sessions:** Maintains session persistence by directing requests from the same client to the same backend instance based on HTTP cookies.

### Network Load Balancer (NLB)

**Key Features of NLB:**

- **Protocol Support:** Handles TCP, UDP, and TLS traffic, suitable for applications that require direct network connections.
  
- **Performance:** Supports millions of requests per second with low latency, ideal for high-performance applications.
  
- **Preserve Source IP:** Passes the client's original IP address to backend applications, which is beneficial for applications requiring client IP visibility.
  
- **Sticky Sessions (Client IP based):** Maintains session affinity based on the client's IP address, useful for applications that require consistent connections from the same client.

### Selecting Between ELB Types

Choose between ALB and NLB based on application requirements:

- **ALB:** Ideal for HTTP and HTTPS traffic, provides advanced routing capabilities based on request attributes, supports TLS offloading, and integrates with various authentication protocols.
  
- **NLB:** Suitable for TCP, UDP, and TLS protocols, offers high performance with low latency, preserves client IP addresses, and supports static IP and elastic IP addresses for direct client access.

### Conclusion

Amazon Elastic Load Balancing (ELB) offers scalable, highly available load balancing solutions tailored to different application needs. By leveraging ALB or NLB, AWS users can ensure optimal application performance, scalability, and reliability without managing complex load balancing infrastructure.

### Resources

- [AWS: Elastic Load Balancer Product Comparison](https://aws.amazon.com/elasticloadbalancing/features/#Compare)
- [AWS: AWS Certificate Manager](https://aws.amazon.com/certificate-manager/)
- [AWS: Authenticate Users using an Application Load Balancer](https://aws.amazon.com/blogs/security/how-to-set-up-multi-factor-authentication-for-amazon-elb-using-rsa-securid/)
- [AWS: How AWS WAF Works](https://aws.amazon.com/waf/)
