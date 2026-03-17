# Implementation Guide: Email

# Experience in Account

# Engagement

Salesforce, Spring ’ 26

```
Last updated: November 17, 2025
```

© Copyright 2000–2026 Salesforce, Inc. All rights reserved. Salesforce is a registered trademark of Salesforce, Inc., as are other

```
names and marks. Other marks appearing herein may be trademarks of their respective owners.
```

## CONTENTS

- Enhanced Email for Account Engagement
- Prerequisites for Setting Up Enhanced Email
- Using Email Templates and Email Content Together
- Considerations for Designing and Sending Emails
- Set Up Enhanced Email in Account Engagement
   - Assign Admin Permissions for Enhanced Email
   - Create a Domain for Enhanced Email
   - Configure Digital Experiences for Enhanced Email
   - Assign User Permissions for Enhanced Email
   - Enhanced Email Experience Permissions
- Design, Test, and Send Emails
   - Considerations for Using HML Fields for Emails in Lightning
   - Create Enhanced Emails
   - Preview and Test Emails
   - Send Emails
   - Reuse Email Content for List Emails
- Guidelines for Creating Custom Report Types for Email Content



## Enhanced Email for Account Engagement

```
EDITIONS
```
```
Available in: All Account
Engagement Editions with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
Connect to customers with emails that are easy to design on the Salesforce platform. After you
build email templates or email content, customize them with HML merge fields. Then, choose
whether to send an individual email or add it to a program in Engagement Studio. Streamline
writing time by reusing email content, or send and resend email content to different segments.
Tailor the send experience, and track email engagements to determine how well your email content
is performing.

## Prerequisites for Setting Up Enhanced Email

```
Using the enhanced email experience in Account Engagement relies on a few other features.
Using Email Templates and Email Content Together
With the enhanced email experience in Account Engagement, you can select an email template before you start building your email
content. An email template is a reusable layout. It can help you boost productivity and encourage consistency among content
creators, but it isn’t a required component of an enhanced email send. It’s your choice whether email templates are a good fit for
your business processes.
Considerations for Designing and Sending Emails
Review these considerations before using the enhanced email experience in Account Engagement.
Set Up Enhanced Email in Account Engagement
To set up the enhanced email experience for interactive and engaging email design, we recommend that a Salesforce admin and
an Account Engagement admin work together.
Design, Test, and Send Emails
Interactively design emails from scratch or from a template and send emails from the email content record. You can also preview
and test your email before sending it.
Guidelines for Creating Custom Report Types for Email Content
Create custom report types that include email content and list email data. Marketers can then create reports to analyze and better
understand the performance of their email content. Review the following guidelines and examples of reports.
```
Prerequisites for Setting Up Enhanced Email

```
EDITIONS
```
```
Available in: All Account
Engagement Editions with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
Using the enhanced email experience in Account Engagement relies on a few other features.

To use enhanced email, Connected Campaigns and Handlebars Merge Language must be enabled.
You must also have a verified Salesforce Connector. Find out more about these features.

**-** Connect Account Engagement Campaigns to Salesforce Campaigns
**-** Personalize Content with Handlebars Merge Fields
**-** Setting Up a Salesforce Connection for Accounts Purchased After February 11, 2019

If you need assistance navigating Marketing Setup or with other Salesforce basics, check out these
trails and modules on Trailhead.

**-** Salesforce User Basics
**-** Navigate Setup


**-** User Management

