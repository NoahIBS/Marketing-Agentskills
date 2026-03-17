# Account Engagement Setup

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

- INTRODUCTION
- PLAN YOUR ACCOUNT ENGAGEMENT IMPLEMENTATION.
- ENGAGEMENT BUSINESS UNIT. INSTALL THE APPEXCHANGE PACKAGE AND CREATE AN ACCOUNT
- Install the AppExchange Application for Account Engagement
- Enable Account Engagement in Salesforce
- SET UP SALESFORCE USER SYNC.
- User Sync Basics
- Identify or Create Users in Salesforce
- Assign Salesforce Users to Account Engagement
- Transfer User Management to Salesforce
- SET UP THE ACCOUNT ENGAGEMENT LIGHTNING APP.
- Give Users Access to the Account Engagement Lightning App
- TRACK PROSPECT ENGAGEMENT IN SALESFORCE.
- Add the Matched Leads Lightning Component
- Comparison of Engagement History Features
- MAP ACCOUNT ENGAGEMENT AND SALESFORCE FIELDS.
- Map Custom Lead Fields to Contact Fields
- Add Standard Fields to Lead and Contact Pages
- Create Custom Prospect Fields
- Map Salesforce and Account Engagement Custom Fields
- Show Account Engagement Data in Salesforce
- MANAGE AND UNPAUSE THE SALESFORCE CONNECTOR.
- Set Up Connected Campaigns
- Define Marketing Data Sharing Rules
- Configure and Unpause the Salesforce Connector (v2)
   - Trigger the Initial Prospect Sync
- ADD A TRACKER DOMAIN IN ACCOUNT ENGAGEMENT.
- IMPLEMENT TRACKING CODE.


**ADD AND VERIFY A DOMAIN FOR EMAIL SENDING.................. 22**

```
IMPLEMENT DKIM AUTHENTICATION FOR ACCOUNT ENGAGEMENT
EMAIL........................................................... 23
```
**NEXT STEPS...................................................... 24**

**Contents**


## INTRODUCTION

Account Engagement is your solution for B2B marketing automation and includes powerful tools that generate leads so your sales team
can close more deals. This guide helps you get your Account Engagement business unit online and ready for your marketing team to
build out marketing assets and get campaigns underway.

Setup includes tasks that often span multiple teams, so it’s important to have everything you need in place before you begin. Use the
planning worksheet in this guide to get organized and identify who you need to successfully set up Account Engagement. If you’re
setting up more than one business unit, we recommend you complete an implementation plan for each business unit.

```
Tip: Business unit setup requires both a Salesforce admin and an Account Engagement admin. To reduce the need for multiple
admins, you can create a custom permission set in Salesforce to delegate Account Engagement tasks to a marketing admin.
```

## PLAN YOUR ACCOUNT ENGAGEMENT IMPLEMENTATION.

Print or save this worksheet to help you map out your implementation from start to finish. If you’re using multiple business units, make
a copy for each one. Some setup tasks require both a Salesforce admin and an Account Engagement admin to complete. We recommend
your implementation stakeholders plan and collaborate closely to execute setup tasks.

Download the Account Engagement Implementation Planning Worksheet

#### SEE ALSO:

```
Designate an Admin for Marketing Setup Tasks
```

## INSTALL THE APPEXCHANGE PACKAGE AND CREATE AN

## ACCOUNT ENGAGEMENT BUSINESS UNIT

First, your Salesforce admin must install the AppExchange package for Account Engagement, then create a business unit in Marketing
Setup. After you assign an admin for your business unit, set up Salesforce User Sync.

## Install the AppExchange Application for Account Engagement

```
Before setting up your Salesforce connector, install the Account Engagement (Pardot) AppExchange package in your Salesforce org.
```
## Enable Account Engagement in Salesforce

```
A Salesforce admin must enable new business units and appoint an Account Engagement admin. If you have multiple business
units, appoint an Account Engagement admin to each unit.
```
Install the AppExchange Application for Account Engagement

```
USER PERMISSIONS
```
```
To install the Pardot
package:
```
**-** Download AppExchange
    Packages (in Salesforce)

Before setting up your Salesforce connector, install the Account Engagement (Pardot) AppExchange
package in your Salesforce org.

```
Important: Don’t install the package directly from AppExchange. You must install the package
as described here.
```
**1.** Get the installation link.

