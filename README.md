# AWS Lambda EBS Snapshot Cleanup

This AWS Lambda function automatically deletes unused EBS snapshots based on the following conditions:

If the snapshot is not attached to any volume, it is deleted.

If the snapshot's associated volume exists but is not attached to a running EC2 instance, it is deleted.

If the snapshot's associated volume no longer exists (i.e., deleted), the snapshot is also deleted.

## Prerequisites

AWS account with access to EC2 and Lambda

IAM role with permissions for EC2 snapshot and volume management

AWS CLI or AWS Management Console for deployment

## AWS Permissions Required

Ensure the IAM role assigned to this Lambda function has the following permissions:

<img width="301" alt="Image" src="https://github.com/user-attachments/assets/99a0117f-c1da-43a8-8ba2-5f657d2c63f9" />

## Deployment Steps

**1. Create a Lambda Function**

Open the AWS Lambda Console.

Click Create function > Author from scratch.

Set the function name, select Python 3.x runtime.

Assign the necessary IAM role with EC2 permissions.

Paste the Python script (lambda_function.py) in the editor and Deploy.

**2. Automate with AWS CloudWatch**

To run this function automatically on a schedule, use Amazon CloudWatch Event Rules:

Go to AWS CloudWatch Console.

Navigate to Rules > Create Rule.

Choose Event Source > Schedule.

Set a Cron Expression (e.g., cron(0 0 * * ? *) for daily execution at midnight UTC).

Select Lambda Function as the target and choose your deployed function.

Click Create Rule.
