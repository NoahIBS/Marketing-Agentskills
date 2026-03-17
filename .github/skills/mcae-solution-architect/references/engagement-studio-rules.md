# Engagement Studio Rules for Score-Based Qualification

## Rule Steps Overview

**Rule Steps** in Engagement Studio pause the prospect journey and evaluate conditions. Unlike trigger steps (which wait for prospect action), rule steps execute immediately based on *current prospect properties*.

## Using Score in Rule Steps

### Rule Definition: "Prospect's Score"

The Rule definitions available in Engagement Studio include **"Prospect's Score"** as a path-determination criterion.

**Syntax**:
```
IF Prospect's Score [condition] [value]
THEN [path: yes/no/default]
```

**Conditions** (depends on rule type):
- Equals
- Greater than (>)
- Less than (<)
- Between (range)
- Is null

### Example: Score-Based Nurture Path

```
Step: Rule - Qualification Check
  Condition: Prospect's Score > 50
  
  If YES:
    → Send Email: Nurture Series #1
    → Wait 3 days
    → Rule: Score > 75?
      If YES: Assign to Sales
      If NO: Send Email: Nurture Series #2
  
  If NO:
    → Send Email: Awareness Content
    → Wait 7 days
```

## Score-Based Rule Steps in Practice

### Step 1: Initial Nurture Gate
```
Recipient Lists: All form submissions (whitepaper download, webinar signup)
↓
Step 1: Action - Adjust Score
  → +10 points (set all prospects to baseline 10 for engagement)
↓
Step 2: Rule - First Nurture Threshold
  IF Prospect Score ≥ 10
    Yes → Send Email: Welcome Series #1
    No → Skip (should not occur)
↓
Step 3: Trigger - Email Open
  IF prospect opens Welcome Email
    Yes → Wait 1 day → Rule: Score Check
    No (Max Wait) → 14 days → Rule: Score Check
```

### Step 2: Mid-Funnel Engagement
```
Step N: Rule - Marketing Qualified Threshold
  IF Prospect Score ≥ 85
    Yes → Send Email: Sales-Enabled Content
         → Wait 3 days
         → Assign to Group: Sales Development Team
    No → Send Email: Additional Nurture
       → Wait 7 days
```

### Step 3: Sales Handoff
```
Step N+1: Rule - Sales Qualified Threshold
  IF Prospect Score ≥ 100
    Yes → Assign to User: [Sales User]
         → Add to Salesforce Campaign: Active Pipeline
         → Notify User: New sales-qualified prospect
    No → Continue Engagement Program
```

## Combining Score with Other Criteria

Rule steps can combine multiple conditions (up to 5). Example:

```
IF Prospect Score ≥ 85
  AND
   Prospect Grade = A
  THEN
   Assign to Sales (Priority)

IF Prospect Score ≥ 75
  AND
   Prospect Grade = B
  THEN
   Assign to Sales (Standard)

IF Prospect Score < 75
  OR
   Prospect Grade = C or D
  THEN
   Continue Nurturing
```

## Common Engagement Studio Actions with Score

Once a score threshold is met, pair rule steps with these actions:

| Action | Use Case | Example |
|---|---|---|
| **Adjust Score** | Celebrate engagement milestone | +15 points for form submission |
| **Assign to User** | Route sales-qualified prospects | Send to available sales rep |
| **Assign to Group** | Route to department | Send to Sales Development Team |
| **Add to Salesforce Campaign** | Track pipeline contribution | Add to "SQLs - Active" campaign |
| **Send Email** | Deliver role-specific content | Sales VP email vs. buyer email |
| **Notify User** | Alert sales team | Slack/email alert when Score ≥ 100 |
| **Add to List** | Segment for future programs | Add to "Hot Prospects" list |

## Wait Periods with Rule Steps

Rule steps evaluate **immediately** when a prospect arrives. However, you can build wait periods *after* the rule:

```
Rule Step: Score ≥ 85?
├─ Yes → [Send Email] → Wait 2 days → [Next Step]
└─ No → [Send Email] → Wait 5 days → [Next Step]
```

## Testing Rule Logic

Before activating your program, test rule logic in the **Test** tab of Engagement Studio:

1. Click **Test** tab in program
2. Navigate through steps manually
3. The test shows you which path each rule evaluates (Yes/No)
4. Adjust rule conditions if needed
5. Click **Start** when logic is confirmed

## Performance Tips

- **Limit conditions**: 5 conditions max per rule step (platform limit)
- **Order rules efficiently**: Put most-common threshold first
- **Avoid rule spam**: Don't check the same score twice in a row with different values
- **Use triggers for changes**: If you need to react immediately to engagement, use trigger steps; rules are for state-based evaluation
