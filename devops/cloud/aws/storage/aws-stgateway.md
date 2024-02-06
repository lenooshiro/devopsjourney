# AWS Storage Gateway


## Introduction
AWS Storage Gateway allows you to provide a gateway between your own datacenter storage system and AWS S3 or Glacier.

It's a software that can be installed within your datacenter, which allows integration between your on-premise storage and AWS.

This allows you to scale your storage requirements both securely and cost efficiently.

## Configurations

There's three types on configurations available:

### File Gateways

- Allows you to store your files within AWS S3
- Ability to mount of map drives to an S3 bucket as if it was shared locally
- A local cache is also provisioned for accessing your most recently accessed files to optimize latency

On first configuration, you must associate it with a S3 bucket, then the gateway will present it as a NFS v3 or v4.1 file system.

### Volume Gateways

<b>Stored Volume Gateways</b>
- Used to backup your local storage volumes to S3
- Your entire local data will remain on-premise
- Volumes created by Volume Gateways are mounted as iSCSI devices.

As data is written into these devices, the data is actually written on your local storage, but then the Storage Gateways asynchronously copies this data to AWS S3 as EBS snapshots.  

<b>Cached Volume Gateways</b>
- Similar to Volume Gateways, but the primary data storage is S3 rather than local storage.
- Local data storage is used for buffering and a local cache for recently accessed data.
- During the creation, they are presentes as iSCSI volumes. You also need to select some local disks to act as local cache and buffer for data waiting to be uploaded to S3.

<b>Gateway VTL (Virtual Tape Library)</b>
- Allows you to backup data to S3
- Use AWS Glacier for archiving
- Your applications and backup software can mount tape drives using the Media Changer as an iSCSI device

Virtual Tape Library is a cloud based tape backup solution, allowing you to replace your physical tape backup infrastructure components with virtual ones.