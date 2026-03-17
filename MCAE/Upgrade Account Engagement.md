# Implementation Guide:

# Upgrade Account Engagement

# Business Units

Salesforce, Spring ’ 26

```
Last updated: November 17, 2025
```

© Copyright 2000–2026 Salesforce, Inc. All rights reserved. Salesforce is a registered trademark of Salesforce, Inc., as are other

```
names and marks. Other marks appearing herein may be trademarks of their respective owners.
```

## CONTENTS

- CREATING MULTIPLE PARDOT BUSINESS UNITS.
- Guidelines for Creating Multiple Business Units
- Implementation Planning Worksheet
- IMPLEMENTING MULTIPLE BUSINESS UNITS.
- Enable Account Engagement Lightning App
   - Requirements for the Account Engagement Lightning App
   - Give Users Access to the Account Engagement Lightning App
- Create Additional Business Units
- Upgrade the Connector
   - Considerations for Upgrading to v2 of the Salesforce Connector
   - Upgrade to Salesforce Connector v2
- Implement Salesforce User Sync
   - User Sync Basics
   - Considerations for Moving to the Latest Version of User Sync
   - Assign Salesforce Users to Account Engagement
   - Update Profile and Role Mapping
- Implement Marketing Data Sharing
   - Guidelines for Using Marketing Data Sharing
   - Configure Marketing Data Sharing Rules



## CREATING MULTIPLE PARDOT BUSINESS UNITS.

```
EDITIONS
```
```
Available in: Account
Engagement Advanced and
Premium Editions
```
Enterprises with multiple divisions can focus on their own marketing goals while maintaining a
global view of campaign performance by creating multiple Account Engagement business units.
This guide walks you through the main implementation steps when you upgrade to an Account
Engagement edition that supports multiple business units.

## Guidelines for Creating Multiple Business Units

```
Before you upgrade to an Account Engagement edition that supports multiple business units,
review these guidelines.
Upgrade Checklist
Before you start implementation, address these prerequisites to set up your upgrade for success.
Implementation Planning Worksheet
To make your Account Engagement implementation as efficient as possible, print and use this worksheet to decide how to handle
each task for your implementation. Engage with stakeholders from across your business, such as the admin in charge of reporting,
marketing directors, and sales leadership.
```
Guidelines for Creating Multiple Business Units

Before you upgrade to an Account Engagement edition that supports multiple business units, review these guidelines.

```
Note: In this guide, “upgrade” refers to upgrading to an edition that supports multiple business units. The upgrade is a
behind-the-scenes licensing change that grants your account new functionality. When we refer to setting up your business units,
we use “implement.”
```
Before you upgrade, keep these guidelines in mind.

**-** Upgrading doesn’t require that you use multiple business units. If you need only one business unit, don’t provision additional ones.
**-** We recommend using a Salesforce Certified Partner to complete business unit implementation.
**-** Account Engagement Advanced and Premium Editions include additional business units to further partition your data.
**-** When upgrading, a new business unit doesn’t replace your existing account. Your existing prospects, assets, activity history, metadata,
    and configurations are preserved.
**-** If you currently have multiple Account Engagement instances, each one becomes an individual business unit when you upgrade.
**-** Before upgrading, make sure that all your Account Engagement business units have a verified connector and are connected to the
    same Salesforce org. If you have an unverified v1 connector, upgrading can archive your account.
**-** If you have multiple Salesforce orgs, consider consolidating them before you upgrade your edition. Business units that aren’t connected
    to the same Salesforce org can’t interact with each other.

Before you implement business units, keep these considerations in mind.

**-** Don’t unpause the connector and begin syncing until you’ve configured Marketing Data Sharing rules. Turning on syncing before
    rules are configured can send data to the wrong business unit.
**-** You can’t use the same tracker domain in more than one business unit.
**-** Business units can have shared or dedicated sending IP addresses. We can’t guarantee that all business units use the same shared
    IP address, and dedicated IP addresses can’t be shared between business units.


