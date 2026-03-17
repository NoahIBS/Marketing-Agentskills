# Engagement History

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

- Show Engagement History on Records
- Considerations for Engagement History
- Report on Engagement History Data
- Comparison of Engagement History Features
   - Use the Metrics Fields Component
   - Use Engagement History Metrics Related Lists
   - Using the Engagement History Related List
   - Using Engagement History Metrics Lightning Component
   - Add the Engagement History Custom Lightning Component
   - Engagement History Dashboards
- Resources



## Show Engagement History on Records

```
EDITIONS
```
```
Available in: Lightning
Experience
```
```
Available in: Account
Engagement Growth , Plus ,
Advanced , or Premium
Editions with Salesforce
Essentials , Professional ,
Enterprise , Performance ,
Unlimited , and Developer
Editions
```
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

Together, Account Engagement and Salesforce track valuable engagement data that can tell you
how well your marketing assets resonate with your customer base. Turn on Engagement History
and choose where to surface this valuable data throughout Salesforce in the form of fields, related
lists, and Lightning components.

To use Engagement History, you must connect your Salesforce and Account Engagement campaigns.

## Considerations for Engagement History

```
When you work with Engagement History features, keep these considerations in mind.
Report on Engagement History Data
Engagement History gives you access to prospect engagement data in Salesforce. To better
understand this data, create a custom report that contains engagement metrics alongside
campaign and opportunity data. We recommend five common custom report types for reporting
on marketing assets.
Comparison of Engagement History Features
Engagement History is a generic term for a collection of fields, related lists, and other Lightning
components that make it possible to show valuable prospect engagement data on your most
used records.
Resources
Find out more about how to use Engagement History and reports.
```
Considerations for Engagement History

```
EDITIONS
```
```
Available in: Lightning
Experience
Available in: Account
Engagement Growth , Plus ,
Advanced , or Premium
Editions with Salesforce
Essentials , Professional ,
Enterprise , Performance ,
Unlimited , and Developer
Editions
```
When you work with Engagement History features, keep these considerations in mind.

### Prerequisites for Engagement History Features

**-** Engagement History requires a verified Salesforce connector and an active Account Engagement
    user.
**-** Connected Campaigns must be enabled for most features. When campaigns aren’t connected,
    values show 0.

### Setup and Storage

**-** Assets associated with connected campaigns are stored as records in Salesforce and apply to
    storage limits. Engagement activities on these assets remain in Account Engagement, and don’t
    count toward Salesforce storage limits. For example, let’s say a marketing email syncs to
    Salesforce as a list email record. This record counts toward your Salesforce storage limit, but the engagement activities associated
    with the record come directly from Account Engagement and don’t count toward Salesforce storage.
**-** Engagement History metrics are refreshed every few minutes, typically less than 10.


**-** Engagement history data in the custom Lightning component is visible in Salesforce, but isn’t available for reports. To see the most
    up-to-date information reload the page.
**-** Data from email sends to test lists is included in Engagement History and other reports. To exclude test list metrics, associate your
    test email with a test campaign.
**-** For help with setting up Engagement History features, an Account Engagement admin can use the assistant in Marketing Setup.

## Report on Engagement History Data

```
EDITIONS
```
```
Available in: Salesforce
Professional , Enterprise ,
Performance , and
Unlimited Editions with All
Account Engagement
Editions
```
```
USER PERMISSIONS
```
```
To create reports:
```
**-** Sales, Service, or CRM
    permission set
    AND
    Create and Customize
    Reports
    AND
    Report Builder

```
Engagement History gives you access to prospect engagement data in Salesforce. To better
understand this data, create a custom report that contains engagement metrics alongside campaign
and opportunity data. We recommend five common custom report types for reporting on marketing
assets.
```
```
Note: Pardot is now known as Marketing Cloud Account Engagement. We wish we could
snap our fingers to update the name everywhere, but you can expect to see the previous
name in a few places until we replace it, including in the app itself.
Refer to the following lists to configure each custom report type, and use the steps to build the
reports you want.
```
**1.** From Salesforce Setup, enter _Report_ in the Quick Find box, and then select **Report Types**.
**2.** Click **New Custom Report Type**.
**3.** In the Fields Available for Reports section, click **Edit Layout**.
**4.** In the Field Layout Properties section, click **Create New Section**.
**5.** Give the section a title, and then drag the fields as outlined by the asset types listed here.

