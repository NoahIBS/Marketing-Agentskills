# Implementation Guide:

# Enhanced Landing Page

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

- Enhanced Landing Page Experience
- Considerations for the Enhanced Landing Page Experience
- Enhanced Landing Page Experience Permissions
- Set Up the Enhanced Landing Page Experience
- Configure Salesforce CMS for Landing Pages
- Create an Enhanced Landing Page
   - Enhanced Landing Page Record Fields
   - Style Account Engagement Forms on Enhanced Landing Pages
   - Using Form Styles with Enhanced Landing Pages
   - Use Custom Code with Enhanced Landing Pages
- Publish an Enhanced Landing Page



## Enhanced Landing Page Experience

```
EDITIONS
```
```
Available in: All Account
Engagement Editions
```
As of Winter ’22, Account Engagement Lightning App users can choose which experience to use
when creating landing pages. The enhanced landing page experience uses a drag-and-drop editor
and can be accessed from Account Engagement Lightning App only. It’s built on Salesforce, and
supports list views, actions, reporting, and other functionality that comes with Salesforce Lightning
Experience.

Looking for a PDF of this content? Check out the Enhanced Landing Page Experience Implementation
Guide (PDF).

To use the enhanced landing page experience, click the **Landing Pages** tab. Create or open a landing page record, and click **Edit in
Builder**. Landing pages created in the enhanced experience are called enhanced landing pages.

```
Note: Classic landing pages are still available.
```
```
Considerations for the Enhanced Landing Page Experience
Keep these considerations in mind before you work with the enhanced landing page experience.
Enhanced Landing Page Experience Permissions
Various permissions are necessary to set up, create, and publish landing pages in the enhanced landing page experience.
Set Up the Enhanced Landing Page Experience
The enhanced landing page experience is automatically enabled at the same time as the enhanced email experience. If you’ve
already set up one of these features in Account Engagement, no other setup is needed.
```

```
Configure Salesforce CMS for Landing Pages
When you create landing pages with Account Engagement, you can use Salesforce CMS as a unified image repository. The CMS
workspace is where you can save files and control user access. The CMS channel determines where those files can be published.
Images published to your channel become available while marketers are building landing pages.
Create an Enhanced Landing Page
When you create an enhanced landing page, you associate it with a campaign and then edit the content. Drag in templates from
the Layout section to quickly insert rows and columns. Then you can add these component types: Image, Pardot Form, Rich Text,
Button, and HTML.
Publish an Enhanced Landing Page
When you finish designing an enhanced landing page, you can publish it to the web. Before publishing, add settings such as vanity
URL, unpublish redirect URL, and search engine indexing on the landing page record.
```
## Considerations for the Enhanced Landing Page Experience

```
EDITIONS
```
```
Available in: All Account
Engagement Editions
```
```
Keep these considerations in mind before you work with the enhanced landing page experience.
```
### Setting Up Enhanced Landing Pages

**-** The enhanced landing page builder uses the same permissions and Digital Experiences
    integration as enhanced email. If the enhanced email experience is configured, your users can
    typically get started with landing pages right away.
**-** Updates to landing page record layouts typically appear automatically. But if the Lightning record page or page layout for the landing
    page is customized, an admin must manually add new fields and tabs.

### Creating Records

**-** When you create an enhanced landing page, it must be associated with a connected campaign.
**-** The landing page’s campaign must be associated with one business unit. The business unit assignment is required to publish the
    landing page. If you don’t have multiple business units, only Connected Campaigns settings define the relationship.
    A connected campaign and a business unit have a one-to-one relationship that’s controlled in your connector settings. To assign a
    business unit, configure the record type settings and trigger a sync.
**-** If you can’t find a field or tab on the landing page object, such as the Unpublish Redirect URL field, ask your admin to check for recent
    release updates. Some components must be added manually.

### Building Content

**-** You can use Salesforce CMS in the Digital Experiences app as an image repository. You can also include absolute URL links to public
    images hosted by a third party. Salesforce Files aren’t supported.
**-** When you design landing page content, it’s stored in an HTML field. The HTML field must not exceed 384 KB.
**-** Active content, such as JavaScript or SVG files, isn’t supported in enhanced landing pages.
**-** Landing pages are mobile-responsive. On screens smaller than 480 px wide, a landing page’s default width is 320 px.

Enhanced Landing Page Experience Considerations for the Enhanced Landing Page Experience


### Using Iframes

**-** The HTML component supports Iirames. A placeholder for the iframe content appears on the builder canvas and record home.
    Iframed content is rendered only on the published landing page.
