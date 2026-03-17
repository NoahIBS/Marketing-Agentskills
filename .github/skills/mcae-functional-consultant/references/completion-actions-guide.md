# Completion Actions in Account Engagement

## Overview
Completion actions define what happens when a prospect completes a specific asset (form, landing page, email link, etc.). They enable automated actions based on prospect behavior.

## Common Completion Actions

### Send Auto Responder Email
Automatically send an email to the prospect upon completion.
- **Use case:** Welcome emails, confirmations, lead nurturing
- **Configuration:** Select email template, set frequency options
- **Example:** Send confirmation email when prospect submits signup form

### Set Prospect Custom Field
Update custom prospect fields when completion occurs.
- **Use case:** Mark confirmed opt-in status, track milestone completion, scoring
- **Configuration:** Select custom field and set value
- **Example:** Update "Confirmed Opt-In" field to True when prospect clicks confirmation link

### Add to Dynamic List
Automatically add prospect to a list.
- **Use case:** Segmentation, audience building
- **Configuration:** Select dynamic or static list
- **Example:** Add to "Confirmed Subscribers" list

### Assign to User
Route the prospect to a specific sales user.
- **Use case:** Lead assignment, territory management
- **Configuration:** Choose assignment method (rule-based, user, round-robin)
- **Example:** Assign to territory owner based on territory code

### Add to Campaign
Add prospect to a Salesforce campaign.
- **Use case:** Campaign tracking, reporting
- **Configuration:** Select Salesforce campaign

### Score Prospect
Add points to prospect score.
- **Use case:** Lead scoring, qualification tracking
- **Configuration:** Enter point value
- **Example:** Add 10 points for email open, 25 for form submission

## Conditional Completion Actions

Some completion actions can be conditional based on:
- Prospect field values
- Form submission data
- Engagement history

**Example:** "If prospect industry = Technology, assign to Tech territory manager"

## Best Practices

1. **Clear Logic:** Each completion action should have a clear purpose
2. **Sequential Order:** Order matters—earlier actions execute first
3. **Testing:** Test completion actions in sandbox before production
4. **Documentation:** Document custom fields and logic for team reference
5. **Performance:** Avoid excessive completion actions on high-volume forms
