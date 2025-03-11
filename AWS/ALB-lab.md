# AWS Lab - Application Load Balancer

## Objective:
Deploy an Application Load Balancer **(ALB)** with two EC2 instances behind it. Ensure the Security Group **(SG)** configurations allow only **ALB** access to **EC2**
instances while preventing direct access.


## 1: Launch two EC2 Instances

1.1: Login to the [AWS Management Console](https://aws.amazon.com/) and navigate to **EC2** from the **Services** menu.
1.2: Click **Launch Instances**.
1.3: Choose **Amazon Linux 2** AMI
1.4: Install **Apache** by adding the following script in the **User Data** section
```
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Instance ID: $INSTANCE_ID</h1>" > /var/www/html/index.html
```

1.5: AWS will automatically assign a **VPC** to the instances. Ensure the EC2 instances are in the same **VPC** and **Availability Zones(AZ)**.

---

## 2: Create an Application Load Balancer
2.1: Navigate to the **Load Balancer** section and Click Create Application
2.2: Give your **Load Balancer** a name(e.g. ALB-ec2)
2.3: Ensure **IPv4** is enabled.
2.4: Assign the same VPC used by the EC2 instances(this should be the defualt VPC).
2.5: Select the Availability Zone where your EC2 instances are located.