**-** To make sure that your iframe is responsive when you publish your landing page, review the embed code.
    **-** If your embed code is already responsive: Verify that the iframe tag includes a style attribute or a width attribute as a percentage.
       The builder doesn’t change the embed code.
    **-** If your embed code isn’t responsive: Verify that the iframe tag includes the width and height attributes as pixels and doesn’t
       include a style attribute. The builder changes the embed code when it’s rendered, which make the iframe responsive.

### Publishing a Landing Page

**-** You must publish a landing page to make it available online. When you edit a published landing page, the status updates to Published
    (With Changes), and must be published again before the edits appear online.
**-** The public link on a landing page record shows your primary tracker domain. If you enter a vanity URL, the path works with any of
    your custom tracker domains.
**-** You can use a vanity URL on one landing page at a time. If you delete a landing page record that’s using a vanity URL, you can’t use
    that vanity URL again on another record. To reuse a vanity URL, clear it from a landing page record and publish the change. Then,
    you can add the vanity URL to a new record. If you no longer need the original landing page record, you can delete it.
**-** When you publish an enhanced landing page, a related record is created in Account Engagement. This record tracks engagement
    activities and stores metrics, which are synced back to the main landing page record in Salesforce.
**-** When you unpublish an enhanced landing page in Salesforce, the related record is archived in Account Engagement. If you republish
    the landing page, we unarchive the related record to retain previous metrics.

### Allocations

**-** Most Account Engagement editions support up to 1,000 enhanced landing pages at one time. Published and unpublished enhanced
    landing pages count toward this number. Classic landing pages are unlimited.
**-** Account Engagement Growth Edition supports 50 landing pages, counting any classic landing pages and published, enhanced
    landing pages.

## Enhanced Landing Page Experience Permissions

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
```
Various permissions are necessary to set up, create, and publish landing pages in the enhanced
landing page experience.
```
### Permission Sets and User Roles

```
The ability to view the Landing Page object is included in the Account Engagement User, Sales
Cloud User, Service Cloud User, and CRM User permission sets.
An admin can create the Create Account Engagement Content permission set on the Content Setup
page of Marketing Setup. The permission set includes access to the drag-and-drop builders for email and landing pages and to Salesforce
CMS via the Digital Experiences app. Users can also manage email content records and activate email content for use in Engagement
Studio.
```
Enhanced Landing Page Experience Enhanced Landing Page Experience Permissions


```
To publish or unpublish a landing page, users must also have a Marketing user role in Account Engagement, or the individual permissions
indicated in the table.
```
### Individual Permissions

```
Permission Name Location Type Description Configuration
Provides access to the On
enhanced email and
```
```
Access Drag and Drop Salesforce Setup System Permissions
Content Builder
landing page builders in
Account Engagement
Lightning App
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
Provides access to View, Create, Delete
Account Engagement
landing page records
```
```
Account Engagement Marketing tab
Settings, User Roles
```
```
Landing Pages
```
```
Provides access to View
Account Engagement
campaigns
```
```
Account Engagement Marketing tab
Settings, User Roles
```
```
Campaigns
```
```
Provides access to View
Account Engagement
forms
```
```
Account Engagement Marketing tab
Settings, User Roles
```
```
Forms
```
Enhanced Landing Page Experience Enhanced Landing Page Experience Permissions


