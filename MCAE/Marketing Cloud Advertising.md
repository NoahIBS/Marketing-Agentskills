# Marketing Cloud Advertising

# and Account Engagement

# Implementation Guide

Salesforce, Spring ’ 26

```
Last updated: November 17, 2025
```

© Copyright 2000–2026 Salesforce, Inc. All rights reserved. Salesforce is a registered trademark of Salesforce, Inc., as are other

```
names and marks. Other marks appearing herein may be trademarks of their respective owners.
```

## CONTENTS

- ACCOUNT ENGAGEMENT. GETTING STARTED WITH MARKETING CLOUD ADVERTISING AND
- IMPLEMENTATION OVERVIEW.
- Requirements
- Implementation Worksheet
- SALESFORCE SETUP.
- Create a Salesforce Campaign
- Create a Salesforce Report
- ACCOUNT ENGAGEMENT SETUP.
- MARKETING CLOUD SETUP.
- Create a Data Import in Email Studio
- Create an Automation in Automation Studio
- Create an Audience in Marketing Cloud Advertising



## GETTING STARTED WITH MARKETING CLOUD ADVERTISING

## AND ACCOUNT ENGAGEMENT

```
EDITIONS
```
```
Available in: All Account
Engagement Editions with
the purchase of Marketing
Cloud or Marketing Cloud
Advertising.
```
Marketing Cloud Advertising and Account Engagement are both powerful tools built for marketers.
Connecting them helps maximize your marketing efforts by giving prospects and customers a more
personalized experience across channels. After you connect the apps, Account Engagement prospect
data is funneled into an Advertising Audience so you can better tailor your social media marketing.

**-** Advertising is part of Marketing Cloud, but can be purchased as a standalone product. This
    process works the same whether you have only Advertising or full Marketing Cloud access.
**-** You can repeat this process to use Account Engagement prospect data for multiple Advertising
    Audiences.
**-** Connection setup requires you to complete tasks in three places: Account Engagement, Salesforce, and Marketing Cloud (or standalone
    Advertising).
**-** Depending on your permissions and the structure of your org, it’s possible you need more than one person to complete this setup.
    Check out the implementation overview section in this guide for a printable planning worksheet.
**-** Review the requirements in the Implementation Overview section of this guide and make sure you plan for any resources you need
    before you begin.


## IMPLEMENTATION OVERVIEW.

```
EDITIONS
```
```
Available in: All Account
Engagement Editions with
the purchase of Marketing
Cloud or Marketing Cloud
Advertising.
```
After you complete the setup process, prospect data from Account Engagement is fed into Marketing
Cloud Advertising via Salesforce. The setup process outlined in this guide facilitates the flow of data
from Account Engagement to Salesforce, and then from Salesforce to Marketing Cloud Advertising.

This graphic gives a high-level overview of the data flow after setup is complete. A Pardot prospect
is added to a Salesforce campaign, which updates a Salesforce report, which is used to create a
Marketing Cloud data extension. The data extension is the source for an Advertising Audience.

## Requirements

```
Before you begin the setup process, review the requirements for connecting Marketing Cloud Advertising and Account Engagement.
Implementation Worksheet
You can print this worksheet to help you plan and decide how to handle each task. You must complete the tasks in Salesforce and
Account Engagement before you can complete the setup in Marketing Cloud.
```
Requirements

```
EDITIONS
```
```
Available in: All Account
Engagement Editions with
the purchase of Marketing
Cloud or Marketing Cloud
Advertising.
```
Before you begin the setup process, review the requirements for connecting Marketing Cloud
Advertising and Account Engagement.

You must have a connected third-party social account equipped for advertising, plus these system
requirements:

```
Salesforce Account Engagement Marketing Cloud
```
**- • •** Full access to Marketing
    Cloud OR access to

```
Permission to view, add, Marketing user permissions
and edit campaign
objects
```
**-** A verified Salesforce
    connector Marketing Cloud
       Advertising
**-** Marketing Cloud Connect
enabled