## Using Email Templates and Email Content Together

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Essentials ,
Professional , Enterprise ,
Performance , Unlimited ,
and Developer Editions
```
```
With the enhanced email experience in Account Engagement, you can select an email template
before you start building your email content. An email template is a reusable layout. It can help
you boost productivity and encourage consistency among content creators, but it isn’t a required
component of an enhanced email send. It’s your choice whether email templates are a good fit for
your business processes.
```
```
Note: The email templates created in the Email Template Builder are used in Lightning
Experience and Account Engagement Lightning App. Information about classic email templates
is also available: Classic Email Templates
In Lightning, a template made in the Email Template Builder is a basic layout that contains default
content. You can use it as a starting point for customizing future email messages, or send it as-is. An email content record contains
metadata and content that’s used for one or more email sends.
Email Templates
Usage: The Email Template Builder is available for use by Account Engagement, Sales Cloud, and Service Cloud users. In Account
Engagement, you can select an email template as the basis for creating an email content record. Sales and Service users can send their
templates in a few ways, such as in Sales Engagement or the docked composer.
Reporting: Standard reports for email templates include engagement metrics and usage. In Account Engagement, engagement metrics
appear in the Email Content related list on an email template record.
Email Content
Usage: The drag-and-drop builder for email content is available in Account Engagement only. Email content records created in Account
Engagement can’t be shared to Sales or Service users.
Reporting: Engagement metrics for marketing emails appear in several places including the Email Sends related list, Engagement History,
and List Email reports. You can review metrics on a specific send record or look at aggregate metrics on an email content record. Metrics
for operational emails aren't included in the Email Sends related list or Engagement History.
```
```
Example: Marketing manager Gina creates an event invitation template that provides space for a banner, logistical information,
and RSVP button. For brand consistency, she adds her company’s default header and footer. She names it Template: Event Invitations.
Later, the event specialist, Kamal creates an email content record for an upcoming meet and greet at a local restaurant. When he
starts building the email, he selects Gina’s template to work from. He fills in specific content in each area: an image from their last
meet-and-greet, the restaurant name, the event time and date, and the link to where he’s tracking RSVPs.
```
```
Example: A few sales reps tell Gina that they also want to invite people to the meet-and-greet. She and Kamal create another
email template with the event information. They name this public template Event Invitation: July Meet-and-Greet. Now the finalized
template appears to all the sales reps so that they can send it directly to their leads and contacts.
```
Enhanced Email for Account Engagement Using Email Templates and Email Content Together


## Considerations for Designing and Sending Emails

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
Review these considerations before using the enhanced email experience in Account Engagement.
```
### Browsers and Edition Availability

**-** The enhanced email experience is available only in Account Engagement Lightning App.
**-** You can preview email in sandboxes, but you can’t send test emails. To test the CMS image
    repository integration select the default CDN domain during channel setup.
**-** Support for managing and sending email content is limited in Developer Editions. Access to
    Salesforce CMS images and the ability to send an email aren’t enabled.
**-** Internet Explorer 11 and Microsoft Edge aren’t supported browsers for designing emails in this experience.

### Email Content and CMS Management

**-** Users with the Manage Email Content user permission see all email content records. You can’t filter or hide email content records.
**-** You can’t delete an email content record with related sends.
**-** Email content records can’t be recovered after deletion.
**-** If an email content record is deleted from an associated CMS workspace, you’ll be unable to edit the email if you try to open it from
    the Email Content tab in Account Engagement.
**-** To upload a CMS image when designing emails, a user must be a contributor to the associated CMS workspace.
**-** Developers can build custom Lightning Web Components to help bring third-party surveys, webinars, or other content into your
    emails.

### Building and Tracking Emails

**-** You can edit the HTML Body field in the drag-and-drop editor only. The field isn’t editable on the email content record or via the
    API.
**-** Pardot Merge Language (PML) variable tags aren’t supported. Use Handlebars Merge Language (HML) merge fields instead.
**-** Account Engagement-only standard and custom fields are unavailable as HML merge fields. Use Salesforce standard and custom
    fields instead. Or, map your custom Account Engagement fields to Salesforce fields.
**-** The following tools aren’t supported: folders, dynamic content, snippets, and A/B testing.
**-** The domain associated with the CMS channel is only visible to customers in image URLs and email source code.

### Account Engagement Business Units

**-** When an email is sent or activated for automation, the campaign, list, sender, and reply-to options are based on the user’s current
    business unit.
**-** Your CMS channel is related to one domain and used for all sends. If you have multiple business units, the same domain and channel
    are always used.
**-** Email content and templates ignore an asset’s business unit assignment when tracking engagement. For example, if you send
    Business Unit A’s form through an email connected to Business Unit B, we still attribute the form engagement to Business Unit A.

