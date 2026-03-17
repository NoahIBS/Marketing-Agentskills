---
name: mcae-functional-consultant
description: "Answer how-to and feature questions for Account Engagement: creating forms and custom fields, handling prospect confirmation workflows, segmenting with dynamic lists, and configuring completion actions. Use when: building forms, setting up opt-in processes, configuring prospect automation, creating segments, validating MCAE capabilities."
argument-hint: "e.g., How do I set up a confirmed opt-in process? Can MCAE do progressive profiling? How do I segment by engagement?"
---

# Account Engagement Functional Consultant

Guide for answering how-to questions and feature validation about Account Engagement setup, forms, workflows, and segmentation.

## When to Use

- Building forms and landing pages
- Creating custom prospect fields
- Setting up opt-in/confirmation workflows
- Configuring completion actions
- Creating dynamic lists and segments
- Automating prospect workflows
- Verifying MCAE features and capabilities
- Best practices for forms and segmentation

## Quick Topics

### Forms & Landing Pages

**How-to questions:**
- How do I create a form in Account Engagement?
- What fields can I add to a form?
- How do I set up progressive profiling?
- Can I embed forms on external websites?

**Key steps:**
1. Content → Forms → New Form
2. Add form fields (map to prospect fields or custom fields)
3. Configure completion actions (email, scoring, list assignment)
4. Set form permissions and visibility
5. Test and publish

**Feature highlights:**
- Progressive profiling (show different fields on repeat visits)
- Form handlers for advanced workflows
- Embeddable forms
- Conditional completion actions

### Custom Prospect Fields

**How-to questions:**
- How do I create a custom prospect field?
- Can custom fields sync to Salesforce?
- What field types are supported?

**Key steps:**
1. Account Engagement Settings → Object and Field Configuration → Prospect Fields
2. Click Add Custom Field
3. Select field type (Checkbox, Picklist, Text, Number, Date, Text Area)
4. Define values if using Picklist
5. Save and configure Salesforce sync if needed

**Common fields:**
- Confirmed Opt-In (Checkbox) — for email verification
- Lead Status (Picklist) — for funnel tracking
- Engagement Level (Picklist) — for segment based on activity
- Custom scoring buckets (Text) — for qualification

### Completion Actions

**Supported actions:**
- Send auto responder email
- Set prospect custom field
- Add to dynamic list
- Assign to user
- Add to campaign
- Score prospect
- Conditional logic available

**Example workflow:** "If prospect submits form → Send confirmation email + Add to 'New Subscribers' list + Score +25 points"

### Dynamic Lists & Segmentation

**Creating segments:**
1. Marketing → Segmentation → Lists (or Prospects → Segmentation in Lightning)
2. Click Add List → Select "Dynamic List"
3. Set Rules (Match All/Any with conditions)
4. Preview and confirm
5. Click Run Rules to activate

**Common criteria:**
- Prospect field values (Industry, Job Title, Country)
- Engagement history (Email clicked, Form submitted)
- Custom field values (Confirmed Opt-In, Score range)
- Campaign membership
- Behavioral triggers

**Example:** Segment prospects by:
- Confirmed vs. unconfirmed opt-in
- High/medium/low engagement
- Sales-ready vs. nurturing audience
- ICP match (industry + company size)

## Implementation Patterns

### Confirmed Opt-In Workflow

```
1. Prospect submits signup form
   ↓
2. Completion action: Send confirmation email + Add to "Not Confirmed" list
   ↓
3. Form handler with custom field update
   ↓
4. Prospect clicks confirmation link
   ↓
5. Form handler: Set Confirmed Opt-In = True + Move to "Confirmed" list
   ↓
6. Use "Confirmed Opt-In" list for marketing campaigns
```

### Lead Nurturing by Engagement

```
1. Track engagement (email opens, clicks, form submissions)
   ↓
2. Dynamic lists segment by engagement level
   ↓
3. Score based on behavior
   ↓
4. Route sales-ready leads (high score) to assignment
   ↓
5. Nurture medium/low with targeted content
```

## Feature Validation Examples

**Can MCAE...?**

✅ **Progressive profiling** — Show different form fields based on existing information  
✅ **Email verification** — Confirmed opt-in with form handlers and custom fields  
✅ **Lead scoring** — Automatic points for engagement, threshold-based routing  
✅ **Dynamic segmentation** — Auto-populate lists based on behavior/fields  
✅ **Conditional automation** — Different actions based on prospect data  
✅ **Form pre-fill** — URL parameters populate prospect known fields  
✅ **Unsub management** — Dynamic lists to exclude opted-out prospects  

❌ **A/B testing (forms)** — Not natively; track variants manually  
❌ **Complex conditional logic (in forms)** — Limited; use workflows instead  

## References

- [Completion Actions Guide](./references/completion-actions-guide.md)
- [Segmentation & Dynamic Lists](./references/segmentation-guide.md)
- [Forms & Custom Fields](./references/forms-fields-guide.md)

## Prerequisites

Before implementing workflows:
- Verified Salesforce Connector
- Assigned MCAE admin permissions
- Defined custom fields if needed
- Planned field sync strategy
- Identified key prospect attributes

## Best Practices

1. **Forms:** Keep short (3-5 fields), use progressive profiling
2. **Custom Fields:** Name clearly, document purpose, sync selectively
3. **Completion Actions:** Keep logic simple, order matters
4. **Segmentation:** Use AND for precision, OR for breadth
5. **Testing:** Always test workflows in sandbox first
6. **Documentation:** Document custom fields and automation rules
7. **Maintenance:** Review segments quarterly, archive unused lists

## Tips

- Use checkboxes for status tracking (syncs better)
- Picklists are more reportable than text fields
- Run list rules after adding criteria to see impact
- Test form handlers with real submissions before going live
- Combine multiple completion actions for complex workflows
- Document why each dynamic list exists (for team alignment)
