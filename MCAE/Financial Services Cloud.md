# Financial Services Cloud

# Installation Guide

Salesforce, Spring ’ 26

```
Last updated: November 17, 2025
```

© Copyright 2000–2026 Salesforce, Inc. All rights reserved. Salesforce is a registered trademark of Salesforce, Inc., as are other

```
names and marks. Other marks appearing herein may be trademarks of their respective owners.
```

## CONTENTS

- Get Ready to Use Financial Services Cloud
- Pre-Installation Tasks for Accounts and User Profiles
- Pre-Installation Tasks for Lightning Experience
- Financial Services Cloud Packages
- Install the Managed Package
- Install the Unmanaged Extension Packages
- Post-Installation Tasks
- Configure Navigation to Individual and Group Profiles
- Lightning Pages Setup
- Add Values to the Lead Status Picklist
- Add Values to the Opportunity Stage Picklist
- Add Users
- Page Layouts and Global Actions Setup
- Add Customer Roles
- Deploy the Client Segmentation App
- Enable CRM Analytics
- Assign Client Segmentation App App Administrator Permissions
- Assign Client Segmentation App User Permissions
- Get Your Data Ready to Create the Client Segmentation App
- Set Field-Level Security to Enable Creation of the Client Segmentation App
- Create and Share an App from the Client Segmentation App Template
- Schedule the Data Synch and Dataflow for the Client Segmentation App
- Understand Client Segmentation App Limitations



## Get Ready to Use Financial Services Cloud

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
To start using Financial Services Cloud, complete the tasks in this guide.

```
Note: When creating custom fields or objects, don’t use the same API names as any packaged
objects or fields. If you use the same names, the custom fields or objects can interfere with
flows, processes, and triggers in Financial Services Cloud.
```
## Pre-Installation Tasks for Accounts and User Profiles

```
Before installing Financial Services Cloud, set up accounts and the user profiles.
Pre-Installation Tasks for Lightning Experience
Financial Services Cloud requires Lightning Experience. Configure Lightning Experience before installing the Financial Services Cloud
packages.
```
Pre-Installation Tasks for Accounts and User Profiles

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
Before installing Financial Services Cloud, set up accounts and the user profiles.

1. Enable the Contacts to Multiple Accounts Feature
    The Contacts to Multiple Accounts feature must be enabled to support the Financial Services
    Cloud data model.
2. Create the User Profiles

```
You use profiles to grant advisors, personal bankers, and relationship managers access to
Financial Services Cloud features. To create the required profiles, clone and customize the
Standard User profile provided by Salesforce.
```
Enable the Contacts to Multiple Accounts Feature

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
The Contacts to Multiple Accounts feature must be enabled to support the Financial Services Cloud
data model.

**1.** From Setup, enter _Account Settings_ in the Quick Find box, and then select **Account**
    **Settings**.
**2.** Select Allow users to relate a contact to multiple accounts.


Create the User Profiles

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
You use profiles to grant advisors, personal bankers, and relationship managers access to Financial
Services Cloud features. To create the required profiles, clone and customize the Standard User
profile provided by Salesforce.
When you install the Financial Services Cloud packages, map these cloned profiles to the Advisor,
Personal Banker, and Relationship Manager profiles provided in each package.
```
**1.** From Setup, enter _Profiles_ in the Quick Find box, and then select **Profiles**.
**2.** Clone the Standard User profile.
**3.** Give it a name, such as _Advisor_.
**4.** Save your changes.
**5.** Repeat to create the Personal Banker and Relationship Manager profiles.

## Pre-Installation Tasks for Lightning Experience

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Financial Services Cloud requires Lightning Experience. Configure Lightning Experience before
installing the Financial Services Cloud packages.
```
1. Enable Lightning Experience
    To use Financial Services Cloud, Lightning Experience must be enabled in your org. Financial
    Services Cloud is supported only in Lightning Experience.