```
This package updates your Salesforce org with a custom application, custom tab, and custom
fields under leads and contacts. To display all fields, modify your view.
```
**2.** Review actions, and click **Install**.
**3.** On Step 2 of the install wizard (Choose security level), select **Grant access to admins only**.

Enable Account Engagement in Salesforce

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
To enable Account
Engagement for your org:
```
**-** Customize Application
    and Modify All Data
To create business units:
**-** Customize Application
    and Modify All Data

A Salesforce admin must enable new business units and appoint an Account Engagement admin.
If you have multiple business units, appoint an Account Engagement admin to each unit.

```
Important: The admin assigned to set up the business unit can’t be changed and their name
can’t be edited. If that user is removed from Account Engagement or their role is updated,
their name remains as a historical record on the business unit setup page.
```
**1.** From Marketing Setup, under Business Unit Setup, click **Assign Admin**.
**2.** Name your business unit and assign your Account Engagement admin. If you’re working with
    multiple business units, we recommend setting up one business unit at a time.
**3.** Save your changes. After you save, the admin receives an email to start the setup process for
    their business unit.
**4.** In Marketing Setup click **Setup Assistant** and turn on Account Engagement in your Salesforce
    org to make the Lightning app available only to your Account Engagement admins.


```
After you complete provisioning and admin assignment, contact your Account Engagement admin to make sure they received the email
to set up their assigned business unit. Work closely with your Account Engagement admin to complete key setup tasks, such as setting
up Salesforce User Sync.
```
Install the AppExchange Package and Create an Account Enable Account Engagement in Salesforce
Engagement Business Unit


## SET UP SALESFORCE USER SYNC.

Salesforce User Sync makes it easy to create and manage Account Engagement users from Salesforce, so we strongly recommend you
set it up as part of your implementation. To set up User Sync, your Salesforce admin assigns users to Account Engagement from Salesforce.
Then, your Account Engagement admin transfers user management to Salesforce.

## User Sync Basics

```
User Sync moves Account Engagement user access settings to Marketing Setup in Salesforce. Synced user records in Account
Engagement are read-only and inherit information from Salesforce.
Identify or Create Users in Salesforce
Before you set up Salesforce User Sync, make sure you know which users need access to Account Engagement. If you’re brand new
to Salesforce, create new users that you then assign to Account Engagement.
Assign Salesforce Users to Account Engagement
First, have your Salesforce admin assign Salesforce users to Account Engagement. We recommend that you begin with the users
who manage the implementation. After users are assigned, transfer user management to Salesforce and return to Marketing Setup
at any time to assign more users.
Transfer User Management to Salesforce
After your Salesforce admin has assigned users to Account Engagement, your Account Engagement admin can map Salesforce
profiles to user roles in Account Engagement. Then, the Account Engagement admin transfers user management to Salesforce to
create an Account Engagement profile for users assigned from Salesforce.
```
User Sync Basics

User Sync moves Account Engagement user access settings to Marketing Setup in Salesforce. Synced user records in Account Engagement
are read-only and inherit information from Salesforce.

```
Note: Pardot is now known as Marketing Cloud Account Engagement. We wish we could snap our fingers to update the name
everywhere, but you can expect to see the previous name in a few places until we replace it, including in the app itself.
```
Process Overview

If you use the legacy version of User Sync, make sure you also review Considerations for Moving to the Latest Version of User Sync. If
you're not sure what your User Sync status is, see Find the Right User Sync Documentation.

To take advantage of Salesforce User Sync, first assign Salesforce users to Account Engagement and then transfer user management to
Salesforce. This process requires a Salesforce admin and an Account Engagement admin. Depending on the structure of your business,
it’s possible you need more than one person to complete all the tasks.

This video walks through User Sync setup: Manage Engagement Users with Salesforce User Sync (English Only).

User Management

Here’s how user management works after user management is transferred to Salesforce.


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

Salesforce Profiles and Account Engagement Roles

```
When you assign users to Account Engagement, you add them to the Marketing Users group or the Sales Users group. User group
assignments can be used for sharing rules, and they correspond to default Account Engagement role assignments.
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

Set Up Salesforce User Sync User Sync Basics


## Identify or Create Users in Salesforce

```
Before you set up Salesforce User Sync, make sure you know which users need access to Account Engagement. If you’re brand new to
Salesforce, create new users that you then assign to Account Engagement.
```
#### SEE ALSO:

```
Add a Single User
Add Multiple Users
```
## Assign Salesforce Users to Account Engagement

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

```
First, have your Salesforce admin assign Salesforce users to Account Engagement. We recommend
that you begin with the users who manage the implementation. After users are assigned, transfer
user management to Salesforce and return to Marketing Setup at any time to assign more users.
Assigned users don’t have access until you set up permissions for Account Engagement Lightning
App. Users assigned to the Sales Users group in Salesforce are given the Sales role in Account
Engagement. Changing a user’s role must be done in Salesforce.
```
**1.** From Marketing Setup, in the Quick Find box, enter _Business_ , and then select **Business**
    **Unit Setup**.
**2.** Next to your business unit, click **Manage Users**.
**3.** Click **Edit User Assignments**.
**4.** Use the dropdowns to add users to the Marketing Users group and the Sales Users group.
**5.** Save your changes. To see a list of your assigned users, click **View All Users**.

Set Up Salesforce User Sync Identify or Create Users in Salesforce


```
After users are assigned, the Account Engagement admin can transfer user management to Salesforce where a profile is created for each
assigned user.
```
## Transfer User Management to Salesforce

```
EDITIONS
```
```
Available in: Account
Engagement business units
created after July 20, 2020
or with Salesforce User Sync
enabled before that date
```
```
USER PERMISSIONS
```
```
To transfer user
management to Salesforce:
```
**-** Account Engagement
    Administrator role

```
After your Salesforce admin has assigned users to Account Engagement, your Account Engagement
admin can map Salesforce profiles to user roles in Account Engagement. Then, the Account
Engagement admin transfers user management to Salesforce to create an Account Engagement
profile for users assigned from Salesforce.
```
**1.** Open the Salesforce Connector page.
    **-** In Account Engagement, select **Admin** and then select **Connectors**. Click next to the
       Salesforce Connector, and select **Edit**.
    **-** In the Lightning app, select **Account Engagement Settings** and then **Connectors**. Click
       next to the Salesforce connector, and select **Edit Settings**.
**2.** Click the **User Sync** tab.
**3.** Review the default user roles for each Salesforce profile. If needed, use the dropdowns to change
    the assigned roles. You can come back and edit the profile-to-role mapping table later.
**4.** Save your changes, and then click **Opt In** to transfer user management to Salesforce.
After user management is transferred, a profile is created for each user assigned in Salesforce. User changes in Salesforce typically take
about 10 minutes to take effect.

Set Up Salesforce User Sync Transfer User Management to Salesforce


## SET UP THE ACCOUNT ENGAGEMENT LIGHTNING APP.

To grant users access to Account Engagement, set up the Account Engagement Lightning app. The Lightning app offers an elevated
integration experience and allows your sales and marketing teams to work side-by-side on one platform.

## Give Users Access to the Account Engagement Lightning App

```
To give users access, an admin must enable the Account Engagement Lightning App and assign the required permissions to users.
```
Give Users Access to the Account Engagement Lightning App

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

To give users access, an admin must enable the Account Engagement Lightning App and assign
the required permissions to users.

Pardot is now known as Marketing Cloud Account Engagement. We wish we could snap our fingers
to update the name everywhere, but you can expect to see the previous name in a few places until
we replace it, including in the app itself.

Before you start this task:

**-** Enable Account Engagement. In Marketing Setup, select **Setup Assistant** and expand the
    **Send Your First Email** section. Next to Turn on Account Engagement Lightning App, click **On**.
**-** Verify that your Account Engagement and Salesforce users are linked. We recommend using
    Salesforce User Sync.
**1.** Give users access to the B2BMA Canvas connected app.

```
a. From Salesforce Setup, in the Quick Find box, enter Connected , and then select Manage
Connected Apps.
b. Select b2bma_canvas.
c. To assign the connected app to users who need access, click Manage Profiles or Manage
Permission Sets.
```
**2.** Assign the Account Engagement User, Sales Cloud User, Service Cloud User, or CRM User permission set.

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

```
a. From Salesforce Setup, in the Quick Find box, enter App Manager , and then select App Manager.
b. Find the Account Engagement app with the App Type Lightning, and then edit it.
c. Click User Profiles , and then select all profiles that need access to the app.
```

```
After the app is enabled, it appears in the App Launcher for all users with a Sales Cloud, Service Cloud, or CRM user seat who have the
app permission assigned.
```
Set Up the Account Engagement Lightning App Give Users Access to the Account Engagement Lightning App


