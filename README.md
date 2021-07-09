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
6. Instances - Number of servers) (Continued Below)

<br />

    (In the configuration select “Create a new IAM role” in a new tab while this configuration is opened→ Create a new role → EC2 → Next: Permissions → Select AmazonEC2RoleforSSM (Simple Systems Manager is a way to login to that machine) → Next: Tags → Next: Reviews → Fill in the details. Role Name: MyEC2Role) 

<br />

1. (Continuation) → In the IAM Role.
2. Next: Add Storage.
3. Review and launch.
4. Launch (It is going to ask you whether to create a key pair. Key pairs are used to get into the server, we don’t need one because we are using SSM as it’s another way of login into the server).
5. Proceed without a key pair in the drop down menu.
6. To view the progress select “View Instances” (It should turn from yellow to green).

<br />

### Sessions Manager

<br />

    There are a couple of ways to get into an instance:
        1. SSH (If the key pair was created. For here the setting must be configured such as chmod and others).
        2. SSM – Simple Systems Manager, which is AWS’s recommended way.

<br />

### Using the Simple Systems Manager to access an instance:

<br />

1. In services. 
2. SSM.
3. Session Manager (This is under Node Manager).
4. Start a session.
5. Log in as the root user and then the user can be changed as the ec2-user (sudo su – ec2-user)/


<br />

1. In services.
2. EC2. 
3. Instances.
4. Stop the instances so it would not cost us anything

<br />

### AMI

* An AMI can be understood as a copy of your server. 

<br />

1. Services.
2. EC2.
3. Instances.
4. Select the image.
5. Go to actions. 
6. Image and Instances. 
7. Create an Image → Name: fresh-000.
8. Select the pop up of the due pending image creation (Comes under “Images → AMI” → Launch (It will take you to the settings where creating an instance is used, you can just  go to review and finish it).

<br />

### Auto Scaling Groups

<br />

1. Services.
2. EC2.
3. Auto Scaling.
4. Auto Scaling Group - What is does is, it allows you to ensure that multiple instances or servers are running. So it will have a rule to say that one server is running and if not then launch a new server, also auto scaling groups are used to meet the demand of whatever traffic you have so it will spin up traffic when the demands are high and close when the metrics are low).
5. Create an auto scaling group.
6. Get Started.
7. Name: Auto Scale → 

<br />

1. Services.
2. EC2.
3. Under “Auto Scalling” select “Auto Scaling Groups”.
4. Create an auto scaling group → “Name: fresh-asg” and select “MyInstance” as the launch template.
5. Configure settings (Select a vpc and select two subnets).
6. Skip the “Configure advanced options”.
7. Configure Group size and scaling policies - Scaling policies are ways in which you can determine how the auto scaling group should react to changes within its environment, so if you have a lot of cpu utilization, when there is a lot of data transfer in or when there is a lot of memory.
8. Skip Add Notifications.
9. Skip Add Tags.
10. Go to review.
11. Create the Auto scaling group by scrolling right down after reviewing everything. 

<br />

1. Once the Auto scaling group has been created → Select it.
2. Go to instances → If it doesn’t load on the right side select instances.
3. Go to the instances tab → and terminate the instance → 
4. Go back to the auto scaling group, select instance management and you’ll see the instance as unhealthy → And what it’ll do as a response is launch a new instance.
5. A new instance will be loaded in place of the unhealthy one.
6. Delete the auto scaling group where the instance too will be deleted. You may have to type “delete” to proceed. 


<br />

### Elastic Load Balancer

<br />

* **The elastic load balancer tries to put a load balancer in front of the instances, the idea is when traffic comes into a web application, it is going to evenly distribute the traffic into multiple instances generally running in different availability zones. So if one AZ is busy it will transport the traffic to another AZ so the user accessing the application would not experience a down time.**

<br />

