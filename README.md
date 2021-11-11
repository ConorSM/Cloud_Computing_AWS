# Cloud Computing
- On-Demand availability of computer system resources - esp. data storage and computing power

## Amazon Web Services (AWS)
- Amazon Web Service
- One of the largest cloud services provider
- Provides a mixture of IaaS, PaaS, and SaaS
### AWS Global Infrastructure

#### AWS Regions
- Locations that the AWS cloud spans
- At least two data centres per region
- Not all regions have all services available
#### AWS Availability Zones (AZs)
- The data centres within each region
#### Advantages of Cloud Computing and AWS
- Go global in minutes
- No need to spend on running and maintaining data centres
- increase speed and agility
- Scalable
- Only pay for what you use
### Public Cloud - Private Cloud and Hybrid Cloud use cases
- IaaS - PaaS - SaaS
- Cloud Data Centres

## AWS Services
- Elastic Compute Cloud `EC2`
- Simple Storage Service `S3`
- Virtual Private Network `VPC`
- Internet Gateway `IG`
- Route Tables `RT`
- Subnet `sn`
- Network Access Control `NALs`
- Security Groups `SG`
- Cloudwatch `CW`
- Simple Notification Service `SNS`
- Simple Queue Service `SQS`
- Load Balancers `LB` - `ALB` - `ELB` - `NLB`
- Autoscaling Groups `ASG`
- Amazon Machine Image `AMI`
- Dynamodb - Mongodb

# Steps to Create EC2 Instance
- Go to EC2 dashboard
- Launch instance
## Choose an AMI
- Select Ubuntu Server 16.04 LTS 64-bit (x86) AMI
## Choose an Instance Type
- Select t2 micro instance type
## Configure Instance Details
- Subnet - DevOpsStudent default
## Add storage
- Default
## Tags
- Key: Name; Value: devops_conor_app
## Configure Security Group
- 
  