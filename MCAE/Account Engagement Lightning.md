# Account Engagement Lightning

# App Implementation Guide

Salesforce, Spring ’ 26

```
Last updated: November 17, 2025
```

© Copyright 2000–2026 Salesforce, Inc. All rights reserved. Salesforce is a registered trademark of Salesforce, Inc., as are other

```
names and marks. Other marks appearing herein may be trademarks of their respective owners.
```

## CONTENTS

- Pardot Lightning App Implementation Guide
- Requirements for the Account Engagement Lightning App
- What Salesforce Data Is Available in Account Engagement?
- Give Users Access to the Account Engagement Lightning App
- Guidelines for Using the Account Engagement Lightning App
- Troubleshooting Common Account Engagement Lightning App Problems



## Pardot Lightning App Implementation Guide

```
EDITIONS
```
```
Available in: Professional ,
Enterprise , Performance ,
and Unlimited Editions with
Account Engagement
```
With Account Engagement Lightning app, your sales and marketing teams can operate side by
side on one platform. Follow this guide to make implementing the app quick and easy.

## Requirements for the Account Engagement Lightning App

```
Review requirements and prepare your Salesforce org before you enable the Account
Engagement Lightning App.
What Salesforce Data Is Available in Account Engagement?
Account Engagement and Salesforce have different authorization and sharing models. Data is shared through the Salesforce connector
via the connector user, so Account Engagement can show any data that the connector user has access to. Because of how the
systems connect, you can assume that Account Engagement users have at least as much access to Salesforce data as the connector
user.
Give Users Access to the Account Engagement Lightning App
To give users access, an admin must enable the Account Engagement Lightning App and assign the required permissions to users.
Guidelines for Using the Account Engagement Lightning App
Keep these guidelines in mind when using Account Engagement in Lightning Experience.
Troubleshooting Common Account Engagement Lightning App Problems
Find out how to solve the most common problems with Account Engagement Lightning app enablement.
```
Requirements for the Account Engagement Lightning App

Review requirements and prepare your Salesforce org before you enable the Account Engagement Lightning App.

General

To enable the Account Engagement Lightning App, your org must meet these requirements.

**-** Lightning Experience is enabled in Salesforce.
**-** Account Engagement includes a verified Salesforce connector.
    **-** If your business unit was created before February 12, 2019, see Salesforce Connector Implementation Guide (PDF) for help.
    **-** If your business unit was created after February 12, 2019, see Salesforce Connector v2 Implementation Guide (PDF) for help.
    **-** If you manage multiple business units, see Multiple Business Units Implementation Guide (PDF) for help.

User Access

To access the Account Engagement Lightning App, users must have a Salesforce or Identity license. Other licenses, such as Salesforce
Platform and Salesforce Platform One, don’t provide the right access.

### 1


```
Sales or Identity licensed users also need one of the following permission sets:
```
**-** Account Engagement User—Grants access to the app only. Doesn’t include full access to campaigns. Available for all Account
    Engagement editions purchased or upgraded after February 12, 2019.
**-** Sales Cloud User, Service Cloud User, or CRM User—Grants full Salesforce access, including the Account Engagement Lightning App.
    Available for all Account Engagement editions.

## What Salesforce Data Is Available in Account Engagement?

```
Account Engagement and Salesforce have different authorization and sharing models. Data is shared through the Salesforce connector
via the connector user, so Account Engagement can show any data that the connector user has access to. Because of how the systems
connect, you can assume that Account Engagement users have at least as much access to Salesforce data as the connector user.
```
```
Authorization and Sharing Basics
Authorization is a user’s ability to read, create, update, or delete an object. Sharing is a user’s ability to view, update, or delete a record.
Salesforce has another level in its sharing model—field level security. Field permissions control whether a user can see, edit, and delete
the value for a particular field on an object.
```
```
How It’s Controlled in Account
Engagement
```
```
Security Type How It’s Controlled in Salesforce
```
```
Authorization Profiles and permission sets User roles
```
```
Organization-wide sharing settings, role Groups and folders
hierarchy, sharing rules, manual sharing.
```
```
Sharing
```
```
Field Security Field level security None
```
### 2

Pardot Lightning App Implementation Guide What Salesforce Data Is Available in Account Engagement?