```
Salesforce Account Engagement Marketing Cloud
```
**-** A Marketing Cloud File Transfer Protocol
    (FTP) account and be an FTP user

### SEE ALSO:

```
Connect Clouds with Marketing Cloud Connect
SFTP Accounts in Marketing Cloud Engagement
```
## Implementation Worksheet

```
You can print this worksheet to help you plan and decide how to handle each task. You must complete the tasks in Salesforce and
Account Engagement before you can complete the setup in Marketing Cloud.
```
Salesforce Tasks

```
Task Owner Notes
```
```
Create a campaign
```
```
Create a report
```
Account Engagement Tasks

```
Task Owner Notes
```
```
Choose from: completion actions,
segmentation rules, automation rules, page
actions, or an Engagement Studio program.
```
```
Define how prospects are added to the
Salesforce campaign
```
Marketing Cloud Tasks

```
Task Owner Notes
```
```
Create a data import in Email Studio
```
```
Create an automation in Automation Studio
```
```
Create an Advertising Audience in Marketing
Cloud Advertising
```
Implementation Overview Implementation Worksheet


## SALESFORCE SETUP.

In Salesforce, create a campaign to add Account Engagement prospects to. Then, create a report based on that campaign.

## Create a Salesforce Campaign

```
First, create a campaign in Salesforce.
Create a Salesforce Report
After you create your campaign, build a report for your campaign in Salesforce.
```
Create a Salesforce Campaign

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Essentials ,
Group , Essentials ,
Professional , Enterprise ,
Performance , Unlimited ,
and Developer Editions
```
```
USER PERMISSIONS
```
```
To view campaigns
```
**-** Read on campaigns
To customize member status
values
**-** Edit on campaigns and
    _Marketing User_
checked in your user
information

First, create a campaign in Salesforce.

**1.** From the Campaigns tab, click **New**.
**2.** Select a record type, then click **Next**.
**3.** Name your campaign, set the status to **In Progress** , the type to **Social Media** , and leave the
    start and end dates blank.
**4.** Select **Active** , and then click **Save**.


## Create a Salesforce Report

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Essentials ,
Group , Essentials ,
Professional , Enterprise ,
Performance , Unlimited ,
and Developer Editions
Available in: Enhanced
Folder Sharing
```
```
USER PERMISSIONS
```
```
To create, edit, and delete
reports in private folders:
```
**-** Create and Customize
    Reports
To create, edit, and delete
reports in public and private
folders:
**-** Report Builder OR Report
    Builder (Lightning
    Experience)

```
After you create your campaign, build a report for your campaign in Salesforce.
```
**1.** From the Reports tab, click **New Report**.
**2.** Select **Campaigns with Campaign Members** as the report type, then click **Continue**.
**3.** Click and name your report.
**4.** On the Outline tab, select **Email** as a column for your report.
**5.** Apply any other desired columns. If you plan to use Facebook or Google Advanced Match
    capabilities for your Advertising Audience, include any information you want to match.
**6.** Click the **Filters** tab and apply these filters:
    **a.** Show me: My active campaigns
    **b.** Campaign Name equals the name of the campaign you created in the previous section.
**7.** Apply any other desired filters. We recommend you apply a date filter such as Member Status
    Update Date to limit the report to campaign members from a specific time frame.
**8.** Click **Save & Run**.

Salesforce Setup Create a Salesforce Report


## ACCOUNT ENGAGEMENT SETUP.

```
EDITIONS
```
```
Available in: All Account
Engagement Editions
```
In Account Engagement, choose how prospects are added to the campaign you created in Salesforce.
You can add prospects to Salesforce campaigns via completion actions, segmentation rules,
automation rules, page actions, or Engagement Studio program actions.

### SEE ALSO:

```
Segmentation Rules
Automation Rules
Page Actions
Engagement Program Actions
```

## MARKETING CLOUD SETUP.

```
EDITIONS
```
```
Available in: Marketing
Cloud or Marketing Cloud
Advertising with Marketing
Cloud Connect enabled.
```
The setup in Marketing Cloud involves three separate tasks: create a data import, an automation,
and an Advertising Audience. The tasks in this section are the same regardless of whether you have
full access to Marketing Cloud or have purchased only Marketing Cloud Advertising.

