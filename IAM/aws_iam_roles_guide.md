# IAM Role

An **IAM Role** is a secure way to grant temporary permissions to users, applications, or AWS services without using long-term usernames or access keys.

## Key Concepts

* **Trust Policy vs. Permission Policy:**
  * **Trust Policy (Trust Relationship):** Defines **who** or **what** is allowed to assume the role (e.g., the `ec2.amazonaws.com` service, another AWS account, or an external identity provider).
  * **Permission Policy:** Defines **what** AWS actions and resources the trusted entity can access once the role is assumed (e.g., `AmazonS3ReadOnlyAccess`).
* **EC2 Instance Profile:** A container for an IAM role that passes role information to an EC2 instance when it starts or updates. When you create a role for EC2 in the AWS Management Console, AWS automatically creates an instance profile with the same name behind the scenes.

## Step-by-Step Guide: Creating and Attaching an IAM Role to an EC2 Instance

### Step 1: Launch an EC2 Instance

Launch an EC2 instance in the AWS Management Console as per your requirements.

### Step 2: Connect to the EC2 Instance

Select your running EC2 instance and click **Connect** (using EC2 Instance Connect or SSH) to open a terminal session.

### Step 3: Test S3 Access Before Attaching a Role

Once connected to the EC2 instance, run the command to list S3 buckets:

```bash
aws s3 ls
```

<!-- Insert screenshot of Access Denied / Unable to locate credentials output here -->

It should **deny access** (or report `Unable to locate credentials`) because the EC2 instance does not yet have an IAM role attached.

### Step 4: Navigate to IAM Roles

Go to the AWS Management Console and navigate to **IAM** > **Roles** > click **Create role**.

<!-- Insert screenshot of IAM Roles dashboard and Create role button here -->

### Step 5: Select Trusted Entity Type

Select the **Trusted entity type** as per your requirements (choose **AWS service**).

<!-- Insert screenshot of Trusted entity type selection here -->

### Step 6: Select Use Case

Under **Use case**, select **EC2** (since we want to create a role for an EC2 instance), then click **Next**.

<!-- Insert screenshot of EC2 use case selection here -->

### Step 7: Add Permissions Policy

In the **Add permissions** step, search for and select **`AmazonS3ReadOnlyAccess`** (because we want to list S3 buckets; if you need access to other AWS services, attach their respective policies). Click **Next**.

<!-- Insert screenshot of attaching AmazonS3ReadOnlyAccess policy here -->

### Step 8: Name the Role and Review Trust Policy

Enter a descriptive **Role name**. On this page, you can also review the **Trust policy** (or trust relationship) JSON, which allows the EC2 service (`ec2.amazonaws.com`) to assume this role via `sts:AssumeRole`.

<!-- Insert screenshot of Role name and Trust policy JSON here -->

### Step 9: Create Role

Click **Create role** to finalize the role creation.

<!-- Insert screenshot of newly created IAM Role here -->

> **Note:** **Maximum session duration** ensures credentials are temporary and dynamic—within the configured duration, temporary security credentials are automatically rotated/changed in the backend by AWS via the Instance Metadata Service (IMDS).

### Step 10: Attach the IAM Role to the EC2 Instance

1. Go back to the **EC2 Console** > **Instances** and select your running instance.
2. Click **Actions** > **Security** > **Modify IAM role**.
3. Select the IAM role you just created from the dropdown and click **Update IAM role**.

<!-- Insert screenshot of EC2 Actions > Security > Modify IAM role here -->

### Step 11: Verify Role Identity and S3 Access from the EC2 Instance

Reconnect to your EC2 instance terminal and verify which IAM role the instance is currently assuming:

```bash
aws sts get-caller-identity
```

The output should display an `assumed-role` ARN containing your new role name. Next, run the list S3 buckets command again:

```bash
aws s3 ls
```

<!-- Insert screenshot of successful S3 bucket listing output here -->

You should now see the list of your S3 buckets returned in the output without configuring any static access keys.

## Troubleshooting & Best Practices

* **Still getting `Unable to locate credentials`?**
  * Confirm that the IAM role update in Step 10 finished saving and that the instance is in the `running` state.
  * Ensure no hardcoded or expired credentials exist in `~/.aws/credentials` on the EC2 instance, as local credential files take precedence over an attached IAM role.
* **Getting `AccessDenied` even with the role attached?**
  * Check if the target S3 bucket has a **Bucket Policy** or **Service Control Policy (SCP)** with an explicit `Deny` statement blocking access.
* **Follow Least Privilege & Clean Up:**
  * In production environments, replace broad managed policies like `AmazonS3ReadOnlyAccess` with custom policies restricted to specific bucket ARNs.
  * Terminate test EC2 instances and delete unused test roles when finished to avoid ongoing AWS charges.