## TRACK PROSPECT ENGAGEMENT IN SALESFORCE.

```
EDITIONS
```
```
Available in: Professional ,
Enterprise , Performance ,
and Unlimited Editions with
Account Engagement
Growth , Plus , Advanced , or
Premium Edition Edition
```
Your campaigns track valuable engagement data that can tell you how well your marketing assets
resonate with your customer base. When you bring all of the activity types and metrics in one place,
you have a collection of features called Engagement History. Decide what Account Engagement
data is most valuable to you and your users, and surface it throughout Salesforce.

Engagement History is an umbrella term for a variety of features–engagement metrics overviews,
engagement activity feeds, and data visualization.

```
Note: Engagement History Dashboards aren’t supported in Account Engagement Sandboxes.
```
```
Add the Matched Leads Lightning Component
Use the Matched Leads Lightning component to find and convert engaged leads from an account record in Salesforce. The component
lists the most relevant account leads ordered by level of engagement.
Comparison of Engagement History Features
Engagement History is a generic term for a collection of fields, related lists, and other Lightning components that make it possible
to show valuable prospect engagement data on your most used records.
```

## Add the Matched Leads Lightning Component

```
EDITIONS
```
```
Lightning App Builder
available in: both Salesforce
Classic and Lightning
Experience
```
```
Lightning Home and utility
bar pages available in:
Lightning Experience
Lightning app and record
pages available in: both the
Salesforce mobile app and
Lightning Experience
```
```
Email application pane
pages available in: both
Salesforce Classic and
Lightning Experience
```
```
Available in: Group ,
Essentials , Professional ,
Enterprise , Performance ,
Unlimited , and Developer
Editions
```
```
USER PERMISSIONS
```
```
To add the Matched Leads
component:
```
**-** Customize Application

```
Use the Matched Leads Lightning component to find and convert engaged leads from an account
record in Salesforce. The component lists the most relevant account leads ordered by level of
engagement.
```
**1.** From Setup, in the Quick Find box, enter _Lightning App Builder_ , and then select
    **Lightning App Builder**.
**2.** Select the page where you want to add the component, and click **Edit**.
**3.** In the Components list, enter _Matched Leads_ , and then select **Matched Leads**.
**4.** Drag the **Matched Leads** component where you want it to appear in the page layout.
**5.** Save your work.
**6.** To specify who can use the page layout, click **Activation** , and then enter the assignment details.

## Comparison of Engagement History Features

```
USER PERMISSIONS
```
```
To use Engagement History:
```
**-** Account Engagement
    User, CRM User, Sales
    Cloud User, or Service
    Cloud User permission
    set

```
Engagement History is a generic term for a collection of fields, related lists, and other Lightning
components that make it possible to show valuable prospect engagement data on your most used
records.
Pardot is now known as Marketing Cloud Account Engagement. We wish we could snap our fingers
to update the name everywhere, but you can expect to see the previous name in a few places until
we replace it, including in the app itself.
```
```
Note:
```
**-** All Engagement History components require a CRM User, Sales Cloud User, or Service
    Cloud User permission set.

Track Prospect Engagement in Salesforce Add the Matched Leads Lightning Component


**-** The majority of Engagement History components are available with all Account Engagement editions. Engagement History
    Dashboards require Growth, Plus, Advanced, or Premium edition.
**-** Components using the List Emails object include automated emails from Engagement Studio, completion actions, and
    automation rules. They don’t include operational emails.
**-** Objects marked in this table with an asterisk (*) show engagement history data by default.

```
Feature Available On... Data Storage Prerequisites
```
```
Metrics Fields • Campaign Salesforce • Connected Campaigns
```
**-** Marketing Link* **•** Field-level security: Access to engagement
**-** Marketing Form* history metrics
**-** Landing Page*
**-** List Email

```
Related List (Marketing Assets) Campaign Salesforce • Connected Campaigns
```
```
Related List (Activities) • Account Engagement • Logged in to Account Engagement via
Salesforce SSO
```
```
Lead
```
**-** Contact
**-** Account
**-** Person Account
**-** List Email
**-** Marketing Link*
**-** Marketing Form*
**-** Landing Page*

```
Engagement History Metrics Campaign Salesforce
Lightning Component
```
**-** Connected Campaigns

