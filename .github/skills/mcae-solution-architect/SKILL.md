---
name: mcae-solution-architect
description: 'Map user stories to complete MCAE implementations using score-based lead qualification. Use when: designing prospect nurture workflows, building score-based handoff rules, or implementing ABM programs. Covers forms → scoring → engagement studio rules → automation flows → CRM sync.'
---

# MCAE Solution Architect: Score-Based Lead Qualification

## What This Skill Does

Guides you from a **user story** (marketing objective) to a **complete technical implementation** in Account Engagement, using the **score-based lead qualification model**.

Instead of traditional "lead stages" (Lead → Contact → Opportunity), MCAE qualifies prospects by numeric score thresholds. This skill teaches you to:

1. **Design scoring strategy**: Define what actions/attributes earn points
2. **Build Engagement Studio programs**: Create branching logic based on score
3. **Layer Salesforce Flows**: Add automation that wouldn't fit in Engagement Studio
4. **Sync to CRM**: Hand off sales-qualified prospects to Salesforce
5. **Measure effectiveness**: Track conversion rates between score thresholds

## When to Use

- **User Story Input**: "As a Marketing Manager, I want to nurture leads after webinar attendance and automatically assign sales-qualified leads to the sales team."
- **Design Input**: "We have a 4-email drip campaign; how do we route hot leads mid-campaign?"
- **Compliance Input**: "We need to segment by industry and send different emails based on engagement level."
- **ABM Input**: "We're tracking 10 target accounts; how do we score by account momentum?"

## Core Concepts (Read First)

Before building, understand MCAE's scoring model:
- [Score-Based Qualification Guide](./references/score-qualification-guide.md) — How scoring works, qualification tiers, score vs. grade

## Step-by-Step Implementation

### Step 1: Define Scoring Strategy

**Objective**: Decide what actions add/subtract points, and at which score threshold prospects are "ready" for sales.

**Questions to Answer**:
1. What is the **starting score**? (0 = blank slate, or 10 = baseline for subscribing to list?)
2. What engagement activities earn points?
   - Email open: +5 or +10?
   - Form submission: +20 or +25?
   - Whitepaper download: +15?
   - Meeting request: +50?
3. Are there automatic score triggers?
   - Salesforce opportunity created: +50
   - Opportunity lost: -100
4. What is the **MQL threshold**? (e.g., Score ≥ 75 = marketing qualified)
5. What is the **SQL threshold**? (e.g., Score ≥ 100 = sales qualified)
6. Do you combine score with **Grade** (A/B/C/D for fit)?
   - Example: Score ≥ 85 AND Grade = A → high priority
   - Example: Score ≥ 75 AND Grade = B → standard priority

**Output**: A "Scoring Model" document defining all point values and thresholds.

### Step 2: Create Forms with Completion Actions

Set up landing page forms that trigger initial scoring:

**Reference**: [MCAE Functional Consultant Skill](../mcae-functional-consultant/) — "Creating Forms and Completion Actions"

**Key Step**:
- Form → Completion Action: "Adjust Score +10" (or custom amount)
- This immediately adds points when prospect fills out form

### Step 3: Design Engagement Studio Program with Score-Based Rules

Build the nurture workflow using **Rule Steps** (not just triggers):

**Reference**: [Engagement Studio Rules Guide](./references/engagement-studio-rules.md)

**Structure**:
```
Program Start: [Recipient List: Form submitters]
  ↓
Step 1: Action - Adjust Score (+5)
  → Reward for list membership
  ↓
Step 2: Send Email "Welcome"
  → Wait 2 days
  ↓
Step 3: Trigger - Email Open?
  → If YES: +10 points
  → If NO (max 14 days): Continue
  ↓
Step 4: Rule - Mid-Level Check
  IF Score ≥ 50:
    → Send "Next-Level Content"
  ELSE:
    → Send "Beginner Content"
  ↓
[Continue branching based on score thresholds]
  ↓
Step N: Rule - Handoff Gate
  IF Score ≥ 100 AND Job_Title != "Intern":
    → Assign to Sales User
    → Send "Sales Team Intro" Email
    → Add to Salesforce Campaign
  ↓
Program End
```

