# Amazon EC2 Instance Storage and Amazon Elastic Block Store

## Amazon EC2 Instance Store

Amazon EC2 Instance Store provides temporary block-level storage for your EC2 instances. This storage is physically attached to the host computer and is tied to the lifecycle of your instance, making it ephemeral. When you delete the instance, the instance store is also deleted.

### Ideal Use Cases

- **Cluster-based workloads**: Such as Hadoop clusters that benefit from the speed of locally attached volumes and the resiliency of replicated data.
- **Temporary storage**: For data that changes frequently, such as buffers, caches, scratch data, and other temporary content.

## Amazon Elastic Block Store (Amazon EBS)

Amazon EBS provides block-level storage that can be attached to Amazon EC2 instances. These storage devices, called EBS volumes, function similarly to external drives attached to your laptop.

### Characteristics

- **Single Attachment**: Most EBS volumes can be attached to only one EC2 instance at a time. Recently, AWS introduced the multi-attach feature for specific instance types, allowing volumes to be attached to multiple EC2 instances within the same Availability Zone.
- **Detachable**: You can detach an EBS volume from one EC2 instance and attach it to another within the same Availability Zone.
- **Persistent Storage**: EBS volumes persist independently from the lifecycle of the EC2 instances to which they are attached.

### Scaling Amazon EBS Volumes

1. **Increase Volume Size**: You can scale up the volume size up to a maximum of 16 TB.
2. **Attach Multiple Volumes**: EC2 instances can have a one-to-many relationship with EBS volumes, allowing additional volumes to be added for more storage capacity.

### Use Cases

- **Operating Systems**: Boot/root volumes to store an operating system (EBS-backed AMIs).
- **Databases**: For transactional reads and writes.
- **Enterprise Applications**: Reliable block storage for business-critical applications.
- **Throughput-Intensive Applications**: Applications performing long, continuous reads and writes.

### Amazon EBS Volume Types

| Type                         | Description                                                               | Use Cases                                                    | Volume Size   | Max IOPS/Volume | Max Throughput/Volume |
|------------------------------|---------------------------------------------------------------------------|--------------------------------------------------------------|---------------|------------------|------------------------|
| EBS Provisioned IOPS SSD     | Highest performance SSD for latency-sensitive transactional workloads     | I/O-intensive NoSQL and relational databases                 | 4 GB-16 TB    | 64,000           | 1,000 MB/s             |
| EBS General Purpose SSD      | Balances price and performance for a wide variety of transactional workloads | Boot volumes, low-latency interactive apps, development, and test | 1 GB-16 TB    | 16,000           | 250 MB/s               |
| Throughput Optimized HDD     | Low-cost HDD for frequently accessed, throughput-intensive workloads       | Big data, data warehouses, log processing                    | 500 GB-16 TB  | 500              | 500 MB/s               |
| Cold HDD                     | Lowest cost HDD for less frequently accessed workloads                    | Colder data requiring fewer scans per day                    | 500 GB-16 TB  | 250              | 250 MB/s               |

### Benefits of Using Amazon EBS

- **High Availability**: EBS volumes are automatically replicated within their Availability Zone to prevent data loss.
- **Data Persistence**: EBS volumes persist even when the associated instance is terminated.
- **Data Encryption**: All EBS volumes support encryption.
- **Flexibility**: Modify volume type, size, and IOPS without stopping the instance.
- **Backups**: Create backups of any EBS volume using snapshots.

## EBS Snapshots

EBS snapshots are incremental backups that save only the blocks that have changed since the last snapshot. These snapshots are stored in Amazon S3 and are managed through the EBS console.

### Key Points

- **Incremental**: Only the changed data is backed up.
- **Redundancy**: Snapshots are stored redundantly across multiple Availability Zones.
- **Recovery**: Snapshots can be used to create new volumes, either in the same or different Availability Zones.

## Resources

- [AWS: Amazon Elastic Block Store (Amazon EBS)](https://aws.amazon.com/ebs/)
- [AWS: Amazon EBS FAQs](https://aws.amazon.com/ebs/faqs/)
