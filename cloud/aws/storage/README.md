# Amazon Web Services - Storage

There's a wide variety of storage services offered by AWS, available for you to use based on your requirements and use cases. Depending on the type of data you need to store and how durable or sensitive this data needs to be, these factors can greatly impact on your decision on which service it's better for you.

<b> AWS Storage Services</b>
- [Amazon Simple Storage Service (Amazon S3)](aws-s3.md)
- Amazon S3 Glacier
- Amazon EC2 Instance Storage
- Amazon Elastic Block Store (EBS)
- Amazon Elastic File System (EFS)
- Amazon CloudFront

<b>Transfer data methods (for storage into and out of AWS)</b>
- AWS Storage Gateway
- AWS Snowball

<b>Why so many storage services?</b>

Although they all perform the same funcion, which is to store data, each solution also provides different benefits and features such as:
- Costs variants
- Storage capacity
- Security features (such as encryption and access control)
- Varied levels of durability
- Varied levels of availability
- Read/write speed
- Accessibility
- Media type
- Auditable and traceable
- Backup and file storage

Not all of your data is to be treated exactly the same, since some of them have very specific requirements. That's why there's a lot of different storage types, to allow you to select the most appropriate service to attend your needs.

## Data Storage Caracterization

There's 3 categories of data storage:

- Block Storage: data is stored in chunks known as blocks. They are stored on a volume and attached to a single instance providing very low latency. It's similar to a DAS storage.

- File Storage: data is stored as separated files with a series of directories. It is stored within a file system and shared access ir provided for multiple users. It's similar to a NAS storage.

- Object Storage: objects are stored across a flat address space. They are referenced by a unique key and each one can also have a metadata associated to it to help categorize and identify the object.