**Test**: Use the **Test** tab in Engagement Studio to walk through the program and verify rules execute correctly.

### Step 4: Add Salesforce Flows (If Needed)

For actions Engagement Studio can't handle, use Salesforce Flows:

**Reference**: [Automation Flows Guide](./references/automation-flows-guide.md)

**When to use Flows**:
- Auto-create Salesforce Lead when prospect score ≥ 100
- Sync prospect data to Salesforce in real-time (not just at end of program)
- Call external APIs or webhooks based on score changes
- Bulk operations (e.g., reset scores monthly for inactive prospects)

**Example Flow**:
```
Trigger: Prospect updated, Score ≥ 100
Actions:
  1. Get existing Salesforce Lead (by email)
  2. If NOT found: Create Lead with prospect details
  3. Update prospect: SalesforceLeadId = [new Lead]
  4. Notify Sales Manager
```

### Step 5: Set Up CRM Sync & Handoff

Configure the **Salesforce Connector** to sync qualified prospects to CRM:

**Reference**: [MCAE Functional Consultant Skill](../mcae-functional-consultant/) — "CRM Syncing Prospects"

**Setup**:
- Connector setting: Sync prospects with Score ≥ [your threshold, e.g., 85 or 100]
- Field mapping: Map MCAE prospect fields → Salesforce Lead/Contact fields
- Lead assignment: Salesforce assignment rules auto-assign leads to sales reps
- Test sync: Create test prospect, reach score threshold, verify lead appears in SF

### Step 6: Monitor & Iterate

**Metrics to Track**:
- % of prospects reaching each score threshold (50, 75, 100)
- Conversion rate from MQL (Score ≥ 75) to SQL (Score ≥ 100)
- Sales feedback: "Are Score ≥ 100 prospects actually sale-ready?"
- Pipeline contribution: How many Sales ≥ 100 prospects became opportunities?

**Monthly Checkpoints**:
1. Do threshold values need adjustment? (E.g., if 90% reach Score ≥ 100, raise threshold to 120)
2. Are point values realistic? (E.g., if email open = +10, prospects over-inflate score without deep engagement)
3. Is sales team using assignments? (If no, training might be needed; if yes, can we assign even earlier?)
4. What content drives the highest score? (Focus future efforts there)

## Complete Example

See [Implementation Examples](./references/implementation-examples.md) for:
- **Example 1**: Whitepaper → Sales Handoff (step-by-step)
- **Example 2**: Multi-touch Attribution with Score Decay
- **Example 3**: Behavioral Segmentation (Researcher vs. Buyer)
- **Example 4**: Account-Based Marketing (ABM) Scoring

## Common Pitfalls

| Mistake | Why It Fails | Fix |
|---|---|---|
| **Score starts too high** | Too many prospects hit handoff threshold; not actually qualified | Set initial score = 0; let engagement earn points slowly |
| **Threshold too low** | Sales team gets unqualified leads, loses trust in program | Define "ready for sales" with sales team first; start conservative |
| **No rule branching** | All prospects follow same path regardless of engagement | Use Rule Steps to create YES/NO branches based on score |
| **Score inflates without engagement** | Prospect reaches Score ≥ 100 by list membership alone | Reserve high points for actions (form fills, email clicks), not passive traits |
| **No CRM handoff defined** | Prospects exit MCAE but never reach sales | Build explicit "Assign to User" + "Add to Salesforce Campaign" steps |
| **Combine score + grade** | Only using score for qualification ignores prospect quality/fit | Create rules like: Score ≥ 85 AND Grade = A → priority; Score ≥ 75 AND Grade = B → standard |

## Next Steps

1. **Document your scoring model** (define point values, thresholds)
2. **Build a pilot program** (1-2 nurture tracks)
3. **Test in sandbox** (Engagement Studio Test tab)
4. **Review with sales team** (confirm handoff criteria)
5. **Activate & monitor** (watch metrics for 2-4 weeks)
6. **Iterate** (adjust thresholds based on data)

## Related Skills

- [MCAE Functional Consultant](../mcae-functional-consultant/) — Forms, lists, completion actions, engagement basics
- [Marketing Cloud Next](../marketing-cloud-next/) — Integrated campaigns with data imports
