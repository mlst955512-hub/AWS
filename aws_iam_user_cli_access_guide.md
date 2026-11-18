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

<img width="841" height="141" alt="image" src="https://github.com/user-attachments/assets/c4236371-5d79-400c-a6bc-848e54f7c2b0" />

---

## Step 3: Navigate to IAM Security Credentials

Create an access key for the IAM user you created:

1. Go to **Root account** > **IAM** > **IAM users** > open user (`demo-user-11182026`).
2. Navigate to **Security credentials** > **Access keys** > click **Create access key**.

> **Note:** Access Keys (access key and secret key) allow you to interact with AWS services programmatically via the CLI and SDK.

<img width="1144" height="248" alt="image" src="https://github.com/user-attachments/assets/4b7c17bf-e1ff-42b8-83f5-5202a63c323e" />

---

## Step 4: Select Access Key Use Case

Select **Command Line Interface (CLI)** as the use case interface for creating the access key.

<img width="914" height="357" alt="image" src="https://github.com/user-attachments/assets/e2531647-72d8-453b-a83a-832862b15b65" />

---

## Step 5: Retrieve Created Access Keys

Once the key is created, copy or download your **Access Key ID** and **Secret Access Key** immediately.

<img width="809" height="276" alt="image" src="https://github.com/user-attachments/assets/fe8dcca7-9e30-4f9a-83f0-cd06f6989359" />

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

<img width="1109" height="108" alt="image" src="https://github.com/user-attachments/assets/6fceeb87-2502-41b4-b607-60c2789a3ffb" />

---

## Step 7: Verify CLI Access (Troubleshooting `AccessDenied`)

Test an AWS CLI command (such as listing IAM users):

```bash
aws iam list-users
```

You will receive an `AccessDenied` error because no permissions have been attached to the IAM user yet.

<img width="1109" height="102" alt="image" src="https://github.com/user-attachments/assets/c0c42cb6-0347-446b-b959-2bef27d09304" />

---

## Step 8: Navigate to Add Permissions

Log back into the AWS Management Console, go to **IAM** > **Users** > select your IAM user, and click **Add permissions**.

<img width="714" height="350" alt="image" src="https://github.com/user-attachments/assets/1c4b66c9-77cb-46c1-b132-6b85baa81ad4" />

---

## Step 9: Attach Read-Only IAM Policy

Attach the `IAMReadOnlyAccess` policy to grant the user read-only access to IAM resources:

1. Select **Attach policies directly**.
2. Search for and select **`IAMReadOnlyAccess`**, then save changes.

<img width="1144" height="444" alt="image" src="https://github.com/user-attachments/assets/881d2d41-dc46-4ec1-98f8-5c7a229bf78a" />

<img width="1144" height="227" alt="image" src="https://github.com/user-attachments/assets/c94edd32-2329-4e5b-9046-302200ccc9a9" />

---

## Step 10: Verify IAM User Listing in CLI

Run the CLI command again to verify that permissions are working properly:

```bash
aws iam list-users
```

You should now see the list of IAM users returned in the output.

<img width="899" height="530" alt="image" src="https://github.com/user-attachments/assets/a721996e-b108-4d63-bcd5-9be9b047ac15" />