Enable Lightning Experience

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
To use Financial Services Cloud, Lightning Experience must be enabled in your org. Financial Services
Cloud is supported only in Lightning Experience.
```
**1.** From Setup, click **Get Started** in the Migration Assistant tile at the top of the menu.
**2.** Choose which features to enable. Consider enabling the recommended supporting features.

```
Tip: Duplicate management is supported for person accounts in Financial Services Cloud.
```
**3.** Enable Lightning Experience.
**4.** Click **Finish Enabling Lightning Experience**.
**5.** In the dropdown below your Salesforce username, click **Switch to Lightning Experience**.
    Unless noted otherwise, the remaining steps in this guide are provided for Lightning Experience.

Get Ready to Use Financial Services Cloud Create the User Profiles


## Financial Services Cloud Packages

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
Financial Services Cloud functionality is available from two packages.

```
Note: The URLs for the Financial Services Cloud packages are in the Product Specific Terms
section of your order form.
```
## Install the Managed Package

```
The managed package contains most of the Financial Services Cloud functionality. This
functionality includes custom fields and objects, list views and profiles of clients and households,
and administrative configurations.
Install the Unmanaged Extension Packages
Install the unmanaged extension packages after you have installed the Financial Services Cloud managed package. The unmanaged
extension package provides field sets that configure how fields display in the client and household profiles. The unmanaged referral
package provides the retail banking dashboard. The unmanaged commercial banking extension package provides the commercial
banking dashboard.
```
Install the Managed Package

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
The managed package contains most of the Financial Services Cloud functionality. This functionality
includes custom fields and objects, list views and profiles of clients and households, and
administrative configurations.

**1.** In the Product Specific Terms section of your order form, copy the URL for the Financial Services
    Cloud managed package.
**2.** Paste the URL into your browser navigation bar, and press Enter.
**3.** If you received a password from Salesforce, enter it.
**4.** Select **Install for Specific Profiles**.
**5.** Scroll to the Select Specific Profiles section, and map the profiles that you created in the pre-installation tasks to the package profiles.

```
For the Advisor profile, set the access level to Advisor. For the Personal Banker profile, set the access level to Personal Banker. For
the Relationship Manager profile, set the access level to Relationship Manager.
```
**6.** Click **Install**.

```
If the installation takes a while, you can click Done and the installation completes in the background. Check your email for confirmation
that the installation was successful.
```
If the package installation fails, see Why did my installation or upgrade fail?

```
Note: If you test the package installation using an Apex test, the test might return an error due to hard-coded elements such as
date format. For this reason, an Apex test is not recommended.
```

## Install the Unmanaged Extension Packages

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Install the unmanaged extension packages after you have installed the Financial Services Cloud
managed package. The unmanaged extension package provides field sets that configure how fields
display in the client and household profiles. The unmanaged referral package provides the retail
banking dashboard. The unmanaged commercial banking extension package provides the
commercial banking dashboard.
```
**1.** In the Product Specific Terms section of your order form, copy the URL for the Financial Services
    Ext unmanaged package.
**2.** Paste the URL into your browser navigation bar and press Enter.
**3.** If you received a password from Salesforce, enter it.
**4.** Select **Install for Specific Profiles**.
**5.** Scroll to the Select Specific Profiles section, and map the profiles that you created in the pre-installation tasks to the package profiles.
    For the Advisor, Personal Banker, and Relationship Manager profiles, set the access level to **Full Access**.
**6.** Click **Install**.
    If the installation takes a while, you can click **Done** and the installation completes in the background. Check your email for confirmation
    that the installation was successful.
**7.** Repeat the steps for the unmanaged referral package and unmanaged commercial banking extension package.
If the package installation fails, see Why did my installation or upgrade fail?

```
Install the Unmanaged Extension Package for Prebuilt Retail Banking Service Processes
Install the unmanaged extension package after you install the Financial Services Cloud managed package. The unmanaged package
extension for Financial Services Cloud Service Processes for retail banking offers pre-configured and customizable retail banking
service processes built using Service Process Studio. Each process includes an OmniScript for request intake through assisted and
self-service channels. It features flows and email templates for streamlined fulfillment, and BIAN-inspired outbound Mulesoft APIs
for integration with core banking and other external systems.
Install the Unmanaged Extension Package for Prebuilt Wealth Management Service Processes
Install the unmanaged extension package after you install the Financial Services Cloud managed package. The unmanaged package
extension for Financial Services Cloud Service Processes for Wealth Management offers pre-configured and customizable wealth
management service processes built using Service Process Studio. Each process includes an OmniScript for request intake through
assisted and self-service channels. It features flows and email templates for streamlined fulfillment, and BIAN-inspired outbound
Mulesoft APIs for integration with Custodial or Books and Records platform.
```
Financial Services Cloud Packages Install the Unmanaged Extension Packages


Install the Unmanaged Extension Package for Prebuilt Retail Banking Service

