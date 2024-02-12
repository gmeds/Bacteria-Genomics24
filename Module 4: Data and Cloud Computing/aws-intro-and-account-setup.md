# AWS Services Overview: A Spectrum of Cloud Solutions

AWS offers a vast array of services, categorized into several core domains, catering to diverse computing needs. Here's a glimpse into some prominent categories and their specific services:

**Compute:**

    - Amazon EC2: Virtual servers in the cloud, scalable and customizable for various workloads.
    - Amazon Lightsail: Simplified virtual servers for beginners, pre-configured for basic needs.
    - Amazon ECS & EKS: Container orchestration services for managing containerized applications.
    - AWS Lambda: Serverless compute service for running code without managing servers.

**Storage:**

    - Amazon S3: Scalable object storage for various data types, from website assets to backups.
    - Amazon EBS: Block storage for persistent data attached to EC2 instances.
    - Amazon Glacier: Deep archive storage for long-term data retention at extremely low costs.

**Databases:**

    - Amazon RDS: Managed relational database service for popular engines like MySQL, PostgreSQL, and Aurora.
    - Amazon DynamoDB: NoSQL database with high performance and scalability for big data workloads.
    - Amazon Redshift: Data warehouse service for large-scale data analytics and business intelligence.

# Signing in to AWS web services
The first step to working with Amazon is to sign in to their services if you have never had an account.
## What you need:
- Email address
- Payment details such as credit card

**Note: We will mostly be using the free tier for this. So you will not be charged.**
Access the link to AWS here https://portal.aws.amazon.com/billing/signup#/start/email

![image](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/8d0c9551-3013-4dc7-b77f-d394877f6717)

Enter your email details and a preferred AWS account name, then complete the sign-in process. You will also need to enter payment details

You will always be required to verify your account. Amazon will inform you of the details they require through their support. I would rate their support as excellent.
Once you have signed in, let us take time to explore the AWS management console:

![ENV SETUP(2)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/cdfcb7ab-07ae-4843-a580-3905fb85f5cf)


What you will find when you log in to your account:

- **Unified search and navigation:** Easily find the specific service or resource you need.
- **Recently Visited Services:** Located below the search bar, this section saves you time by displaying services you've recently accessed, making it easy to jump back in without having to search again.
- **Services Drop-Down Menu:** This menu within the toolbar provides a comprehensive list of all available AWS services, making it convenient to navigate and explore different options.
- Support Drop-Down Menu: This menu offers helpful links to various support resources, including documentation, tutorials, FAQs, and contact information. Whether you need quick answers or in-depth guidance, this menu helps you find the support you need.
- **Region Drop-Down Menu:** By switching between regions in this menu, you can manage resources and view information specific to your desired geographical location, ensuring compliance with data residency requirements or optimizing performance based on proximity.

If you click on the services drop-down menu, you will most likely find an interface like this:

![image](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/4d741244-4974-4b29-b079-f22eccc1f6cd)

## Creating a budget:
Creating a budget is a good thing, to allow you to track how you spend, ensuring that you stay within your budget limits. Setting up a budget also lets you get alarms when you exceed your thresholds.

To set up a budget head over to the console, and within the search bar, just search budget, and select it.

![ENV SETUP](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/a47c1e8a-7145-4d9d-a611-de3abca734f7)

**Click on Create Budget!** 

This will bring you to an interface that appears like this:

![image](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/80a1992a-55e6-4a16-87b2-23417fe7e610)

We are interested in using a template as shown in the arrow. Click on that. We will also set our budget to monthly, I think this is more rational.

![ENV SETUP(4)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/a2955f07-f689-4f81-a40e-f4d59a72dcba)


- **Enter the budget name**
- **Enter your budgeted amount**
- **Enter the email that you would wish to receive notifications, then**

Click on the **create budget** at the bottom of the page.

![ENV SETUP(5)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/b0372ffe-e221-4bdf-a7bc-807a7392acb0)

**Identity and Access Management (IAM)**

In most cases, you will not want to log in to amazon using your root account. Or, you might be having a single account but accessible to multiple users. Assume you were working as a team.
IAM allows:

- **Who:** Who can access your resources (users, groups, applications)
-**What:** What resources they can access (S3 buckets, EC2 instances, Lambda functions)
- **How:** How they can access them (permissions, authentication methods)

**IAM Components:**

    - Users: Represent human users who interact with AWS resources.
    - Groups: Collection of users sharing similar permissions.
    - Roles: Set of temporary permissions for applications or services.
    - Policies: Documents that define permissions for users, groups, or roles.
    - Access Keys: Credentials used by users to programmatically access AWS resources.
    - MFA (Multi-Factor Authentication): Adds an extra layer of security for logins.

**Benefits of IAM:**

    - Enhanced Security: Limits access to resources based on the principle of least privilege.
    - Improved Compliance: Adheres to security regulations and audits.
    - Centralized Management: Simplify access control across your AWS account.
    - Cost Optimization: Prevent unauthorized usage and optimize resource costs.

**Key Use Cases:**

    - Granting users access to specific AWS services (EC2 for developers, S3 for marketing team).
    - Creating temporary access for applications using roles.
    - Enforcing least privilege by assigning granular permissions.
    - Implementing multi-factor authentication for critical users.
    - Enforcing security best practices and compliance requirements.

**Getting Started with IAM:**

For this lecture, we will learn how to create a user group, then add users. This can be important if you want many users to have simialr access rights to the AWS account.

From the AWS dashboard, go into the search bar and search **IAM**:

You will get an interface like this, the just pick IAM:

![ENV SETUP(7)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/93431fe8-5620-45a3-a51c-902a4ddc516b)

Once in the IAM dashboard:

- Click on users
- Add user name
- Click on *Provide user access to the AWS Management Console*
- Click on *I want to create an IAM user*
- Click on *custom password* then set your password.
- Click *add user to group* if a group is available.

![ENV SETUP(10)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/8ea816fd-7df8-4233-a717-9f0283560df2)

The final output should be like this, then just click *Create user*

![ENV SETUP(11)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/29f83eea-a3e4-497f-9cbf-609507fe9b59)

**User groups**

For groups, access the dashboard once again:

![ENV SETUP(8)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/dd4c3cc6-08eb-4d05-ae25-db837cd24bd0)

- Click on user groups
- Click on create group

![ENV SETUP(9)](https://github.com/gmeds/Bacterial-Genomics24/assets/157685223/a3a92667-baf5-4155-90a0-b61e06eace73)

- Enter group name
- Add users if available.
- Finally, add policies that the group will have authority/permisions over.

**Some of the policies to consider:**
- AmazonEC2FullAccess
- AmazonEKSClusterPolicy
- AmazonEKSWorkerNodePolicy
- AmazonS3FullAccess
- AWSAccountUsageReportAccess
- AWSBudgetsReadOnlyAccess
- AWSCloudShellFullAccess
- AWSServiceCatalogAdminFullAccess
- CostOptimizationHubReadOnlyAccess
- IAMUserChangePassword

Additional Resources:

    AWS IAM User Guide: https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html: https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction.html
    AWS IAM Best Practices: https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html: https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html
    AWS IAM FAQs: https://aws.amazon.com/iam/faqs/: https://aws.amazon.com/iam/faqs/
