# Security (Amazon IAM)

## Introduction

Amazon IAM (Identity and Access Management) service is a key security feature that allows you to manage specific access controls within your environment for your users.

Essentially, it gives us the ability to manage, control and govern authentication, authorization and access control mechanism of identities to your resources within your AWS account.

## Authentication Process

The process where Amazon gives access to a user is based on two stages:

- Identify who the user is by, for example, presenting his username

    - The identification within IAM is unique to the user, meaning it's not possible to have 2 user accounts with the same name within the same AWS account.

- Verify that the user is who he claim that he is

    - This is achieved by supplying additional data. When using a username, we can verify by supplying the password.

Authorization defines what an entity can access within your AWS account once it has been authenticated. For example, the user's list of permissions for specific AWS resources, such as Full Access to EC2 or Read-Only to RDS.

Access Control is he mechanism to access a secured resource. For example:
- Username and password
- Multi-Factor Authentication (MFA)
- Federated Access

MFA is an additional safety step to the username and password. Federated Access allows users external to AWS to access resources without having to supply AWS credentials from a valid IAM account. They provide credentials from identity providers such as Azure Active Directory, for example.

## Features

AWS IAM has a lot of features used to centrally manage and control security permissions for any identity requiring access to your AWS account and resources.

- IAM Resources: provides a summary overviews of your IAM resources using a simple count of the number of users, user groups, roles, customer-managed policies and identity providers you have configured

- Best Practices: provides a list of IAM best practices that AWS recommends with links on how to implement them.

From the Access Management option, on the side menu, you'll find:

- Users: the users objects representing a person or an identity users by an application. They are unique values with an Amazon Resource Name (ARN) associated to each one of them. You can also configure a MFA for those users, which will add an extra security layer asking for a random 6 digit number form a linked MFA device after their usual password.

- User Groups: those are objects like users, but they are not used in any authentication process. They are a group where users can be associated with and have policies that will allow of deny access to AWS resources.

- Roles: are used to allows users, applications and other aws services to receive a set of temporary IAM permissions to access AWS resources. It's similar to an user objects, it's an identity wiith permissions policies that determines what the identity can and can not do. However, the roles don't define a single person, they are designed to be assumed by any identity or service that needs to temporarily acquire a set of permissions. Additionally, roles don't have passwords associated with their identities, they are just assumed as long as you have permissions for that.

- Policies: they are written as JSON documents and are used to define what can and can't be accessed. You can attach policies to users, roles and user groups. You can use managed policies or inline policies:
    - Managed policies: it's a library of usable policies and offers two options: AWS Managed Policies (predefined policies granting access to AWS services) and Customer Managed Policies (policies created and written by the customer/administrator)
    - Inline policies: not stored in a library, intead it's written and explicitly embedded within a user, roule ou user group. As a result, the same policy can't be applied to another identity like a Managed Policy can.

- Identity Providers: allows external access (Federated Access) from trusted sources such as Google Accounts or Azure Active Directory

- Password Policies (Account Settings): you can enforce a password policy, and it's a best practice to do so. Should be used to enforce the minimum security requirements to be met for any password standard that your organization might have to adhere to. It's applied to all IAM users in your account.

- Security Token Service Endpoints: it allows you to request temporary and limited-priviledge credentials for both IAM users and federated users. STS Endpoints provides a list os regions that are eithers activated or deactivated for STS. By default, they are all activated, but it's recommended to deactive the ones you are not going to use.

From the Access Reports option, you'll find:

- Access Analyzer: this page allows you to generate "findings", meaning it will show a list of occurences when a policy on a resource within your zone of trust allows access from outside this zone of trust. For example: a bucket allowing a different account to upload objects will be shown here so you can be aware of that access.

- Credential Report: allows you to generate and download a CSV file containing a list of all your IAM users and their credentials. This provides a quick and easy way to review your accounts and the last time they were used, when was the last time the password was changed and if they have MFA enabled.

- Organizational Activity: if using AWS Organizations, allows you to select a Organizational Unit (OU) or account to view its service activity over the past 365 days. You can see which user had which activity, in addition to what they ahve accessed over a given time frame.

- Service Control Policies: linked with the Organizational Activity, it lists any Service Control Policies that are applicable to the account and the number of identities affected. SCP are different from identity-based policies as they do not grant permission themselves, instead they are used by AWS Organizations to set a boundary of permissions for AWS accounts. For example: if a user has full access to S3, RDS and EC2 and a SCP associated with that AWS account denied access to S3, then that user would only be able to access RDS and EC2. SCP have the overriding precedence and determine the maximum level of permissions allowed.