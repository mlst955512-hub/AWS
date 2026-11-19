# IAM User

This guide walks through creating a new AWS IAM user, configuring console access, logging in as the IAM user, and assigning permissions.

## Step-by-Step Guide: Creating and Configuring an IAM User

### Step 1: Navigate to IAM Users

Log in to the **AWS Management Console**, go to **IAM**, and select **Users** (then click **Create user**).

### Step 2: Enter User Name

Enter a descriptive **User name** for the new IAM user.

### Step 3: Provide Console Access

If you want the user to access the AWS Management Console, select the option **Provide user access to the AWS Management Console** (and choose **I want to create an IAM user**).

<!-- Insert screenshot for Step 3: Console access selection -->

---

### Step 4: Set Custom Password

Select **Custom password**, enter your password, and optionally check **Users must create a new password at next sign-in**.

<!-- Insert screenshot for Step 4: Custom password configuration -->

---

### Step 5: Set Permissions

On the **Set permissions** page, you have three options:

* **Add user to group:** Add the user to an existing group or create a new group.
* **Copy permissions:** Copy the exact permissions from an existing group or user.
* **Attach policies directly:** Attach specific managed or custom policies directly to the user as per your requirements.

<!-- Insert screenshot for Step 5: Set permissions options -->

> **Note:** You can skip this step and add permissions after creating the user.

### Step 6: Review and Create

Review all user details, console access settings, and permissions to ensure everything is accurate.

### Step 7: Create User

Click **Create user** to finalize the account creation.

### Step 8: Retrieve Sign-in Instructions

After user creation, you will be presented with the **Retrieve password / Sign-in instructions** page containing the Console sign-in URL, User name, and Console password.

<!-- Insert screenshot for Step 8: Sign-in instructions and .CSV download -->

> **Note:** You can download the `.csv` file for your records or email the sign-in instructions directly to the user.

### Step 9: Browser Session Behavior (FAQ)

> **Question:** Can we use these sign-in instructions in the same browser session where we are currently logged in to the root account?
>
> **Answer:** No, you cannot log in to an IAM user account in the same standard browser session where the root account is logged in (logging in will sign out the root session). Use an Incognito/Private window or a different browser instead.

### Step 10: Log in as the IAM User

Open a new Incognito/Private browser window and use the sign-in URL and credentials to log in:

* **Account ID or alias:** Enter your 12-digit root AWS Account ID or Account Alias (found under **IAM** > **Dashboard** > **AWS Account**).
* **IAM user name & Password:** Enter the newly created user credentials.
* If you selected the password reset option in **Step 4**, you will be prompted to create a new password upon first sign-in.

<!-- Insert screenshot for Step 10: IAM user sign-in and password reset -->

### Step 11: Observe Default `AccessDenied` State

Upon logging in, you will notice that all resources show **Access Denied**. This happens because no permissions were attached during creation, and IAM users have **no access by default** (implicit deny).

<!-- Insert screenshot for Step 11: Access Denied in AWS Console -->

### Step 12: Add Permissions to the IAM User

Switch back to your **Root / Admin** browser session, go to **IAM** > **Users**, select the newly created IAM user, and click **Add permissions**.

<!-- Insert screenshot for Step 12: Navigating to Add permissions -->

### Step 13: Attach `IAMReadOnlyAccess` Policy

Select **Attach policies directly**, search for **`IAMReadOnlyAccess`**, check the box next to it, and proceed to add the permission.

<!-- Insert screenshot for Step 13: Selecting IAMReadOnlyAccess policy -->

### Step 14: Verify Policy Attachment

Confirm that the **`IAMReadOnlyAccess`** policy is now listed under the user's **Permissions policies**.

<!-- Insert screenshot for Step 14: Policy attached confirmation -->

### Step 15: Verify Access in the IAM User Session

Switch back to your **IAM User** browser window, refresh the IAM dashboard or policies page, and verify that you can now view IAM resources without `AccessDenied` errors.