Processes

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Install the unmanaged extension package after you install the Financial Services Cloud managed
package. The unmanaged package extension for Financial Services Cloud Service Processes for retail
banking offers pre-configured and customizable retail banking service processes built using Service
Process Studio. Each process includes an OmniScript for request intake through assisted and
self-service channels. It features flows and email templates for streamlined fulfillment, and
BIAN-inspired outbound Mulesoft APIs for integration with core banking and other external systems.
Before you begin:
```
**-** To run the retail banking service processes in your Salesforce org, you must install OmniStudio
    package version 246.5 or later.
**-** Enable Lightning web security for LWC in Session Settings. See Enable Lightning Web Security in an Org.
**1.** To install the package, paste this URL into your browser navigation bar and press **Enter**.
**2.** Log in to the org in which to install the package.
**3.** If you want to provide package access to the installing admin’s profile or any profile with Customize Application permission, select
    **Install for Admins Only**.
**4.** If you want to provide package access to all internal custom profiles, select **Install for All Users**.
**5.** If you want to provide package access to specific profiles in your org, select **Install for Specific Profile**. You can set each profile to
    have full access or no access for the new package and all its components.
**6.** To see an overlay with the list of components in the package, click **View Components**.
**7.** Click **Install**.
    The installation can take some time. To complete the installation in the background, click **Done**. Check your email for confirmation
    that the installation was successful.

```
If the package installation fails, see Why did my installation or upgrade fail?
```
Install the Unmanaged Extension Package for Prebuilt Wealth Management

Service Processes

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Install the unmanaged extension package after you install the Financial Services Cloud managed
package. The unmanaged package extension for Financial Services Cloud Service Processes for
Wealth Management offers pre-configured and customizable wealth management service processes
built using Service Process Studio. Each process includes an OmniScript for request intake through
assisted and self-service channels. It features flows and email templates for streamlined fulfillment,
and BIAN-inspired outbound Mulesoft APIs for integration with Custodial or Books and Records
platform.
```
**-** To run the wealth management service processes in your Salesforce org, you must install
    OmniStudio package version 246.5 or later.
**-** Enable Lightning web security for LWC in Session Settings. See Enable Lightning Web Security in an Org.
**1.** To install the package, paste this URL into your browser navigation bar and press **Enter**.
**2.** Log in to the org in which to install the package.

```
Install the Unmanaged Extension Package for Prebuilt Retail
Banking Service Processes
```
Financial Services Cloud Packages


**3.** If you want to provide package access to the installing admin’s profile or any profile with Customize Application permission, select
    **Install for Admins Only.
4.** If you want to provide package access to all internal custom profiles, select **Install for All Users**.
**5.** If you want to provide package access to specific profiles in your org, select **Install for Specific Profile**. You can set each profile to
    have full access or no access for the new package and all its components.
**6.** To see an overlay with the list of components in the package, click **View Components**.
**7.** Click **Install**.
    The installation can take some time. To complete the installation in the background, click **Done**. Check your email for confirmation
    that the installation was successful.

```
If the package installation fails, see Why did my installation or upgrade fail?
```
```
Install the Unmanaged Extension Package for Prebuilt Wealth
Management Service Processes
```
Financial Services Cloud Packages


## Post-Installation Tasks

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
After you’ve installed the managed and unmanaged packages, complete these Financial Services
Cloud setup and configuration tasks.

```
Note: The Financial Services Cloud managed package includes several validation rules
enabled for different packaged objects. Modifying or deactivating these validation rules can
result in data model integrity errors.
```
## Configure Navigation to Individual and Group Profiles

```
Standard URLs that point to account and contact detail pages require a different navigation
path for an individual’s information. When users interact with detail page links, you want them
to navigate to an individual or group profile, not the individual’s account or contact record. You can configure overrides to redirect
these URLs.
Lightning Pages Setup
Give users the most important information about their books of business.
Add Values to the Lead Status Picklist
To help users track their leads, add picklist values to the Lead Status field.
Add Values to the Opportunity Stage Picklist
To help users track their open client opportunities, add picklist values to the Stage field.
Add Users
Add the necessary User Profile permissions to enable users to manage their books of business from Financial Services Cloud, and
then create users.
Page Layouts and Global Actions Setup
Give users access to actions and related lists from accounts and contacts in Financial Services Cloud.
Add Customer Roles
When users create a customer record, they specify the customer’s role within a household, such as client, spouse, domestic partner,
or dependent. These roles are picklist values for the Role field on the Account Contact Relationship object. Define the roles that
represent the types of household members that your firm tracks.
```
Configure Navigation to Individual and Group Profiles

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
Standard URLs that point to account and contact detail pages require a different navigation path
for an individual’s information. When users interact with detail page links, you want them to navigate
to an individual or group profile, not the individual’s account or contact record. You can configure
overrides to redirect these URLs.

**1.** From Setup, open **Object Manager** , open **Contact** , and click **Buttons, Links, and Actions**.
**2.** Next to View, select **Edit**.
**3.** Under Salesforce Classic Override, select **Visualforce Page** , and then select
    **ContactDetailRedirect [FinServ_ContactDetailRedirect]** from the dropdown.
**4.** Save your changes.


