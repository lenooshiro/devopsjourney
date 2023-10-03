# Amazon DynamoDB

## Introduction

Amazon DynamoDB is a NoSQL database, which means it doesn't use the common Structured Query Language (SQL). It's a type of database that uses key-value store, a collection of items or records that you can look up for data using the primary key for each item or through the use of indexes.

Like RDS, DynamoDB is also a fully managed service, where many of the administrative tasks are managed by AWS, such as backups and security patches.

## Creating and Configurind a Database

Since it's a fully managed service by AWS, creating a database is as simply as the following steps:

- Set tables up
- Configure provisioned throughput

The throughput means the level of read/write capacity that you want AWS to reserve for your tables. You will be charged for the amount of throughput configured plus the total amount of storage used by your data.

DynamoDB is also schemaless, there's no strict design;schema that every record must conform to, as long as there's a proper key, every record can contain a varying set of attributes. Every record don't need to have the same attributes or even the same number of attributes.

## Read/Write Capacity Modes

When creating your table, you will need to choose one of the following modes:

- Provisioned
- On-Demand

<b>Provisioned</b>

Allows you to choose sets of read/write per second. It's measured in Read/Write Capacity Units (RCU and WCU) with each action using 1 or more RCU/WCU. Generally, you use this option if you already knows how much workload of traffic you're working with.

<b>On-Demand</b>

Does not provision RCU/WCUs, they are scaled on demand. It's usually used when you don't know how much workload you're working with, and it's not much cost-effective. With time, you'll understand how much load you have and you can change to Provisioned Mode later.