**-** Sending domains can be unique or the same across business units.
**-** Salesforce Engage is supported but available only in English. Email plug-ins aren’t supported.
**-** Connected campaigns maintain a one-to-one relationship with business units.
    **-** For cross-business unit campaigns, create a campaign per business unit, and then connect them with a parent campaign.
    **-** Aggregated metrics show on in the parent campaign.
**-** Advanced Edition includes two business units. Premium Edition includes five business units. You can purchase additional business
    units as needed.

Upgrade Checklist

```
Before you start implementation, address these prerequisites to set up your upgrade for success.
First, do a general audit of your existing accounts. You want to bring over only relevant data and your best configurations.
```
```
Note: When you upgrade your account to a business unit, your account data is preserved. However, you can’t move historical
data to a new business unit, so plan your upgrade carefully.
```
**-** Review your account’s end-to-end configuration. Make note of how your configuration needs change for business units.
**-** Is the data in your account relevant, recent, and valid? If not, clean up your database before upgrading.
**-** Are you moving from one Account Engagement business unit to multiple business units? Make note of the assets to recreate in your
    new business units and which prospects to import. Perform any other database hygiene you must do before you begin the upgrade.
On your Account Engagement Settings page, get the following information.
**-** Your Salesforce connector version. You need your version number during the upgrade.
**-** Whether your account allows multiple prospects with the same email address (AMPSEA). If your account isn’t AMPSEA-enabled,
    your first business unit isn’t either. However, any additional business units that you provision are AMPSEA-enabled. Whether your
    account is AMPSEA-enabled doesn’t impact enablement, but sync behavior is different between AMPSEA and non-AMPSEA accounts.
Finally, use the Implementation Planning Worksheet to plan your upgrade.

#### SEE ALSO:

```
Find Your Salesforce Connector Version
```
## Implementation Planning Worksheet

```
To make your Account Engagement implementation as efficient as possible, print and use this worksheet to decide how to handle each
task for your implementation. Engage with stakeholders from across your business, such as the admin in charge of reporting, marketing
directors, and sales leadership.
```
```
Task Owner Notes
```
```
Engage with a registered Salesforce Partner
experienced with the implementation of
multiple business units.
```
```
Identify existing business units and audit for
edition & feature adoption. (Optional)
```
Creating Multiple Pardot Business Units Upgrade Checklist


```
Task Owner Notes
```
```
Choose what to base your business units
on—such as geography, divisions, product
lines, or acquisitions.
```
```
Decide how many business units you need
initially.
```
```
Think about how many business units you
need later.
```
```
Decide how many prospects you need
across all business units.
```
```
List which user to appoint as the admin for
each business unit.
```
```
List which users need access to which
business units.
```
```
Decide which Salesforce fields you want in
each business unit.
```
```
Decide which custom objects you want in
each business unit.
```
```
Outline criteria for Marketing Data Sharing
rules, which control what Salesforce data
syncs to each business unit.
```
```
List the tracker domains you want to use
with each business unit.
```
```
Create a plan to aggregate datasets from
each business unit for global reporting.
```
Creating Multiple Pardot Business Units Implementation Planning Worksheet


## IMPLEMENTING MULTIPLE BUSINESS UNITS.

Now that you’ve done the prep work and reviewed the guidelines for implementing multiple business units, begin implementation. We
suggest following these steps in order.

## Enable Account Engagement Lightning App

