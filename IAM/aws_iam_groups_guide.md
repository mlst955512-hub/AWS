# IAM Group

An IAM Group is a collection of IAM users that lets you specify permissions for multiple users at once, making it easier to manage access.

* A user can be a part of multiple groups.
* A user can have permissions inherited from a group or attached individually.

> **Note:** Follow the **Principle of Least Privilege** (only grant the minimum access that is actually required).

---

## Active Directory (AD)

A centralized Identity and Access Management (IAM) system used to manage users, computers, groups, and permissions across an organization.

---

## Step-by-Step Guide: Creating and Configuring an IAM Group

### Step 1: Navigate to IAM User Groups

Go to the AWS Management Console and navigate to **IAM** > **User groups**.

<!-- Insert screenshot for Step 1 here -->

### Step 2: Create a New IAM Group

Create a group named **`Architects`**. During creation, you can select which users will be part of this group.

<!-- Insert screenshot for Step 2 here -->

### Step 3: Create Users and Add Them to the Group

Create two IAM users (**`architect-1`** and **`architect-2`**) and add both of them into the **`Architects`** group.

<!-- Insert screenshot for Step 3 here -->

### Step 4: Attach Permissions to the Group

Open the **`Architects`** group, go to the **Permissions** tab, click **Add permissions**, and select the desired policy to attach.

<!-- Insert screenshot for Step 4 here -->

### Step 5: Verify Inherited Permissions on the IAM User

Open one of the IAM users (`architect-1` or `architect-2`) and check their **Permissions** tab. You will see that the policy is inherited directly from the **`Architects`** group.

<!-- Insert screenshot for Step 5 here -->