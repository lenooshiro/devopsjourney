# Amazon VPN and Direct Connection

## Introduction

VPN (Virtual Private Networks) is a way to connect two remote networks across the internet.
Amazon offers two kinds of VPN services:
- VPN site-to-site: to securely connect your on-premises network or branch office to a VPC
- Client VPN : to securely connects users to AWS or on-premises network

## VPN Site to Site

To configure a VPN Site-to-Site, first you need to create a Virtual Gateway and attach it to your VPC. It works the same way as an Internet Gateway, allowing public subnet to communicate with the internet.

In the datacenter, we need to install a Customer Gateway, which will be our endpoint to stablish a connection with the Virtual Gateway. It can be a piece of hardware of a software virtual appliance, but it need to be hosted within the datacenter.

During the creation of the Virtual Gateway, you'll need to provide some information such as the Customer Gateway IP address and the type of IP routing (static or dynamic).

After both gateways are installed, we can initiate the VPN Tunnel, which is an encrypted link where data can pass from the customer network to or from AWS/VPC. It can only be initiated from our Customer Gateway side.

The next step if to change the private subnet's Route Table, adding a route saying that any data going to the datacenter's IP, will target the Virtual Gateway.

Then we need to configure the Security Group of the private subnet. If you want to allow SSH or RDP access coming from the datacenter, the additional rule would be similar to the following:

```
SSH     TCP     22      192.168.0.0/16
RDP     TCP     3389      192.168.0.0/16
```
<i>with 192.168.0.0/16 being our datacenter ip network</i>

## Direct Connect

While the VPN connection uses the internet to stablish a connection with your VPC, the Direct Connect doesn't. Instead, it uses a private infrastructure to connect directly with your VPC, so there's no public network involved.

The difference in architecture is that there's an entity in between your datacenter and AWS infrastructure. This entity is an AWS Partner that holds the infrastructure of the Direct Connect. Inside of it, there's the partner router and an aws router.

The way it works is as follows:

- From your datacenter, you stablish a private connection to the Direct Connect infrastructure, connecting to the partner's router
- From the partner's router, it will then connect with the aws's router
- From the aws's router, it will connect to AWS infrastructure

There's two types of connection interfaces that you can configure, public and private. The difference is at the last part of the connection.

If it's private, aws's router will connect directly to a virtual gateway that you created within your VPC.

If it's public, aws's router will connect to the region where you have your public resources, and will be able to access them from there.