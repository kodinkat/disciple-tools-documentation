# S3 Storage Setup Guide

This guide provides step-by-step instructions for setting up S3-compatible storage with your Disciple.Tools instance. Each provider has specific requirements and configuration steps.

## Prerequisites

Before setting up S3 storage, ensure you have:

- Administrator access to your Disciple.Tools instance
- An account with your chosen S3 provider
- Basic understanding of cloud storage concepts

## General Setup Process

The general process for setting up any S3 provider follows these steps:

1. **Create an S3 bucket** with your provider
2. **Generate access credentials** (Access Key and Secret Key)
3. **Configure bucket permissions** for Disciple.Tools access
4. **Enter credentials** in Disciple.Tools storage settings
5. **Test the connection** to verify everything works

## Provider-Specific Setup

### AWS S3 Setup

AWS S3 is the most popular cloud storage service. Follow these steps to set up AWS S3 with Disciple.Tools:

#### Step 1: Create an S3 Bucket

1. Log in to your [AWS Management Console](https://aws.amazon.com/console/)
2. Navigate to the S3 service
3. Click **Create bucket**
4. Choose a unique bucket name (must be globally unique)
5. Select your preferred region
6. Configure bucket settings:
   - **Block Public Access**: Keep all settings enabled for security
   - **Bucket Versioning**: Optional, but recommended
   - **Server-side encryption**: Enable for additional security


#### Step 2: Create IAM User and Access Keys

1. Navigate to the IAM service in AWS Console
2. Click **Users** → **Create user**
3. Enter a username (e.g., "disciple-tools-storage")
4. Select **Programmatic access** only
5. Attach the following policy (create custom policy if needed). Make sure to replace `your-bucket-name` with your actual bucket name:

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetObject",
                "s3:PutObject",
                "s3:DeleteObject",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::your-bucket-name",
                "arn:aws:s3:::your-bucket-name/*"
            ]
        }
    ]
}
```

6. Save the **Access Key ID** and **Secret Access Key**

#### Step 3: Configure Disciple.Tools

1. In Disciple.Tools, go to **Settings (D.T)** → **Storage**
2. Enable the storage connection
3. Select **AWS S3** as provider
4. Enter your credentials:
   - **Access Key**: Your AWS Access Key ID
   - **Secret**: Your AWS Secret Access Key
   - **Region**: Your bucket's AWS region (e.g., `us-east-1`)
   - **Bucket**: Your S3 bucket name
   - **Endpoint**: Leave blank for AWS S3
   - **Path-style endpoint**: Leave disabled

### MinIO Setup

MinIO is a popular self-hosted S3-compatible storage solution. Here's how to set it up:

#### Step 1: Install and Configure MinIO

1. Install MinIO on your server following the [official documentation](https://min.io/docs/minio/kubernetes/upstream/index.html)
2. Create a bucket using the MinIO console or command line
3. Set up access credentials through MinIO's user management

#### Step 2: Configure MinIO Bucket

1. Access your MinIO console (usually at `http://your-server:9001`)
2. Create a new bucket for Disciple.Tools
3. Configure bucket policies for read/write access
4. Create access keys for the bucket


#### Step 3: Configure Disciple.Tools

1. In Disciple.Tools, go to **Settings (D.T)** → **Storage**
2. Enable the storage connection
3. Select **MinIO** as provider
4. Enter your credentials:
   - **Access Key**: Your MinIO access key
   - **Secret**: Your MinIO secret key
   - **Region**: Use `us-east-1` (MinIO default)
   - **Bucket**: Your MinIO bucket name
   - **Endpoint**: Your MinIO server URL (e.g., `http://your-server:9000`)
   - **Path-style endpoint**: Enable this for MinIO


### Backblaze B2 Setup

Backblaze B2 offers cost-effective cloud storage with S3-compatible API. Here's the setup process:

#### Step 1: Create B2 Account and Bucket