Enhanced Email for Account Engagement Considerations for Designing and Sending Emails


### Images

**-** You can select images from a single Salesforce CMS channel only. Salesforce Files aren’t supported and don’t load when emails are
    sent.
**-** Always use a publicly available, absolute URL for your links.
**-** SVG images, JavaScript, and other active content aren’t supported in email content.

### Email Templates

**-** To select an email template for use with email content, make sure that the template doesn’t contain Salesforce Files. Also, the related
    entity type must be Lead, Contact, or None.
**-** Enhanced letterhead isn’t supported for email templates built in the Email Template Builder.
**-** When you change the email template on the email content record, the Subject and HTML Body fields are overwritten with the
    template values. These two field values remain if you remove the template later, but don’t replace it.
**-** We recommend that you avoid including Account Engagement-only merge fields, such as Email Preference Center, in an email
    template. When Sales or Service users select an email template to send to a lead or contact, the merge fields break.
**-** You can’t create via API an email template that uses the enhanced sending experience.
**-** Tags aren’t supported in the Email Template Builder.

### Allocations

**-** The maximum character allowance for the HTML Body and Text Body fields is 384,000 characters.
**-** You can send a test email to a maximum of 10 test lists of 100 recipients each. Or, you can send a test to up to 50 individual addresses.
**-** If you exceed the character limit for an HTML component, try splitting the content into two HTML blocks.

Enhanced Email for Account Engagement Considerations for Designing and Sending Emails


## Set Up Enhanced Email in Account Engagement

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
USER PERMISSIONS
```
```
To connect Account
Engagement and Salesforce:
```
**-** Customize Application
    AND
    Modify All Data
To connect campaigns:
**-** Account Engagement
    Administrator role
    AND
    B2B Marketing
    Automation App
    permission set license
To configure Digital
Experiences:
**-** Modify All Data
    OR
    Create CMS Workspaces
    and Channels

```
To set up the enhanced email experience for interactive and engaging email design, we recommend
that a Salesforce admin and an Account Engagement admin work together.
```
```
Note: Access to workspaces and channels in Digital Experiences is included with any
Salesforce edition that supports Account Engagement.
```
1. Assign Admin Permissions for Enhanced Email
    Make sure that the person configuring enhanced email in Account Engagement has the
    appropriate access. You can quickly create a permission set with the necessary permissions on
    the Content Setup page. A Salesforce admin is best equipped to assign the permissions that
    are required.
2. Create a Domain for Enhanced Email
    Stored images used for your emails are associated with a domain you manage. Enhanced email
    requires a domain that’s configured using a content delivery network (CDN) over HTTPS. Select
    any verified domain that meets that criteria.
3. Configure Digital Experiences for Enhanced Email
    When you send enhanced email with Account Engagement, you can use the Digital Experiences
    app as a unified image repository. Digital Experiences offers a CMS workspace where you can
    save files and control user access and a CMS channel where those files can be published. When
    you use Digital Experiences with enhanced email, the images published to your channel become
    available while marketers are building emails.
4. Assign User Permissions for Enhanced Email
    To give users access to the Email Content object and to Salesforce Digital Experiences, assign
    permissions. A Salesforce admin is best equipped to assign the required permissions.
5. Enhanced Email Experience Permissions
    Various permissions are necessary to set up, create, and send enhanced email from Account
    Engagement.

Enhanced Email for Account Engagement Set Up Enhanced Email in Account Engagement


### Assign Admin Permissions for Enhanced Email

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
USER PERMISSIONS
```
```
To access Marketing Setup:
```
**-** View Setup and
    Configuration
    AND
    Customize Application
To create permission sets:
**-** Manage Profiles and
    Permission Sets
To assign permission sets:
**-** Assign Permission Sets