## Lightning Pages Setup

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Give users the most important information about their books of business.
```
1. Assign a Home Page Layout to Specific Apps, Record Types, and Profiles
    Assign Financial Services Cloud home pages to different apps and app-and-profile combinations
    to give your users access to a Home page perfect for their role.
2. Assign Lightning Pages to Display Financial Services Cloud Data
    You can assign different Lightning pages to the various Financial Services Cloud apps to display
    specific account record types. You can also choose which profiles can access the page. The
    two-column page layout is ideal for the Retail Banking app, the one-column layout is best suited
    to the Retail Banking Console, and the three-column suits both apps.

Assign a Home Page Layout to Specific Apps, Record Types, and Profiles

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Assign Financial Services Cloud home pages to different apps and app-and-profile combinations
to give your users access to a Home page perfect for their role.
```
```
Note: New releases of Financial Services Cloud upgrade the Lightning home pages and
overwrite any changes. To add or remove Lightning components from a home page, clone
the page. Click Clone next to the page you want to modify in Lightning App Builder.
```
**1.** From Setup, enter _Lightning App Builder_ in the Quick Find box, and then select
    **Lightning App Builder**.
**2.** Click **View** next to the Lightning page that you want to assign as a home page, as shown in
    the table.
**3.** Click **Activation**.
**4.** If you created a page or opened a page that needs adjustment, make the necessary changes, click **Save** , and then click **Activate**.
**5.** On the activation screen, click the tab to assign the page to a combination of Lightning apps, record types, and profiles.
**6.** Follow the steps to activate the page.
**7.** Review and save your changes.

```
Lightning Page Name Profile
```
```
Home System Administrator, Advisor
```
```
Banking Home Page Personal Banker
```
```
Commercial Banking Home Page Relationship Manager
```
Post-Installation Tasks Lightning Pages Setup


Assign Lightning Pages to Display Financial Services Cloud Data

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
You can assign different Lightning pages to the various Financial Services Cloud apps to display
specific account record types. You can also choose which profiles can access the page. The
two-column page layout is ideal for the Retail Banking app, the one-column layout is best suited
to the Retail Banking Console, and the three-column suits both apps.
```
**1.** From Setup, enter _Lightning App Builder_ in the Quick Find box, and then select
    **Lightning App Builder**.
**2.** Click **View** next to the Lightning Page you want to assign, as shown in the table.
**3.** Click **Activation**.
**4.** Click the **App, Record Type, and Profile** tab.
**5.** Click **Assign to Apps, Record Types, and Profiles**.
**6.** Select the apps, and click **Next**.
**7.** Select the record type, and click **Next**.
**8.** Select the profiles, and click **Next**.
**9.** Review and save your assignments.

```
Record Profile
Type
```
```
Lightning Page Name App
```
```
Client Record Page Wealth Management Individual Advisor, System Admin
```
```
Client Record Page Wealth Management Household Advisor, System Admin
```
```
Advisor, Personal Banker,
System Admin
```
```
Banking Business Account Page Retail Banking, Retail Banking Console Business
```
```
Advisor, Personal Banker,
System Admin
```
```
Banking Business Contact Page Retail Banking, Retail Banking Console Business
```
```
Advisor, Personal Banker,
System Admin
```
```
Banking Household Page - One Column Retail Banking Console Household
```
```
Advisor, Personal Banker,
System Admin
```
```
Banking Household Page - Two Column Retail Banking Household
```
```
Advisor, Personal Banker,
System Admin
```
```
Banking Individual Page - One Column Retail Banking Console Individual
```
```
Advisor, Personal Banker,
System Admin
```
```
Banking Individual Page - Two Column Retail Banking Individual
```
```
Assign Lightning Pages to Display Financial Services Cloud
Data
```
Post-Installation Tasks


## Add Values to the Lead Status Picklist

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
To help users track their leads, add picklist values to the Lead Status field.
```
**1.** From Setup, open **Object Manager** , then **Lead** , and select **Fields & Relationships**.
**2.** Select **Lead Status**.
**3.** If the picklist values Working - Contacted and Nurturing - Contacted aren’t present.
    **a.** Click **New**.
    **b.** For the label and API name, enter _Working - Contacted_.
    **c.** Save your changes.
    **d.** Add the Nurturing - Contacted picklist value by repeating these steps.
**4.** Configure the picklist values.
    **a.** From Setup, enter _Lead Processes_ in the Quick Find box, and then select **Lead Processes**.
    **b.** Click **Lead process**.
    **c.** If they aren't present, add Unqualified, New, Working - Contacted, Nurturing - Contacted, and Qualified (Converted) from Available
       Values to Selected Values.
    **d.** If it isn't set, select **New** as the default value.
    **e.** Save your changes.

