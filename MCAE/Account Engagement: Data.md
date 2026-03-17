# Account Engagement: Data

# Cloud Integration

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

- Connecting Account Engagement and Data Cloud
- Connect Account Engagement to Data Cloud
- Importing Account Engagement Data into Data Cloud
   - Import Prospect Data from Account Engagement into Data Cloud
   - Cloud Considerations for Importing Engagement Data from Account Engagement into Data
   - Import Email Engagement Data from Account Engagement into Data Cloud
- Use Account Engagement Data with Data Cloud



## Connecting Account Engagement and Data Cloud

```
EDITIONS
```
```
Available in: Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
```
Salesforce Data Cloud organizes and unifies data across Salesforce and other external data sources.
Import Account Engagement data into Data Cloud to drive calculated insights and build segments.

You can bring these data types from Account Engagement into Data Cloud.

**-** Prospect data
**-** Email engagement data
**-** Form engagement data
**-** Landing page engagement data
**-** Tracked web page engagement data

To get started, connect Account Engagement to Data Cloud and then import your data.

## Connect Account Engagement to Data Cloud

```
To ingest your prospect engagement data, connect your Account Engagement business units to Data Cloud.
```
## Importing Account Engagement Data into Data Cloud

```
Prepare and import data from your Account Engagement business units into Data Cloud.
Use Account Engagement Data with Data Cloud
Use Account Engagement data with Data Cloud to drive calculated insights, build segments, and use other Data Cloud features.
```
Connect Account Engagement to Data Cloud

```
EDITIONS
```
```
Available in: Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
```
```
USER PERMISSIONS
```
```
To configure Data Cloud:
```
**-** Data Cloud Admin AND
    Data Cloud Marketing
    Admin

To ingest your prospect engagement data, connect your Account Engagement business units to
Data Cloud.

**1.** From Setup, in the Quick Find box, enter _Data Cloud_.
**2.** Under Salesforce Integrations, select **Marketing** > **Account Engagement**.
**3.** Click **Get Started**.
**4.** Add the Account Engagement business units that you want to connect to the Selected Business
    Unit column, and then click **Done**.
    You can only connect business units that are associated with your Data Cloud instance. You
    can also add or remove business units later.

After your business units are connected, export Account Engagement data for ingestion into Data
Cloud.

Importing Account Engagement Data into Data Cloud

Prepare and import data from your Account Engagement business units into Data Cloud.


### Import Prospect Data from Account Engagement into Data Cloud

```
To import prospect data from Account Engagement into Data Cloud, configure permissions, create data streams, and then map the
data streams to data model objects (DMOs).
Considerations for Importing Engagement Data from Account Engagement into Data Cloud
Before you import marketing asset engagement data into Data Cloud, review considerations for timing, criteria, limitations, Data
Cloud credits, and removing data from Data Cloud.
Import Email Engagement Data from Account Engagement into Data Cloud
To import email engagement data from Account Engagement into Data Cloud, create data streams, and then map the data streams
to data model objects (DMOs).
```
### Import Prospect Data from Account Engagement into Data Cloud

```
EDITIONS
```
```
Available in: Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
```
```
USER PERMISSIONS
```
```
To edit permission sets:
```
**-** Salesforce Admin
To configure Data Cloud and
edit data streams:
**-** Data Cloud Marketing
    Data Aware Specialist

```
To import prospect data from Account Engagement into Data Cloud, configure permissions, create
data streams, and then map the data streams to data model objects (DMOs).
Before you start, connect Account Engagement to Data Cloud and set up a Salesforce Connection
in Data Cloud.
```
Configure Permissions

**1.** From Setup, in the Quick Find box, enter _PermissionSets_.
**2.** Select the **Data Cloud Salesforce Connector** permission set, and click **Object Settings**.
**3.** Select **Contacts** , and click **Edit**.
**4.** Add read access to the fields within the permission set.
**5.** Save your work.
**6.** Repeat this process for leads.

```
Create a Data Stream and Add Fields for the Contact and Lead
Objects
```
**1.** In Data Cloud, create and deploy a data stream using the Sales Data bundle within the Salesforce CRM connected source. Choose
    the default options when creating your data stream.
    If you’ve already deployed a data stream for the contact and lead objects, you don’t need to deploy a new data stream, and you can
    continue to the next step.
**2.** On the Data Streams tab, select the Salesforce CRM data stream for contacts.
**3.** Click **Add Source Fields** and select the fields that you want to add to your data stream.
**4.** Save your work.
**5.** Repeat this process for the lead object.

Map Account Engagement Data to Data Model Objects

**1.** In Data Cloud, on the Data Streams tab, select the Salesforce CRM data stream for contacts.
**2.** Under Data Mapping, click **Review**.

```
Import Prospect Data from Account Engagement into Data
Cloud
```
Connecting Account Engagement and Data Cloud


**3.** To create a mapping connection, select the data lake object (DLO) field to map, and then click the related data model object (DMO)
    field. You can select an object from your data model or add a custom object.
    A confirmation appears with an arrow connecting the fields.
**4.** To pull Data Cloud segment membership into Account Engagement, create a custom field in your DMO with these values, and map
    the Contact ID to that field.
    **a.** For Field Label, enter _AccountEngagement IntegrationID_.
    **b.** For Field API Name, use Account_Engagement_Integration_ID.
    **c.** For Data Type, select **Text**.
**5.** Save your work.
**6.** Repeat these steps for the leads data stream.
You can now use these DMOs to drive calculated insights and create segments in Data Cloud.

### Considerations for Importing Engagement Data from Account Engagement

### into Data Cloud

