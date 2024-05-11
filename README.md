In this simple project, I deployed a static website with AWS S3 using ClouFront as the CDN

Unleash Your Brand with a Powerful Static Website

Looking for a fast, affordable, and secure way to establish your online presence? Look no further than static websites! Unlike their dynamic counterparts, static websites are lightweight and straightforward, perfect for showcasing your portfolio, business, or personal brand.

This guide will equip you with the knowledge to build and deploy your static website using the power of Amazon Web Services (AWS). We'll explore:

Static Websites Demystified: Dive into the core principles of static websites, understand their advantages, and discover how they compare to dynamic websites.
Leveraging Amazon S3: Unleash the potential of Amazon S3, your one-stop platform for secure and scalable storage of your website's files.
Boosting Performance with Amazon CloudFront: Maximize your website's speed and accessibility for global audiences by utilizing Amazon CloudFront's Content Delivery Network (CDN) service.
Ready to get started?

By the end of this guide, you'll be equipped to build and launch your stunning static website with the backing of AWS's robust infrastructure.

![Screenshot_2024-05-11_03_34_51](https://github.com/JSPGARBA/Hosting-a-Static-Website-using-AWS-S3-and-CloudFront/assets/86578841/61c4d760-c492-49fb-8c26-de1165dd17e8)


Step 1 - Creating a Bucket on Amazon S3
a) After logging into your AWS Console, under Services > All Services, search for “S3” and click on it to go to the S3 dashboard.
LINK
b) On the S3 Dashboard, click on the Create Bucket button to create a new storage bucket to store your static website files.
c) Enter a bucket name. The name has to be globally unique, so just try with another name if you get an error “Bucket with the same name already exists”.
d) Upload static wesite files


Step 2 - Step 3 - Enabling Static Website Hosting on S3 Bucket
link

Step 3 - Add a Bucket Policy
Before anyone could access the website on the bucket, we need to explicitly tell S3 Bucket to allow that.
On the Bucket overview page, click on the Permissions tab, scroll down and look for Bucket policy section.
b) On the Bucket policy section, click on the Edit button.

c) To grant public read access for your website on this bucket, copy the following bucket policy, and paste it in the Bucket policy editor below. For the “Resource” modify the homeworkout-aws to your bucket name.

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::jspbuckett-aws/*"
        }
    ]
}
You must change the jspbuckett-aws to your bucket name

Click on the Save changes button when you are done.
link

Step 4 Return to the Bucket overview page

Click on the Properties tab

Scroll to the bottom and look for Static website hosting section

You can find the URL under Bucket website endpoint. Click on it to view your website.

link


Step 5 - Creating a CloudFront Distribution
a) From the top navigation under Services > All Services, search for “CloudFront” and click on it.
b) On the CloudFront Distributions page, click on the Create distribution button.
link
c) On the Create distribution page > under Origin section > for Origin domain > enter the Amazon S3 static website endpoint from Step 4 e) earlier.
d) Leave other settings under Default cache behavior section to the default.
e) Under Settings section > for Alternate domain name (CNAME), you may give your own domain name if you have one (we are not using it as of now).
f) Enter “index.html” for Default root object. This file name must match with the index document file name entered in Step 3 c) previously on S3.
g) Leave other settings intact. Scroll to the bottom and click on the Create distribution button.
h) As you remember from earlier, CloudFront will now distribute all your files to edge locations around the world. This process will take some time to complete.
link

Conclusion
You have successfully setup a high performance and highly available static website on AWS using Amazon S3 and Amazon CloudFront. All these without setting up a single server machine.

If you are using a new AWS account, this will most likely cost you nothing as well.