```
Engagement History Custom Account Engagement
Lightning Component
```
**- •** Logged in to Account Engagement via
    Salesforce SSO

```
Lead
```
**-** Contact
**-** Person Account

```
CRM Analytics platform
This data is updated
every 8 hours.
```
```
Engagement History Dashboard
Lightning Component
```
**-** Campaign **•** Pardot permission set
**-** Account **•** Connected Campaigns (for a dashboard on
**-** Lead campaign records only)
**-** Contact
**-** Person Account
**-** Opportunity

Track Prospect Engagement in Salesforce Comparison of Engagement History Features


## MAP ACCOUNT ENGAGEMENT AND SALESFORCE FIELDS.

To make sure Account Engagement and Salesforce share data properly, edit your lead and contact page layouts in Salesforce and map
Salesforce and Account Engagement fields.

## Map Custom Lead Fields to Contact Fields

```
Mapping fields in Salesforce ensures that the contact record pulls in all Account Engagement data from the lead record during
conversion.
Add Standard Fields to Lead and Contact Pages
To get a full view of your customer, you can add marketing engagement data to your lead and contact records. Add standard fields
from Account Engagement onto your lead and contact page layouts.
Create Custom Prospect Fields
When the default fields in Account Engagement don’t capture the prospect data you need, create your own custom fields. You can
map and sync your custom fields with the CRM.
Map Salesforce and Account Engagement Custom Fields
To allow syncing, map prospect and account custom fields.
Show Account Engagement Data in Salesforce
The AppExchange application adds Account Engagement fields and Visualforce pages, but they’re not displayed automatically. To
display them, add them to your Salesforce lead and contact page layouts.
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


## Add Standard Fields to Lead and Contact Pages

```
EDITIONS
```
```
Available in: both Salesforce
Classic and Lightning
Experience
```
```
Page layouts available in: all
editions
```
```
Creation and deletion of
page layouts available in:
Professional , Enterprise ,
Performance , Unlimited ,
and Developer Editions
```
```
USER PERMISSIONS
```
```
To add standard fields:
```
**-** Customize Application

```
To get a full view of your customer, you can add marketing engagement data to your lead and
contact records. Add standard fields from Account Engagement onto your lead and contact page
layouts.
```
**1.** Find the Lead or Contact page layout.
    **-** If you’re using Lightning Experience, from Setup, in the Quick Find box, enter _Object_
       _Manager_ , and then select **Object Manager**. Click the name of the object (Lead or Contact)
that you want to manage, and scroll to the Page Layouts section.
    **-** If you’re using Salesforce Classic, from Setup, in the Quick Find box, enter the object name
       (Lead or Contact), and then select **Page Layouts**.
**2.** Open the layout that you want to edit.
**3.** In the Page Layout Builder, select **Fields** , and then scroll to find the Account Engagement fields.
    Pardot is now known as Marketing Cloud Account Engagement. We wish we could snap our
    fingers to update the name everywhere, but you can expect to see the previous name in a few
    places until we replace it, including in the app itself.
**4.** Drag the fields onto your layout.
**5.** To add Account Engagement action buttons to the layout, select **Buttons** , and then drag the
    buttons to your layout.
**6.** Save your work.
**7.** To preview the updated page layout, navigate to a lead or contact record, and then confirm that the selected fields or buttons appear.

## Create Custom Prospect Fields

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
To create custom fields:
```
**-** Account Engagement
    Administrator role

```
When the default fields in Account Engagement don’t capture the prospect data you need, create
your own custom fields. You can map and sync your custom fields with the CRM.
```
**1.** Open the Prospect Fields page.
    **-** In Account Engagement, select **Admin** > **Configure Fields** > **Prospect Fields**.
    **-** In the Lightning app, select **Account Engagement Settings** > **Object and Field**
       **Configuration** > **Prospect Fields**.
**2.** Click **+ Add Custom Field**.
**3.** Name the field. The name is used internally for identification, and isn’t visible to prospects.
**4.** Don’t edit Custom Field ID. This ID isn’t visible to prospects.
**5.** Configure field settings.

Map Account Engagement and Salesforce Fields Add Standard Fields to Lead and Contact Pages


**6.** When finished, click **Create custom field** to save.

## Map Salesforce and Account Engagement Custom Fields

```
USER PERMISSIONS
```
```
To map fields:
```
**-** Account Engagement
    Administrator role