```
Make sure that the person configuring enhanced email in Account Engagement has the appropriate
access. You can quickly create a permission set with the necessary permissions on the Content
Setup page. A Salesforce admin is best equipped to assign the permissions that are required.
```
**1.** From Marketing Setup, in the Quick Find Box, enter _Content_ , and then select **Content Setup**.
**2.** To create the necessary permission set, click **Create Permission Set** and save.
**3.** From Setup, click **Manage Assignments**.
**4.** On the permission set page, click **Manage Assignments** again.
**5.** To select the admin user who configures email, click **Add Assignments**.
**6.** Select a user, and then click **Assign**.
**7.** For easy access to Salesforce Digital Experiences, add the CMS Workspaces and CMS Channels
    tabs to your Account Engagement Lightning App toolbar.

### Create a Domain for Enhanced Email

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
USER PERMISSIONS
```
```
To add or edit a domain:
```
**-** Manage Custom
    Domains

```
Stored images used for your emails are associated with a domain you manage. Enhanced email
requires a domain that’s configured using a content delivery network (CDN) over HTTPS. Select any
verified domain that meets that criteria.
You have three choices when selecting a domain.
```
**-** Your Salesforce My Domain. With My Domain, you can include your company name in your
    URL. See My Domain.
**-** An existing custom domain that you already own and that uses a content delivery network
    (CDN) over HTTPS. See Custom Domains.
**-** A new domain that you purchase and configure from a domain registrar that you choose.
To verify the domain you choose to use for enhanced email, complete these steps.
**1.** Review the considerations for the Salesforce CDN.
**2.** Complete the prerequisites for a custom domain and the prerequisites for the Salesforce CDN.
**3.** Set up a custom domain that uses the Salesforce CDN.

Enhanced Email for Account Engagement Assign Admin Permissions for Enhanced Email


### Configure Digital Experiences for Enhanced Email

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
USER PERMISSIONS
```
```
To configure Digital
Experiences workspaces
and channels:
```
**-** Modify All Data
    OR
    Create CMS Workspaces
    and Channels

```
When you send enhanced email with Account Engagement, you can use the Digital Experiences
app as a unified image repository. Digital Experiences offers a CMS workspace where you can save
files and control user access and a CMS channel where those files can be published. When you use
Digital Experiences with enhanced email, the images published to your channel become available
while marketers are building emails.
Digital Experiences contributors must have the Salesforce user license.
```
```
Note: Digital Experiences can be used with enhanced email and landing page experiences.
```
**1.** Click the Digital Experiences Home action menu, select **CMS Channel** , choose a Public Channel,
    and then click **Create Channel**.
    Using a public channel ensures that you can delete the Pardot package in the future.
**2.** Name the channel something descriptive, such as Email Content or a business unit name, and
    then save it. You can edit the channel name at any time.
**3.** To configure a channel’s domain, edit the channel.
    **a.** From the channel list, click the action menu, and then select **Edit**.
    **b.** Select **Enable Domain** , choose the domain you configured from the dropdown, and then
       save.
**4.** Click the Digital Experiences Home action menu, select CMS Workspace, and then click **Add Workspace**.
**5.** To configure your workspace, follow the prompts.
    **a.** Name the workspace and select the channel you want to include.
    **b.** Select the Salesforce users that need access to the workspace, and then select a role for each.
       A content manager has full access to a workspace’s files. A content admin can also edit the workspace settings.

```
c. Select the languages you want to support and include a default language.
d. Review your settings, and then click Done.
```
**6.** From the Content Setup page, click **Select Channel** , choose the one you created from the dropdown, and save.

Enhanced Email for Account Engagement Configure Digital Experiences for Enhanced Email


