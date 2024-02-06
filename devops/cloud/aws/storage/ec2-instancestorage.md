# EC2 Instance Storage

These kind of volumes physically resides on the same host that provides your EC2 instances. They act like local disk drives, allowing you to store data locally.

They only provide ephemeral storage, meaning that they offer no means of persistency. Any data in those volumes is considered temporary. It's not recommended to store critical or valuable data on these kind of volumes as it could be lost should an unexpected event occur.

Your data will be lost if your instance is stopped or terminated. However, it will not be lost on restart.

The benefits of this kind of storage are:

- No additional cost (since it's already included in the price of an EC2 instance)
- I/O speed is very high
- Ideal for cache or buffer for rapidly changing data without the need for retention
- Often used within a load balancing group, where data is replicated and pooled between the fleet

Instance stores are not available in all types of instances. The capacity however will increase with the size of the EC2 instance.

Regarding security, they have the same as provided by EC2 since they are not really storage options like the others, but simply storage volumes attached to the host and is a part of the EC2 instance.

Do <b>not</b> use instance storage if:
- Data needs to be persistent
- Data needs to be accessed and shared with multiple entities