```
EDITIONS
```
```
Available in: Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
```
```
Before you import marketing asset engagement data into Data Cloud, review considerations for
timing, criteria, limitations, Data Cloud credits, and removing data from Data Cloud.
```
```
Amount of Time Needed for Importing
When you start importing engagement data from Account Engagement to Data Cloud, it can take
days or weeks to complete the first import based on the number of eligible activities.
After the first import, Account Engagement prepares new activities as they’re created. This process
begins within minutes, but it can take hours or days based on the number of new activities. Data Cloud checks the connection every
hour for new activities that are ready for import.
```
```
Import Criteria
Engagement data is imported to Data Cloud when all these criteria are met.
```
**-** The activity occurs after the Filter By Date that you specify when configuring the Data Cloud connector in Account Engagement.
**-** The prospect performing the activity is synced with Salesforce CRM via the Account Engagement Salesforce Connector.
**-** The activity is performed on a marketing asset record with a connected campaign that’s syncing with Salesforce CRM.
Operational email engagement data and Email Preference Open activities aren’t included.

```
Data Cloud Credits
You can import as many as activities as you want from Account Engagement to Data Cloud. However, imports consume Data Cloud
credits, and larger imports consume more credits.
```
```
Removing Data from Data Cloud
To remove engagement data, pause the connector in Account Engagement. Then, delete the data in Data Cloud. You can’t use Account
Engagement to remove your data from Data Cloud.
```
```
Considerations for Importing Engagement Data from Account
Engagement into Data Cloud
```
Connecting Account Engagement and Data Cloud


### Import Email Engagement Data from Account Engagement into Data Cloud

```
EDITIONS
```
```
Available in: Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
```
```
USER PERMISSIONS
```
```
To configure Data Cloud and
edit data streams:
```
**-** Data Cloud Marketing
    Data Aware Specialist

```
To import email engagement data from Account Engagement into Data Cloud, create data streams,
and then map the data streams to data model objects (DMOs).
Before you start, connect Account Engagement to Data Cloud and review considerations for
importing email engagement data to Data Cloud.
```
Create a Data Stream for the List Email Object

**1.** In Data Cloud, create a Saleforce CRM data stream for the List Email object. Under Object Details,
    select the **Other** category.
**2.** Deploy the data stream to the default data space.

Map the List Email DLO to a DMO

**1.** In Data Cloud, from the list email data stream record, go to Data Mapping.
**2.** Click **Start**.
**3.** Add the Bulk Email Message DMO.
**4.** Manually map these fields. Don’t change the automatically generated mappings.
    **a.** Map Campaign ID to Campaign.
    **b.** Map List Email ID to Bulk Email Message Id.
**5.** Save your work.

Create a Data Stream for the Email Activity Object

**1.** In Data Cloud, create a Marketing Cloud Account Engagement data stream for the email activity object.
**2.** Deploy the data stream.

(Optional) Add Mappings from the Email Activity Data Stream to the DMO

**1.** In Data Cloud, from the email activity data stream record, go to Data Mapping.
**2.** Click **Review**.
**3.** Add more mappings if needed, but don’t change the automatically generated mappings.

```
Import Email Engagement Data from Account Engagement
into Data Cloud
```
Connecting Account Engagement and Data Cloud


## Use Account Engagement Data with Data Cloud

```
EDITIONS
```
```
Available in: Enterprise ,
Performance , and
Unlimited Editions with
Account Engagement
```
```
USER PERMISSIONS
```
```
To create segments in Data
Cloud:
```
**-** Data Cloud Marketing
    Manager OR Data Cloud
    Marketing Specialist
To add segments to a
dynamic list in Account
Engagement:
**-** Account Engagement
    Administrator or
    Marketing role AND
    Data Cloud Marketing
    Manager OR Data Cloud
    Marketing Specialist

```
Use Account Engagement data with Data Cloud to drive calculated insights, build segments, and
use other Data Cloud features.
Before you start, connect Account Engagement to Data Cloud and import Account Engagement
data into Data Cloud.
```
### Driving a Calculated Insight in Data Cloud

```
You can use a calculated insight to define and calculate multidimensional metrics in Data Cloud
based on prospect data or email engagement data from Account Engagement. You can also use
calculated insights to define segment criteria.
For more information, see Calculated Insights and Calculated Insights in Segments.
```
### Create a Segment in Data Cloud

```
You can use your Account Engagement prospect data that’s mapped to data model objects (DMOs)
to create a segment in Data Cloud.
```
**1.** In your default data space, create a segment in Data Cloud based on a DMO that has the Account
    Engagement Integration ID.
**2.** Segment your data with attributes.
**3.** Publish your segment in Data Cloud.

### Create a Dynamic List from a Data Cloud Segment

```
After you create a Data Cloud segment, you can create a dynamic list in Account Engagement to pull in your segment. You can have up
to 25 dynamic lists per business unit and up to one million prospects per list.
```
**1.** Create a dynamic list using a name that’s similar to the Data Cloud segment that you’re connecting the dynamic list to, and select
    Dynamic List.
**2.** For Dynamic List Type, select **Data Cloud segment**.
**3.** For Data Cloud Segment, select a segment from the default data space.
    You can only select a published segment. A segment can be connected to one dynamic list per business unit at a time.
**4.** Save your work.
    A new dynamic list can take up to 3 hours to populate the first time it’s connected to a Data Cloud segment. A dynamic list can take
    up to 1 hour to update after a Data Cloud segment is refreshed.

```
Data Cloud segments and Account Engagement dynamic lists update automatically based on criteria. Monitor your segments and
dynamic lists over time, and adjust your criteria as needed.
```
Connecting Account Engagement and Data Cloud Use Account Engagement Data with Data Cloud


