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

-   AWS GovCLoud Regions allow customers to host sensitive **Controlled Unclassified Information** and other types of regulated workloads.

-   GovCloud Regions are only operated by employees who are citizens of the US, and in its soil.

-   The are **only** accessible to U.S. entities and root account holders who pass a screening process.

    ![image](https://user-images.githubusercontent.com/84306023/124895239-0003d000-dffa-11eb-9088-67d2362da83f.png)
    
<br />

## Setting Up AWS and other configurations

### Billing Preferances

Select the User → My Billing Preferances → Preferences → Billing Preferances → Select the options and then save the configured preferences.

<br />

### Budgets - Whether you’re going over your predefined budgets and some forecast costs as well)

In the services menu search for “Budgets” → Create a new budget (You get two new budgets in the US) → 

<br />

For billing and services type cloudwatch ( This Monitors resources and applications)→ Billing Metrics (this always lives in the US West 01) → US East 01 (N. Virginia – The region that I selected) → Alarms (there are 10 free alarms)  → Create an alarm and do the editing as you wish. 

<br />

### Change IAM (Manage Access to AWS resources) Users Sign-in link

Change the sign in url to:
Customize → project-fresh → save

<br />

### Activate MFA on the root account (Adding an additional code after entering the username and password):

IAM Dashboard → Under “Best Practices” → Root Credentials → MFA (Multi Factor Authentication) → Select “Virtual MFA Device” and press continue → Select Google Authenticator on your Android device → On the phone select Scan the QR Code and hold the phone on the computer → And add the two MFA codes one after the other (there is a wheel that is spinning, so it should be added once the first wheel has finished spinning) 

<br />

### Create an Individual IAM User other than the root account for operating with your day to day work:

IAM Dashboard → Below IAM Resources → Select Users → Add User → User Name: DevOps → Access type is Programmatic Access & AWS Management Console Access and select “Next: Permissions” → Create a group called “Admin”  and give it “AdministratorAccess” (You can also select power users which doesn't give you access to manage users & groups) and then select “Next: Tags”→ Next: Review → Create User →

<br />

**The below image shows the user created:**

![image](https://user-images.githubusercontent.com/84306023/125027605-19615680-e0a4-11eb-8e59-dd2e3a74f8cd.png)




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

   







