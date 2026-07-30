---
title : "Prerequisites"
date : 2026-06-08 
weight : 2
chapter : false
pre : " <b> 5.2. </b> "
---

To start deploying the **AI Pulmonary Diagnostic Suite** system, we need to prepare the AWS working environment, including granting the necessary IAM permissions and initializing sample data via AWS CloudShell.

In this workshop, we'll use the **N. Virginia (us-east-1)** region.

### 1. Configuring IAM Permissions
Attach the following IAM permission policy to your AWS User or Role to have sufficient rights to deploy and clean up the MLOps resources used in this workshop.

*(Note: In a real-world environment, you should apply the principle of least privilege. The policy below has been relaxed a bit for the convenience of this hands-on lab).*

```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "MLOpsWorkshopPermissions",
            "Effect": "Allow",
            "Action": [
                "sagemaker:*",
                "s3:*",
                "lambda:*",
                "apigateway:*",
                "cloudwatch:*",
                "logs:*",
                "iam:PassRole",
                "iam:CreateRole",
                "iam:AttachRolePolicy",
                "iam:PutRolePolicy"
            ],
            "Resource": "*"
        }
    ]
}
```

After attaching this policy, you can verify your permissions by going to the **IAM Console** -> **Users** -> selecting your user -> **Permissions**. You should see the new policy attached.

![Checking IAM Permissions](/images/5-Workshop/5.2-Prerequisite/iam-policy.png)

### 2. Setting Up a Working Environment with AWS CloudShell
Instead of installing AWS CLI and Python on your personal machine, we'll use **AWS CloudShell** — a browser-based terminal environment that AWS has already configured for us.

**Step 1:** From the AWS Management Console, click the **CloudShell** icon in the top-right corner.

![Opening AWS CloudShell](/images/5-Workshop/5.2-Prerequisite/open-cloudshell.png)

**Step 2:** Wait about 1-2 minutes for CloudShell to initialize the environment. Once the command prompt appears, click **Actions** -> **Upload file** in the top-right corner of CloudShell and upload the project's compressed source code (for example: `AI-Pulmonary-Diagnostic-Suite.zip`).

**Step 3:** Unzip the source code and move into the project folder (since this is a project I'd already built beforehand but hadn't yet deployed to AWS, we need to unzip it and move into the project directory to continue the deployment):

```bash
unzip AI-Pulmonary-Diagnostic-Suite.zip
cd AI-Pulmonary-Diagnostic-Suite-main
```
**Step 4:** Install the Python libraries needed for preprocessing and MLOps from the requirements.txt file:

```bash
pip install -r requirements.txt
```
Once installation finishes, you'll see:

![Installing Python libraries](/images/5-Workshop/5.2-Prerequisite/install-reqs.png)

### 3. Initializing the Data Lake and Sample (Toy) Data
To train the lung diagnosis model, we need X-ray/CT images. The project already includes a script to automatically create an Amazon S3 bucket and upload sample data to the cloud.

Run the following command in CloudShell:

```bash
python src/data/create_toy_dataset.py
```

Once the script finishes running, the system will automatically create the bucket and upload the medical image folders (for example: NORMAL, PNEUMONIA).

To confirm, you can visit the Amazon S3 console. You'll see a newly created bucket containing the images used for the next model training step.

![Checking the S3 Bucket](/images/5-Workshop/5.2-Prerequisite/create-toy-dataset.png)

At this point, your environment is fully ready!

*The final result of the preparation step is going from a dataset of 5,800 images down to a 120-image dataset (toy dataset) to make it easier to deploy the model within the workshop. You can verify this by opening the newly created S3 bucket and viewing the subfolders containing the images.*