1. Create an instance → Amazon Linux 2 here → t2.micro as it’s free.
2. 2 number of instances & IAM Role: MyEC2Instance (as we don’t have to ssh into it) 
3. Pass until the next steps and go to “Configure Security Groups” and select the default one.
4. Review and launch and proceed without a key pair.
5. View Instances.
6. Name the two instances as InstanceA & InstanceB.

<br />

1. Load Balancing under the EC2 Console.
2. Load Balancers.
3. Create Load Balancer - There are four kinds of load balancers (application, network, gateway, and classic) select the application load balancer.
4. Type “my-alb” as the name, scheme would be “internet facing” , make sure it is running in two availability zones, else there will be complain. 
5. Go to the next step (configure security settings), SSL and HTTPS will not be used here so nothing has to be done in the configure security settings.
6. Select “default” in the configure security groups.
7. In configure routing there is a need to create a new target group, the target group has references to instances where we want to draw traffic to. The name of it would be “ my-target-group”.
8. Register targets and select the instances.
9. Click next and then create. 

<br />

*   Note: There will be a DNS name for this load balancer. The way the traffic of the load balancer would be routed would be by pointing it to here. Then it will go to the listeners and the listeners would go to a port (ex: port 80). It would have rules where it will forward that traffic to that target group. Sleelct the target and it will show the targets. 

<br />

* **Now delete the load balancers. Unlike the auto scaling group the instances will have to be taken down by ourselves.**

<br />

### Simple Storage Service (S3)

<br />

1. Services. 
2. S3 - It can be noticed on top that it shows as global, and not specific to a region, however the bucket that would be created would be specific to a region. A region is a place where it contains the files). 
3. Create a Bucket.
4. Bucket Name: fresh12 (the name is like the domain name, so it should be specific), select the region.
5. Create a bucket.
6. Select the bucket and upload a file → 

<br />

### CloudFront

<br />

* **CloudFront is used as a CDN, as a content distribution network. The idea here is let’s say you have files static files or video files and you want to share it across the world and you want those to load as quickly as possible and make the shortest route to the end user and that is where CloudFront a CDN comes in. So its going to whatever your static content is and it is going to copy it to multiple edge locations around the world and so when someone tries to access your content it is going to that nearby edge locations as oppose to going really far away to get that content.**

<br />

1. Services.
2. CloudFront.
3. Create Distribution.
4. Get Started. 
5. Select the S3 bucket that we created (fresh12).
6. Create Distribution. 

<br />

*   Note: So the uploaded file will be available around the world at a super fast level. 

<br />

*   Note: Similar to the elastic domain name in CloudFront has a Domain Name. So the traffic would it the domain name and would then route the traffic to the nearest edge location. 

<br />

*   Note: If needed you can disable and delete it. Even if you don’t delete it, it won’t charge you anything as you’ve disable it. 

<br />

### Relational Database Services (RDS)

<br />

1. Services.
2. RDS.
3. Create Database.
4. Under the dashboard select database and select “Create Database” - It has quite a few options and it has Amazon Aurora selected which is one of the most expensive options, select PostgreSQL instead of it.
5. Templates (Continued Below)

<br />

-   Note: In the types of templates you get three types. Production, Dev/Test, and FreeTier. The idea with production is for a very large company, they’re setting you up with every bell and whistle under the sun here, dev/test is for small or medium size, and the free tier for is to gain experience suitable for what is doing here. For free tier you only get 750 hours of RDS

<br />

6. Free tier.
7. In settings type a password. 
8. In the DB instance class select Burstable classes(db.t3.micro), the Storage will be general purpose and set to 20 GiB (Continued Below)
    
<br />

-   Note: There is autoscalling so it will automatically increase the storage if it runs out, that will be ticked off here.

<br />

9. From below in additional configuration from the database options select a database name: exampro_fresh.
10. In backup turn to 0 days so it will not take a snapshot of the database → Turning off performance insights too as it’s no needed here.
11. Create Database.
12. Select the database that was just created and see the statistics it displays.
13. Destroy the database if needed

<br />

*   Note: To access this database you’ll have to assemble all the requirements. You need this port number, username & password which we was setup earlier. 