## Add Values to the Opportunity Stage Picklist

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
To help users track their open client opportunities, add picklist values to the Stage field.
```
**1.** From Setup, open **Object Manager** , open **Opportunity** , then select **Fields & Relationships**.
**2.** Select **Stage**.
**3.** Create opportunity stage picklist values that suit your business process. We suggest Assessment
    Needed, Develop Proposal, Client Presentation, and Initiate Transfer.
    **a.** From Opportunity Stages Picklist Values, click **New**.
    **b.** Name the stage.
    **c.** Enter the probability that the stage represents.
       We suggest these percentages: Assessment Needed—25, Develop Proposal—50, Client Presentation—75, and Initiate
       Transfer—90.

```
d. Save your changes.
```
**4.** Configure the sales processes.
    **a.** From Setup, enter _Sales Processes_ in the Quick Find box, and then select **Sales Processes**.
    **b.** Click **Opportunity Process**.
    **c.** Remove any existing values from Selected Values and add the stages created above.
    **d.** Save your changes.
    **e.** Repeat these steps for Wallet Share.

Post-Installation Tasks Add Values to the Lead Status Picklist


## Add Users

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Add the necessary User Profile permissions to enable users to manage their books of business from
Financial Services Cloud, and then create users.
```
1. Configure User Profile Permissions
    Enable the required permissions and a field-level security setting for the user profiles, including
    the System Administrator profile. You can edit profiles that you created and mapped to the
    packaged profiles. However, you can’t change the packaged Advisor Access, Personal Banker
    Access, and Relationship Manager Access permission sets. If you want to add or remove
    permissions, clone the packaged permission and modify the new version.
2. Create Users
    Create users and assign them the required permissions so that they can access Financial Services Cloud.

Configure User Profile Permissions

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Enable the required permissions and a field-level security setting for the user profiles, including the
System Administrator profile. You can edit profiles that you created and mapped to the packaged
profiles. However, you can’t change the packaged Advisor Access, Personal Banker Access, and
Relationship Manager Access permission sets. If you want to add or remove permissions, clone the
packaged permission and modify the new version.
Make edits to the profiles that you created or cloned, not to the Standard User profile. The Standard
User profile doesn’t have access to packaged features.
```
**1.** From Setup, enter _Profiles_ in the Quick Find box, and then select **Profiles**.
**2.** Click **Advisor** :
    **a.** In the Field-Level Security section, select **View** next to **Task**. Edit the task, and enable read access for the Type field.
    **b.** In the Field-Level Security section, select **View** next to **Event**. Edit the event, and enable read access for the Type field.
    **c.** In the Record Type Setting section, verify the Events defaults to Advisor Event, Leads defaults to Person Referrals, Opportunities
       defaults to Opportunity (Wallet Share), and Tasks defaults to Advisor Task.
    **d.** In the Administrative Permissions section, enable the **View Dashboards in Public Folders** and **View Reports in Public Folders**
       permissions.
    **e.** In the General User Permissions section, enable the **Drag-and-Drop Dashboard Builder** , **Edit Case Comments** , **Import Leads** ,
       **Manage Cases** , **Manage Leads** , **Transfer Cases** , **Transfer Leads** , and **View My Team’s Dashboards** permissions.
**3.** Click **Personal Banker** :
    **a.** In the Field-Level Security section, select **View** next to **Task**. Edit the task, and enable read access for the Type field.
    **b.** In the Record Type Setting section, for Standard Record Type Settings, ensure that Leads defaults to Person Referrals, Leads
       defaults to Person Referrals, Opportunities include the Opportunity (Wallet Share), and defaults to General, and Task is set to
       Master.
    **c.** In the Record Type Setting sections, for Customer Record Type Setting, verify whether Billing Statements include Credit and
       Debit, and defaults to Credit.
**4.** Click **System Administrator** :
    **a.** In the Field-Level Security section, select **View** next to **Task**. Edit the task, and enable read access for the Type field.

Post-Installation Tasks Add Users


```
b. In the Record Type Setting section, ensure that Events defaults to Advisor Event., Leads defaults to Person Referrals, Opportunities
defaults to Opportunity (Wallet Share), and Tasks defaults to Advisor Task
```
Create Users

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Create users and assign them the required permissions so that they can access Financial Services
Cloud.
```
**1.** Create a user.
    **a.** From Setup, enter _Users_ in the Quick Find box, and then select **Users**.
    **b.** Create a user. Assign it the Salesforce user license and the Advisor, Personal Banker, or
       Relationship Manager profile.
    **c.** Save your changes.