### Assign User Permissions for Enhanced Email

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
USER PERMISSIONS
```
```
To access Marketing Setup:
```
**-** View Setup and
    Configuration
    AND
    Customize Application
To create permission sets:
**-** Manage Profiles and
    Permission Sets
To assign permission sets:
**-** Assign Permission Sets

```
To give users access to the Email Content object and to Salesforce Digital Experiences, assign
permissions. A Salesforce admin is best equipped to assign the required permissions.
```
**1.** From Marketing Setup, in the Quick Find box, enter _Content_ , and then select **Content Setup**.
**2.** Click **Manage Assignments**.
**3.** On the Create Account Engagement Content permission set page, click **Manage Assignments**.
**4.** Click **Add Assignments** , and then select the users who need the permission set.
**5.** Click **Assign**.
**6.** For easy access to files, encourage users to add CMS Workspace and CMS Channel tabs to their
    navigation.
    **a.** Open the Account Engagement Lightning App.
    **b.**
       To edit tabs, click on the navigation.
    **c.** Click **Add More Items**.
    **d.** With **All** selected, search for CMS and select **CMS Workspaces** and **CMS Channels**.
    **e.** Click **Add 2 Nav Items** and save.

```
To allow a non-admin user to create workspaces and channels in the Digital Experiences app, assign
the user the Create CMS Channels and Workspaces system permission.
```
### Enhanced Email Experience Permissions

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
Various permissions are necessary to set up, create, and send enhanced email from Account
Engagement.
Pardot is now known as Marketing Cloud Account Engagement. We wish we could snap our fingers
to update the name everywhere, but you can expect to see the previous name in a few places until
we replace it, including in the app itself.
```
```
Permission Sets and User Roles
An admin can create and assign the Create Account Engagement Content permission set on the
Content Setup page in Marketing Setup. The permission set includes access to the drag-and-drop builder, the ability to manage email
content, and access to Salesforce CMS (Content Management System) and its Channels and Workspace tabs.
To preview, test, or send an email, users must also have a Marketing user role in Account Engagement, or the individual permissions
indicated in the table.
```
Individual Permissions

```
Permission Name Location Type Description Configuration
```
```
Provides access to the On
email content editor in
```
```
Access Drag and Drop Salesforce Setup System Permissions
Content Builder
```
Enhanced Email for Account Engagement Assign User Permissions for Enhanced Email


```
Permission Name Location Type Description Configuration
```
```
Account Engagement
Lightning App
```
```
Allows users to make an Optional
email content record
```
```
Activate Email for Salesforce Setup System Permissions
Automation
available in Engagement
Studio
```
```
Allows users to create, On
edit, and delete email
content
```
```
Manage Email Content Salesforce Setup System Permissions
```
```
Allows non-admin users Optional
to create channels and
```
```
Create CMS Workspaces Salesforce Setup System Permissions
and Channels
workspaces in Salesforce
CMS
```
```
Allows users to add Optional
custom components to
```
```
View Setup and Salesforce Setup System Permissions
Configuration
enhanced email
templates
```
```
Provides access to On
Salesforce CMS
```
```
Salesforce CMS Salesforce Setup App Assignments
(standard__SalesforceCMS)
```
```
Makes the CMS Channels Available, Visible
tab available for selection
```
```
CMS Channels Salesforce Setup Object Settings
```
```
in Account Engagement
Lightning App
```
```
Makes the CMS Available, Visible
Workspaces tab available
```
```
CMS Workspaces Salesforce Setup Object Settings
```
```
for selection in Account
Engagement Lightning
App
```
```
Provides access to View
prospect record data
```
```
Account Engagement Prospects tab
Settings, User Roles
```
```
Prospects
```
```
Provides access to View
Account Engagement
campaigns data
```
```
Account Engagement Marketing tab
Settings, User Roles
```
```
Campaigns
```
```
Provides access to Create/Edit, Send to List
enhanced emails and
sending pipeline
```
```
Account Engagement Marketing tab
Settings, User Roles
```
```
Emails
```
```
Provides access to View
segmentation lists
```
```
Account Engagement Marketing tab
Settings, User Roles
```
```
Segmentation Lists
```
Enhanced Email for Account Engagement Enhanced Email Experience Permissions