<br />

### LAMBDA

<br />

1. Services.
2. Search for lambda. 
3. Create a function.
4. Author from scratch → Name: myLambda, Runtime: Ruby 2.7, select under permissions “Create a new role with Basic Lambda Permissions”  so it could write to cloudwatch launch.
5. Create Function 

*   So the big benefit of Lambda is, you don’t have to worry about the servers you just write your code and  it will run. The tradeoff here is that they run for only a small amount of time of about up to 15 minutes.  But they generally run for 1 second or less. 

*   In the code add 
        -   ‘puts “Hello World” ’ below # T000 implement
6. Test.
7. Event Name: helloworld.
8. Create.
9. Monitor.
10. View logs in cloudwatch. 
11. If you want to add a triger you can go down and add one →
12.  + Add Trigger → And select the service you want to run.

<br />

## An Introduction on the EC2 Pricing Models

<br />

**Link:** https://aws.amazon.com/ec2/pricing/

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125059640-2b092500-e0c9-11eb-9688-049198c605f1.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125060128-a9fe5d80-e0c9-11eb-9f17-082dcde0bdba.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125060274-d2865780-e0c9-11eb-99c9-1a994ff8db92.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125060331-e5009100-e0c9-11eb-9912-bf49068e4ead.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125060381-f21d8000-e0c9-11eb-8e5b-ee1e43af56ba.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125060433-01043280-e0ca-11eb-9ff5-c1bbfad63b7e.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125060642-327cfe00-e0ca-11eb-9686-ac8b919e78e8.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125060713-445ea100-e0ca-11eb-9999-211b73044d57.png)


<br />

## AWS Support Plans

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125061132-a8816500-e0ca-11eb-8e7d-c213d86e915c.png)


<br />

## AWS Marketplace

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125061412-f302e180-e0ca-11eb-8b81-b35da5d7170a.png)


<br />

   * So for this:
       1. Services.
       2. EC2.
       3. AMI.
       4. On the left hand size select “AWS Marketplace”.
       5. Search for tensorflow or any other service you prefer like “Gaucamole”. 

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125061731-42491200-e0cb-11eb-8ef8-49da42743040.png)


<br />

###   **AWS Trusted Advisor has five types**

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125061992-89cf9e00-e0cb-11eb-86c0-7d623c12d186.png) 


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125062125-b08dd480-e0cb-11eb-9cec-9008827d34f4.png)


<br />

##  An example of AWS Trusted Advisor Billing & Pricing

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125062345-e7fc8100-e0cb-11eb-97bc-6248e82651bd.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125062552-242fe180-e0cc-11eb-9b4d-d54e21b0b9ff.png)


<br />

*   Note: Consolidated billing is a feature turned on by default when you’re using your organization and when you have multiple member accounts.

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125062780-648f5f80-e0cc-11eb-9970-439cb7a960e3.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125062966-94d6fe00-e0cc-11eb-98c6-8cc7abb02556.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125063023-a3bdb080-e0cc-11eb-9565-243b4fd309a6.png)

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125063104-b3d59000-e0cc-11eb-8a75-b4be7dd7a675.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125063156-c3ed6f80-e0cc-11eb-9930-205b97a22cd3.png)


<br />

   ### How to create a budget:
   
   1. Services.
   2. AWS Budgets.
   3. Create a budget.
   4. Cost Budget.
   5. Budget Name: Overall Costs, can even go to budget planning → Budget amount: 100 → Filter and then select dimension: services values: EC2.
   6. Add Alert Threshold alert if it reaches the 80% threshold, ad add the email addresses.
   7. Create a budget