**2.** Assign permission sets.
    **a.** Click **Permission Set Assignments** , and then click **Edit Assignments**.
    **b.** Under Available Permission Sets, choose the permission sets and click **Add**.
    **c.** For users with the Personal Banker profile, add the Financial Services Cloud Standard and Personal Banker Access permission
       sets.
    **d.** For users with the Advisor profile, add the Financial Services Cloud Standard and Advisor Access permission sets.
    **e.** For users with the Relationship Manager profile, add the Financial Services Cloud Standard and Relationship Manager Access
       permission sets.
    **f.** Save your changes.

## Page Layouts and Global Actions Setup

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Give users access to actions and related lists from accounts and contacts in Financial Services Cloud.
```
1. Add Global Actions to Publisher Layouts
    A global action lets users easily record details about client tasks, events, and calls by launching
    an action from the Salesforce header.
2. Configure the Account Contact Relationship Page Layout
    Give relationship managers, personal bankers, and advisors access to the fields in the account
    contact relationship layout to let them create and maintain relationship groups.

Post-Installation Tasks Create Users


Add Global Actions to Publisher Layouts

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
A global action lets users easily record details about client tasks, events, and calls by launching an
action from the Salesforce header.
```
**1.** Replace the default actions available to users in the Salesforce mobile app and Lightning
    Experience.
    **a.** From Setup, enter _Global Actions_ in the Quick Find box, and then select **Publisher**
       **Layouts**.
    **b.** Select **New**.
    **c.** Name the publisher layout, such as Advisor Publisher Layout.
    **d.** Save your changes.
    **e.** In the Salesforce Mobile and Lightning Experience Actions section, select the override option.
    **f.** Remove these actions: **New Event** , **New Task** , and **Log a Call**.
    **g.** In the palette, select the **Mobile & Lightning Actions** category. D
    **h.** Drag the actions **FinServ__NewEventAdvisor** , **FinServ__NewTaskAdvisor** , and **FinServ__LogACallAdvisor** to the Salesforce
       Mobile and Lightning Experience Actions section. Make sure that you’re dragging the correct actions by hovering over the action
       and checking the name.
    **i.** Save your changes.
**2.** Assign the Advisor Publisher Layout to the Advisor profile.
    **a.** From the list of Global Publisher Layouts, click **Publisher Layout Assignment**.
    **b.** Select **Edit Assignment**.
    **c.** In the table, select the cell for the Advisor profile, and choose **Advisor Publisher Layout** from the dropdown list.
    **d.** In the table, select the cell for the Personal Banker profile, and choose **RB Global Layout** from the dropdown list.
    **e.** In the table, select the cell for the Relationship Manager profile, and choose **RB Global Layout** from the dropdown list.
       If you have created other profiles, assign them these layouts as needed.

```
f. Save your changes.
```
Configure the Account Contact Relationship Page Layout

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
Give relationship managers, personal bankers, and advisors access to the fields in the account
contact relationship layout to let them create and maintain relationship groups.
```
**1.** From Setup, open **Object Manager** , then **Account Contact Relationship** , and click **Page**
    **Layouts**.
**2.** From the Page Layouts section, click **Page Layout Assignment**.
**3.** For the Advisor, Personal Banker, and Relationship Manager profiles, select **Account Contact**
    **Relationship Layout (Installed Package: WealthManagement)**.
**4.** Save your changes.

Post-Installation Tasks Add Global Actions to Publisher Layouts


## Add Customer Roles

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Professional ,
Enterprise , and Unlimited
Editions
```
```
When users create a customer record, they specify the customer’s role within a household, such as
client, spouse, domestic partner, or dependent. These roles are picklist values for the Role field on
the Account Contact Relationship object. Define the roles that represent the types of household
members that your firm tracks.
```
**1.** From Setup, open **Object Manager** , open **Account Contact Relationships** , then click **Fields**
    **& Relationships**.
**2.** Select **Roles**.
**3.** Delete the standard Salesforce roles picklist values.
**4.** Add picklist values as needed.
    We suggest the roles. Client, Dependent, Domestic Partner, Spouse, Grantor ,Beneficiary, Board Member, Employee, Trustee, and
    Other.
**5.** Save your changes.

Post-Installation Tasks Add Customer Roles


## Deploy the Client Segmentation App

The Client Segmentation App app helps financial advisors identify key actions for high-potential clients and accounts. Deploy it after
you complete the Wealth Management implementation tasks. Dashboards from the Client Segmentation App app replace Financial
Services Cloud embedded dashboards available on the Advisor Analytics tab.

```
Note: Client Segmentation App is not part of CRM Analytics for Financial Services, which is a separate application enabled by its
own license and available for extra cost.
```
Client Segmentation App app dashboards are based on the latest CRM Analytics dashboard designer. The older classic designer will be
retired on June 30, 2019, and the Advisor Analytics tab will no longer be available in Financial Services Cloud. Customers are advised to
remove the Advisor Analytics tab before then. Contact your Salesforce representative to learn more about the transition.