## Set Up the Enhanced Landing Page Experience

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
To assign permissions:
```
**-** Assign Permission Sets
    and
    View Setup and
    Configuration

```
To configure CMS in the
Digital Experiences app:
```
**-** Salesforce admin role
    OR
    Create CMS Channels
    and Workspaces system
    permission

```
The enhanced landing page experience is automatically enabled at the same time as the enhanced
email experience. If you’ve already set up one of these features in Account Engagement, no other
setup is needed.
```
**1.** From Marketing Setup, in the Quick Find box, enter _Content_ , and then select **Content Setup**.
**2.** Review the prerequisites, and complete any that are missing.
**3.** To create the permission set that allows users access to the email and landing page experiences,
    click **Create Permission Set** , review the details, and save.
    If the Create button is inactive, the permission set has already been created. Skip to the next
    step.
**4.** To open the permission set, click **Manage Assignments**.
**5.** From the Create Account Engagement Content permission set page, click **Manage**
    **Assignments**.
**6.** Select the users who need the permissions, and click **Assign**.
**7.** Back in Marketing Setup, follow the steps to create a CMS workspace and channel.
    The selected channel is used in the drag-and-drop builders for enhanced email and landing
    pages.
**8.** Encourage users to add the Landing Pages tab to their Account Engagement Lightning App
    toolbar.
Users with the Create Account Engagement Content permission set can now create and edit landing pages. To publish a landing page,
a user must have an admin or marketing user role.

## Configure Salesforce CMS for Landing Pages

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
```
USER PERMISSIONS
```
```
To configure Salesforce
CMS:
```
**-** Modify All Data
    OR
    Create CMS Workspaces
    and Channels

```
When you create landing pages with Account Engagement, you can use Salesforce CMS as a unified
image repository. The CMS workspace is where you can save files and control user access. The CMS
channel determines where those files can be published. Images published to your channel become
available while marketers are building landing pages.
CMS contributors must have the Salesforce user license. Salesforce CMS can be used with the
enhanced email and landing page experiences in Account Engagement.
```
**1.** Click the CMS Home action menu, select **CMS Channel** , and then click **Create Channel**.
**2.** Name the channel something descriptive, such as Marketing Content or a business unit name,
    and then save it. You can edit the channel name at any time.
**3.** Edit the new channel to configure its domain.
    **a.** From the channel list, click the action menu, and then select **Edit**.
    **b.** Select **Enable Domain** , choose the domain you configured from the dropdown, and then
       save.
**4.** Click the CMS Home action menu, select CMS Workspace, and then click **Add Workspace**.
**5.** To configure your workspace, follow the prompts.

Enhanced Landing Page Experience Set Up the Enhanced Landing Page Experience


```
a. Name the workspace and select the channel you want to include.
b. Select the Salesforce users that need access to the workspace, and then select a role for each.
A content manager has full access to a workspace’s files. A content admin can also edit the workspace settings.
```
```
c. Select the languages you want to support and include a default language.
d. Review your settings, and then click Done.
```
**6.** From the Content Setup page, click **Select Channel** , choose the one you created from the dropdown, and save.

## Create an Enhanced Landing Page

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
To edit an enhanced landing
page:
```
**-** Access Drag-And-Drop
    Builder
To add images from
Salesforce CMS:
**-** Digital Experiences app
    assignment

```
When you create an enhanced landing page, you associate it with a campaign and then edit the
content. Drag in templates from the Layout section to quickly insert rows and columns. Then you
can add these component types: Image, Pardot Form, Rich Text, Button, and HTML.
```
```
Note: Pardot is now known as Marketing Cloud Account Engagement. We wish we could
snap our fingers to update the name everywhere, but you can expect to see the previous
name in a few places until we replace it, including in the app itself.
```
**1.** In Account Engagement Lightning App, open the Landing Pages tab and then click **New**.
    If you don’t see this tab, check the More tab or edit your toolbar to include it.
**2.** Enter a name and campaign, and then save.
**3.** To make the landing page available at a URL that you choose, enter a vanity URL.
**4.** To redirect viewers if the landing page is ever removed, enter a secure, absolute URL in the
    Unpublished Redirect URL field.
**5.** To add content to the landing page, click **Edit in Builder**.
**6.** Add or drag in a prebuilt layout from the Layouts list.
**7.** Click an item in the Components list and drag it into the canvas.
**8.** Use the editing pane to customize the content and style of each component.
**9.** Save your work.
The landing page now appears on the Landing Pages list view in Draft status. To publish your changes, return to the record view and
click **Publish**.

```
Enhanced Landing Page Record Fields
Enhanced landing pages in Account Engagement include a variety of fields that contain content, redirect instructions, and other
helpful information. Sections include Information, Engagement Metrics, Publication Information, System Information, and Content
and Settings tabs.
Style Account Engagement Forms on Enhanced Landing Pages
You can adjust the colors, fonts, and other styles of an Account Engagement form in the editing panel of the enhanced landing page
builder. The styles that you add here apply to the landing page only and don’t overwrite the form record’s original styles.
Using Form Styles with Enhanced Landing Pages
You can customize styles on the form component in enhanced landing pages. Make sure that you’re familiar with the relationship
between Account Engagement form records and enhanced landing pages before you get started.
```
Enhanced Landing Page Experience Create an Enhanced Landing Page


```
Use Custom Code with Enhanced Landing Pages
To further customize landing pages, you can add custom code, including script, style, comment, noscript, and link tags to the header
and footer code. You can also copy, edit, or remove code at any time. The header and footer code blocks are available on the Settings
tab of an enhanced landing page record.
```
### Enhanced Landing Page Record Fields