<br />
<br />
<br />

   ![image](https://user-images.githubusercontent.com/84306023/125063886-a967c600-e0cd-11eb-8cba-769f9714560a.png)


<br />
<br />
<br />

   ![image](https://user-images.githubusercontent.com/84306023/125063968-c3a1a400-e0cd-11eb-8b59-c3a6eacf628c.png)


<br />
<br />
<br />

   ![image](https://user-images.githubusercontent.com/84306023/125064066-de741880-e0cd-11eb-9467-9c9de925e649.png)


<br />
<br />
<br />

   ![image](https://user-images.githubusercontent.com/84306023/125064159-f9468d00-e0cd-11eb-89d4-8f2e3fa90e10.png)


<br />
<br />
<br />

![image](https://user-images.githubusercontent.com/84306023/125064734-986b8480-e0ce-11eb-84d5-fffe722bf2c6.png)


<br />
<br />
<br />

   *  So for this:
   1. Add two new instances and for the tagging Key: 
   2. Project and Value: TerokNo
   3. Continue doing the same as the remaining way.
   4. To see what is happening go to the instances page.

   5. Go to services. 
   6. Resource Groups & Tag Editor.
   7. Create a resource group →Tag Based → Group Criteria (check whether it’s there in all supported resource groups).
   8. Tags: enter the key and value →  Add.
   9. Preview Group Resources.
   10. GroupName: TerokNo.
   11. Create Group 

   *   You can check the New resource group in the AWS Resource Groups → Saved Resource Groups.

   *   Also in the same section you can see the manage tags in the tag editor and entering the tag key & value. Then searching for the resources. From here the tags can be removed or added. 

    -   Adding a tag.
         1. Select all the tags.
         2. Manage tags of selected resources.
         3. Add Tag.
         4. Tag Key: Federation & Tag Value: StarFleet.
         5. Review and apply Tag Changes.
         6. Go to instances to see the changes in tags.
         7. Remove the Tag if you want to

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125065531-8ccc8d80-e0cf-11eb-8d85-4381e71f280e.png)


<br />

*   **AWS Quick starts -** https://aws.amazon.com/quickstart/?solutions-all.sort-by=item.additionalFields.sortDate&solutions-all.sort-order=desc&awsf.filter-tech-category=*all&awsf.filter-industry=*all&awsf.filter-content-type=*all

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125065678-bd142c00-e0cf-11eb-9a6a-3367824afaeb.png)


<br />

   1. From the user account press the drop down button.
   2. My Billing Dashboard.
   3. Cost & Usage Reports.
   4. Create Report → Name: MyCostAndUsage (Tick “Include Resource IDs).
   5. Configure S3 Bucket (S3 Bucket Name: jibs-cost-and-usage).
   6. Tick “I have confirmed that this policy is correct” → Report Path Prefix:  MyPrefix → Time Granularity: Daily → Compression type: Zip.
   7. Next → Review and Complete.

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125066343-84c11d80-e0d0-11eb-96c2-a87ec8c5b5ec.png)


<br />

   *   **There are two places where you can manage your organizations. They are IAM & Amazon Organizations.**

       * Organization Activity
       1. Services.
       2. Identity and Access Management.
       3. AWS Organizations.
       4. Organization Activity.

       1. Services.
       2. Organizations (AWS Organizations).
       3. Create Organization.
       4. Verify Your AWS Organization Account sent to your email.


        * You can create organization units → in AWS Organizations → In the Actions Drop down menu select 
        1. “Create: Organization Unit” → Name: Developers.
        2. Add AWS Account → AWS Account Name: Jibs, email: jibraan35@gmail.com → Verify the email that was sent.
        3. To access the account, the only way is to say you’ve forgotten the password.
        4. To move an acocunt to an organization unit select the account and press move to the directory. 

   *  Policies help you to access resources, so for example you’ll have only ec2 by naming it.
   
        1. In actions have it as EC2.
        2. And then select “All Actions”. Resources.
        3. All Resources. 

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125071883-804c3300-e0d7-11eb-9e6c-9c8012b2a184.png)


<br />

   4. Move on to the conditions and do this by allowing in the code.
   5. Create Policy.
  

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125072296-0bc5c400-e0d8-11eb-9fe3-35464456ab30.png)


