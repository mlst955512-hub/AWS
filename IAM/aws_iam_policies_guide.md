# IAM Policy

An IAM Policy is a JSON document that defines what actions are allowed or denied on which AWS resources, and under which conditions.

## Key Terminology

* **ARN (Amazon Resource Name):** A unique identifier created by AWS for AWS resources.

<!-- Insert screenshot for ARN / IAM Policy overview here -->

---

## Step-by-Step Guide: Creating an IAM Policy

### Step 1: Navigate to IAM Policies

Go to the AWS Management Console and navigate to **IAM** > **Policies** > click **Create policy**.

<!-- Insert screenshot for Step 1 here -->

### Step 2: Define Policy Using JSON Format

Switch to the **JSON** editor tab to write or review the policy structure:

* **`Version`:** Specifies the supported policy language version, attributes, and syntax (e.g., `"2012-10-17"`).
* **`Statement`:** Defines the main policy rules (what to allow or deny).
* **`Sid` (Statement ID):** An optional identifier or comment used to describe the statement.
* **`Effect`:** Specifies whether the statement results in an **`Allow`** or **`Deny`**.
* **`Action`:** Lists the specific API operations allowed or denied (e.g., `StartInstances`, `StopInstances`, `DeleteBucket`).
* **`Resource`:** Specifies which AWS resource(s) the actions apply to (using ARNs or `*` for all).

<!-- Insert screenshot for Step 2 (JSON format) here -->

### Step 3: Use the Visual Editor (Alternative Method)

You can also configure permissions using the **Visual** editor tab:

1. Click **Select a service** and choose **IAM**.

<!-- Insert screenshot for Step 3 (Visual Editor service selection) here -->

### Step 4: Select Allowed Actions

Choose the actions to allow in the policy based on your requirements. You can also search for specific actions directly (for example: `ListUsers`, `ListUserPolicies`).

<!-- Insert screenshot for Step 4 (Action selection) here -->

### Step 5: Review Generated JSON

After selecting these actions in the Visual editor, switch back to the **JSON** tab—you will see that the JSON policy code has automatically updated to reflect your selections.

<!-- Insert screenshot for Step 5 (Updated JSON tab) here -->

### Step 6: Name and Create the Policy

Click **Next**, give your policy a descriptive name, and click **Create policy**.

> **Note:** Once this policy is created, you can attach it to any IAM user, group, or role.

<!-- Insert screenshot for Step 6 (Name and create policy) here -->