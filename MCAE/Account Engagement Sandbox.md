# Account Engagement Sandbox

# Implementation Guide

Salesforce, Spring ’ 26

```
Last updated: December 18, 2025
```

© Copyright 2000–2026 Salesforce, Inc. All rights reserved. Salesforce is a registered trademark of Salesforce, Inc., as are other

```
names and marks. Other marks appearing herein may be trademarks of their respective owners.
```

## CONTENTS

- ACCOUNT ENGAGEMENT SANDBOXES.
- SANDBOXES. CONSIDERATIONS FOR USING ACCOUNT ENGAGEMENT
- INSTALL THE SANDBOX APPEXCHANGE PACKAGE.
- CREATE AN ACCOUNT ENGAGEMENT SANDBOX BUSINESS UNIT.
- TURN ON THE ACCOUNT ENGAGEMENT LIGHTNING APP.
- SET UP SALESFORCE USER SYNC.
- Assign Salesforce Users to Account Engagement
- Transfer User Sync Management to Salesforce
- APP. GIVE USERS ACCESS TO THE ACCOUNT ENGAGEMENT LIGHTNING
- MAP ACCOUNT ENGAGEMENT AND SALESFORCE FIELDS.
- Map Custom Lead Fields to Contact Fields
- CONNECTOR MANAGE AND UNPAUSE THE SALESFORCE-ACCOUNT ENGAGEMENT
- Set Up Connected Campaigns
- Define Marketing Data Sharing Rules
- Add a Tracker Domain and Implement Tracking Code
- Configure and Unpause the Salesforce Connector (v2)
- TESTING FEATURES IN YOUR ACCOUNT ENGAGEMENT SANDBOX.



## ACCOUNT ENGAGEMENT SANDBOXES.

Create Account Engagement sandboxes to test changes and customizations before you implement them in production.

An Account Engagement sandbox is a test version of an Account Engagement Business Unit that's provisioned from a Salesforce sandbox.
Use this guide to get your sandbox online and ready to support your team so that you can implement changes with confidence.

For example, you can test these common scenarios in a sandbox before you make changes in production.

**-** New and updated features
**-** New and updated Marketing Data Sharing rules
**-** Prospect field sync behavior
**-** API configurations
**-** New and updated automation rules and completion actions
**-** User access changes


## CONSIDERATIONS FOR USING ACCOUNT ENGAGEMENT

## SANDBOXES

When using Account Engagement sandboxes, keep these considerations in mind.

**-** Before you can work with a sandbox, you must have Account Engagement correctly set up in production. See the Account Engagement
    Setup Implementation Guide.
**-** Account Engagement sandboxes are supported only in Account Engagement Lightning App. If you purchased Account Engagement
    after October 11, 2021, Account Engagement Lightning App is enabled by default. To set up the app, see the Account Engagement
    Lightning App Implementation Guide.
**-** Account Engagement sandboxes are available in Account Engagement Advanced and Premium editions and as a paid add-on in
    Account Engagement Plus edition.
**-** Data and configurations aren’t shared between sandboxes and production environments and can’t be migrated to production
    environments. When you’re ready to implement changes, recreate them in your production business unit.
**-** A sandbox doesn’t operate with the same support as a production business unit, so performance is sometimes slower.
**-** You can’t move an Account Engagement sandbox to a different Salesforce sandbox.
**-** Account Engagement sandboxes don’t support B2B Marketing Analytics, Engagement History dashboards, the Google Ads connector,
    Salesforce Engage, and email sends, previews, and tests.
**-** If you have a Salesforce sandbox that was created before you purchased Account Engagement Business Units, refresh your Salesforce
    sandbox before you begin. If you can’t refresh the sandbox, use the Match Licenses tool to replicate the licenses, limits, and features
    of your production org in your sandbox.
**-** Don’t refresh your Salesforce sandbox after you create an associated Account Engagement sandbox. Refreshing the Salesforce
    sandbox deletes the Account Engagement sandbox.
**-** Sandboxes without login activity for 150 days are deleted. You’re notified before a sandbox and its data are scheduled to be deleted.
**-** API calls to an Account Engagement sandbox use demo.pardot.com for endpoints, not pi.pardot.com.