If you installed the Financial Services Cloud – Einstein Analytics managed package, replace it by using the Client Segmentation App
template. The template creates an app with dashboards that your team accesses through CRM Analytics.

Before deploying the Client Segmentation App app, review the following considerations.

**-** Client Segmentation App is available only in English. Localization is not supported.
**-** All users see the same date, time, and number formats, regardless of their locale and language settings.
**-** Multicurrency is not supported. When Financial Services Cloud extracts your org’s default currency, it uses the currency for monetary
    values and doesn’t convert to another currency. Labels with the ‘$’ symbol are not converted to reflect the default currency.

```
Tip: Follow the steps in the order shown to deploy the Client Segmentation App app.
```
```
Enable CRM Analytics
Before creating the Client Segmentation App app, enable CRM Analytics in your Salesforce org.
Assign Client Segmentation App App Administrator Permissions
Enable administrators to create an app from the Client Segmentation App template and manage it by assigning the Client
Segmentation Admin permission set.
Assign Client Segmentation App User Permissions
Enable users to view the Client Segmentation App app by assigning the Client Segmentation Analytics User permission set.
Get Your Data Ready to Create the Client Segmentation App
Data in your org has to meet specific requirements before you can create the Client Segmentation App app.
Set Field-Level Security to Enable Creation of the Client Segmentation App
Before creating the Client Segmentation App app, make sure the Analytics Integration User has access to all fields used in the app.
Create and Share an App from the Client Segmentation App Template
Follow these steps to create and share an app from the Client Segmentation App template.
Schedule the Data Synch and Dataflow for the Client Segmentation App
When you create the app, the creation process includes a data sync and a dataflow that imports the latest data to CRM Analytics.
Schedule the app to refresh every day to ensure that Client Segmentation App uses up-to-date data.
```

```
Understand Client Segmentation App Limitations
The Client Segmentation app gives you limited access to CRM Analytics capabilities and features.
```
### SEE ALSO:

```
Use Financial Services Cloud CRM Analytics Solutions
CRM Analytics Limitations
```
## Enable CRM Analytics

```
Before creating the Client Segmentation App app, enable CRM Analytics in your Salesforce org.
```
```
Note: If you see a blue Launch CRM Analytics button in the upper right corner, CRM Analytics is already enabled and you can
skip to “Assign Client Segmentation App App Administrator Permissions”.
From Setup, enter GettingStarted in the Quick Find box, and then select Getting Started. Click Enable CRM Analytics.
```
### SEE ALSO:

## Assign Client Segmentation App App Administrator Permissions

Assign Client Segmentation App App Administrator Permissions

```
Enable administrators to create an app from the Client Segmentation App template and manage it by assigning the Client Segmentation
Admin permission set.
```
**1.** From Setup, enter _Users_ in the Quick Find box, and then select **Users**.
**2.** Click the user name with the System Administrator profile.
**3.** Click **Permission Set Assignments** , and then click **Edit Assignments**.
**4.** Select the Client Segmentation Admin permission set.
**5.** Click **Add** , then click **Save**.
**6.** Repeat these steps for all users who need to create and manage the Client Segmentation App app.

## Assign Client Segmentation App User Permissions

```
Enable users to view the Client Segmentation App app by assigning the Client Segmentation Analytics User permission set.
```
**1.** From Setup, enter _Users_ in the Quick Find box, and then select **Users**.
**2.** Click the name of a user who requires access to the Client Segmentation App app.
**3.** Click **Permission Set Assignments** , and then click **Edit Assignments**.
**4.** Select the Client Segmentation Analytics User permission set.
**5.** Click **Add** , then click **Save**.
**6.** Repeat these steps for all users who need to view the Client Segmentation App app.

Deploy the Client Segmentation App Enable CRM Analytics


## Get Your Data Ready to Create the Client Segmentation App

```
Data in your org has to meet specific requirements before you can create the Client Segmentation App app.
Your org must have at least the following data:
```
**-** One record in the FinancialAccount object
**-** Record types
During app creation, CRM Analytics checks your org’s data to be sure it meets minimum requirements. If it doesn’t, you see a message
describing what needs to be fixed.

## Set Field-Level Security to Enable Creation of the Client Segmentation App

```
Before creating the Client Segmentation App app, make sure the Analytics Integration User has access to all fields used in the app.
If users don’t have proper field-level security permissions when they run a dataflow, the dataflow can fail. Here’s how to set Salesforce
field-level security to enable the Analytics Integration User to see all fields used in the app.
```
Lightning Experience