```
If your company isn’t already using Account Engagement Lightning App, we recommend starting here. Your users get access to the
same user interface that they’re using in Salesforce. It’s customizable, so you can personalize your workspace to include tabs that
you use in Salesforce. The app also provides access to the Business Unit Switcher for users that work with more than one business
unit.
Create Additional Business Units
When you create additional business units, you must appoint admin to activate them. The Account Engagement Setup Assistant
makes it easy to create business units. You can skip this step if you don’t need more than one business unit.
Upgrade the Connector
If you still use Salesforce connector v1, we recommend upgrading to v2. Account Engagement is optimized for v2. Connector v
doesn’t use a Salesforce license, allows access to the Business Unit Switcher, allows on-demand metadata sync, and is always
connected.
Implement Salesforce User Sync
User Sync helps you manage users per business unit from Salesforce Setup. You can use role hierarchy and public group membership
to dynamically dictate which Salesforce users have access to each business unit. Using role hierarchy and public group membership
also ensures that users have the same level of access to data in both Account Engagement and Salesforce.
Implement Marketing Data Sharing
Before you unpause the connector and begin syncing between your business units and Salesforce, set up Marketing Data Sharing.
Use Marketing Data Sharing to create rules for syncing a subset of leads, contacts, opportunities, and custom objects.
Unpause the Connector and Start a Sync
If your connector is in a paused state, unpause it to begin syncing your business units.
```
Enable Account Engagement Lightning App

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
If your company isn’t already using Account Engagement Lightning App, we recommend starting
here. Your users get access to the same user interface that they’re using in Salesforce. It’s
customizable, so you can personalize your workspace to include tabs that you use in Salesforce.
The app also provides access to the Business Unit Switcher for users that work with more than one
business unit.

```
Requirements for the Account Engagement Lightning App
Review requirements and prepare your Salesforce org before you enable the Account
Engagement Lightning App.
Give Users Access to the Account Engagement Lightning App
To give users access, an admin must enable the Account Engagement Lightning App and assign the required permissions to users.
```

### Requirements for the Account Engagement Lightning App

```
Review requirements and prepare your Salesforce org before you enable the Account Engagement Lightning App.
```
```
General
To enable the Account Engagement Lightning App, your org must meet these requirements.
```
**-** Lightning Experience is enabled in Salesforce.
**-** Account Engagement includes a verified Salesforce connector.
    **-** If your business unit was created before February 12, 2019, see Salesforce Connector Implementation Guide (PDF) for help.
    **-** If your business unit was created after February 12, 2019, see Salesforce Connector v2 Implementation Guide (PDF) for help.
    **-** If you manage multiple business units, see Multiple Business Units Implementation Guide (PDF) for help.

```
User Access
To access the Account Engagement Lightning App, users must have a Salesforce or Identity license. Other licenses, such as Salesforce
Platform and Salesforce Platform One, don’t provide the right access.
```
```
Sales or Identity licensed users also need one of the following permission sets:
```
**-** Account Engagement User—Grants access to the app only. Doesn’t include full access to campaigns. Available for all Account
    Engagement editions purchased or upgraded after February 12, 2019.
**-** Sales Cloud User, Service Cloud User, or CRM User—Grants full Salesforce access, including the Account Engagement Lightning App.
    Available for all Account Engagement editions.

Implementing Multiple Business Units Requirements for the Account Engagement Lightning App


### Give Users Access to the Account Engagement Lightning App

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
    **a.** From Marketing Setup, in the Quick Find box, enter _Permission Sets_ , then select **Account Engagement User** , **Sales**
       **Cloud User** , **Service Cloud User** , or **CRM User** from the list.
    **b.** Click **Manage Assignments**.
    **c.** Click **Add Assignments** and choose all users who need access.
    If you prefer using a custom permission set, create and assign one with the **Allow access to all Pardot features** app permission.
    For maximum flexibility, don’t choose a license for the new permission set. To access the Lightning App, users still need the Account
    Engagement User, Sales Cloud User, Service Cloud User, or CRM User permission set license.
**3.** Make the Lightning App visible to profiles.
    **a.** From Salesforce Setup, in the Quick Find box, enter _App Manager_ , and then select **App Manager**.
    **b.** Find the Account Engagement app with the App Type Lightning, and then edit it.
    **c.** Click **User Profiles** , and then select all profiles that need access to the app.

```
After the app is enabled, it appears in the App Launcher for all users with a Sales Cloud, Service Cloud, or CRM user seat who have the
app permission assigned.
```
## Create Additional Business Units

```
USER PERMISSIONS
```
```
To create business units:
```
**-** Manage Marketing
    Setup Tasks

```
When you create additional business units, you must appoint admin to activate them. The Account
Engagement Setup Assistant makes it easy to create business units. You can skip this step if you
don’t need more than one business unit.
```
**1.** From Marketing Setup, in the Quick Find box, enter _Account_ , and then select **Business Unit**
    **Setup**.

