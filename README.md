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
- ssh 22 from own IP
- HTTP 80
- App 3000

## ssh debugging
```
eval ssh-agent
ssh-add "keyfile.pem"
```

## Set up App Environment
- update and upgrade system
- install nginx
- nginx enabled
- check public IP globally
  
- install node correct version
- install required dependencies
- `app code` currently available on `localhost`
- task: `find out how to migrate/transfer/copy data from on prem to cloud`
  - scp
  - or clone git (better)
- npm install
- npm start

## Reverse Proxy on App
```
sudo rm -rf /etc/nginx/sites-available/default
sudo cp app/app/default /etc/nginx/sites-available/
sudo systemctl restart nginx
sudo systemctl enable nginx
systemctl status nginx
npm start
```

## EC2 Instance for Mongodb
- Security group
  - ssh 22 from own IP
  - port 27017 from app public IP
- Environment
```
# be careful of these keys, they will go out of date
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv D68FA50FEA312927
echo "deb https://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

sudo apt-get update -y
sudo apt-get upgrade -y

# sudo apt-get install mongodb-org=3.2.20 -y
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

# remove vm mongod.conf and replace with local version
sudo rm -rf /etc/mongod.conf
sudo cp /home/vagrant/app/environment/db/mongod.conf /etc/

# if mongo is is set up correctly these will be successful
sudo systemctl restart mongod
sudo systemctl enable mongod
```

- Mongod.conf (restart and enable mongod after)
  ```
  # network interfaces
  net:
    port: 27017
    bindIp: 0.0.0.0
  ```

## Connecting App and Mongodb
- In app instance
```
sudo echo 'export DB_HOST="mongodb://ip:27017/posts"' >> ~/.bashrc
source ~/.bashrc
node app/app/seeds/seed.js
npm start
```

  