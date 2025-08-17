# Flask Serverless App with Zappa

This project demonstrates how to deploy a simple **Flask application** as a **serverless service** on AWS Lambda using **Zappa**.  
It is part of **Lab Activity** for the Cloud Computing module.

---

## 🚀 Project Overview
- A lightweight Flask web app with a single route (`/`) returning:
 ***"Hello, from Serverless Flask!"***

---

- Deployment to AWS Lambda and API Gateway using **Zappa**.
- Configurations defined in `zappa_settings.json`.

---

---

## ⚙️ Configuration (`zappa_settings.json`)

```json
{
  "zappa_deploy_dev": {
    "app_function": "app.app",
    "aws_region": "us-east-1",
    "exclude": [
      "boto3",
      "dateutil",
      "botocore",
      "s3transfer",
      "concurrent"
    ],
    "profile_name": "default",
    "project_name": "lab-activity-20",
    "runtime": "python3.13",
    "s3_bucket": "zappa-s3bucket-1"
  }
}

```

Key values:

- app_function: Entry point for the Flask app (app.app).
- aws_region: AWS region (us-east-1).
- runtime: Python runtime (python3.13).
- s3_bucket: Deployment bucket for Lambda package.

---

## 🛠️ Setup & Deployment

#### 1. Install dependencies
```
pip install flask zappa
```

#### 2. Initialize Zappa (if not already)
```
zappa init
```

#### 3. Deploy the app
```
zappa deploy zappa_deploy_dev
```

#### 4. Update after changes
```
zappa update zappa_deploy_dev
```

#### 5. Remove deployment (optional)
```
zappa undeploy zappa_deploy_dev
```

## 🌐 Accessing the App

- Once deployed, Zappa will provide an API Gateway URL.
- Visit the endpoint in your browser to see:

**Hello, from Serverless Flask!**

---

## 📌 Notes

- Ensure AWS CLI is configured with valid credentials (aws configure).
- The deployment uses the S3 bucket zappa-s3bucket-1.
- Python 3.13 runtime is specified (make sure it’s supported in your AWS Lambda environment).

---