Implementing Multiple Business Units Give Users Access to the Account Engagement Lightning App


**2.** Enter a name for the business unit. The company name field in Account Engagement Settings is the business unit name. The company
    name field overwrites the business unit name in Salesforce Setup.
**3.** Choose an admin for the business unit. The admin is responsible for activating the business unit and adding users.
**4.** Save the business unit.
After you save the business unit, the appointed admin receives a welcome email to guide them through the activation process. After
activation, the admin can give other users the Administrator role on the Users page on the Account Engagement Settings tab. The
original admin is read-only and can’t be changed.

## Upgrade the Connector

```
If you still use Salesforce connector v1, we recommend upgrading to v2. Account Engagement is optimized for v2. Connector v2 doesn’t
use a Salesforce license, allows access to the Business Unit Switcher, allows on-demand metadata sync, and is always connected.
```
```
Note: If your business unit already uses v2, skip this step.
```
### Considerations for Upgrading to v2 of the Salesforce Connector

```
Version 2 of the Salesforce connector offers improvements, like on-demand metadata sync, Business Unit Switcher, and the integration
user. Before you upgrade, familiarize yourself with the changes from v1 to v2.
Upgrade to Salesforce Connector v
Upgrade to v2 of the Salesforce connector to take advantage of its benefits. You upgrade each business unit individually.
```
### Considerations for Upgrading to v2 of the Salesforce Connector

```
EDITIONS
```
```
Available in: All Account
Engagement Editions
```
```
Version 2 of the Salesforce connector offers improvements, like on-demand metadata sync, Business
Unit Switcher, and the integration user. Before you upgrade, familiarize yourself with the changes
from v1 to v2.
```
Important Considerations

```
Important:
```
**-** Upgrading the connector makes permanent changes. Carefully read these considerations before starting the upgrade process.
**-** Pardot is now known as Marketing Cloud Account Engagement. We wish we could snap our fingers to update the name
    everywhere, but you can expect to see the previous name in a few places until we replace it, including in the app itself.
**-** The upgrade isn’t reversible. After you confirm the upgrade, you can’t revert to v1.
**-** You can’t change the Salesforce org that your Account Engagement business unit is connected to after the upgrade. Before upgrading,
make sure that your v1 connector is connected to the correct Salesforce production org. If you connect to a sandbox, you can’t
connect to a production org later.
**-** Connector v2 inherits your v1 connector settings.
**-** Decide if you want to use your existing connector user or the integration user. If you opt to use your existing connector user, they
must be added to the Pardot_to_SF_Integration_Secure_Connected_App connected app before you begin the upgrade. If you use
the integration user, a system admin or a user with Modify All Data or Customize Application permission must authenticate to start
the upgrade.

Implementing Multiple Business Units Upgrade the Connector


**-** If you use Marketing Data Sharing and choose the integration user, you can’t limit which Salesforce records are synced with Account
    Engagement. To limit which records are shared to Account Engagement, choose the connector user instead.
**-** After the upgrade, you can’t unarchive v1 connectors in the Account Engagement recycling bin.
**-** To use the Business Unit Switcher, you must upgrade to v2 of the connector and have Salesforce User Sync enabled. As user that is
    assigned to more than one business unit can use the switcher.

Connector v1 and v2 Comparison

```
Feature v1 v2 Details
New business units are created
with a v2 connector in place.
```
```
Automatically created during No Yes
new business unit provisioning
```
```
Connector v2 can use the
integration user, which has the
```
```
Includes Account Engagement No Yes
Integration User
correct permissions to integrate
Account Engagement with
Salesforce
```
```
Connector v1 requires a licensed
user to act as the connector user.
```
```
Uses a Salesforce license Yes No
```
```
Connector v2 can use the
integration user, which doesn’t
consume a Salesforce license.
```
```
Connector v2 lets you pause
prospect and custom object
```
```
Can pause syncing No Yes
```
```
syncing to make configuration
or data changes.
```
```
With the click of a button,
Account Engagement syncs your
```
```
Refresh metadata on demand No Yes
```
```
metadata from Salesforce. For
example, if you create a custom
object and you map it to
Account Engagement, you can
sync it instantly. With v1, you
have to wait for the background
process that pulls the object
(every 4 hours).
```
```
With connector v1, you can
unverify the connection
```
```
Unverify the connector Yes No
```
```
between Account Engagement
and Salesforce to make
configuration or data changes.
Unverifying isn’t necessary with
v2, because you can pause
syncing.
```
```
Considerations for Upgrading to v2 of the Salesforce
Connector
```
Implementing Multiple Business Units