```
Note: To complete the setup in Marketing Cloud, make sure you have an enabled File Transfer
Protocol (FTP) account and that you’re an FTP user.
```
## Create a Data Import in Email Studio

```
Create a data import to transfer your Salesforce report data into Marketing Cloud.
Create an Automation in Automation Studio
Use an automation to sync your Salesforce report data to Marketing Cloud.
Create an Audience in Marketing Cloud Advertising
Create an Advertising Audience based on your Salesforce report data extension.
```
Create a Data Import in Email Studio

```
EDITIONS
```
```
Available in: Marketing
Cloud or Marketing Cloud
Advertising with Marketing
Cloud Connect enabled.
```
```
USER PERMISSIONS
```
```
To create a data import:
```
**-** Marketing Cloud
    Administrator or
    Channel Manager role

Create a data import to transfer your Salesforce report data into Marketing Cloud.

**1.** In Email Studio, hover over Interactions and click **Import**.
**2.** Click **Create**.
**3.** Name your data import and fill out the required fields. For File Location, choose **Salesforce**
    **Objects & Reports**.
**4.** Click **Report** , then click **Select**.
**5.** Check the box for your Salesforce report, and click **OK**.
**6.** Under Included, select the fields you want to sync from Salesforce. Under Key, check a field to
    use as an identifier for prospects in your Advertising Audience, such as Email.
**7.** Click **Save Config** to return to the New Import screen.
**8.** Click **Save**.


### SEE ALSO:

```
File-Naming Patterns
```
## Create an Automation in Automation Studio

```
EDITIONS
```
```
Available in: Marketing
Cloud or Marketing Cloud
Advertising with Marketing
Cloud Connect enabled.
```
```
USER PERMISSIONS
```
```
To create an automation:
```
**-** Marketing Cloud
    Administrator or
    Channel Manager role
    with Create, Edit, Execute
    permission

```
Use an automation to sync your Salesforce report data to Marketing Cloud.
```
**1.** In Automation Studio, click **New Automation**.
**2.** Click **Untitled Automation** and enter a name for your automation, then click **Done**.
**3.** Click **Schedule** , drag it into your workflow under Starting Source, and click **Configure** to set
    the data sync frequency.

```
Tip: We recommend syncing once a day to ensure ads are relevant to your audience.
```
**4.** Click **Done**.
**5.** Click **Import File** , drag it into your workflow as Step 1, and click **Choose**.
**6.** Select the data import for your Salesforce report you created in Email Studio, then click **Done**.
**7.** Click **Save**. To confirm that everything is working as expected, click **Run Once**.
**8.** Under Schedule, click **Active** , and then click **Activate** in the confirmation modal.

Marketing Cloud Setup Create an Automation in Automation Studio


## Create an Audience in Marketing Cloud Advertising

```
EDITIONS
```
```
Available in: Marketing
Cloud or Marketing Cloud
Advertising with Marketing
Cloud Connect enabled.
```
```
USER PERMISSIONS
```
```
To create an Advertising
Audience:
```
**-** Marketing Cloud:
    Administrator or
    Channel Manager role
    with Create, Edit, and
    Publish Audiences
    permission

```
Create an Advertising Audience based on your Salesforce report data extension.
```
**1.** In Marketing Cloud Advertising, navigate to Advertising Audiences.
**2.** Click **+ Create Audience**.
**3.** Enter a name for the audience and choose a destination ad network.
**4.** Select an ad account.
**5.** Click **Configure**.
**6.** On the configuration page, click **Data Extension**.
**7.** Under Synchronized Data Extensions, select the data extension you created for your Salesforce
    report.
**8.** Click **Save**.
After you configure the audience, setup is complete. The audience updates as Account Engagement prospects are added to your
Salesforce campaign. Processing times vary depending on the volume of data.

Marketing Cloud Setup Create an Audience in Marketing Cloud Advertising