1. Sign up for a [Backblaze B2 account](https://backblaze.com/b2)
2. Create a new bucket in the B2 console
3. Choose a unique bucket name
4. set the bucket type to private
5. Encryption can be enabled for additional security
6. Note your bucket name. Ex : `my-disciple-tools-bucket`
7. Note your Endpoint. Ex : `s3.us-west-000.backblazeb2.com`
8. Note your Region. Ex : `us-west-000`. (you get this from the endpoint, it's the part after `s3.` and before `.backblazeb2.com`)


#### Step 2: Generate Application Keys

1. In the B2 console, go to **Application Keys**
2. Click **Add a New Application Key**
3. Configure the key:
   - **Key Name**: "Disciple.Tools Storage"
   - **Allow access to Bucket(s)**: Select your bucket
   - **Type of Access**: Read and Write
4. Save the **Key ID** and **Application Key**


#### Step 3: Configure Disciple.Tools

1. In Disciple.Tools, go to **Settings (D.T)** → **Storage**
2. Enable the storage connection
3. Select **Backblaze B2** as provider
4. Enter your credentials:
   - **Access Key**: Your B2 Key ID
   - **Secret**: Your B2 Application Key
   - **Region**: Your B2 region (e.g., `us-west-000`)
   - **Bucket**: Your B2 bucket name
   - **Endpoint**: `https://s3.us-west-000.backblazeb2.com` (adjust region)
   - **Path-style endpoint**: Leave disabled


### Cloudflare R2 Setup

Cloudflare R2 offers zero egress fees and S3-compatible storage. Here's how to set it up:

#### Step 1: Create R2 Bucket

1. Log in to your [Cloudflare dashboard](https://dash.cloudflare.com)
2. Navigate to **R2 Object Storage**
3. Click **Create bucket**
4. Enter a bucket name. You can let Cloudflare auto set the location.
5. Under **Settings**, copy the S3 API endpoint for your account. It will look like `https://your-account-id.r2.cloudflarestorage.com`


#### Step 2: Generate API Token

1. Click R2 Object Storage section and then **Manage R2 API tokens**
2. Click **Create Account API token**
3. Configure the token:
   - **Token name**: "Disciple.Tools Storage"
   - **Permissions**: Object Read & Write
   - **Bucket**: Select "Apply to specific buckets only" and then select your bucket
4. Save the **Access Key ID** and **Secret Access Key**


#### Step 3: Configure Disciple.Tools

1. In Disciple.Tools, go to **Settings (D.T)** → **Storage**
2. Enable the storage connection
3. Select **Cloudflare R2** as provider
4. Enter your credentials:
   - **Access Key**: Your R2 Access Key ID
   - **Secret**: Your R2 Secret Access Key
   - **Region**: `auto` (Cloudflare R2 default)
   - **Bucket**: Your R2 bucket name
   - **Endpoint**: `https://your-account-id.r2.cloudflarestorage.com` (make sure not to include /bucket-name)
   - **Path-style endpoint**: Leave disabled for R2


## Testing Your Setup

After configuring any provider, always test your connection:

1. Click the **Test Connection** button in Disciple.Tools storage settings
2. Wait for the test to complete
3. Check for any error messages
4. If successful, you'll see a confirmation message

![Connection Test Success](./imgs/storage/setup/connection-test-success.png)


## Troubleshooting Setup Issues

Common setup issues and solutions:

### Connection Timeout
- Check your endpoint URL
- Verify network connectivity
- Ensure firewall allows outbound HTTPS connections

### Access Denied Errors
- Verify your access keys are correct
- Check bucket permissions
- Ensure the bucket exists and is accessible

### Invalid Region Errors
- Use the correct region format for your provider
- For some providers, use `auto` or `us-east-1` as default

For more detailed troubleshooting, see the [Storage Troubleshooting Guide](./storage-troubleshooting.md).

---

## Next Steps

- [Learn about user file upload features →](./storage-usage.md)
- [Troubleshoot common issues →](./storage-troubleshooting.md)
- [Return to main storage documentation →](./storage.md)