```
EDITIONS
```
```
Available in: All Account
Engagement Editions
```
```
Enhanced landing pages in Account Engagement include a variety of fields that contain content,
redirect instructions, and other helpful information. Sections include Information, Engagement
Metrics, Publication Information, System Information, and Content and Settings tabs.
```
```
Note: If you don’t see these fields, your landing page records require customization. An
admin can add the Content and Settings tabs in the Lightning App Builder.
```
Information

**-** Landing Page Name—The descriptive name of the landing page. This value isn’t visible to landing page visitors.
**-** Campaign—The name of the campaign associated with the landing page.
**-** Content—The HTML of your landing page. The content HTML file is stored behind the scenes, but you can access a preview of the
    landing page on the Content tab.
**-** Status—The status of the landing page. Available values are Draft, Published, and Published (with changes). Default value is Draft.
**-** Public Link—The public URL where the landing page is available based on your primary tracker domain. This field is blank until you
    publish the landing page for the first time. The URL is removed when the landing page is unpublished.
**-** Content Last Saved—The timestamp for the most recent update to the landing page. Changes to these fields trigger the timestamp
    to be updated: Landing Page Name, Campaign, Content, Header Code, Footer Code, Vanity URL, Search Engine Indexing, and
    Unpublish Redirect URL.
**-** Content Last Saved By—The name of the person who most recently updated the landing page. Changes to these fields trigger the
    timestamp to be updated: Landing Page Name, Campaign, Content, Header Code, Footer Code, Vanity URL, Search Engine Indexing,
    and Unpublish Redirect URL.
**-** Last Published—The timestamp for the most recent publication of the landing page.
**-** Last Published By—The username of the person who most recently published the landing page.
**-** Hide from Search Engine Indexing—Indicates whether the landing page is available for public search. By default, landing pages are
    searchable, so the box is deselected.
**-** Vanity URL—The path portion of your preferred landing page URL to be appended to your tracker domains. The Vanity URL field
    doesn’t support a full URL.
**-** Unpublish Redirect URL—The URL used when the landing page is unpublished. By default, an unpublished landing page redirects
    to the website in Account Engagement Settings. To redirect viewers to another site, enter a complete URL that starts with https://.

System Information

**-** Created By—The username of the person who created the landing page record.
**-** Last Modified By—The username of the person who most recently edited any part of the landing page record.
**-** Source—Indicates either a classic landing page or an enhanced landing page. Classic landing pages are labeled Account Engagement.
    Enhanced landing pages are labeled Salesforce.

Enhanced Landing Page Experience Enhanced Landing Page Record Fields


Settings Tab

**-** Header Code—A field for more styles, links, and scripts. This field appears in the Settings tab.
**-** Footer Code—A field for more styles, links, and scripts. This field appears in the Settings tab.