```
To allow syncing, map prospect and account custom fields.
Keep these considerations in mind when mapping fields.
```
**-** Before you can map custom fields, create the corresponding custom field in Account
    Engagement.
**-** If a Salesforce field is already mapped, it doesn’t display in the dropdown.
**-** Custom field mapping isn’t case sensitive. For example, the two custom fields Account_Type
    and account_type on the contact record must map to the same field on the prospect record.
**-** To map a custom field on both the lead object and contact object to the same Account Engagement field, the API name of the
    Salesforce fields must be identical.
**-** Account Engagement fields don’t sync with lookup or geolocation Salesforce field types. Learn how sync behavior works.
**-** Don’t map number type fields to Salesforce phone type fields. Phone fields contain non-number characters and don’t sync correctly.
    Instead, map Salesforce phone type fields to text type fields.
**1.** Open the Prospect Fields page.
    **-** In Account Engagement, select **Admin** > **Configure Fields** > **Prospect Fields**.
    **-** In the Lightning app, select **Account Engagement Settings** > **Object and Field Configuration** > **Prospect Fields**.
**2.** From the Salesforce Field Name dropdown, choose the field you want to map.
**3.** To sync field setting changes from Salesforce, select **Keep this field’s type and possible values (for dropdowns, radio buttons,**
    **checkboxes) in sync with the CRM**.
**4.** (Optional) Edit sync behavior.
Repeat these steps for each custom field you want to sync.

```
Note: Mapping an Account Engagement custom field with a Salesforce field doesn’t trigger a sync with the CRM.
```
## Show Account Engagement Data in Salesforce

```
USER PERMISSIONS
```
```
To customize page layouts:
```
**-** Customize Application
    (in Salesforce)

```
The AppExchange application adds Account Engagement fields and Visualforce pages, but they’re
not displayed automatically. To display them, add them to your Salesforce lead and contact page
layouts.
```
```
Note: Pardot is now known as Marketing Cloud Account Engagement. We wish we could
snap our fingers to update the name everywhere, but you can expect to see the previous
name in a few places until we replace it, including in the app itself.
```
**1.** Open a lead or contact page layout for editing.
**2.** Add the Account Engagement custom fields to the page layout.
    **a.** Add a section to the layout.
    **b.** Name the section.
    **c.** Select **2-Column** , and click **OK**.

Map Account Engagement and Salesforce Fields Map Salesforce and Account Engagement Custom Fields


```
d. Return to the Fields section of the drag-and-drop editor, and scroll right to locate the custom fields.
e. Drag all the custom fields in to the new section.
f. (Optional) Drag the Google Analytics fields to the section.
```
**3.** Add Account Engagement activities and list membership to your layout.
    **a.** Add a section to the layout.
    **b.** Name the section.
    **c.** Select **1-Column** , and click **OK**.
    **d.** In the editor, scroll to the Visualforce Pages section.
    **e.** Drag Pardot Activities, Pardot List Membership, and Pardot Social Data to the new section.
**4.** Save your work.
Repeat these steps for lead and contact page layouts.

Map Account Engagement and Salesforce Fields Show Account Engagement Data in Salesforce


## MANAGE AND UNPAUSE THE SALESFORCE CONNECTOR.

New Account Engagement business units come equipped with Version 2 of the Salesforce connector, which is created in a paused state.
There are a few things we recommend you have set up before you unpause the connector and begin syncing data with Salesforce.

## Set Up Connected Campaigns

```
It’s a great idea to connect your Account Engagement and Salesforce campaigns. You can save time, reduce clutter, and get access
to valuable cross-product features. For example, work with campaign influence attribution models, Engagement History, and Einstein
Campaign Insights for a complete view of your business. Plus, you can work with prospects and data without leaving Salesforce.
```
## Define Marketing Data Sharing Rules

```
If you have Account Engagement Advanced or Premium edition, you can use Marketing Data Sharing rules to define what data you
want to sync with Salesforce objects.
Configure and Unpause the Salesforce Connector (v2)
Version 2 of the Salesforce connector is created in a paused state. An Account Engagement admin must configure the connector
and unpause it to begin syncing data.
```
#### SEE ALSO:

```
Salesforce Connector Settings
```
Set Up Connected Campaigns