```
Feature v1 v2 Details
```
```
Switch the business unit you’re
working in. This feature is
```
```
Use the Business Unit Switcher No Yes
```
```
supported only with connector
v2 and Salesforce User Sync.
```
```
Connector v1 must be verified
for users to sync. With connector
```
```
Salesforce User Sync Yes Yes
```
```
v2, user data continues to sync,
even when the connector is
paused.
```
What to Expect During and After the Connector Upgrade

**-** If you choose to use the Account Engagement Integration User, they could have a higher level of permissions than your previous
    connector user. Connector v2 is created in a paused state, which gives you a chance to set up Marketing Data Sharing to prevent
    unwanted record syncing. After you have configured Marketing Data Sharing, you must unpause the connector to begin syncing.
    If you selected the connector user, the connector is created in an unpaused state.
**-** During the upgrade process, the connector’s data sync is paused, and the connector status is set to Upgrading.
**-** When the upgrade is complete, the connector’s status is set to a green checkmark, and the user who initiated the upgrade receives
    an email notification.

### Upgrade to Salesforce Connector v

```
USER PERMISSIONS
```
```
To upgrade the Salesforce
connector:
```
**-** Account Engagement
    Administrator role

```
Upgrade to v2 of the Salesforce connector to take advantage of its benefits. You upgrade each
business unit individually.
```
**1.** Navigate to the Account Engagement business unit you want to upgrade.
**2.** In the Lightning app, select **Account Engagement Settings** , and then select **Connectors**.
**3.** Next to the Salesforce connector, click , and select **Upgrade**.

## Implement Salesforce User Sync

```
User Sync helps you manage users per business unit from Salesforce Setup. You can use role hierarchy and public group membership
to dynamically dictate which Salesforce users have access to each business unit. Using role hierarchy and public group membership also
ensures that users have the same level of access to data in both Account Engagement and Salesforce.
```
```
User Sync Basics
User Sync moves Account Engagement user access settings to Marketing Setup in Salesforce. Synced user records in Account
Engagement are read-only and inherit information from Salesforce.
Considerations for Moving to the Latest Version of User Sync
If Salesforce User Sync was enabled before July 20, 2020, there are some important things to know before moving to the latest
version.
```
Implementing Multiple Business Units Upgrade to Salesforce Connector v


```
Assign Salesforce Users to Account Engagement
From Marketing Setup in Salesforce, assign users to Account Engagement. You can assign users individually, or based on public
group, role, or role and subordinates.
Update Profile and Role Mapping
Salesforce User Sync includes a Map Salesforce Profiles to Account Engagement Roles table on the User Sync tab Account Engagement
Settings. An Account Engagement admin can use the table to remap these roles at any time.
```
### User Sync Basics

```
User Sync moves Account Engagement user access settings to Marketing Setup in Salesforce. Synced user records in Account Engagement
are read-only and inherit information from Salesforce.
```
```
Note: Pardot is now known as Marketing Cloud Account Engagement. We wish we could snap our fingers to update the name
everywhere, but you can expect to see the previous name in a few places until we replace it, including in the app itself.
```
```
Process Overview
If you use the legacy version of User Sync, make sure you also review Considerations for Moving to the Latest Version of User Sync. If
you're not sure what your User Sync status is, see Find the Right User Sync Documentation.
To take advantage of Salesforce User Sync, first assign Salesforce users to Account Engagement and then transfer user management to
Salesforce. This process requires a Salesforce admin and an Account Engagement admin. Depending on the structure of your business,
it’s possible you need more than one person to complete all the tasks.
This video walks through User Sync setup: Manage Engagement Users with Salesforce User Sync (English Only).
```
```
User Management
Here’s how user management works after user management is transferred to Salesforce.
```
**-** An Account Engagement user record is created for any user assigned to Account Engagement in Salesforce. You can assign users
    individually, or based on public group, role, or role and subordinates.