### Style Account Engagement Forms on Enhanced Landing Pages

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
To edit a builder landing
page:
```
**-** Access Drag-And-Drop
    Builder

```
You can adjust the colors, fonts, and other styles of an Account Engagement form in the editing
panel of the enhanced landing page builder. The styles that you add here apply to the landing page
only and don’t overwrite the form record’s original styles.
Form styles can be applied to the background, field labels, inputs, checkboxes, radio buttons, and
the submit button. Editable styles vary based on the element type. Styles apply to the form
component and not the selected form itself. For example, if you add Form A and apply styles, and
then replace it with Form B, the styles that you added still appear in the component.
To reset the styles, remove the form component, and then add it again.
```
```
Note: When you open a landing page with form that was added before Spring ’22, the
original styles don’t change unless you apply additional styles in the Style tab.
```
**1.** Open a landing page and click **Edit in Builder**.
**2.** Add a form.
**3.** On the form’s editing pane, click **Style**.
**4.** Expand a section to customize the available style settings.
**5.** When you’re finished, save the page.
**6.** To publish changes, go back to the landing page record and click **Publish**.

### Using Form Styles with Enhanced Landing Pages

```
EDITIONS
```
```
Available in: All Account
Engagement Editions
```
```
You can customize styles on the form component in enhanced landing pages. Make sure that you’re
familiar with the relationship between Account Engagement form records and enhanced landing
pages before you get started.
The most important thing to know is that styles applied on the Account Engagement form record
are used everywhere that form appears, even if you edit the styles in the enhanced landing page
builder. There are a few ways to apply styles to a form.
```
**-** Use the form styles on the Look and Feel section.
**-** Apply custom code in the Above Form section.
**-** Use the Style tab on a form component in the enhanced landing page builder.
To allow users to edit a form’s styles in the enhanced landing page builder, verify that the form record’s Styles tab shows Default for
every item (1). Click **Clear** to revert to the default font color (2).

```
Style Account Engagement Forms on Enhanced Landing
Pages
```
Enhanced Landing Page Experience


```
To retain original styles on branded forms on enhanced landing pages, protect the form against certain style changes by modifying your
custom styles on the Account Engagement form record.
```
```
Note: If you try to edit styles in a form component and the changes don’t take effect, check for existing styles. Open the form
record’s Look and Feel section and the Above Form source code to identify if any styles are overriding your changes.
```
```
Form Style Properties
Many properties are available on the Form component’s Styles tab.
Background
The background color controls the color of the page or container behind your landing page content.
Form Position
Form position controls the form’s margins within its container.
Labels
Label styles control the label’s position and font details for each of your form’s inputs.
Inputs
Input properties apply to text fields, text areas, and dropdowns.
The properties Background Color, Border Color, and Border Width also apply to checkboxes and radio buttons.
Dropdown Icon Color controls the down arrow icon inside the dropdown field.
Focus styles are applied when someone moves to a form field, frequently with a mouse click or the Tab key. Focus and Error styles
don’t appear on the canvas but are visible on the published landing page.
Checkboxes and Radio Buttons
These styles apply to checkboxes and radio buttons only.
Alignment options indicate whether boxes or buttons appear horizontally or vertically.
The Selected State Color controls a checkbox or radio button when someone selects it. This color is used on the button’s border and
the icon inside it: the checkmark for checkboxes and the circle for radio buttons.
Buttons
Buttons properties apply to the form’s submit button only.
Corner Radius controls how rounded the corners of your button are.
```
Enhanced Landing Page Experience Using Form Styles with Enhanced Landing Pages


### Use Custom Code with Enhanced Landing Pages

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
To edit an enhanced landing
page:
```
**-** Access Drag-And-Drop
    Builder
To customize a Lightning
record page:
**-** Customize Application

```
To further customize landing pages, you can add custom code, including script, style, comment,
noscript, and link tags to the header and footer code. You can also copy, edit, or remove code at
any time. The header and footer code blocks are available on the Settings tab of an enhanced
landing page record.
```
**1.** From an enhanced landing page, navigate to the Settings tab.
**2.** For the Header Code or Footer Code block, click **Add**.
    To change existing code in these blocks, click **Edit**.
**3.** Enter the code that you want to include, and then save.
    Header and Footer code blocks support script, style, link, noscript, and comment tags such as
       <!-–hiddentext-->.
**4.** Review and resolve any errors.
**5.** To publish the landing page, click **Publish**.

```
Note: If you can’t find the Settings tab, an admin can add the Header Code and Footer Code
fields using the Lightning App Builder. To add the fields, open a Landing Page Lightning
record page, create a tab and name it Settings. Then, drag in the Landing Pages - Header &
Footer component. Save the page and activate it for users.
```
Enhanced Landing Page Experience Use Custom Code with Enhanced Landing Pages


## Publish an Enhanced Landing Page

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
To edit a builder landing
page record:
```
**-** Access Drag-And-Drop
    Builder
To publish a landing page:
**-** Account Engagement
    Administrator or
    Marketing role
    OR
    A custom user role that
    includes View and
    Create/Edit on Landing
    Pages
To unpublish a landing
page:
**-** Account Engagement
    Administrator or
    Marketing role
    OR
    A custom user role that
    includes View and
    Delete on Landing Pages

```
When you finish designing an enhanced landing page, you can publish it to the web. Before
publishing, add settings such as vanity URL, unpublish redirect URL, and search engine indexing
on the landing page record.
When you create or edit an enhanced landing page, the content and settings are saved but not
published. Some of the fields are validated when you click Publish. To finalize your landing page
or make changes available online, you must publish or republish the landing page.
```
**1.** In Account Engagement Lightning App, open a builder landing page record.
**2.** Preview the landing page on the Content tab.
**3.** In the toolbar, click **Publish**.
**4.** On the Publish window, click **Publish**.
    Review and resolve any validation errors.

```
After you publish a landing page for the first time, the Public Link field is populated and the Status
is updated to Published. To view your page online, paste the public link into your browser.
Engagement History metrics for landing pages include builder landing page metrics. You can use
the Source field to filter statistics.
```
Enhanced Landing Page Experience Publish an Enhanced Landing Page


