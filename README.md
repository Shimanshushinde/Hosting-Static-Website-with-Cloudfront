
# Hosting a Static Website on AWS Using S3 Bucket,Route 53,Certificate Manager and CloudFront.

This guide outlines the steps to build and deploy a static website hosted on Amazon S3, integrating domain management through AWS Route 53. The project focuses on creating a scalable and reliable web presence, perfect for showcasing personal portfolios, blogs, or small web applications.

# Architecture of the Project
![Static website architecture](https://github.com/Shimanshushinde/Hosting-static-website-with-cloudfront/assets/137445826/10de2fc2-833b-4f3f-a9e2-7949b861375d)

## Prerequisites
Before proceeding, ensure the following:

- AWS account with necessary permissions.
- Familiarity with the AWS Management Console.
- Familiarity with S3 Bucket,Route 53,Certificate Manager and CloudFront.

## Steps to Deploy
### Step 1: Design Your Website
- Design own personal website or download an existing template.

### Step 2: Set Up Amazon S3 Bucket
- Go to the AWS Management Console and open the Amazon S3 console.
- Click "Create bucket" and enter a unique name for your bucket("tech2cloud.com").
- In the "Properties" section, enable "Static website hosting."
- Upload your website files to the bucket.
- Set the bucket permissions to allow public access.

### Step 3: Configure S3 Bucket Permissions

```sh
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::tech2cloud.com/*"
        }
    ]
}
```
### Step 4: Purchase a Custom Domain through Amazon Route 53
- Open the Amazon Route 53 console.
- Choose "Domain registration" and then "Register domain"(eg- http://www.tech2cloud.com). 
  
### Step 5: Generate SSL Certificate from AWS Certificate Manager
- Open AWS Certificate Manager "request a certificate"
  
### Step 6: Create a Record Set in Route 53
- In the "Route 53 hosted zones," create a new record set(CNAME record).
- Copy "CNAME name" from Certificate Manager and Past "Record name & value" Click on Create record

### Step 7: Create a CloudFront Distribution
- In CloudFront Click on "Create Distribution" and Copy & "Enter S3 bucket's endpoint" in Origin Domain.
- Viewer protocol policy "Redirect HTTP to HTTPS.
- Create another Record set i.e.'A record type' and Route Trafic to " Alias to CloudFront Distribution"

### Step 8: Test Website
- Access website using domain name,this may take some time.(eg- http://www.tech2cloud.com). 

### Step 9: Update Website and Deployment
- Updating Website: Make changes to local files and Upload the changes to S3 bucket.
- Testing Updates: Verify that your changes are reflected on your website.