**-** The Salesforce user record is the source of truth. All Account Engagement user fields update to match the Salesforce record.
**-** When a user sends an email in Account Engagement, the email is sent from the email address on their Salesforce user record.
**-** Account Engagement user alerts and notifications are sent to their Salesforce email.
**-** If an assigned user is in the recycle bin in Engagement, the user record is restored.
**-** To delete an Account Engagement user, unassign them in Salesforce. Unassigning a user sends their record to the recycle bin in
    Engagement.
**-** If there’s an Account Engagement user with the same email address as a Salesforce user but they’re not mapped, User Sync skips
    them. A new Account Engagement user record isn’t created and the existing user profile isn’t synced.
**-** Changes to user records in Salesforce typically sync within 10 minutes. If you have tens of thousands of users, the sync can take up
    to an hour.

```
Salesforce Profiles and Account Engagement Roles
When you assign users to Account Engagement, you add them to the Marketing Users group or the Sales Users group. User group
assignments can be used for sharing rules, and they correspond to default Account Engagement role assignments.
```
Implementing Multiple Business Units User Sync Basics


```
Salesforce profiles are mapped one-to-one to Account Engagement user roles, but some scenarios require a more granular Salesforce
profile. If your users that share a Salesforce profile need different levels of access in a business unit, you can give a user a more granular
profile.
```
```
Example: Jon and Deepa both have the Marketing profile in Salesforce. Jon needs the Marketing Manager role in the Europe
business unit, and Deepa needs the Marketing role. Because Jon and Deepa share the original profile, and profiles are mapped
one-to-one to user roles, the Salesforce admin creates a unique profile for Jon. The Europe business unit admin maps the new
profile to the correct Account Engagement user role.
```
```
Important: Assign admins and most other Account Engagement users to the Marketing User group in Salesforce. The Sales User
group is only for sales reps who need restricted access to Account Engagement.
After users are assigned to Account Engagement, the Account Engagement admin can update the profile-to-role mapping table for the
Marketing User group, or leave the default mapping in place.
Here’s how roles are determined by default:
```
**-** Users in the Sales Users group always inherit the Sales role in Account Engagement. This role mapping can’t be edited.
**-** Users in the Marketing Users group have their Salesforce profile mapped to the Marketing role in Account Engagement. This mapping
    is editable.
**-** If the Account Engagement admin who created the business unit is in the Marketing Users group, they retain the Account Engagement
    admin role.
This chart shows how user assignments translate to default roles. The default Account Engagement role is editable for all users assigned
to the Marketing Users group in Salesforce.

Implementing Multiple Business Units User Sync Basics


### Considerations for Moving to the Latest Version of User Sync

```
EDITIONS
```
```
Available in: All Account
Engagement Editions where
Salesforce User Sync was
enabled before July 20,
2020
```
```
If Salesforce User Sync was enabled before July 20, 2020, there are some important things to know
before moving to the latest version.
```
```
Note: Pardot is now known as Marketing Cloud Account Engagement. We wish we could
snap our fingers to update the name everywhere, but you can expect to see the previous
name in a few places until we replace it, including in the app itself.
```
**-** After User Sync is enabled, assignments are no longer solely profile-based. Users can be assigned
    to Account Engagement by public group membership, role, role and subordinates, or individually.
**-** Make sure you review User Sync Basics before you transfer user management to Salesforce.
**-** After transferring user management, the User Sync section on the Salesforce connector screen is used only for updating how Salesforce
    profiles map to Account Engagement user roles. The old User Sync settings are replaced by this default behavior.

```
Setting New Default Behavior
```
```
Users inherit their roles from the Map Salesforce Profiles to Pardot
Roles table in user sync settings.
```
```
Update Pardot user role when a user's Salesforce profile changes
```
```
Move Pardot user to the recycle bin when they no longer have Profile-based user assignment doesn’t exist.
an assigned profile
```
```
If there’s a user in Account Engagement with the same CRM
username or email address, User Sync skips them and doesn’t
create a new Account Engagement user record.
```
```
Skip Salesforce user whose email address matches an existing
user record in Pardot
```
### Assign Salesforce Users to Account Engagement

