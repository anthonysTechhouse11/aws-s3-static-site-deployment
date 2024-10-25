# Static Website Hosting on AWS S3 with GitHub Actions

This project demonstrates how to host a static website on AWS S3 and automate deployments using GitHub Actions. Whenever code is pushed to the `main` branch, GitHub Actions automatically syncs the latest changes to the S3 bucket.

## Project Overview

- **AWS S3**: Hosts a simple static website.
- **GitHub Actions**: Automates deployment, pushing updates to the S3 bucket.
- **HTML**: Simple `index.html` file for demonstration purposes.

## Prerequisites

1. **AWS Account** with permissions to access S3.
2. **AWS CLI** installed and configured locally.
3. **GitHub Repository Secrets** for `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`.

## Steps to Set Up

### 1. Set Up the S3 Bucket

1. Log into your AWS account and navigate to the **S3** service.
2. Create a new bucket with a unique name (e.g., `my-static-site-demo`).
3. **Enable Static Website Hosting**:
   - Under "Properties," find the "Static website hosting" section and enable it.
   - Set `index.html` as the index document.
4. **Set Bucket Policy for Public Access**:
   - Go to the "Permissions" tab, then "Bucket Policy," and add this policy to allow public access:

   ```json
   {
     "Version": "2012-10-17",
     "Statement": [
       {
         "Sid": "PublicReadGetObject",
         "Effect": "Allow",
         "Principal": "*",
         "Action": "s3:GetObject",
         "Resource": "arn:aws:s3:::your-bucket-name/*"
       }
     ]
   }
