# AWS-279-Host-A-Website-on-Amazon-S3-
Host A Website on Amazon S3!

Prerequisites:
An AWS account.
Your static website files (HTML, CSS, JS, etc.).
Step-by-Step Process:

Step 1: Create an S3 Bucket
Login to AWS Management Console
Go to the AWS Management Console at https://aws.amazon.com/console/.
Log in with your AWS credentials.
Navigate to S3

In the AWS Management Console, type "S3" in the search bar and select "S3" from the services list.
Create a Bucket

Click the "Create bucket" button.
Enter a unique bucket name (e.g., my-website-bucket). The bucket name must be globally unique.
Choose a region for your bucket.
Click "Create bucket" at the bottom.

Step 2: 
Configure the Bucket for Website Hosting
Select Your Bucket
In the S3 console, click on the bucket you just created.
Enable Static Website Hosting

Go to the "Properties" tab.
Scroll down to the "Static website hosting" section.
Click "Edit".
Select "Enable" for static website hosting.
Specify the index document (e.g., index.html). If you have an error page, specify it (e.g., error.html).
Click "Save changes".


Step 3: Upload Your Website Files
Upload Files
Go to the "Objects" tab within your bucket.
Click the "Upload" button.
Add files or folders containing your website’s content.
Click "Upload" to start the upload process.


Step 4: Set Permissions
Make Your Files Public
After uploading, select all the files and folders you uploaded.
Click "Actions" and select "Make public".
Confirm the action in the dialog that appears.


Step 5: Set Bucket Policy
Bucket Permissions
Go to the "Permissions" tab of your bucket.
Click "Bucket policy".
Paste the following JSON policy into the editor, replacing YOUR-BUCKET-NAME with your bucket name:
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::YOUR-BUCKET-NAME/*"
    }
  ]
}


Step 6: Access Your Website
Website URL
Go to the "Properties" tab of your bucket.
In the "Static website hosting" section, you'll see the "Bucket website endpoint". This is the URL of your website.
Open this URL in your browser to see your website live.


Optional Steps:

Step 7: Domain and SSL (Optional)
Custom Domain with Route 53

If you want to use a custom domain, you can use AWS Route 53 to manage your domain DNS settings.
Create a hosted zone in Route 53.
Add an Alias record pointing to your S3 bucket website endpoint.


SSL with CloudFront
For HTTPS, create a CloudFront distribution.
Use your S3 bucket as the origin.
Use an SSL certificate from AWS Certificate Manager (ACM).
Update your DNS settings to point to the CloudFront distribution.