## INSTALL THE SANDBOX APPEXCHANGE PACKAGE.

```
USER PERMISSIONS
```
```
To install the Account
Engagement package:
```
**-** Download AppExchange
    Packages (in Salesforce)

Before setting up your Salesforce connector, install the Account Engagement (Pardot) AppExchange
package in your Salesforce org.

```
Important: Don’t install the package directly from AppExchange. You must install the package
as described here.
```
**1.** Go to https://pardot-appexchange.herokuapp.com, and click **Sandbox Environments**.

```
This package updates your Salesforce sandbox org with a custom application, tab, and fields
under leads and contacts. If needed, modify your new view to display the fields.
```
**2.** Click **Install**.
**3.** For step 2 of the install wizard, select **Grant access to admins only**.


## CREATE AN ACCOUNT ENGAGEMENT SANDBOX BUSINESS UNIT.

A Salesforce admin can create an Account Engagement sandbox and assign an admin in the Setup app for the Salesforce sandbox.

```
Note: The admin assigned to set up the sandbox can’t be changed, and their name can’t be edited. If that user is removed from
Account Engagement or their Account Engagement role is updated, their name remains as a historical record on Business Unit
Setup in Salesforce.
```
If you’re using a Salesforce sandbox that was created before you purchased Account Engagement, refresh your sandbox before you
begin. If you can’t refresh it, use Match Licenses to sync your production features, licenses, and permission sets to your sandbox.

**1.** From Marketing Setup, under Business Unit Home, click **Assign Admin**.
**2.** Name your sandbox, and assign your Account Engagement admin. You can assign additional admins as users later in the setup
    process.
**3.** Save your changes.

```
After you save, the Account Engagement admin receives an email to start the sandbox setup process.
```
Contact your Account Engagement admin to make sure that they received the email to set up the sandbox. Work with your Account
Engagement admin to help them set up the sandbox business unit and match it to your production environment.

### SEE ALSO:

```
Push Updated Licenses to Sandbox Orgs
Sandbox Types and Templates
Managing Account Engagement Business Units
```

## TURN ON THE ACCOUNT ENGAGEMENT LIGHTNING APP.

Turn on the Account Engagement Lightning App to make it available in your sandbox org. The app is available only to admins until you
configure user permissions.

**1.** In Marketing Setup, click **Setup Assistant**.
**2.** Expand the Send Your First Email section.

## APP. GIVE USERS ACCESS TO THE ACCOUNT ENGAGEMENT LIGHTNING


## SET UP SALESFORCE USER SYNC.

If your production account uses Salesforce User Sync to create and manage Account Engagement users, set it up as part of your Account
Engagement sandbox implementation.

## Assign Salesforce Users to Account Engagement

```
To use Salesforce User Sync, assign Salesforce users to the Account Engagement sandbox. We recommend first adding the users
necessary to complete your sandbox implementation. You assign more users to the sandbox at any time after implementation.
```
## Transfer User Sync Management to Salesforce

```
After your Salesforce admin has assigned users, your Account Engagement admin can map Salesforce profiles to roles in the sandbox
business unit. Then, the Account Engagement admin transfers user management to Salesforce to create an Account Engagement
profile for each user assigned from Salesforce.
```
### SEE ALSO:

```
Manage Users with Salesforce User Sync
```
Assign Salesforce Users to Account Engagement

```
EDITIONS
```
```
Available in: Account
Engagement business units
created after the Summer
’20 release
```
```
USER PERMISSIONS
```
```
To assign Salesforce users
to business units:
```
**-** Customize application
    and manage users

To use Salesforce User Sync, assign Salesforce users to the Account Engagement sandbox. We
recommend first adding the users necessary to complete your sandbox implementation. You assign
more users to the sandbox at any time after implementation.

**1.** In Marketing Setup, select **Business Unit Setup**.
**2.** Next to your sandbox, click **Manage Users**.
**3.** Click **Edit User Assignments**.
**4.** Use the dropdowns to add users to the Marketing Users group and the Sales Users group.

```
Users assigned to the Sales User group in Salesforce are given the Sales role in Account
Engagement. You can’t change a user’s Account Engagement role in Account Engagement,
but you can change it in Salesforce.
```
**5.** Save your changes.
**6.** To see a list of your Account Engagement users, click **View All Users**.

