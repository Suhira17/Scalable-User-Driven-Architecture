# Scalable-User-Driven-Architecture


![Scalable-User-Driven-Architecture](Scalable-user-driven-architecture.png)

## Abstract

- The architecture is designed to provide a scalable, secure, and resilient environment for hosting a web application that can handle varying levels of user demand. It uses a combination of computing, storage, database, and security services from AWS to ensure that the application remains available and responsive.

## Steps 

1. *Infrastructure Setup:*
   - Two AWS Virtual Private Clouds (VPCs) are set up in different regions (ap-south-1 and us-east-1) for geographical diversity and redundancy.

2. *Compute Resources:*
   - Within the ap-south-1 VPC, an Amazon EC2 instance is deployed in a public subnet to host the web application. This instance can serve dynamic content and handle user requests.

3. *Auto Scaling:*
   - An Auto Scaling group is configured for the EC2 instance to automatically adjust the number of instances based on demand, ensuring that the application scales up or down as needed.

4. *Static Content Storage:*
   - Amazon S3 buckets are used to store static files for the web application. A cross-region replica is set up between the S3 buckets in both regions to ensure that static content is available and consistent across regions.

5. *Database Services:*
   - Amazon RDS with a MySQL database is used to store application data. A read replica of the RDS instance is created in the us-east-1 region for read scalability and as a disaster recovery strategy.

6. *Security and Access Management:*
   - IAM policies (S3_USER_POLICY and RDS_USER_POLICY) are attached to IAM groups (S3_user_group and RDS_user_group) to control access to the S3 buckets and RDS instances, ensuring that only authorized users and services can access these resources.

7. *Notification Services:*
   - Amazon SNS is integrated to send notifications about important events, such as auto-scaling actions or other administrative alerts.

8. *Administration:*
   - An administrator oversees the entire architecture, likely using the AWS Management Console. They are     responsible for managing resources, monitoring performance, and responding to SNS notifications.


## Conclusion

- This AWS-based scalable architecture is well-suited for hosting a web application. It leverages the scalability of EC2 with Auto Scaling, the durability and availability of S3 with cross-region replication, the reliability of RDS with a read replica, and the security of IAM for access control. The use of SNS ensures that administrators are kept informed of critical events. This architecture is designed to handle increased load efficiently, maintain high availability, and provide a secure environment for user-driven applications.