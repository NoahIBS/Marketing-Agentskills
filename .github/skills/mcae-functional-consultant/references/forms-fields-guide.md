# Forms and Custom Fields in Account Engagement

## Forms Overview

Account Engagement forms are used to capture prospect information and trigger automations.

### Form Types

**Account Engagement Forms**
- Built within MCAE
- Embeddable on external websites
- Can trigger completion actions
- Support form handlers for advanced use cases

**Form Handlers**
- Custom endpoints for capturing data
- More flexibility than standard forms
- Used for advanced workflows (like confirmed opt-in)
- Accept data from external sources

### Form Configuration

1. **Form Fields:** Map to prospect fields
   - Standard fields (Email, First Name, Last Name, Company)
   - Custom prospect fields
   
2. **Progressive Profiling:** Show different fields based on history
   - Reduces friction on repeat visits
   - Builds profile over time

3. **Completion Actions:** Define what happens when form is submitted
   - Send email
   - Add to list
   - Update custom fields
   - Assign to user
   - Score prospect

4. **Form Permissions:** Control visibility and access

## Custom Prospect Fields

### Creating Custom Fields

**In Account Engagement (Classic):**
- Admin → Configure Fields → Prospect Fields → Add Custom Field

**In Lightning App:**
- Account Engagement Settings → Object and Field Configuration → Prospect Fields

### Field Types

- **Text:** Short text values
- **Text Area:** Longer text content
- **Checkbox:** True/False values (common for status tracking)
- **Picklist:** Dropdown selection
- **Number:** Numeric values
- **Date:** Date selection

### Sync with Salesforce

Custom fields can sync to Salesforce as:
- Custom Lead Fields mapping to Contact Fields
- Custom Account fields
- Linked to automation rules

**Important:** Field sync must be configured in Salesforce Connector settings.

## Common Custom Field Use Cases

1. **Confirmed Opt-In** (Checkbox)
   - Tracks email confirmation status
   - Used in dynamic lists
   - Triggers completion actions

2. **Lead Status** (Picklist)
   - Tracks progression in funnel
   - Supports conditional routing
   - Enables score-based automation

3. **Engagement Level** (Picklist)
   - High/Medium/Low based on activity
   - Drives segmentation
   - Informs nurturing strategy

4. **Lead Score Bucket** (Text/Number)
   - Qualitative score categories
   - Used for reporting

## Forms Best Practices

- Keep forms short (fewer fields = higher conversion)
- Use progressive profiling for repeat visitors
- Test form behavior before Publishing
- Monitor form completion rates
- Use completion actions to drive engagement immediately
- Align form fields with sales team needs

## Custom Field Best Practices

- Name fields clearly and consistently
- Document field purpose and values
- Sync only what's needed to Salesforce
- Use picklists for categorization (more reportable)
- Test field mapping before going live