It’s a great idea to connect your Account Engagement and Salesforce campaigns. You can save time, reduce clutter, and get access to
valuable cross-product features. For example, work with campaign influence attribution models, Engagement History, and Einstein
Campaign Insights for a complete view of your business. Plus, you can work with prospects and data without leaving Salesforce.

#### SEE ALSO:

```
Connected Campaigns Implementation Guide
```
Define Marketing Data Sharing Rules

If you have Account Engagement Advanced or Premium edition, you can use Marketing Data Sharing rules to define what data you
want to sync with Salesforce objects.

```
Note: Sometimes, assigned users have more access to Salesforce data in Account Engagement than they do in Salesforce. To
restrict access, manually create sharing rules that match your Marketing Data Sharing rules and apply them to the Account
Engagement marketing user group.
```
#### SEE ALSO:

```
Marketing Data Sharing
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

### Trigger the Initial Prospect Sync

```
After you’ve connected Salesforce and Account Engagement, import existing leads and contacts into Account Engagement. The
connector doesn’t automatically create prospects from existing Salesforce leads and contacts. After import, Account Engagement
syncs the prospect record with the existing Salesforce lead or contact record. Future updates to records in either system then sync
automatically.
```
Trigger the Initial Prospect Sync

```
After you’ve connected Salesforce and Account Engagement, import existing leads and contacts into Account Engagement. The connector
doesn’t automatically create prospects from existing Salesforce leads and contacts. After import, Account Engagement syncs the prospect
record with the existing Salesforce lead or contact record. Future updates to records in either system then sync automatically.
```
```
Note: If your business unit allows multiple prospects with the same email address, you must import by CRM ID to match leads
and contacts with prospects. If you don’t import by CRM ID, prospects imported by email address create duplicate leads or contacts
in Salesforce. New Account Engagement business units allow multiple prospects with the same email address by default.
```
Manage and Unpause the Salesforce Connector Configure and Unpause the Salesforce Connector (v2)


## ADD A TRACKER DOMAIN IN ACCOUNT ENGAGEMENT.

```
USER PERMISSIONS
```
```
To manage domains in
Account Engagement:
```
**-** Account Engagement
    Administrator role

Use a tracker domain in Account Engagement to rewrite links and vanity URLs for tracking. To set
up a tracker domain, work with an IT partner or a hosting provider to edit CNAME records.

```
Note: Pardot is now known as Marketing Cloud Account Engagement. We wish we could
snap our fingers to update the name everywhere, but you can expect to see the previous
name in a few places until we replace it, including in the app itself.
```
**1.** Open the Domain Management page.
    **-** In Account Engagement, select **Admin** and then select **Domain Management**.
    **-** In the Lightning app, select **Account Engagement Settings** and then **Domain Management**.
**2.** Click **Add Tracker Domain**.
**3.** Enter a tracking domain.

```
If you use multiple tracker domains, make sure that each subdomain matches the root domain. For example, use go.siteA.com for
the root domain siteA.com.
```
**4.** To allow Account Engagement form code to be used on web pages associated with the tracker domain, select **Allow iframed**
    **assets on this domain**.
    Allowing iframing only for specific domains is an added layer of security for your Account Engagement assets. You can control general
    iframing restrictions in your Business Unit Settings. See Restrict or Limit Iframing for Account Engagement Assets.
**5.** Select a default campaign.
**6.** Work with your IT team or hosting provider to set up a CNAME record for the subdomain you want to use. Set the record to point
    to go.pardot.com.
**7.** Work with your IT team or hosting provider to add validation keys to the CNAME records for your root domain.

```
To download a validation file in TXT format, click Tools. You can also copy the validation key for the domain and add it to a TXT file
you create.
```
**8.** Wait for your DNS to propagate, which can take up to 24 hours.
**9.** From the Domain Management page, click the gear icon for your domain, and click **Validate**.

After you validate a domain, change the default protocol to HTTPS. Then, add the tracking code on your web pages.

Business units created after February 15, 2021 use HTTPS for tracker domains by default. If your business unit was created before February
15, 2021, enable SSL for individual tracker domains to secure them with HTTPS.


## IMPLEMENT TRACKING CODE.

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
To view tracking code:
```
**-** Account Engagement
    Administrator or
    Marketing role

Each Account Engagement campaign has its own unique tracking code. Add the code to a web
page to track visitor and prospect activity. We recommend that you add the code to high-value
pages only, such as landing pages or specific product listings. Don’t place the code on more general
pages like the home page on your website.