## Design, Test, and Send Emails

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
Interactively design emails from scratch or from a template and send emails from the email content
record. You can also preview and test your email before sending it.
```
### Considerations for Using HML Fields for Emails in Lightning

```
Some HML merge fields in Salesforce aren’t supported in Account Engagement. To use these
field values, map custom fields from Account Engagement to existing Salesforce fields. Keep
these scenarios in mind when using HML fields in the enhanced email experience.
Create Enhanced Emails
Provide basic email information to create an email content record, and then build from scratch or edit existing email content. To
make email creation even easier, Account Engagement offers email templates that help you reuse email designs.
Preview and Test Emails
Before sending your email, preview it as a specific prospect, and then test send it to troubleshoot personalization issues. You can
send a test email to a test list or to individual email addresses. Test emails don’t include merge field data.
Send Emails
After you design your email content, define a campaign, an audience, tracker domain, sender options, and completion actions.
Reuse Email Content for List Emails
Edit and reuse existing email content to create and send new emails. Resend email content to different recipients and segments as
unique list email sends. You can also view related email sends for specific email content.
```
### Considerations for Using HML Fields for Emails in Lightning

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited editions
```
```
Some HML merge fields in Salesforce aren’t supported in Account Engagement. To use these field
values, map custom fields from Account Engagement to existing Salesforce fields. Keep these
scenarios in mind when using HML fields in the enhanced email experience.
Account Engagement-only custom fields aren’t available for selection in email content.
```
```
Data displayed in
the merge field
when the email
sends
```
```
Syntax is the Same
Between
Salesforce and
Account
Engagement Fields
```
```
Is the field
available for
selection in the
builder?
```
```
Field Scenario
```
```
The email displays the
field data in Account
Engagement
```
```
Salesforce and Yes Yes
Account Engagement
both have the field by
default
```
```
The email displays the
field data in Account
Engagement
```
```
Account Engagement Yes Yes
custom field is synced
to a Salesforce default
field
```
```
The email displays the
field data in Account
Engagement
```
```
Account Engagement Yes Yes
custom field is synced
```
Enhanced Email for Account Engagement Design, Test, and Send Emails


```
Data displayed in the
merge field when the email
sends
```
```
Syntax is the Same
Between Salesforce and
Account Engagement Fields
```
```
Is the field available for
selection in the builder?
```
```
Field Scenario
```
```
to a Salesforce custom field
```
```
Unable to send the email in
lightning
```
```
Field is only in Salesforce as a Yes N/A
default or custom field
```
```
The email displays the field data
in Account Engagement
```
```
Field is only in Salesforce as a Yes Yes
default or custom field but has
the same field name as an
Account Engagement field
```
### Create Enhanced Emails

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
USER PERMISSIONS
```
```
To build an email:
```
**-** Manage Email Content
    AND
    Access Drag-and-Drop
    Content Builder
To add custom components
in email templates:
**-** View Setup and
    Configuration

```
Provide basic email information to create an email content record, and then build from scratch or
edit existing email content. To make email creation even easier, Account Engagement offers email
templates that help you reuse email designs.
The email Subject and HTML Body field content is automatically copied from the template that you
select.
```
**1.** From the Email Content tab, click **New**.
**2.** Enter an email name for internal use.
**3.** To begin from an email template, select a template.
    Only email templates created from the email template builder are available for selection.
**4.** Save your work.
**5.** To add components and customize your content, click **Edit in Builder**.
    **-** To try out the new content builder, select **New email experience**. To learn more, see
       Create Content in Marketing Cloud Growth.
    **-** To continue using the standard Enhanced Email builder, select **Existing email experience**.
**6.** Drag a component from the list to the canvas where you want it to appear.
    An editing pane opens where you can add content and style fields.
**7.** After you add your content, save your work.
To work with the text-only version of your email, edit the email content record. In the Text Body
field, enter new text, or click **Sync from HTML** to use the text that you added in the builder.

Enhanced Email for Account Engagement Create Enhanced Emails


### Preview and Test Emails

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
USER PERMISSIONS
```
```
To preview an email:
```
**-** Manage Email Content
    AND
    Account Engagement
    Administrator or
    Marketing role
    OR
    Custom user role in
    Account Engagement
    that includes View on
    Prospects
To send a test email:
**-** Manage Email Content
    AND
    Account Engagement
    Administrator or
    Marketing role
    OR
    A custom user role in
    Account Engagement
    that includes Create/Edit
    and Send to List on
    Email, View on
    Campaign, and View on
    Segmentation Lists

