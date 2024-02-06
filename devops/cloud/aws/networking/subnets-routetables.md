# AWS Networking - Subnets and Route Tables

## Introduction

Subnets allows you to segment your VPC into multiple different networks by defining a range of IP adresses within your VPC. You launch AWS resources such as EC2 instances into those subnets. It's used to create a better management for your resources or to isolate certain resources from the others.

## Creating a VPC Subnet

When creating a VPC, you need to give it a name and a CIDR block adress. 

> A CIDR block is a collection of IP addresses that share the same network prefix and number of bits. It can have a subnet mask between a range of IPs from /16 to /28.

### Types of Subnets

For the subnets, you need to give them a CIDR block address as well. You can create two types of subnets:

- Public: this subnet is accessible from outside of your VPC. They have two IP addresses, the internal IP address and the public IP address. 

- Private: in this subnet any resources created within a private subnet are inaccessible by default from the internet. They only have the internal IP address.

Every subnet that you create is, by default, a private subnet. To make it public, you need to configure the following:

- add an Internet Gateway (a component managed by AWS that attaches to your VPC and act as a gateway between your VPC and the outside world/internet)
- add a route to the public subnet's route table

Each subnet has a route table by default, and can only be associated to one (but a route table can be associated to multiple subnets). Every route table contains a Destination field and a Target field and there's already an entry there with the local route, this enables your subnets to communicate to each other. Add a new route with the values "0.0.0.0" in the Destination field and the Internet Gateway in the Target field, this will essentially make the Subnet able to communicate with the Internet.

## Reserved IPs

When defining a CIDR block adress, you must have in mind that AWS reserve some of the first addresses for specific uses.

For example: let's define a subnet with mask /24

```
Subnet: 10.0.1.0/24
Total ips: 256
Total usable ips: 251

Reserved IPs
10.0.1.0 = Network
10.0.1.1 = AWS Routing
10.0.1.2 = AWS DNS
10.0.1.3 = Future uses
10.0.1.255 = Broadcast address
```