```
EDITIONS
```
```
Available in: All Account
Engagement Editions
```
```
USER PERMISSIONS
```
```
To assign Salesforce users
to business units:
```
**-** Customize Application
    and Manage Users
To enable Salesforce User
Sync or transfer user
management to Salesforce:
**-** Account Engagement
    Administrator role

```
From Marketing Setup in Salesforce, assign users to Account Engagement. You can assign users
individually, or based on public group, role, or role and subordinates.
```
```
Note: We recommend that most users, including admins, be assigned to the Marketing
Users group. Use the Sales Users group for Sales reps only.
```
**1.** From Marketing Setup, in the Quick Find box, enter _Business_ , then select **Business Unit**
    **Setup**.
**2.** Next to your business unit, click **Manage Users**.
**3.** Click **Edit User Assignments**.
**4.** Add users to the Marketing Users group and the Sales Users group.
**5.** Save your changes. To see a complete list of your assigned users, click View All Users.
After you assign users, the Account Engagement admin can update the roles for users in the
Marketing Users group, and then transfer user management to Salesforce.

Implementing Multiple Business Units Considerations for Moving to the Latest Version of User Sync


### Update Profile and Role Mapping

```
USER PERMISSIONS
```
```
To edit Salesforce User Sync
mappings:
```
**-** Account Engagement
    Administrator role

```
Salesforce User Sync includes a Map Salesforce Profiles to Account Engagement Roles table on the
User Sync tab Account Engagement Settings. An Account Engagement admin can use the table
to remap these roles at any time.
```
**1.** Open the Connectors page.
    **-** In Account Engagement, select **Admin** and then select **Connectors**.
    **-** In the Lightning app, select **Account Engagement Settings** and then **Connectors**.
**2.** Click next to the Salesforce connector, and then select **Edit Settings**.
**3.** Find the User Sync section.
    **-** In the Lightning app, click the User Sync tab.
    **-** In Account Engagement, scroll to Salesforce User Sync.
**4.** Use the dropdowns to map Salesforce profiles to Account Engagement roles.
**5.** Save your work.
When you update a profile’s mapping, all assigned Account Engagement users with the Salesforce profile are given the new role within
10 minutes. If you have tens of thousands of users, the sync can take up to an hour.

## Implement Marketing Data Sharing

```
EDITIONS
```
```
Available in: Account
Engagement Lightning App
in Account Engagement
Premium Edition and
Account Engagement
Advanced Edition
purchased or upgraded
after February 12, 2019
```
```
Before you unpause the connector and begin syncing between your business units and Salesforce,
set up Marketing Data Sharing. Use Marketing Data Sharing to create rules for syncing a subset of
leads, contacts, opportunities, and custom objects.
```
### Guidelines for Using Marketing Data Sharing

```
When using Marketing Data Sharing, keep these guidelines in mind.
Configure Marketing Data Sharing Rules
Use Marketing Data Sharing rules to sync a subset of leads, contacts, opportunities, and custom
objects.
```
### Guidelines for Using Marketing Data Sharing

```
When using Marketing Data Sharing, keep these guidelines in mind.
```
**-** If you want to use Marketing Data Sharing rules for leads or contacts, criteria must be created for both leads and contacts.
**-** A lead or contact created by the Account Engagement integration user or connector user match the Marketing Data Sharing rule
    criteria by default.
**-** The ObjectChangeLog isn’t supported in orgs with Marketing Data Sharing. If you previously used the ObjectChangeLog to selectively
    sync records with Account Engagement, convert your sharing preferences to Marketing Data Sharing rules.
**-** Pause the connector before you set up or edit Marketing Data Sharing rules. Otherwise, you risk syncing data to the wrong business
    unit.
**-** If you have multiple business units, you must add criteria for both leads and contacts in each business unit.

Implementing Multiple Business Units Update Profile and Role Mapping


