# Amazon Redshift

## Introduction

Amazon Redshift is a fast, fully-managed, petabyte-scale data warehouse. And it's designed for high performance and analysis of information capable of storing and processing petabytes of data and provide access to this data, using your existing business intelligence tools, using standard SQL.

It operates as a relational database management system (RDMS) and its compatible with other RDMS applications. Redshift itself is based upon PostgreSQL but contains some differences.

## Data Warehouse

A data warehouse is a central repository of information that can be analyzed to make more informed decisions. Professionals who need to extract information from data to make decisions, such as business analysts and data engineers/scientists, can access the data through business intelligence (BI) tools, SQL clients and others analytics applications.

## Data Operations

Data warehouses need to be able to store huge amounts of data, and needs to performs differents operations, such as:

- data cleansing: to identify, correct, replace or remove incomplete records from a table or record set
- ETL (extract, transform and load)

## ETL

- extraction: retrieving data from one or more resources
- transformation: process of mapping, reformatting, conforming, adding meaning and more to prepare data to be consumed
- loading: insert the transformed data into the target database store/warehouse

## Components

- Cluster: core component of a Redshift service. It run its own Redshift engine that contains at least 1 database. It's composed by a group of nodes with at least 1 node.

- Nodes: nodes are processing units that contains its own CPU, storage and memory according to their types, with each one offering different perfomances. If there's more than 1 node in a cluster, then we also have a Leader Node. The leader is responsible for coordinating communication between your computer nodes and external applications accessing your Redshift data warehouse.

- Node slices: each node is split into slices, each with their own share of memory and disk. They process operations given by the Leader Node, so they can perform parallel operations across all slices and nodes at once for the same query.

Each node has their own capacity, and this determines how many slices each one can be split into.

## Communication

The various external applications (analytics and business intelligence tools) can communicate with Redshift through standard ODBC interface (open data base connectivity) or through JDBC (java data base connectivity) for PostgreSQL.

## Integration

Redshift also integrates with Cloudwatch, allowing you to monitor performance of your physical resources, such as CPU utilization and throughput.

Any data related to query or load performance is only accessible from within Redshift console.