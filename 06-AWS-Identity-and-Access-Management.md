# AWS Identity and Access Management (IAM) - Notes

## What is IAM?
IAM is a web service that enables you to manage access to your AWS account and resources. It provides a centralized view of who and what are allowed inside your AWS account (authentication), and who and what have permissions to use and work with your AWS resources (authorization).

### Key Features of IAM
- **Global Scope**: IAM configurations can be seen and used from any AWS Region.
- **Integration**: IAM is integrated with many AWS services by default.
- **Password Policies**: Establish complexity requirements and mandatory rotation periods for passwords.
- **MFA Support**: Enhance security by enabling multi-factor authentication.
- **Identity Federation**: Allows users with existing passwords from corporate networks or internet identity providers to gain temporary access.
- **No Additional Cost**: IAM is available to all AWS customers at no additional charge.

## IAM Users
An IAM user represents a person or service that interacts with AWS. Users have a name and a set of credentials, and any activity done by that user is billed to your account.

### IAM User Credentials
- **AWS Management Console Access**: Username and password.
- **Programmatic Access**: Access keys for AWS CLI and AWS API.

## IAM Groups
An IAM group is a collection of users that inherit permissions assigned to the group. This simplifies permission management and is scalable as the number of users increases.

### Benefits of IAM Groups
- Easier permission management for multiple users.
- Organize users by job function (e.g., developers, security, admins).
- Users can belong to multiple groups.
- Groups cannot contain other groups.

## IAM Policies
IAM policies are JSON documents that define permissions to AWS services and resources. Policies are attached to IAM users, groups, or roles.

### Policy Structure
- **Version**: Specifies the policy language version.
- **Effect**: Defines whether the statement allows or denies access.
- **Action**: Describes the specific actions that will be allowed or denied.
- **Resource**: Specifies the object(s) the statement covers.

### Example Policies
**Admin Access Policy**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "*",
            "Resource": "*"
        }
    ]
}
```

**Granular Access Policy**
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "iam:ChangePassword",
                "iam:GetUser"
            ],
            "Resource": "arn:aws:iam::123456789012:user/${aws:username}"
        }
    ]
}
```

## Resources for Further Reading
- [What is IAM?](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html)
- [AWS IAM Identities](https://docs.aws.amazon.com/IAM/latest/UserGuide/id.html)
- [Access Management with AWS IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/access.html)