```
Assigned Account Engagement users don’t have access to the sandbox until you set up permissions for the Account Engagement
Lightning App.
```
Transfer User Sync Management to Salesforce

After your Salesforce admin has assigned users, your Account Engagement admin can map Salesforce profiles to roles in the sandbox
business unit. Then, the Account Engagement admin transfers user management to Salesforce to create an Account Engagement profile
for each user assigned from Salesforce.

**1.** In Account Engagement, select **Account Engagement Settings** and then select **Connectors**.


**2.** Next to the Salesforce connector, click , and select **Edit Settings**.
**3.** On the User Sync tab, review the default Account Engagement roles for the Salesforce profiles. If needed, use the dropdowns to
    change the assigned Account Engagement roles.
    You can come back and edit the profile-to-role mapping table later.
**4.** Save your changes.
**5.** To transfer user management to Salesforce, click **Opt In**.
After user management is transferred, Account Engagement users are created for each user assigned in Salesforce. User changes to
sandbox configurations can take more time than they do in production.

Set Up Salesforce User Sync Transfer User Sync Management to Salesforce


## GIVE USERS ACCESS TO THE ACCOUNT ENGAGEMENT

## LIGHTNING APP

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

Grant users the same access that they have in the production account to the Account Engagement
sandbox.

**1.** Verify that your Account Engagement and Salesforce users are linked.

```
We recommend using Salesforce User Sync. See Manage Users with Salesforce User Sync.
```
**2.** In Marketing Setup, open the Setup Assistant, and make sure that Account Engagement is
    turned on.
**3.** Give users access to the B2BMA Canvas connected app.

```
a. From Salesforce Setup, in the Quick Find box, enter Connected , and then select Manage
Connected Apps.
b. Select b2bma_canvas.
c. To assign the connected app to users who need access, click Manage Profiles or Manage Permission Sets.
```
**4.** Assign permission sets to users.

```
a. From Marketing Setup, in the Quick Find box, enter Permission Sets , and then select Account Engagement User , Sales
Cloud User , Service Cloud User , or CRM User from the list.
b. Click Manage Assignments.
c. Click Add Assignments and select the users who need access.
```
**5.** Make the Lightning App visible to profiles.

```
a. From Salesforce Setup, in the Quick Find box, enter App Manager , and then select App Manager.
b. Find the Account Engagement app with the App Type Lightning, and then select Edit.
c. Click User Profiles , and select the profiles that need access to the app.
```
After the app is enabled, it appears in the App Launcher for users with a Sales Cloud, Service Cloud, or CRM user seat who have the app
permission assigned.


## MAP ACCOUNT ENGAGEMENT AND SALESFORCE FIELDS.

To make sure Account Engagement and Salesforce share data properly, edit your lead and contact page layouts in Salesforce, and map
Salesforce and Account Engagement fields.

## Map Custom Lead Fields to Contact Fields

```
Mapping fields in Salesforce ensures that the contact record pulls in all Account Engagement data from the lead record during
conversion.
```
Map Custom Lead Fields to Contact Fields

```
USER PERMISSIONS
```
```
To map lead fields:
```
**-** Customize Application
    (in Salesforce)

Mapping fields in Salesforce ensures that the contact record pulls in all Account Engagement data
from the lead record during conversion.

```
Note: Pardot is now known as Marketing Cloud Account Engagement. We wish we could
snap our fingers to update the name everywhere, but you can expect to see the previous
name in a few places until we replace it, including in the app itself.
```
```
Important: Don’t map the Pardot URL lead field and Pardot URL contact field. Mapping
these fields to each other creates duplicate prospects and breaks Visualforce pages.
```
**1.** In Salesforce, navigate to the object management settings for leads by going to **Setup** > **Object Manager** > **Lead** > **Fields &**
    **Relationships**.
**2.** In the Lead Custom Fields & Relationships section, click **Map Lead Fields**.
**3.** Click the **Contact** tab, and map the fields.
**4.** Save your work.


## MANAGE AND UNPAUSE THE SALESFORCE-ACCOUNT

## ENGAGEMENT CONNECTOR