**-** Marketing Data Sharing rules must be unique for each Account Engagement business unit. If rules aren’t unique, sync issues can
    occur that skew your data.
**-** If you create a record in Salesforce that doesn’t meet Marketing Data Sharing rules, it isn’t created in Account Engagement. But if
    you later import a prospect into Account Engagement with the same email as that record, a new lead is created.
**-** If a Salesforce record stops meeting rule criteria, whether due to record updates or changes to rule criteria, the corresponding Account
    Engagement record is sent to the recycle bin.
**-** Prevent duplicate entries by using CRM ID to import prospects. Each prospect is directly matched and linked to a lead or contact
    record in Salesforce based on the ID.
**-** Imported prospects that don’t match Marketing Data Sharing rules are archived.
**-** Sometimes users send Account Engagement email to a lead or contact that doesn’t exist in a business unit. If the lead or contact
    doesn’t match the rule criteria, a prospect is created and archived immediately, and the email isn’t sent to the person.

### Configure Marketing Data Sharing Rules

```
EDITIONS
```
```
Available in: Account
Engagement Lightning App
in Account Engagement
Premium Edition and
Account Engagement
Advanced Edition
purchased or upgraded
after February 12, 2019
```
```
USER PERMISSIONS
```
```
To configure Marketing Data
Sharing rules:
```
**-** Account Engagement
    Administrator role

```
Use Marketing Data Sharing rules to sync a subset of leads, contacts, opportunities, and custom
objects.
```
```
Important: Before making changes, pause the Salesforce connector and ensure that all your
business units are using the Salesforce connector v2.
Before creating Marketing Data Sharing rules, keep these considerations in mind.
```
**-** Each object can have only one rule. Each rule can be based on one Salesforce field and uses
    the equals operator.
**-** You can base a rule only on Salesforce fields that aren’t mapped to an Account Engagement
    field. The field must belong to the rule’s object, and the connector user must have read and
    edit access to it. If needed, change the field-level security to give the connector user access to
    the field.
**-** Marketing Data Sharing rules must be unique for each Account Engagement business unit. If
    a rule isn’t unique, sync issues can occur that skew your data.
**-** The Default setting for an object uses the connector user’s permissions to control which records
    sync. When you create a rule for an object, both the rule and the connector user’s permissions
    control which records sync.
**-** Marketing Data Sharing rules are case-sensitive. Make sure that you match the capitalization
    for the corresponding field values in Salesforce.
**1.** In the Lightning app, select **Account Engagement Settings** and then select **Connectors**. Click next to the Salesforce connector
    and then elect **Edit Settings**. Select **Marketing Data Sharing**.
**2.** Open a rule for editing.
**3.** Configure the rule.
**4.** Save the rule.
    When an object has a rule, the details appear in the Criteria column on the Marketing Data Sharing tab.

```
Example: If you want to sync only the leads in Europe, create a rule on the lead object based on the “region” custom field:
region__c= Europe.
If you use Marketing Data Sharing rules for leads or contacts, criteria must be created for both leads and contacts. If you have multiple
business units, you must add criteria for both leads and contacts in each business unit.
```
Implementing Multiple Business Units Configure Marketing Data Sharing Rules


Unpause the Connector and Start a Sync

```
If your connector is in a paused state, unpause it to begin syncing your business units.
```
```
Note: Users, metadata, and campaigns continue to sync while the connector is paused.
```
```
Warning: Configure Marketing Data Sharing rules before unpausing the connector. Otherwise, your data can sync to the wrong
business unit.
```
**1.** Open the Salesforce Connector page.
    **-** In Account Engagement, select **Admin** and then select **Connectors**. Click next to the Salesforce Connector, and select
       **Edit**.
    **-** In the Lightning app, select **Account Engagement Settings** and then **Connectors**. Click next to the Salesforce connector,
       and select **Edit Settings**.
**2.** Review your connector settings.
**3.** To begin syncing, click the icon, and select **Unpause**.

#### SEE ALSO:

```
Pause the Salesforce Connector v
```
Implementing Multiple Business Units Unpause the Connector and Start a Sync



