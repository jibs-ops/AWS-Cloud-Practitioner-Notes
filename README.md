# AWS-Cloud-Practitioner-Notes

- AWS CCP has some very unique offering whereas no other AWS Certifications offer, which is that they provide a strong focus on billing and business centric concepts.

<br />

## Overview of the AWS Global Infrastructure

**Links** - https://aws.amazon.com/about-aws/global-infrastructure/ & https://docs.aws.amazon.com/whitepapers/latest/aws-overview/global-infrastructure.html

**Where does all this Cloud Computing Run?**

81 Availability Zones within 25 Geographic Regions around the world. There are way more Edge locations that AZs.

- AWS serves over a million active customers in more than 240 countries and territories. 
- They are steadily expanding their global infrastructure in order help customers achieve lower latency and higher throughput, and to ensure that the customers data resides only in the AWS Region specified.
- Regions is the physical location somewhere in the globe with Multiple Aailability Zones.
- Edge Locations are Data Centers owned by a trusted partner of AWS.

![image](https://user-images.githubusercontent.com/84306023/124888963-39d1d800-dff4-11eb-9f73-fb4f52325a70.png)

<br />

### Regions

![image](https://user-images.githubusercontent.com/84306023/124890738-f9735980-dff5-11eb-8fdc-cdb0b52f20ef.png)

- If you want to use any feature or service you will have to select US-East 01. US-East 01 is North Virginia where you see all the billing information. 
- Most companies or enterprises has to run in 3 Azs (Availability Zones).

<br />

![image](https://user-images.githubusercontent.com/84306023/124892001-19574d00-dff7-11eb-9992-ae9922303324.png)

<br />


![image](https://user-images.githubusercontent.com/84306023/124892671-aef2dc80-dff7-11eb-9fb1-75a5579a0512.png)

<br />


### GovCloud (US)
<br />

-   AWS GovCLoud Regions allow customers to host sensitive **Controlled Unclassified Information** and other types of regulated workloads.

-   GovCloud Regions are only operated by employees who are citizens of the US, and in its soil.

-   The are **only** accessible to U.S. entities and root account holders who pass a screening process.

    ![image](https://user-images.githubusercontent.com/84306023/124895239-0003d000-dffa-11eb-9088-67d2362da83f.png)
    
<br />

## Setting Up AWS and other configurations

### Billing Preferances

1. Select the User.
2. My Billing Preferances.
3. Preferences.
4. Billing Preferances.
5. Select the options and then save the configured preferences.

<br />

### Budgets - Whether you’re going over your predefined budgets and some forecast costs as well)

1. In the services menu search for “Budgets”.
2. Create a new budget (You get two new budgets in the US) → 

<br />

1. For billing and services type cloudwatch ( This Monitors resources and applications)
2. Billing Metrics (this always lives in the US West 01).
3. US East 01 (N. Virginia – The region that I selected). 
4. Alarms (there are 10 free alarms).
5. Create an alarm and do the editing as you wish. 

<br />

### Change IAM (Manage Access to AWS resources) Users Sign-in link

    -   Change the sign in url to:
            -   Customize → project-fresh → save

<br />

### Activate MFA on the root account (Adding an additional code after entering the username and password):

1. IAM Dashboard → 
2. Go to “Best Practices” and select Root Credentials.
3. MFA (Multi Factor Authentication).
4. Select “Virtual MFA Device” and press continue.
5. Select Google Authenticator on your Android device. 
6. On the phone select Scan the QR Code and hold the phone on the computer.
7. And add the two MFA codes one after the other (there is a wheel that will be spinning, so it should be added once the first wheel has finished spinning) 

<br />

### Create an Individual IAM User other than the root account for operating with your day to day work:

1. IAM Dashboard.
2. Below IAM Resources.
3. Select Users.
4. Add User.
5. User Name: DevOps → Access type is Programmatic Access & AWS Management Console Access.
6. Select “Next: Permissions”.
7. Create a group called “Admin”  and give it “AdministratorAccess” (You can also select power users which doesn't give you access to manage users & groups).
8. Then select “Next: Tags”.
9. Next: Review.
10. Create User

<br />

**The below image shows the user created:**

![image](https://user-images.githubusercontent.com/84306023/125027605-19615680-e0a4-11eb-8e59-dd2e3a74f8cd.png)

1. Go to services and search for IAM.
2. Login to the user by selecting the “IAM Users sign-in link url: https://project-fresh.signin.aws.amazon.com/console”.
3. Enter the password and then change the password

<br />

1. Go back to IAM here (because the access key was exposed here).
2. Go to Users (DevOps).
3. Security Credentials. 
4. If the password was seen make it inactive and create another access key.
5. Create a new access key.

<br />

*   At anytime that you share your credentials you’re going to reset them there but for now as the password is reset it’s not a problem.

<br />

### Set a password policy

<br />

1. IAM Management Console.
2. Access Management.
3. Account Settings.
4. Set Password Policy. 
5. And select the options needed.
6. Save Changes

<br />

### How to launch a server in EC2

<br />

1. Go to the management console.
2. In services select EC2.
3. Launch Instance. 
4. Amazon Linux 2 → t2.micro (Free tier eligible). 
5. Next: Configure Instance Details.
6. Instances (Number of servers) 

<br />

    (In the configuration select “Create a new IAM role” in a new tab while this configuration is opened→ Create a new role → EC2 → Next: Permissions → Select AmazonEC2RoleforSSM (Simple Systems Manager is a way to login to that machine) → Next: Tags → Next: Reviews → Fill in the details. Role Name: MyEC2Role) 

<br />

    → In the IAM Role → Next: Add Storage → Review and launch → Launch (It is going to ask you to create a key pair. Key pairs are used to get into the server, we don’t need one because we are using SSM as it’s another way of login into the server) → Proceed without a key pair in the drop down menu → To view the progress select “View Instances” → It should turn from yellow to green

<br />

### Sessions Manager

<br />

    There are a couple of ways to get into an instance:
        1. SSH (If the key pair was created. For here the setting must be configured such as chmod and others).
        2. SSM – Simple Systems Manager, which is AWS’s recommended way.

<br />

### Using the Simple Systems Manager to access an instance:

<br />

    In services → SSM → Session Manager (This is under Node Manager)→ Start a session → Logs in as the root user and then the user can be changed as the ec2-user (sudo su – ec2-user)


<br />

In services → EC2 → Instances → Stop the instances so it would not cost us anything

<br />

* An AMI can be understood as a copy of your server. 

<br />

    Services → EC2 → Instances → Select the image → Got to actions → Image and Instances → Create an Image → Name: fresh-000 → Select the pop up of the due pending image creation (Comes under “Images → AMI” → Launch (It will take you to the settings where creating an instance is used, you can just  go to review and finish it).

<br />

### Auto Scaling Groups

<br />

Services → EC2 → Auto Scaling → Auto Scaling Group (what is does is, it allows you to ensure that multiple instances or servers are running it will have a rule to say that one server is running and if not then launch a new server, also auto scaling groups are used to meet the demand of whatever traffic you have so it will spin up traffic when the demands are high and close when the metrics are low) → Create an auto scaling group → Get Started → Name: Auto Scale → 

<br />

Services → EC2 → Under “Auto Scalling” select “Auto Scaling Groups” → Create an auto scaling group → “Name: fresh-asg” and select “MyInstance” as the launch template → Configure settings (Select a vpc and select two subnets) → Skip the “Configure advanced options” → Configure Group size and scaling policies (scaling policies are ways in which you can determine how the auto scaling group should react to changes within its environment, so if you have a lot of cpu utilization, when there is a lot of data transfer in or when there is a lot of memory  ) → Skip Add Notifications → Skip Add Tags → Go to review → Create the Auto scaling group by scrolling right down after reviewing everything. 

<br />

Services → EC2 → Under “Auto Scalling” select “Auto Scaling Groups” → Create an auto scaling group → “Name: fresh-asg” and select “MyInstance” as the launch template → Configure settings (Select a vpc and select two subnets) → Skip the “Configure advanced options” → Configure Group size and scaling policies (scaling policies are ways in which you can determine how the auto scaling group should react to changes within its environment, so if you have a lot of cpu utilization, when there is a lot of data transfer in or when there is a lot of memory) → Skip Add Notifications → Skip Add Tags → Go to review → Create the Auto scaling group by scrolling right down after reviewing everything. 

<br />

Once the Auto scaling group has been created → Select it → Go to instances → If it doesn’t load on the right side select instances – Go to the instances tab → and terminate the instance → Go back to the auto scaling group, select instance management and you’ll see the instance as unhealthy → And what it’ll do as a response it launch a new instance → A new instance will be loaded in place of the unhealthy one – Delete the auto scaling group where the instance too will be deleted. You may have to type “delete” to proceed. 


<br />

### Elastic Load Balancer

<br />

* **The elastic load balancer tries to put a load balancer in front of the instances, the idea is when traffic comes into a web application, it is going to evenly distribute the traffic into multiple instances generally running in different availability zones. So if one AZ is busy it will transport the traffic to another AZ so the user accessing the application would not experience a down time.**

<br />

Create an instance → Amazon Linux 2 here → t2.micro as it’s free → 2 number of instances & IAM Role: MyEC2Instance (as we don’t have to ssh into it) → pass the next steps and go to “Configure Security Groups” and select the default one → Review and launch and proceed without a key pair → View Instances → Name the two instances as InstanceA & InstanceB.

<br />

Load Balancing under the EC2 Console → Load Balancers → Create Load Balancer → There are four kinds of load balancers (application, network, gateway, and classic) select the application load balancer → type “my-alb” as the name, scheme would be “internet facing” , make sure it is running in two availability zones, else there will be complain to us→ Go to the next step (configure security settings) → As SSL and HTTPS is not being used nothing has to be done in the configure security settings → Select “default” in the configure security groups → In configure routing there is a need to create a new target group, the target group has references to instances where we want to draw traffic to. The name of it would be “ my-target-group”→ Register targets and select the instances → Click next and then create. 

<br />

*   Note: There will be a DNS name for this load balancer. The way the traffic of the load balancer would be routed would be by pointing it to here. Then it will go to the listeners and the listeners would go to a port (ex: port 80). It would have rules where it will forward that traffic to that target group. Sleelct the target and it will show the targets. 

<br />

* **Now delete the load balancers. Unlike the auto scaling group the instances will have to be taken down by ourselves.**

<br />

### Simple Storage Service (S3)

<br />

Services → S3 → (it can be noticed on top that it shows as global, and not specific to a region, however the bucket that would be created would be specific to a region. A region is a place where it contains the files) Create a Bucket → Bucket Name: fresh12 (the name is like the domain name, so it should be specific), select the region → Create a bucket → Select the bucket and upload a file → 

<br />

### CloudFront

<br />

* **CloudFront is used as a CDN, as a content distribution network. The idea here is let’s say you have files static files or video files and you want to share it across the world and you want those to load as quickly as possible and make the shortest route to the end user and that is where CloudFront a CDN comes in. So its going to whatever your static content is and it is going to copy it to multiple edge locations around the world and so when someone tries to access your content it is going to that nearby edge locations as oppose to going really far away to get that content.**

<br />

    Services → CloudFront → Create Distribution → Get Started → select the s3 bucket that we created (fresh12) → Create Distribution. 

<br />

*   Note: So the uploaded file will be available around the world at a super fast level. 

<br />

*   Note: Similar to the elastic domain name in CloudFront has a Domain Name. So the traffic would it the domain name and would then route the traffic to the nearest edge location. 

<br />

*   Note: If needed you can disable and delete it. Even if you don’t delete it, it won’t charge you anything as you’ve disable it. 

<br />

### Relational Database Services (RDS)

<br />

    Services → RDS → Create Database (Under the dashboard select database and select “Create Database” → It has quite a few options and it has Amazon Aurora selected which is one of the most expensive options, select PostgreSQL → Templates (Continued Below)

<br />

-   Note: In the types of templates you get three types. Production, Dev/Test, and FreeTier. The idea with production is for a very large company, they’re setting you up with every bell and whistle under the sun here, dev/test is for small or medium size, and the free tier for is to gain experience suitable for what is doing here. For free tier you only get 750 hours of RDS

<br />

    (Continuation) Free tier →  In settings type a password → In the DB instance class select Burstable classes(db.t3.micro), the Storage will be general purpose and set to 20 GiB (Continued Below)
    
<br />

-   Note: There is autoscalling so it will automatically increase the storage if it runs out, that will be ticked off here.

<br />

    (Continuation) → From below in additional configuration from the database options select a database name: exampro_fresh → In backup turn to 0 days so it will not take a snapshot of the database → Turning off performance insights too as it’s no needed here → Create Database → Select the database that was just created and see the statistics it displays → Destroy the database if needed

<br />

*   Note: To access this database you’ll have to assemble all the requirements. You need this port number, username & password which we was setup earlier. 

<br />

### LAMBDA

<br />



<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

<br />

   