```
Campaigns Engagement • Primary Object: Campaigns
```
**-** Section 1: Campaigns
**-** Section 2: Parent Campaigns

```
This report includes all landing pages. To include only classic
landing pages, filter the report with the Source “Pardot.”
```
```
Landing Pages Engagement
```
**-** Primary Object: Campaigns
**-** Relationship: Landing Page, where the A record has at least
    one related B record
**-** Section 1: Landing Pages
**-** Section 2: Campaigns
**-** Section 3: Parent Campaigns

```
This report includes all list emails. To include only emails sent
from Account Engagement, filter the report with the From
Address “Pardot Marketing Automation.”
```
```
List Emails Engagement
```
**-** Primary Object: Campaigns
**-** Relationship: List Email, where the A record has at least one
    related B record

Show Engagement History on Records Report on Engagement History Data


**-** Section 1: List Emails
**-** Section 2: Campaigns
**-** Section 3: Parent Campaigns

```
This report includes data associated with any form and form handler. To show only forms
or form handlers, add a filter on the Type field.
```
```
Marketing Forms Engagement
```
**-** Primary Object: Campaigns
**-** Relationship: Marketing Form, where the A record has at least one related B record
**-** Section 1: Marketing Forms
**-** Section 2: Campaigns
**-** Section 3: Parent Campaigns

```
Marketing Links Engagement • This report includes data associated with any custom redirect or file. To show only
redirects or files, add a filter on the Type field.
```
**-** Primary Object: Campaigns
**-** Relationship: Marketing Link, where the A record has at least one related B record
**-** Section 1: Marketing Links
**-** Section 2: Campaigns
**-** Section 3: Parent Campaigns

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
**-** The majority of Engagement History components are available with all Account
    Engagement editions. Engagement History Dashboards require Growth, Plus, Advanced,
    or Premium edition.
**-** Components using the List Emails object include automated emails from Engagement
    Studio, completion actions, and automation rules. They don’t include operational emails.
**-** Objects marked in this table with an asterisk (*) show engagement history data by default.

```
Feature Available On... Data Storage Prerequisites
```
```
Metrics Fields • Campaign Salesforce • Connected Campaigns
```
Show Engagement History on Records Comparison of Engagement History Features


```
Feature Available On... Data Storage Prerequisites
```
**-** Marketing Link* **•** Field-level security: Access to engagement
**-** Marketing Form* history metrics
**-** Landing Page*
**-** List Email