```
Before sending your email, preview it as a specific prospect, and then test send it to troubleshoot
personalization issues. You can send a test email to a test list or to individual email addresses. Test
emails don’t include merge field data.
```
```
Note: For content created using the new email experience, see Create an Email in Marketing
Cloud to learn how to preview and test your emails. The test and preview options in the new
email experience require Data Cloud.
Data from email sends to test lists is included in Engagement History and other reports. To exclude
test list metrics, associate your test email with a test campaign.
```
**1.** Go to the email content record for the email that you want to preview or test.
**2.** From the dropdown, select **Preview As** , and then select a prospect.
**3.** From the dropdown, select **Test**.
**4.** Define the recipients.
    You can select a list from the dropdown or enter individual recipients. Use search to find
    individual recipients and then press Enter to add the email address.

```
A test email is sent.
```
**-** If the current user’s sending domain is verified, the email is sent from that user email address.
**-** If the current user’s sending domain isn’t verified, the email is sent from
    test@[yourverifieddomain].
**-** If you have more than one verified sending domain, the first one in the domain management
    table is used.
**-** If you have no verified sending domain, the email isn’t sent.

Enhanced Email for Account Engagement Preview and Test Emails


### Send Emails

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
USER PERMISSIONS
```
```
To send an email:
```
**-** Manage Email Content
    AND
    Account Engagement
    Administrator or
    Marketing role
    OR
    A custom user role in
    Account Engagement
    that includes Send to List
    on Emails, View on
    Segmentation Lists, and
    View on Campaigns

```
After you design your email content, define a campaign, an audience, tracker domain, sender
options, and completion actions.
You can send an email content record as many times as needed. Send it immediately or schedule
it for later. Account Engagement Premium and Advanced users can also choose to send with Einstein
Send Time Optimization.
```
**1.** Test your email thoroughly and verify that all text, images, and links appear and work as expected.
**2.** In the email content record’s action menu, click **Send**.
**3.** Enter the required values, such as campaign, recipient list, and sender information.
**4.** To configure completion actions, enable a trigger type and then, select the action.
**5.** Select **Send Now** or **Send Later**.
    If you select Send Later, enter a date and time for sending.
**6.** Click **Send**.

Enhanced Email for Account Engagement Send Emails


### Reuse Email Content for List Emails

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
```
```
USER PERMISSIONS
```
```
To send an email:
```
**-** Manage Email Content
    AND
    Access Drag-and-Drop
    Content Builder

```
Edit and reuse existing email content to create and send new emails. Resend email content to
different recipients and segments as unique list email sends. You can also view related email sends
for specific email content.
```
**1.** From the Email Content tab, select an email content record to resend or edit.
**2.** Edit the email information and content from the record, or click **Edit in Builder** to add
    components and customizations.
    Editing an existing email content record changes the content for that record. It doesn’t change
    previously sent emails or create a unique email content record.
**3.** Click **Send** from the record and define recipients, campaign association, and completion actions.
    Each email sent creates a new send record and relates it to the email content record.

```
You can view list emails sent from an email content record on the Related tab of the record.
```
## Guidelines for Creating Custom Report Types for Email Content

```
EDITIONS
```
```
Available in: any Account
Engagement Edition with
Salesforce Professional ,
Enterprise , Performance ,
and Unlimited Editions
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
Create custom report types that include email content and list email data. Marketers can then create
reports to analyze and better understand the performance of their email content. Review the
following guidelines and examples of reports.
To learn how to create custom report types, see Create a Custom Report Type.
```
**-** To create reports that pull data from the email content record, select Email Content as the
    primary object on the custom report type. With Email Content as the primary object, marketers
    could create a report for all engagement statistics by email content record.
**-** To get more report options for all list emails including emails sent from the email content record,
    add list email as a related object on the custom report. With Email Content and List Email as
    objects on the report, marketers could create a report that shows all email sends and related
    statistics by email content record.
**-** With List Email as the primary object, marketers could create a report with email sends and
    related statistics for a given campaign.

Enhanced Email for Account Engagement Reuse Email Content for List Emails