New Account Engagement sandboxes include Version 2 of the Salesforce-Account Engagement connector in a paused state. Before
you unpause the connector and begin syncing data with Salesforce, we recommend that you set up Connected Campaigns, Marketing
Data Sharing rules, tracker domains, and code tracking to match your production account.

## Set Up Connected Campaigns

```
If you use Connected Campaigns in production, set it up for your Account Engagement sandbox before you unpause the
Salesforce-Account Engagement connector.
```
## Define Marketing Data Sharing Rules

```
Recreate the Marketing Data Sharing Rules that you’ve set up in production, or test new ones in your sandbox.
Add a Tracker Domain and Implement Tracking Code
Add tracker domains to your account to rewrite links and create branded or vanity URLs. For each Account Engagement campaign,
implement a unique tracking code to track visitor and prospect activity. Work with your IT team or hosting provider to set up CNAME
records and complete these steps.
Configure and Unpause the Salesforce Connector (v2)
Version 2 of the Salesforce connector is created in a paused state. An Account Engagement admin must configure the connector
and unpause it to begin syncing data.
```
Set Up Connected Campaigns

If you use Connected Campaigns in production, set it up for your Account Engagement sandbox before you unpause the Salesforce-Account
Engagement connector.

### SEE ALSO:

```
Connected Campaigns Implementation Guide
```
Define Marketing Data Sharing Rules

```
EDITIONS
```
```
Available in: Account
Engagement Premium and
Advanced Editions
```
Recreate the Marketing Data Sharing Rules that you’ve set up in production, or test new ones in
your sandbox.

Sometimes users have more access to CRM data in Account Engagement than they do in Salesforce.
To restrict access, manually create sharing rules that match your Marketing Data Sharing Rules, and
apply them to the Account Engagement marketing user group.


## Add a Tracker Domain and Implement Tracking Code

```
Add tracker domains to your account to rewrite links and create branded or vanity URLs. For each Account Engagement campaign,
implement a unique tracking code to track visitor and prospect activity. Work with your IT team or hosting provider to set up CNAME
records and complete these steps.
```
```
Note: Tracker domains must be unique across your business units, including your Account Engagement sandbox business unit.
As long as your subdomains are different, your root domains can be the same. Each tracker domain counts towards your account
limit, even if it’s based on the same domain.
```
### SEE ALSO:

```
Add a Tracker Domain
Implement Tracking Code
```
## Configure and Unpause the Salesforce Connector (v2)

```
Version 2 of the Salesforce connector is created in a paused state. An Account Engagement admin must configure the connector and
unpause it to begin syncing data.
```
**1.** Open the Salesforce Connector page.
    **-** In Account Engagement, select **Admin** and then select **Connectors**. Click next to the Salesforce Connector, and select
       **Edit**.
    **-** In the Lightning app, select **Account Engagement Settings** and then **Connectors**. Click next to the Salesforce connector,
       and select **Edit Settings**.
**2.** Review your connector settings.
    The connector uses the integration user to sync. If you want to sync selected records, change the connector user to a user with the
    appropriate permissions or set up Marketing Data Sharing before unpausing.
**3.** To begin syncing, click , and then select **Unpause**.

Manage and Unpause the Salesforce-Account Engagement Add a Tracker Domain and Implement Tracking Code
Connector


## TESTING FEATURES IN YOUR ACCOUNT ENGAGEMENT SANDBOX.

After your Account Engagement sandbox business unit is set up, add features that you use in production or test new features. Use your
sandbox as a blueprint to manually recreate features in your production business unit.

**-** Create Custom Prospect Fields—If the Account Engagement default fields don’t capture the prospect data that you need, create
    your own custom fields. You can map and sync your custom fields with Salesforce.
**-** Show Account Engagement Data in Salesforce—The AppExchange application adds Account Engagement fields and Visualforce
    pages, but they’re not displayed. To display the fields and pages in Salesforce, add them to your Salesforce lead and contact page
    layouts.
**-** B2BMA—B2B Marketing Analytics is a CRM Analytics app containing Salesforce and Account Engagement data populated via your
    Salesforce connector.
**-** Salesforce Engage—With Salesforce Engage, sales reps can use marketing-approved email templates when they email leads and
    track the effectiveness of the messages in Salesforce.


