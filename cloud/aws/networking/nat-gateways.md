# Amazon NAT Gateways

## Introduction

A NAT Gateway is a component of your VPC that allows private instances to be able to access the internet while blocking connections initiated from the internet.

This basically means that if a EC2 instance that is deployed in a private subnet needs to download some packages from the internet, it can do so through a NAT Gateway configured in a public subnet. The gateway will act as an intermediate between the internet and the private component so it can receive the package from the internet without being exposed to it.

It's important to notice that the NAT Gateway will not accept any inbound communication initiated from the internet, only outbound communication originating from within the VPC.

The NAT Gateway is a component managed by AWS, so you don't need to provision the instance. Just create the NAT Gateway and specify which subnet it will reside in and the IP address, AWS will manage all other configurations.