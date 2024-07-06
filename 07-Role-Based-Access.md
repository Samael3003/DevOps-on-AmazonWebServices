# Role Based Access in AWS - Notes

## IAM Best Practices Summary

### Lock Down the AWS Root User
The root user has full access to all resources and information in your AWS account. To secure the root user:
- Do not share the root user credentials.
- Consider deleting the root user access keys.
- Enable Multi-Factor Authentication (MFA) on the root account.

### Follow the Principle of Least Privilege
Grant only the permissions necessary to perform a job. Start with minimal permissions in IAM policies and add more as required for users, groups, or roles.

### Use IAM Appropriately
IAM is used to secure access to your AWS account and resources. It is not intended for website authentication/authorization or for securing operating systems and networks.

### Use IAM Roles When Possible
Roles provide temporary credentials that expire after a set period (15 minutes to 36 hours). This is more secure and easier to manage than long-term user credentials.

### Consider Using an Identity Provider
For larger teams or businesses, manage employee identity information through an Identity Provider (IdP) such as AWS IAM Identity Center or a third-party provider. This centralizes identity management and simplifies access across multiple AWS accounts.

### Consider AWS IAM Identity Center
For organizations with many employees and AWS accounts, AWS IAM Identity Center allows users to sign in with a single set of credentials. Benefits include:
- Centralized access to all assigned accounts and applications.
- Integration with third-party IdPs for user and group synchronization.
- Separation of duties between IdP and AWS, enhancing cloud access management.

## Resources for Further Reading
- [AWS: Security Best Practices in IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html)
- [How to Create and Manage Users within AWS IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)