```
Important: This process implements first-party tracking code. Business units created after
February 13, 2023 use first-party tracking by default. If you don’t have first-party tracking set
up, update your tracker domains to first-party tracking or you can implement tracking code
for third-party cookie tracking instead.
```
**1.** Open the Domain Management page.
    **-** In Account Engagement, select **Admin** and then select **Domain Management**.
    **-** In the Lightning app, select **Account Engagement Settings** and then **Domain**
       **Management**.
**2.** Scroll to the Tracking Code Generator and select the domain you want to generate code for.
**3.** (Optional) Override the default campaign.
**4.** Copy the code.
**5.** In your web page HTML, paste the campaign tracking code before the close body tag (</body>).


## ADD AND VERIFY A DOMAIN FOR EMAIL SENDING

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
To manage sending
domains:
```
**-** Account Engagement
    Administrator role

To send emails in Account Engagement, you must add at least one verified sending domain. A
domain is verified by a validation key that you add to your DNS records.

```
Note: Looking for a quick overview? Check out this demo video: Configure Email Sending
Domain Authorization
```
**1.** Open the Domain Management page.
    **-** In Account Engagement, select **Admin** and then select **Domain Management**.
    **-** In the Lightning app, select **Account Engagement Settings** and then **Domain**
       **Management**.
**2.** Click **Add New Domain**.
**3.** Enter the domain that you want to send emails from, and click **Create domain**.
**4.** In the Actions column, click **Expected DNS Entries** and copy the validation key.
**5.** Work with your IT team to add the validation key to your DNS configuration as a TXT record for the specific domain or subdomain
    that you want to verify.
**6.** After you update your DNS configuration, return to the Domain Management page in Account Engagement.
**7.** In the Actions column, click **Check DNS Entries** to verify your domain.

Repeat these steps for each domain that you want to send from in Account Engagement.


## IMPLEMENT DKIM AUTHENTICATION FOR ACCOUNT

## ENGAGEMENT EMAIL

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
To manage sending
domains:
```
**-** Account Engagement
    Administrator role

To improve your email deliverability, set up DomainKeys Identified Mail (DKIM) as an additional
form of email authentication. Work with your IT team to implement DKIM for each domain that you
want to send emails from in Account Engagement.

**1.** Open the Domain Management page.
    **-** In Account Engagement, select **Admin** and then select **Domain Management**.
    **-** In the Lightning app, select **Account Engagement Settings** and then **Domain**
       **Management**.
**2.** In the Email Sending Domains section, find the domain that you want to set up DKIM for, and
    click **Expected DNS Entries**.
**3.** Copy the DomainKey value.
**4.** Work with your IT team to add the DomainKey value to your DNS configuration as a TXT record.

After you correctly add your TXT record, your domain shows as verified. If you have errors, Account Engagement provides a link with
details on the Domain Management page.


## NEXT STEPS

After you complete the technical setup for Account Engagement, you can set up any additional features you need. At this point, you
can also bring in your marketing team to start using Account Engagement.

Create and Customize Marketing Assets

Bring in your marketing team to get started creating assets and using Account Engagement. Take advantage of Account Engagement’s
folders and file hosting capabilities, and build out forms, landing pages, templates, and automations for your business.

Recommended Features and Add-Ons

Here are some features we recommend for getting the most out of Account Engagement. Depending on your Account Engagement
edition, these features are available as paid add-ons.

**-** Business to Business Marketing Analytics Plus (B2BMA+): B2BMA+ is a growing collection of intelligent marketing tools for B2B
    marketers. The Account-Based Marketing and Marketing Campaign Intelligence apps help you explore your data and identify
    improvements with Einstein Discovery.
**-** Salesforce Engage: Salesforce Engage lets marketing share its content with sales to boost your company’s selling power. Sales reps
    can use marketing-approved email templates to contact prospects at the right moment and track the effectiveness of the messages
    in Salesforce.
**-** Sandboxes for Account Engagement: Use Sandboxes for Account Engagement to test configuration changes before implementing
    them in your production account. An Account Engagement sandbox is a business unit that is provisioned from a Salesforce sandbox.
    Sandboxes for Account Engagement are available in Advanced and Premium editions, and as a paid add-on in Plus edition.

#### SEE ALSO:

```
B2B Marketing Analytics Plus
Sales Emails and Alerts
Create a Sandbox for Account Engagement
```

