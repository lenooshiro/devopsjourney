# Amazon Security Groups

## Introduction

Security groups are similar to network access controllers where they filter traffic both inbound and outbound, with the difference that NACLs works at the subnet level, and Security Groups works at the instance level.

You can configure a Security Group the same way as configuring a NACLs, they are similar to a table containing some fields where you can specify what is allowed. Be aware that this table doesn't have an Allow/Deny field, by default if there's a rule then it's allowed, if not then it's dropped.

## Example Scenario

Let's imagine a case where we have 3 private subnets, some resources deployed in each one of them and they are all associated with the same NACLs.

Private Subnet A (PS-A)
```
IP: 10.0.1.0/24
Resources: 3 EC2 intances
```

Private Subnet DB (PS-DB)
```
IP: 10.0.2.0/24
Resources: 2 Aurora DB instances
```

Private Subnet B (PS-B)
```
IP: 10.0.3.0/24
Resources: 3 EC2 intances
```

NACLS rules:
```
10 ALL TCP in 0 - 65535 and from source 0.0.0.0 is allowed
00 ALL traffic with all protocols in all ports from source 0.0.0.0 is denied
```

What we want to do is allow every instance in PS-A to communicate with PS-DB while denying any communication from PS-B to PS-DB. The way we can do it is creating a Security Group that allows traffic from PS-A IP and associate with the instances in PS-DB.

The Security Groups would have a rule added such as:
```
MYSQL/Aurora TCP 3306 10.0.1.0/24
```

With this, PS-A can communicate with PS-DB, while PD-B can not.