```
Related List (Marketing Assets) Campaign Salesforce • Connected Campaigns
```
```
Related List (Activities) on page Account Engagement
8
```
**- •** Logged in to Account Engagement via
    Salesforce SSO

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
Lightning Component on page
11
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
Lightning Component on page
13
```
**-** Campaign **•** Pardot permission set
**-** Account **•** Connected Campaigns (for a dashboard on
**-** Lead campaign records only)
**-** Contact
**-** Person Account
**-** Opportunity

```
Use the Metrics Fields Component
Add Engagement History metrics as fields on connected campaigns and asset records. You can also build a custom report based on
the Campaign object. These tools can help you determine which marketing assets are most effective.
Use Engagement History Metrics Related Lists
Add the Engagement History Metrics related list to your campaign records to find the relationships that grow among campaigns,
prospects, and assets.
Using the Engagement History Related List
The Engagement History related list includes an activity feed of recent prospect engagement. It appears by default on most of your
marketing asset records, but you can also add it to your list email, lead, contact, account, or person account records.
```
Show Engagement History on Records Comparison of Engagement History Features


```
Using Engagement History Metrics Lightning Component
Add the Engagement History Metrics Lightning component to your campaign records to show high-level metrics associated with
the marketing assets in your connected campaigns.
Add the Engagement History Custom Lightning Component
Add the Engagement History Custom Lightning component to your lead, contact, and person account records to show how people
interact with your marketing assets. This component comes with your Account Engagement AppExchange package.
Engagement History Dashboards
An Engagement History Dashboard is powered by CRM Analytics and gives sales and marketing users the power to explore and
visualize important data. Embed an Engagement History Dashboard component on campaign, account, lead, contact, person account,
or opportunity records. The dashboard shows widgets that are tailored to each type of record.
```
### Use the Metrics Fields Component

```
EDITIONS
```
```
Available in: Salesforce
Professional , Enterprise ,
Performance , and
Unlimited Editions with All
Account Engagement
Editions
```
```
USER PERMISSIONS
```
```
To view Engagement History
metrics:
```
**-** Account Engagement
    User, CRM User, Sales
    Cloud User, or Service
    Cloud User

```
Add Engagement History metrics as fields on connected campaigns and asset records. You can also
build a custom report based on the Campaign object. These tools can help you determine which
marketing assets are most effective.
```
What’s Included?

**-** Engagement metrics from all asset types, via Salesforce connected campaign records
**-** Automated email metrics from after December 14, 2018

```
Note: This component doesn’t show activity associated with archived prospects, filtered
visitors, or operational emails.
```
Show Engagement History on Records Use the Metrics Fields Component


```
More About Metrics
To show any of these fields on campaign records, add them on the page layout. Choose the fields that make the most sense for your
users, and group them under a section with a label, such as Engagement Metrics. By default, marketing asset records include the available
metrics from this chart.
```
```
Associated Account Engagement Available Metrics
Asset
```
```
Salesforce Object
```
```
List emails and automated email
(operational emails excluded)
```
```
List Email • Total Delivered
```
**-** Delivery Rate
**-** Total Soft Bounced
**-** Total Hard Bounced
**-** Total Opens
**-** Unique Opens
**-** Open Rate Click Through Rate
**-** Unique Click-Through Rate
**-** Click to Open Ratio
**-** Unique Opt-Outs
**-** Opt-Out Rate
**-** Total Spam Complaints
**-** Spam Complaint Rate
**-** Total Tracked Link Clicks
**-** Unique Tracked Link Clicks

```
Landing Page Landing pages • Total View
```
**-** Unique Views
**-** Total Form Submissions
**-** Unique Form Submissions
**-** Form Submission Rate
**-** Total Form Errors
**-** Unique Form Errors
**-** Form Error Rate
**-** Total Tracked Link Clicks
**-** Unique Tracked Link Clicks

```
Marketing Link Files and custom redirects • Total Tracked Link Clicks
```
**-** Unique Tracked Link Clicks

```
Marketing Form Forms and form handlers • Total View
```
**-** Unique Views
**-** Total Form Submissions

Show Engagement History on Records Use the Metrics Fields Component


```
Associated Account Engagement Available Metrics
Asset
```
```
Salesforce Object
```
**-** Unique Form Submissions
**-** Form Submission Rate
**-** Total Form Errors
**-** Unique Form Errors
**-** Form Error Rate
**-** Total Tracked Link Clicks
**-** Unique Tracked Link Clicks

```
Two sets of these fields are available—to reflect the campaign
and the campaign hierarchy.
```
```
Campaigns N/A
```
**-** Total Emails Delivered (via List Email object)
**-** Unique Email Opens (via List Email object
**-** Unique Email Tracked Link Clicks (via List Email object)
**-** Total Form Views (via Marketing Form object)
**-** Total Form Submissions (via Marketing Form object)
**-** Unique Marketing Link Clicks (via Marketing Link object)
**-** Total Landing Page Views (via Landing Page object)
**-** Total Landing Page Form Submissions (via Landing Page
    object)

### Use Engagement History Metrics Related Lists

```
EDITIONS
```
```
Available in: Salesforce
Professional , Enterprise ,
Performance , and
Unlimited Editions with All
Account Engagement
Editions
```
```
Add the Engagement History Metrics related list to your campaign records to find the relationships
that grow among campaigns, prospects, and assets.
```
What’s Included?

**-** Engagement metrics from all asset types, via Salesforce connected campaign records
**-** Automated email metrics from after December 14, 2018

```
Note: This component doesn’t show filtered visitor activity or activity associated with archived
prospects.
```
Show Engagement History on Records Use Engagement History Metrics Related Lists


```
More About Engagement History Metrics
To display the metrics you need most, place the Engagement History Metrics related list on your campaign records. The Metrics related
list displays performance indicators for each asset type. For example, sends and opens for a list email, or views and form submissions for
a landing page.
Related lists for Landing Page, List Email, Marketing Form, and Marketing Link are available in the related lists section of your page layouts.
The List Emails related list includes automated emails from Engagement Studio, completion actions, and automation rules. It doesn’t
include operational emails. The Program Name field isn’t default on this related list, but you can add it in the page layout editor.
```
### Using the Engagement History Related List

```
EDITIONS
```
```
Available in: Salesforce
Professional , Enterprise ,
Performance , and
Unlimited Editions with All
Account Engagement
Editions
```
```
The Engagement History related list includes an activity feed of recent prospect engagement. It
appears by default on most of your marketing asset records, but you can also add it to your list
email, lead, contact, account, or person account records.
```
What’s Included?

**-** Engagement metrics from all asset types that originate in Account Engagement
**-** Some automated email activities, depending on where the related list is
**-** Localization based on your business unit locale setting (or Salesforce, when User Sync is in
    enabled)

```
Note: This component doesn’t show filtered visitor activity or activity associated with archived prospects.
```
Show Engagement History on Records Using the Engagement History Related List


```
More About Engagement History
To show this activity data on a record, drag the Engagement History related list to a tab on your page layout. We recommend placing
it on a tab that doesn’t load by default because a long list can affect page load speed.
This related list shows the last 30 days of data and presents different data fields depending on the object that displays it. Available fields
for each object are listed in this chart.
```
```
Object Available Fields
```
```
Account • Prospect
```
**-** Asset Name
**-** Asset Type
**-** Activity Type
**-** Activity Date

```
Lead, Contact, Person Account • Asset Name
```
**-** Asset Type
**-** Activity Type
**-** Activity Date

```
List Email, Marketing Form, Marketing Link, Landing Page • Prospect
```
**-** Activity Type
**-** Activity Date

Show Engagement History on Records Using the Engagement History Related List


### Using Engagement History Metrics Lightning Component

```
EDITIONS
```
```
Available in: Salesforce
Professional , Enterprise ,
Performance , and
Unlimited Editions with All
Account Engagement
Editions
```
```
Add the Engagement History Metrics Lightning component to your campaign records to show
high-level metrics associated with the marketing assets in your connected campaigns.
```
What’s Included?

**-** Engagement metrics from all asset types, via Salesforce connected campaign records
**-** Automated email metrics from after December 14, 2018

```
Note: This component doesn’t show activity associated with archived prospects, filtered
visitors, or operational emails.
```
```
To add this component, open the Lightning App Builder and look in the Standard components list. Select and drag the Engagement
Metrics component into a tab on your page layout.
```
Show Engagement History on Records Using Engagement History Metrics Lightning Component


### Add the Engagement History Custom Lightning Component

```
EDITIONS
```
```
Available in: Salesforce
Professional , Enterprise ,
Performance , and
Unlimited Editions with All
Account Engagement
Editions
```
```
USER PERMISSIONS
```
```
To view Engagement History
metrics:
```
**-** Account Engagement
    User, CRM User, Sales
    Cloud User, or Service
    Cloud User

```
Add the Engagement History Custom Lightning component to your lead, contact, and person
account records to show how people interact with your marketing assets. This component comes
with your Account Engagement AppExchange package.
What’s Included?
```
**-** Engagement activities from all asset types that originate in Account Engagement
**-** Some automated email activities, depending on where the related list is
**-** Localization based on your business unit locale setting (or based on Salesforce, when User Sync
    is enabled)

```
Note: This component doesn’t show filtered visitor activity or activity associated with archived
prospects.
```
**1.** From Setup, in the Quick Find box, enter _Lightning App Builder_ , and then select
    **Lightning App Builder**.
**2.** Select the Lead or Contact page that you want to work with, and click **Edit**.
**3.** In the Components list, enter _Engagement History_ , and then select **Engagement**
    **History**.
**4.** Drag the **Engagement History** component where you want it to appear in the page layout.
**5.** Save your work.
**6.** To manage assignment details, click **Activation**.

```
Engagement History Custom Lightning Component Activity Glossary
These prospect activities appear in the Engagement History Custom Lightning component. The component doesn’t show activities
for archived prospects.
```
```
Engagement History Custom Lightning Component Activity Glossary
These prospect activities appear in the Engagement History Custom Lightning component. The component doesn’t show activities for
archived prospects.
```
```
Activity Description
Prospect clicked an AddThis icon in an email and shared your
marketing content.
```
```
AddThis Share
```
```
Prospect clicked a tracked link. Includes custom redirects and
tracked links in emails, thank you content, and social messages.
```
```
Tracked Link Clicked
```
```
Email sent to the prospect hard bounced due to an invalid email
address. The prospect was automatically marked Do Not Email. If
```
```
Email Hard Bounce
```
```
your account allows multiple prospects with the same email
address, prospect records show a bounce if a prospect with the
same email address bounces.
```
```
Email Open Prospect opened an email.
```
```
Email Resubscribe Prospect resubscribed to emails from the unsubscribe page.
```
Show Engagement History on Records Add the Engagement History Custom Lightning Component


```
Activity Description
```
```
Email Sent Prospect was sent an email.
```
```
Email sent to the prospect soft bounced due to the prospect’s mail
server being unavailable. The prospect is still mailable, but is marked
```
```
Email Soft Bounce
```
```
Do Not Email after five soft bounces. If your account allows multiple
prospects with the same email address, the prospect record shows
a bounce if a prospect with that email address bounces.
```
```
Prospect reported spam from the prospect’s email client. This
prospect is marked Do Not Email.
```
```
Email Spam Complaint
```
```
Prospect clicked unsubscribe in an Account Engagement email or
unsubscribed from an Email Preference Center. If your account
```
```
Email Unsubscribe
```
```
allows multiple prospects with the same email address, prospect
records show an unsubscribe when a prospect with that email
address unsubscribes.
```
```
Email Preferences Open Prospect viewed an email preference page.
```
```
Form View Prospect viewed a form or form handler.
```
```
Prospect had an error when submitting a form or form handler.
Errors are often due to the prospect leaving a field blank or
submitting invalid information.
```
```
Form Error
```
```
Prospect successfully submitted a form or form handler, including
forms on landing pages.
```
```
Form Success
```
```
Landing Page View Prospect viewed a landing page.
```
```
Prospect clicked a link to a non-image file hosted by Account
Engagement.
```
```
File Accessed
```
```
Prospect contacted one of your users through the Olark live chat
connector, and the chat conversation was recorded.
```
```
Olark Live Chat
```
```
Opportunity Associated Opportunity was associated with this prospect.
```
```
Opportunity Created Opportunity was created for this prospect.
```
```
Opportunity Lost Opportunity for this prospect was lost.
```
```
Opportunity Won Opportunity for this prospect was won.
```
```
Priority Page View Prospect viewed a priority page.
```
```
Prospect searched for a term on your website’s site search. The
search term is also listed in the activity.
```
```
Site Search
```
```
Wistia Video Viewed Wistia video played or viewed.
```
```
A prospect’s visitor session. Includes the number of pages viewed
during the session and referrer information.
```
```
Website Visit
```
```
Prospect attended a webinar via GoToWebinar, WebEx, or
ReadyTalk.
```
```
Webinar Attended
```
Show Engagement History on Records Add the Engagement History Custom Lightning Component


```
Activity Description
```
```
Prospect registered for a webinar via GoToWebinar, WebEx, or
ReadyTalk.
```
```
Webinar Registered
```
```
Webinar Invited Prospect invited to a webinar.
```
```
Webinar Accepted Prospect accepted webinar invitation.
```
```
Prospect absent from a webinar that the prospect registered for
via GoToWebinar, WebEx, or ReadyTalk.
```
```
Webinar Absent
```
```
Event Registered Prospect registered for an event.
```
```
Event Attended Prospect attended an event.
```
```
Natural Search Prospect visit resulting from natural search.
```
```
Paid Search Prospect visit resulting from paid search.
```
### Engagement History Dashboards

```
EDITIONS
```
```
Available in: Salesforce
Professional (with API
access), Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
Growth , Plus , Advanced , or
Premium Edition
```
```
An Engagement History Dashboard is powered by CRM Analytics and gives sales and marketing
users the power to explore and visualize important data. Embed an Engagement History Dashboard
component on campaign, account, lead, contact, person account, or opportunity records. The
dashboard shows widgets that are tailored to each type of record.
```
```
Considerations for Engagement History Dashboard
When you work with Engagement History Dashboards, keep these considerations in mind.
Engagement History Dashboard Differences
The Engagement History Dashboard is available on a few types of records, and shows slightly
different information based on where it’s placed.
Turn On Engagement History Dashboards
Start exploring Account Engagement marketing data on your Salesforce campaign, account, lead, contact, and person account
records. Use Marketing Setup to turn on the feature and assign permissions. Then, embed a dashboard by adding the Engagement
History Dashboard component to Lightning pages.
```
Considerations for Engagement History Dashboard

```
EDITIONS
```
```
Available in: Salesforce
Professional (with API
access), Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
Growth , Plus , Advanced , or
Premium Edition
```
```
When you work with Engagement History Dashboards, keep these considerations in mind.
```
Permissions and Allocations

**-** If you use Professional Edition, make sure that your org has the API add-on.
**-** Your edition determines how many user licenses are allotted for sales and marketing users.
    **-** Growth: 5
    **-** Plus: 10
    **-** Advanced: 20
    **-** Premium: 20

Show Engagement History on Records Engagement History Dashboards


**-** The Analytics View Only Embedded App permissions set license gives your sales and marketing users access to analytics data and
    Engagement History Dashboards. It doesn’t allow access to Analytics Studio.
**-** The data inside Engagement History Dashboards originates from Account Engagement and is pushed into CRM Analytics. This data
    doesn’t count toward Salesforce storage limits, but records do count toward CRM Analytics data row limits.
**-** Connected Campaigns isn’t required to use Engagement History Dashboards, but it’s recommended for the full dashboard functionality.
**-** For Account Engagement Growth Edition, Engagement History can sync up to 90 days or 50 million rows of data, whichever comes
    first. For Account Engagement Plus, Advanced, and Premium Editions where B2B Marketing Analytics and the Prospect and Activity
    dataset are enabled, these features can sync up to 3 years or 35 million rows in total.
**-** For emails sent through Engagement Studio, the Engagement History dataset includes send data only for engagement programs
    that were created after December 14, 2018.

Working with Dashboards

**-** The first sync is always the biggest. Allow more than 24 hours for the initial sync of metrics data. The dataset is then refreshed every
    8 hours.
**-** Engagement History Dashboards aren’t supported in Internet Explorer 11.
**-** Data from unconnected campaigns is available in the dashboard, but it can’t be acted on. To click an asset or activity, the asset or
    activity must be related to a connected campaign. An application error appears when you attempt to interact with an item related
    to an unconnected campaign.
**-** If data is missing from the dashboard, it’s usually because there’s no data associated for the record in the given timeframe.
**-** Website visits come from the Engagement History dataset and have no corresponding Salesforce records.
**-** Learn how to embed dashboards in Lightning pages.

Dashboards and Multiple Business Units

**-** Because of the nature of leads, contacts, and person accounts, dashboards on these records show data for only one business unit
    at a time.
**-** Dashboards on accounts, campaigns, and opportunities can show data associated with more than one business unit.
**-** A user’s access and sharing settings determines whether they can act on datapoints. For example, if Luz has access to Business Unit
    A only, the Account dashboard can show data that originates in Business Units B and C. However, she can’t open any records from
    B or C.

Using the Opportunity Dashboard

**-** This dashboard uses activity dates to associate engagement to open opportunities.
**-** Reference lines appear only when an opportunity has a role assigned or when the opportunity’s dates fall within the dataset date
    range.
**-** In the Contact widget, contacts with an unassigned contact role are labeled Unspecified. If a contact has no role, it’s labeled None.
**-** If data is missing from the Opportunity dashboard, it’s usually because no opportunity contact roles are assigned.

Show Engagement History on Records Engagement History Dashboards


Engagement History Dashboard Differences

```
EDITIONS
```
```
Available in: Salesforce
Professional (with API
access), Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
Growth , Plus , Advanced , or
Premium Edition
```
```
The Engagement History Dashboard is available on a few types of records, and shows slightly
different information based on where it’s placed.
Engagement History Dashboards have some similarities, such as availability and permissions. All
the dashboards are based on valid, unfiltered visitor and prospect data. Data includes visitors that
have a prospect ID, including archived prospects. But because the dashboards work on a variety of
records, the filtering and widgets used on each dashboard type differ slightly.
The four types of dashboards are based on campaigns, opportunities, accounts, or leads and contacts.
Each type has some basic filtering, which makes the dashboard relevant to the record that it appears
on. From there, users can explore the data with more filters.
```
```
Dashboard Type Available on Description Widgets
```
```
Graph: Engagement
Trends
```
```
Shows engagement
activity on campaign
assets filtered by the
```
```
Campaign dashboard Campaign records
```
```
Table: Engagement
Detail
```
```
selected campaign
record
```
```
Graphs: Campaign
Activities, Engagement
over Time, Most Active
```
```
Shows campaign
activity and active
contacts filtered by the
selected account
record
```
```
Account dashboard Account records
```
```
Table: Engagement
Detail
```
```
Graphs: Activity Over
Time, Engaged
```
```
Shows the person’s
activity by campaign
and asset filtered by
```
```
Lead, contact, and
person account
records
```
```
Lead/Contact
dashboard
Campaigns, Engaged
the selected account Content
record
Table: Engagement
Detail
```
```
Graphs: Activity
Timeline (Filter by
```
```
Shows engagement
activity associated with
contacts or person
```
```
Opportunity Opportunity records
dashboard
Contact), Activity by
accounts that have an Campaign
opportunity contact
Table: Engagement
Detail
```
```
role. This dashboard is
filtered by the selected
opportunity record
and its associated
account
```
Show Engagement History on Records Engagement History Dashboards


Turn On Engagement History Dashboards

```
EDITIONS
```
```
Available in: Salesforce
Professional (with API
access), Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
Growth , Plus , Advanced , or
Premium Edition
```
```
USER PERMISSIONS
```
```
To enable Engagement
History Dashboards:
```
**-** Customize Application
To view Engagement History
Dashboards:
**-** Analytics View Only User
    permission set

```
Start exploring Account Engagement marketing data on your Salesforce campaign, account, lead,
contact, and person account records. Use Marketing Setup to turn on the feature and assign
permissions. Then, embed a dashboard by adding the Engagement History Dashboard component
to Lightning pages.
```
**1.** From Marketing Setup, in the Quick Find box, enter _EngagementHistory_ , and then
    select **Engagement History**.
**2.** Jump to step 3 and turn on Engagement History Dashboards.
**3.** Using the Lightning App Builder, find the Engagement History Dashboard component in the
    Standard section, and drag it into a tab.
**4.** In Marketing Setup, assign the Analytics View Only User permission set to each user who wants
    to see the dashboard.
**5.** Customers using Plus, Advanced, or Premium editions with B2B Marketing Analytics can turn
    on access to up to three years of engagement data. (Optional)
    **a.** From Marketing Setup, in the Quick Find box, enter _Analytics_ , and then select **B2B**
       **Marketing Analytics**.
    **b.** Click **Optional Features** , and expand **Identify Your Most Engaged Prospects**.
    **c.** Click **Enable Dataset**.

```
Note: If your account doesn’t have the system users Analytics Cloud Integration User and
Analytics Cloud Security User, they’re added to your account when you enable Engagement
History Dashboards.
It can take more than 24 hours for data to sync the first time. We recommend that you wait for data to appear before you assign access
to users.
```
## Resources

```
EDITIONS
```
```
Available in: Salesforce
Professional , Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
Growth , Plus , Advanced , or
Premium Edition
```
```
Find out more about how to use Engagement History and reports.
```
**-** Blog: How to Report on Marketing Activities with Engagement History
**-** Knowledge Article: Five recommended custom report types for Engagement History

Show Engagement History on Records Resources


