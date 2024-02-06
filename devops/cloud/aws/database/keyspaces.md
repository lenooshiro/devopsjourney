# Amazon Keyspaces (for Apache Cassandra)

## Introduction

```
Apache Cassandra: is a free open-source, distributed, wide column store, NoSQL database management system designed to handle large amounts of data across many commodity servers, providing high availability with no single point of failure
```

Keyspaces is a serverless and fully managed service, that is highly scalable, highly available and compatible with Apache Cassandra. This means any tools that you already use with Cassandra can be used with Keyspaces normally.

Since it's serverless, this means that administrative tasks such as provisioning, patching and applying updates are made by AWS and also has unlimited throughput, since it's designed for massive-scale solutions.

It's a great choice if you need to build applications where low latency is essential or if you want an easier way to manage your already existing cassandra databases.

## Components

In Cassandra, a keyspace is a group of tables that are related and used by your applications to read and write data. It also helps define how your tables are replicated across multiple nodes in the cluster. In AWS Keyspace, since it's a fully managed service, this entire layer of tables is administered by AWS.

For Keyspaces, tables are where your data entries are stored. In each table there's a primary key (which consists of a partition key) and one or more columns. When a new table is created, encryption at rest is automatically created enabled and any client that wants to connect with the tables will require a TLS connection.

## Throughput

Keyspaces offer two capacity modes for throughput to allows you to customize how it's managed, helping you to optimize it for your workloads:

<b>On-demand</b>

It's the default option when creating your database and it's capable of processing thousands of requests per second.

The pricing is based on the number of reads and writes made in your tables by your applications, meaning you only pay for what you're using.

It's able to scale to any increased throughput that the database has previously reached, however if any additional throughput is needed, Keyspaces is able to respond to meets the requirements of the applications.

It's a good option if you are dealing with unknown of unpredictable workdloads.

<b>Provisioned</b>

Allows you to specify your predicted number of reads and writes per second, which would enable your tables to meet throughput speeds faster than on-demand.

It's a good option if you are dealing with predictable workdloads.

You can also use automatic scaling if you experience fluctuations in your workload, or as your database naturally grows, using upper and lower thresholds.

## Cassandra Query Language (CQL)

Keyspaces uses CQL, a language that is similar to SQL. You can run queries from the Keyspaces dashboard (within the AWS management console), use the CQL Editor or use a CQLSH client.

You can also run programatically using Apache 2 Cassandra Client Driver.