<br />

   * Assign the policy to the group and the user.
    1.  AWS Accounts.
    2.  Policies.
    3.  Service control Policies.
    4.  Select Only EC2 and from the below actions select attach policy.
    5.  And now select the group or user.
    6.  Go to My Account and close the account if needed from right below.   

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125072719-8db5ed00-e0d8-11eb-9a27-0044d0e454b2.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125072765-9dcdcc80-e0d8-11eb-8186-1e10ae425895.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125072801-ab835200-e0d8-11eb-8777-7176e66ba3f3.png)
   
   * A Provisioning is an easy way of setting up resources for you, and it can be done via code and GUI.


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125072879-c950b700-e0d8-11eb-81f0-f8ec33f93529.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125072908-d66da600-e0d8-11eb-9899-fe1272f8d3c5.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125072941-e4232b80-e0d8-11eb-85b5-a4d2c588c33f.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125072985-f4d3a180-e0d8-11eb-86e6-2a8d0c2a1654.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073012-0026cd00-e0d9-11eb-8f50-4a08ec0ab132.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073068-146aca00-e0d9-11eb-8a84-c91a5541d365.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073121-22204f80-e0d9-11eb-95c6-86135b9c61b6.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073155-2b112100-e0d9-11eb-9bee-6079e0678ce1.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073220-40864b00-e0d9-11eb-8e1c-586a3af74b7e.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073247-4a0fb300-e0d9-11eb-8464-be03008b8850.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073304-5d228300-e0d9-11eb-950d-0cf701085e3d.png)


<br />

   * How to get an AWS Artifact
    1. Services.
    2. AWS Artifact.
    3. Select the artifact. 
    4. Agree to their conditions and download it. (Adobe Acrobat is the only reader available to use). 

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073505-b1c5fe00-e0d9-11eb-9e2a-9587db6ad15c.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073547-c2767400-e0d9-11eb-93d8-a0d7478641b4.png)


<br />

   * Link AWS Shield - https://aws.amazon.com/shield/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073571-cd310900-e0d9-11eb-8dee-d4d7834e4e71.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073715-023d5b80-e0da-11eb-86cc-3f4b6c402fc7.png)


<br />

   * DDOS – Stands for Distributed denial of service attack and this is a malicious attempt to distrupt normal traffic by flooding a website by  number of fake traffic. It’s come with AWS Shield and it is turned on for AWS customer by default at no additional cost. 

<br />

   * Shield Advanced must be paid upfront. 

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125073973-521c2280-e0da-11eb-9106-b80a17827cc7.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074027-619b6b80-e0da-11eb-8da0-fec68ece2909.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074073-6fe98780-e0da-11eb-9581-c29bfe17487c.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074122-7e37a380-e0da-11eb-9277-72862109d596.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074773-58f76500-e0db-11eb-8590-f67921c3544f.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074796-63196380-e0db-11eb-8d5d-1e1b03b8b34c.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074827-6d3b6200-e0db-11eb-8680-f522923789ea.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074856-76c4ca00-e0db-11eb-854d-42fa356ff066.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074871-80e6c880-e0db-11eb-9977-8c7bdd730e3a.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074899-8a703080-e0db-11eb-8642-7717e33bee0d.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074927-93f99880-e0db-11eb-9a72-b960802f4b20.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125074960-9fe55a80-e0db-11eb-8bc5-9a88ce7c4a39.png)


<br />

   * Before application and network load balancer all that was there was the elastic load balancer. Now it has been renamed to classic load balancer. It basically does the job of application and network load balancer and it works a little different. 

   * Generally you want to use application and network load balancer. But you can still use the classic load balancer.

<br />

   ![image](https://user-images.githubusercontent.com/84306023/125075149-dcb15180-e0db-11eb-9b3e-b93d45867cea.png)


<br />

   ![image](https://user-images.githubusercontent.com/84306023/125075187-e76be680-e0db-11eb-8bd1-dd21b610328f.png)


<br />

   * Be aware that both these only compile PDFs.

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




   