```
Salesforce uses a layered data sharing design that allows you to expose different data sets to different users. This sharing model lets
users do their jobs without seeing data they aren’t supposed to see. There are many ways to control data visibility.
In Account Engagement, access to data is controlled by user roles, groups, and folder permissions. User roles define which features and
data a user can access. Folder permissions give folder access to specific user groups. Folders can’t be used to limit user access to prospects
because prospects can’t be put in folders.
```
```
Note: When an Account Engagement user is connected to a Salesforce user, their permissions in Salesforce control what data
they see in Salesforce.
```
```
Visibility Conflicts
When an Account Engagement user has Salesforce permissions that are more restrictive than the connector user, they can view Salesforce
data in Account Engagement that they don’t have permission to view in Salesforce. This situation is called a visibility conflict.
```
```
Example: Pat is a Salesforce user who doesn’t have permission to view Salesforce campaigns. His Salesforce user is synced to an
Account Engagement user. Pat works on an engagement program and creates a step that adds a prospect to a Salesforce campaign.
Pat sees all synced Salesforce campaigns in the dropdown, and can choose any for the step. Because the connector user has
permission to view and edit campaigns in Salesforce, Pat also has access to view and edit Salesforce campaigns.
To minimize visibility conflicts, we recommend the following steps.
```
**-** Decide what kind of visibility you want your users to have, and document those requirements.
**-** Have your system admins collaborate so that each system is configured to meet your requirements.
**-** Limit the number of users whose Salesforce access is less than the connector user.
**-** When in doubt, contact Salesforce Customer Support for guidance.

## Give Users Access to the Account Engagement Lightning App

```
EDITIONS
```
```
Available in: Professional ,
Enterprise , Performance ,
and Unlimited Editions with
any Account Engagement
Edition
```
```
USER PERMISSIONS
```
```
To enable the Account
Engagement Lightning app:
```
**-** Customize Application
To edit app permissions:
**-** Manage Profiles and
    Permission Sets

```
To give users access, an admin must enable the Account Engagement Lightning App and assign
the required permissions to users.
Pardot is now known as Marketing Cloud Account Engagement. We wish we could snap our fingers
to update the name everywhere, but you can expect to see the previous name in a few places until
we replace it, including in the app itself.
Before you start this task:
```
**-** Enable Account Engagement. In Marketing Setup, select **Setup Assistant** and expand the
    **Send Your First Email** section. Next to Turn on Account Engagement Lightning App, click **On**.
**-** Verify that your Account Engagement and Salesforce users are linked. We recommend using
    Salesforce User Sync.
**1.** Give users access to the B2BMA Canvas connected app.
    **a.** From Salesforce Setup, in the Quick Find box, enter _Connected_ , and then select **Manage**
       **Connected Apps**.
    **b.** Select **b2bma_canvas**.
    **c.** To assign the connected app to users who need access, click **Manage Profiles** or **Manage**
       **Permission Sets**.
**2.** Assign the Account Engagement User, Sales Cloud User, Service Cloud User, or CRM User permission set.

### 3

Pardot Lightning App Implementation Guide Give Users Access to the Account Engagement Lightning App


```
a. From Marketing Setup, in the Quick Find box, enter Permission Sets , then select Account Engagement User , Sales
Cloud User , Service Cloud User , or CRM User from the list.
b. Click Manage Assignments.
c. Click Add Assignments and choose all users who need access.
If you prefer using a custom permission set, create and assign one with the Allow access to all Pardot features app permission.
For maximum flexibility, don’t choose a license for the new permission set. To access the Lightning App, users still need the Account
Engagement User, Sales Cloud User, Service Cloud User, or CRM User permission set license.
```
**3.** Make the Lightning App visible to profiles.
    **a.** From Salesforce Setup, in the Quick Find box, enter _App Manager_ , and then select **App Manager**.
    **b.** Find the Account Engagement app with the App Type Lightning, and then edit it.
    **c.** Click **User Profiles** , and then select all profiles that need access to the app.

```
After the app is enabled, it appears in the App Launcher for all users with a Sales Cloud, Service Cloud, or CRM user seat who have the
app permission assigned.
```
## Guidelines for Using the Account Engagement Lightning App

```
Keep these guidelines in mind when using Account Engagement in Lightning Experience.
```
**-** Navigation is slightly different than standalone Account Engagement.
**-** Tabs for Engagement Studio and Account Engagement Campaigns aren’t displayed by default. Users can add these tabs themselves,
    or a Salesforce admin can add them for all users.
**-** To use the app in Safari, disable the Prevent cross-site tracking preference, which blocks access from Lightning Experience.
**-** Links to Account Engagement in system emails point to the standalone app, not the corresponding screen in the Lightning app.
**-** You can add, remove, and reorder tabs, but you can’t edit sidebar items.

## Troubleshooting Common Account Engagement Lightning App Problems

```
Find out how to solve the most common problems with Account Engagement Lightning app enablement.
You don’t see the b2bma_canvas connected app
Confirm that you’re enabling the app in a production environment. The Account Engagement Lightning app isn’t available in
developer or trial orgs. If you still don’t see the app, contact your Salesforce Account Executive.
Users get an error: “You don’t have permission to view application within namespace[b2bma] and API name [b2bma_canvas]”
Give users access to the connected app.
When users open the app, it doesn’t load
Make sure that your Salesforce connector is verified and that you have connected your users.
Users don’t see the app in the App Launcher
Make sure that Account Engagement Lightning app is enabled. Then, make sure that your users have the CRM User, Sales Cloud
User, or Service Cloud User permission set.
```
### 4

Pardot Lightning App Implementation Guide Guidelines for Using the Account Engagement Lightning App


