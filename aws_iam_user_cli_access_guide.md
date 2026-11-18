# AWS IAM User: Configuring CLI Access

This guide walks through setting up programmatic access for an AWS IAM user via the AWS Command Line Interface (CLI), configuring credentials locally, and troubleshooting initial `AccessDenied` permission errors.

---

## Step 1: Verify or Install AWS CLI

Open Command Prompt (CMD) on your local system and check if the AWS CLI is installed:

```bash
aws --version
```

> **Note:** If it is not installed, download and install it using the [Official AWS CLI Installation Guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html).

---

## Step 2: Understand Programmatic Access

Before generating credentials, keep in mind how CLI authentication works:

> **Note:** Access Keys (**Access Key ID** and **Secret Access Key**) allow you to interact with AWS services programmatically via the AWS CLI and SDKs.

---

## Step 3: Navigate to IAM Security Credentials

Create an access key for the IAM user you created:

1. Go to **Root account** > **IAM** > **IAM users** > open user (`demo-user-11182026`).
2. Navigate to **Security credentials** > **Access keys** > click **Create access key**.

> **Note:** Access Keys (access key and secret key) allow you to interact with AWS services programmatically via the CLI and SDK.

---

## Step 4: Select Access Key Use Case

Select **Command Line Interface (CLI)** as the use case interface for creating the access key.


---

## Step 5: Retrieve Created Access Keys

Once the key is created, copy or download your **Access Key ID** and **Secret Access Key** immediately.

> **Note:** You can skip optional tags/descriptions and add them later after creating the user.

---

## Step 6: Configure AWS CLI Locally

Open Command Prompt and run the configuration command:

```bash
aws configure
```

Provide the prompted details:
* **AWS Access Key ID:** Enter your Access Key ID
* **AWS Secret Access Key:** Enter your Secret Access Key
* **Default region name:** Enter your preferred AWS region (e.g., `us-east-1`)
* **Default output format:** Enter your preferred format (e.g., `json`)

---

## Step 7: Verify CLI Access (Troubleshooting `AccessDenied`)

Test an AWS CLI command (such as listing IAM users):

```bash
aws iam list-users
```

You will receive an `AccessDenied` error because no permissions have been attached to the IAM user yet.

---

## Step 8: Navigate to Add Permissions

Log back into the AWS Management Console, go to **IAM** > **Users** > select your IAM user, and click **Add permissions**.


---

## Step 9: Attach Read-Only IAM Policy

Attach the `IAMReadOnlyAccess` policy to grant the user read-only access to IAM resources:

1. Select **Attach policies directly**.
2. Search for and select **`IAMReadOnlyAccess`**, then save changes.

---

## Step 10: Verify IAM User Listing in CLI

Run the CLI command again to verify that permissions are working properly:

```bash
aws iam list-users
```

You should now see the list of IAM users returned in the output.
