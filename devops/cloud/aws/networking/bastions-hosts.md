# Amazon Bastion Hosts

## Introduction

Bastion Hosts are a component of VPC that allows specific users (such as engineers) to have access to components within a private subnet, for example EC2 instances.

The Bastion Host resides in a public subnet and it's basically an EC2 instance. This instance need to have its own security group where it allows SSH connection from the engineer's specific IP, so it can act as a bridge between the engineer and the resources inside the private subnet.

The Bastion Host Security Group should have a rule similar to the following:

```
SSH     TCP     22      81.140.246.47/32    SSH Inbound from Engineer IP
```

<i>The IP above is just a random IP to better illustrate this example.</i>

After that, we need to configure another Security Groups, but now for the resources inside the private subnet. This rule is to allow SSH connection from the Bastion Host.

```
SSH     TCP     22      vgw-qweasdzxc       SSH Inbound from Bastion Sec. Group
```

<i>The ID above is a random one to represent the Baston Host ID.</i>

Now, if the engineer wants to connect to an EC2 instance within the private subnet, he'll first need to connect via SSH to the Bastion Host, and then SSH again to the EC2 instance.

It's worth noting that you should not store keys inside the Bastion Host when connecting to the resources inside a private subnet. The best way to do this is to use SSH Agent Forwarding, it will connect using the private keys stored in the engineer's pc/client, rather than in the Bastion Host.