**1.** In Setup, enter _object_ in the Quick Find box, and click **Enter**.
**2.** Select **Object Manager**.
**3.** Enter the name of the object whose field-level security you need to edit in the Quick Find box, and click **Enter**.
**4.** Select the object you need to edit, then select **Fields & Relationships**.
**5.** Select the field you need to edit, then select **Set Field-Level Security**.
**6.** Look for the Analytics Cloud Integration User, check the boxes for the required fields under Visible, and click **Save**.
**7.** Repeat steps 5 and 6 for all fields you want to use.
**8.** Refresh your browser cache.

Salesforce Classic

**1.** In Setup, enter the name of the object whose field-level security you need to edit in the Quick Find box and click **Enter**.
**2.** Click the name of the object.
**3.** The next window shows all the fields for the object. Go to the one(s) where you need to edit field-level security.
**4.** Look for the Analytics Cloud Integration User, check the boxes for the required fields under Visible, and click **Save**.
**5.** Repeat steps 2 through 4 for all objects with fields you want to use.
**6.** Refresh your browser cache.
You can now create the Client Segmentation App app.

Deploy the Client Segmentation App Get Your Data Ready to Create the Client Segmentation App


## Create and Share an App from the Client Segmentation App Template

```
Follow these steps to create and share an app from the Client Segmentation App template.
```
### SEE ALSO:

```
Set Field-Level Security to Enable Creation of the Client Segmentation App
```
Create the App

**1.** Navigate to **Analytics Studio**.
**2.** Click **Create** , then select **App**.
**3.** Select **Client Segmentation App**. Then click **Continue**.
**4.** CRM Analytics performs a compatibility check of your org’s data. If it uncovers any issues, you see error messages with instructions
    about how to address them. Fix the issues and try app creation again.
**5.** Name your app and click **Create**.
**6.** View the status of app creation on the next page. The process takes a minute or two. Once it’s complete, refresh the page to see
    your app.

```
Note: If you see an error saying the Analytics Integration User does not have access to selected fields, edit Salesforce field-level
security so the Integration User has the required access.
```
```
Share the App
Now that you’ve created the app, share it with users in your organization. You can share it only with users assigned the Client Segmentation
App admin or user permission sets.
```
**1.** Open your app if it’s not already open. If you’ve navigated away from CRM Analytics Studio, go back to it, select **All Items** , find your
    app, and click it.
**2.**
    Click the Share icon at upper right.
**3.** In the next screen, use the search field under **Invite others:** to find other users in your org.
**4.** Select whether you want to make the selected user a Viewer, Editor, or Manager of the app.

```
Important: Users with the “Use Analytics Templated Apps” permission and Editor or Manager access to the app can create,
edit, and delete assets in the app.
```
**5.** Click **Add** , then click **Save**.

## Schedule the Data Synch and Dataflow for the Client Segmentation App

```
When you create the app, the creation process includes a data sync and a dataflow that imports the latest data to CRM Analytics. Schedule
the app to refresh every day to ensure that Client Segmentation App uses up-to-date data.
```
```
Create and Share an App from the Client Segmentation App
Template
```
Deploy the Client Segmentation App


```
To schedule your app, see Schedule Data Refresh for a CRM Analytics App. Select a time outside normal work hours so the data refresh
doesn’t interrupt business activities.
```
## Understand Client Segmentation App Limitations

```
The Client Segmentation app gives you limited access to CRM Analytics capabilities and features.
A CRM Analytics Growth, CRM Analytics Plus, or CRM Analytics for Financial Services license is required to access full CRM Analytics
capabilities. Consult the chart to see limitations.
```
```
Table 1: Client Segmentation App Limitations
CRM Analytics Growth or Plus; CRM Client Segmentation App
Analytics for Financial Services
```
```
Capability
```
```
Data sources Salesforce and external data Salesforce data
```
```
Object support Standard and custom objects Standard objects only
```
```
Data volume • CRM Analytics Plus: 10 billion rows 10 million rows
```
**-** CRM Analytics Growth: 100 million rows

```
Can customize existing dashboards? Yes No
```
```
Can create dashboards? Yes No
```
```
Can customize existing datasets? Yes No
```
```
Can create datasets? Yes No
```
```
Can create custom CRM Analytics apps? Yes No
```
```
Supports Einstein Discovery and Community Yes No
Cloud integration?
```
```
Supports bulk actions and APEX steps? Yes No
```
```
Supports Sales Cloud Einstein artificial No No
intelligence?
```
```
Supports Salesforce Inbox? No No
```
Deploy the Client Segmentation App Understand Client Segmentation App Limitations


