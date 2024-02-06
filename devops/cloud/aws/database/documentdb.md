# Amazon DocumentDB (for MongoDB)

## Introduction

AWS DocumentDB is a document database service that is built for JSON data management. Is provides high scalability, high availability and high speed. Those documents can be queried and indexed to improve the speed of retrieving data thanks to their data indexed structure.

DocumentDB can scale compute and storage separately. This approach creates a flexible scaling pattern allowing to scale resources as you need to. DocumentDB will automatically increase your storage by 10GB in size, up to a maximum of 64TB.

It's also compatible with MongoDB. Since it's also a document database, you can easily migrate from MongoDB to DocumentDB using the AWS Database Migration System (DMS).

## Architecture

Architectually, DocumentDB is similtar to Neptune. The core component is a cluster, which is composed by a single or multiple DB instances, up to 16 in total (one is the primary instance and the others are replicas). Those instances can be distributed across different availability zones but need to be within a single region.

In this cluster there's a shared cluster storage volume that supports every instance within the cluster, meaning every instance see the same volume.

There will only be one single primary DB instance performing write operations in the cluster at any time. The remaining instances in the cluster will all be read replicas, serving only read requests.

Data synchronization is maintained synchronously between both the primary instance and each replica in the region.

## Connectivity

DocumentDB uses endpoints to connect to different components of your database. Endpoint is an URL address with an identified port that points to your infrastructure, and there's 3 different endpoints:

- Cluster endpoint: points directly to the primary DB instance and should be used by any applications that require both read and write access to the database. When/If the primary instance fails, it'll point to the new primary instance (a replica will be promoted to a primary one, or if there's no replica, DocumentDB will create a new instance).

- Reader endpoint: allows conenctivity with any read replicas configured, and applications can use this endpoint for read access (typically when performing a query). There's only one single read endpoint even if there's multiple replicas, DocumentDB will manage the forwarding of any requests onto specific read replicas

- Instance endpoint: every instance will have a unique endpoint to allow you to direct certain traffic to a specific instance. You might do this for load balancing reasons, for example.

## Backups

DocumentDB performs automatic backups for you based on a shcedule configured during the creation of the database. There's something called <b>point-in-time-recovery</b> that allows you to restore back to any point in time during your retention period. As part of this process, DocumentDB captures any transaction logs that have been created during updates.

The backups are automatically stored on Amazon S3.

The automated backups are performed daily and the retention period can be set between 0 to 35 days. It it's set to 0, then automatic backups will be disabled. You can define when the daily backup will occur in the Backup Window option.