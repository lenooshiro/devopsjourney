# Amazon Quantum Ledger Database (QLDB)

## Introduction

QLDB is a fully managed serverless database service, designed as a ledger database. To put it simply, a ledger database is one used to store the current and historical value of a company's financial data.

Amazon QLDB allows you to store this kind of data in a immutable, transparent and encrypted way using SHA-256, making it highly secure, also QLDB is serverless, all the infrastructure administration, maintenance and scaling is managed by AWS. 

You can also use a database journal that is configured as append-only. It's a immutable transactional log that records all entries in a sequenced manner over time.

## Similarities with blockchain

In blockchain technology a ledger is also used, however in blockchain that ledger is also distributed across multiple hosts is a decentralized environment, while in QLDB, it't managed by a central and trusted authority.

This removes the need of a consensus of everytone across the network, which is a requirement in blockchain.

## Structure

In QLDB, data is placed into tables of Amazon Ion documents.

> Amazon Ion: is a data serialization format created by Amazon. It's a superset os JSON, meaning any JSON document is also a valid Ion document.

Tables are made of a group of Ion documents and their revisions. A revision is basically an update made by someone, and QLDB store this update in addition to all the previous ones in order to keep an audit history of all those changes. This allows you to easily query document history across all document iterations.

Changes to a document is made via database transactions. Amazon QLDB will read data, perform the update as required and then save the changes to the journal.

Each time a change is added to the journal, a sequence number is added to identify its place in the change history. A SHA-256 is used for verification purposes, which creates a cryptographic digest file of the journal.

This can be used to verify the integrity of the changes, helping ensure that the data within the document has not been altered.

## Storage

Amazon QLDB uses two methods of storage:

- Journal storage: storage used to hold the history os changes that have been made within the ledger database.

- Index storage: storage used to provision the tables and indexes within the ledger database, and it's optimized for querying.

Being managed by AWS, both storages are managed for you so there's no need to select any options during the creation of the database.

## Integration with Kinesis

Amazon Kinesis is used to collect, process and analyze real-time streaming data, such as application logs or website clickstreams. It enables you to process and analyze data as it arrives and respond in real time, without the need to wait until all your data is collect before the processing can begin.

You can use QLDB stream to capture all changes made to the journal and feed them to an Amazon Kinesis data stream in near real time.