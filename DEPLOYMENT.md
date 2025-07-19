# Deployment Guide for Tawaf AR Trainer

## Option 1: AWS S3 Static Website Hosting (Recommended)

### Prerequisites
1. AWS Account
2. AWS CLI installed and configured
3. S3 bucket created

### Steps:

#### 1. Create S3 Bucket
```bash
aws s3 mb s3://your-unique-bucket-name
```

#### 2. Configure Bucket for Static Website Hosting
```bash
aws s3 website s3://your-unique-bucket-name --index-document index.html
```

#### 3. Set Bucket Policy for Public Access
Create a file called `bucket-policy.json`:
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::your-unique-bucket-name/*"
        }
    ]
}
```

Apply the policy:
```bash
aws s3api put-bucket-policy --bucket your-unique-bucket-name --policy file://bucket-policy.json
```

#### 4. Deploy Your App
```bash
aws s3 sync . s3://your-unique-bucket-name --exclude '*.git*' --exclude 'node_modules/*' --exclude 'package.json' --exclude 'package-lock.json'
```

#### 5. Access Your App
Your app will be available at:
```
http://your-unique-bucket-name.s3-website-[region].amazonaws.com
```

## Option 2: GitHub Pages (Free)

### Steps:
1. Create a GitHub repository
2. Push your code to the repository
3. Go to Settings > Pages
4. Select source branch (usually `main`)
5. Your app will be available at: `https://your-username.github.io/your-repo-name`

## Option 3: Netlify (Free)

### Steps:
1. Go to [netlify.com](https://netlify.com)
2. Drag and drop your project folder
3. Your app will be deployed instantly
4. Get a URL like: `https://random-name.netlify.app`

## Option 4: Vercel (Free)

### Steps:
1. Go to [vercel.com](https://vercel.com)
2. Import your GitHub repository
3. Deploy automatically
4. Get a URL like: `https://your-project.vercel.app`

## Important Notes for AR Apps

1. **HTTPS Required**: AR.js requires HTTPS for camera access
2. **Mobile Testing**: Test on actual mobile devices, not desktop
3. **Camera Permissions**: Users must allow camera access
4. **Marker Requirements**: Use the hiro marker for testing

## Quick AWS S3 Setup Commands

Replace `your-unique-bucket-name` with a unique name:

```bash
# Create bucket
aws s3 mb s3://your-unique-bucket-name

# Configure for website hosting
aws s3 website s3://your-unique-bucket-name --index-document index.html

# Deploy files
aws s3 sync . s3://your-unique-bucket-name --exclude '*.git*' --exclude 'node_modules/*' --exclude 'package.json' --exclude 'package-lock.json'

# Make public (run this after setting bucket policy)
aws s3api put-bucket-policy --bucket your-unique-bucket-name --policy '{"Version":"2012-10-17","Statement":[{"Sid":"PublicReadGetObject","Effect":"Allow","Principal":"*","Action":"s3:GetObject","Resource":"arn:aws:s3:::your-unique-bucket-name/*"}]}'
``` 