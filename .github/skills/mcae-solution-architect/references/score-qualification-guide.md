# MCAE Prospect Score-Based Qualification Model

## Overview

Unlike traditional lead lifecycle stages (Lead → Contact → Opportunity), Account Engagement uses a **score-based qualification model**. Prospect scores are numeric values that accumulate based on engagement activities, demographic data, and system changes. Score thresholds determine when prospects are ready for specific actions.

## Qualification Tiers

| Score Range | Status | Action | Sales Stage |
|---|---|---|---|
| 0–50 | **Unqualified/Cold** | Initial nurturing, education emails | — |
| 50–85 | **Warm/Nurturing** | Engagement programs, targeted content | Lead |
| 85–99 | **Hot/Marketing Qualified** | Sales engagement emails, assignment to sales group | MQL |
| 100+ | **Sales Qualified** | CRM handoff, opportunity creation, sales team assignment | SQL |

> **Key Difference**: Prospects don't move between "stages" — they move between *score thresholds*. Same prospect record, different treatment based on current score.

## Score Assignment Methods

### 1. Implicit Scoring (Built-in Activities)
Account Engagement automatically scores prospects based on:
- **Email opens**: +5 points (configurable)
- **Link clicks**: +10 points (configurable)
- **Form submissions**: +20 points (configurable)
- **Page views**: +2 points (configurable)
- **Opportunity created**: +50 points (configurable)
- **Opportunity lost**: -100 points (configurable)

### 2. Explicit Scoring (Manual/Automated Adjustments)
Admins and workflows set scores manually:
- **Engagement Studio Actions**: "Adjust Score +10" after whitepaper download
- **Automation Flows**: Score +25 when custom field "Executive" = true
- **Manual Updates**: Sales user manually adjusts score to reflect qualification level

### 3. Grade-Based Scoring (Optional Complementary Field)
Prospects also have a **Grade** field (A, B, C, D) reflecting fit/quality independent of engagement. Combine with Score for comprehensive qualification:
- **Score 85+ AND Grade A** = Sales priority
- **Score 75+ AND Grade B** = Sales follow-up
- **Score < 70 OR Grade D** = Continue nurturing

## Score Persistence

- Scores never expire unless explicitly removed
- Previous engagement is always represented in the final score
- A prospect who hasn't engaged in 6 months retains their score
- Historical engagement creates historical score value

## Qualification Gates (Engagement Studio Rule Steps)

Score thresholds trigger automation in Engagement Studio Rule Steps:

```
IF Prospect Score ≥ 50
  ↓
THEN Send nurture email + Wait 3 days

IF Prospect Score ≥ 85
  ↓
THEN Assign to Sales + Send sales kickoff email

IF Prospect Score ≥ 100
  ↓
THEN Add to Salesforce Campaign + Sync to CRM
```

## Connection to Automation Flows

When Engagement Studio actions alone aren't sufficient, use **Automation Flows** (Salesforce Flow):

1. **Record-Triggered Flow**: When prospect score updates, evaluate if score ≥ 85
2. **Decision Element**: If true → Create Salesforce Lead record
3. **Create Records Element**: Auto-populate lead with prospect data
4. **Update Records Element**: Mark prospect as "Synced to CRM"

## Relationship to CRM Handoff

Score-based qualification in MCAE determines **readiness for CRM handoff**:

| MCAE Score | Salesforce Status | Action |
|---|---|---|
| Score < 85 | Prospect only | Continue nurturing in MCAE |
| Score ≥ 85 | Lead created in Salesforce | Dual-track in MCAE + SF |
| Score ≥ 100 + Opportunity field | Lead with Opportunity | Active sales engagement |

The **Salesforce Connector** syncs qualified prospects (Score ≥ specified threshold) to SF, where they become Leads or Contacts for sales team assignment.

## Best Practices

1. **Start Conservative**: Set initial threshold at 75–85 to avoid premature handoff
2. **Align Across Teams**: Define score ranges with both marketing and sales
3. **Document Score Triggers**: Create a "Scoring Guide" documenting which actions add/subtract points
4. **Review Quarterly**: Test threshold effectiveness; adjust if prospects aren't ready at handoff
5. **Combine with Grade**: Use Grade for fit, Score for engagement — together they predict Sales readiness
