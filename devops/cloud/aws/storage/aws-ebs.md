# AWS Elastic Block Store


## Introduction

Amazon EBS provides storage to your EC2 instances via EBS volumes, which are different from instance store volumes.

It provides durable and persistent block level storage. They can be attached to your EC2 instances and are primarily used for data that must be quickly accessible and requires long-term persistance.

It's particularly well-suited for primary storage for file systems, databases or any applications that requires granular updates and access to raw, unformatted, block-level storage.

Although an EBS can only be attached to a single EC2 instance, you can connect multiple EBS volumes to the same instance.

## Persistence and Backups

Since EBS volumes are persistent, you don't need to worry if your instances are intentionally or unintentionally stopped, restarted or even terminated.

EBS volumes are independent of the EC2 instance, meaning it's a different resource. It's logically attached to the instance, not directly/physically. 

EBS also offers the ability to provide backups of the entire volume. These backups are known as snapshots and you can manually invoke a snapshot of your volume at any time

You can also use Amazon CloudWatch events to perform an automated schedule of backups to be taken at a specific date or time that can be recurring.

These snapshots are then stored on Amazon S3 and are incremental, meaning each subsequently snapshot will only copy data that has changed since the last snapshot was taken.

Once you have a snapshot of an EBS volume, you can then create a new volume from that snapshot.

## Types of EBS

There are two types of EBS volumes available. Each have their own characteristics:

- SSD (solid state drive)
- HDD (hard disk drive)

<b>SSD </b>

Better suited for scenarios where you need to work with smaller blocks of data for transactional workloads, or as boot volumes for your EC2 instances.

<b>HDD</b>

Designer for workloads that requires higher rate of throughput, such as for processing big data or for logging purposes. Essentially, working with large blocks of data.