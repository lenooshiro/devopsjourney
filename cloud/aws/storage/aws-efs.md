# AWS Elastic File System

## Introduction

Amazon EFS is a file-level storage, fully managed, highly available and durable service that, unlike EBS, supports access by multiple EC2 instances simultaneously.

It allows you to create shared file systems that can easily scale to petabytes in size with low latency access.

That way, it provides the ability for users to browse cloud network resources. EC2 instances can access Amazon EFS instances using configured mount points.

Since it's a managed service, there is no need for you to provision any file servers to manage the storage elements or provide any maintenance of those servers. This makes it a very simple option to provide file-level storage within your environment.

It supports both NFS versions 4.1 and 4.0, and uses standard file system semantics such as strong consistency and file locking.

As the file system can be accessed by multiple instances, it makes it a very good storage option for applications that scale across multiple instances allowing for parallel access of data. The EFS file system is also regional, and so any application deployments that span across multiple availability zones can all access the same file systems providing a level of high availability of your application storage layer