# Amazon ElastiCache

## Introduction

Amazon ElastiCache is a service that makes it easy to deploy, operate, and scale open-source, in-memory data stores in the cloud.

This service improves the performance through caching, where web applications allow you to retrieve information from fast managed in-memory data stores instead of relying entirely on slower disk-based solutions.

```
Caching Is a process where you store frequently accessed data in a high-speed data storage. This way we'll be able to retriever information quicker and increase overall performance.
```

## Example Scenario

You have a web application that reads and writes data to persistent storage, however, those kinds of storages (like hard disks) tends to experience some fluctuations in latency, and it can affect the overall performance.

In-memory cache is useful in this scenario. It's generally used to improve read-only operations, and most of the requests received by a web site is read only operations. In-memory cache stores frequently-accessed read-only information and serve it muck quicker than having the application continually request it from the persistent data storage.

## Scaling

When the necessity to scale up your application arises, you can easily vertically scale your web server. However, you can also, instead, add a in-memory caching layer to it. By adding more web server along with an ElastiCache cluster, you can automatically grow your caching layer based on the increasing demand.

This can eliminate or reduce the need to scale up on your persistent data store.

## Engines Supported

- Memcached
- Redis

## Components

- Nodes
- Shards
- Cluster

<b>Nodes</b>

A cache node is a fixed sized chunk of secure network attached RAM, essentially the building block of the ElastiCache service.

<b>Shards (Redis)</b>

A Redis shard, also known as a node group when working with the API and CLI, is a group of up to 6 ElastiCache nodes.

<b>Cluster (Redis)</b>

A Redis cluster contains between one and 90 Redis shards, depending on if cluster mode is enabled or disabled. Data is then partitioned across all of the shards in that cluster.

<b>Cluster (Memcached)</b>

Memcached clusters are a collection of one or more cache nodes. Once you've provisioned a cluster, Amazon ElastiCache automatically detects and replaces failed nodes, which helps reduce the risk of overloaded database, and therefore reduces the website and application load times.