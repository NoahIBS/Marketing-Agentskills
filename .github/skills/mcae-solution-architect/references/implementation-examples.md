# Score-Based Lead Qualification: Implementation Examples

## Example 1: Whitepaper Download → Sales Handoff

**User Story**: "As a Marketing Manager, I want to nurture leads after whitepaper download and automatically hand them off to sales when they reach a certain engagement threshold."

### Setup Steps

#### Step 1: Form Setup
Create a landing page with a form for whitepaper download:
- **Fields**: First Name, Last Name, Email, Company, Job Title (custom field)
- **Form Completion Action**: 
  - Adjust Score: **+10 points** (baseline engagement for asset download)

#### Step 2: Engagement Program Setup
Create an engagement program for whitepaper nurturing:

```
Program Name: "Whitepaper Nurture - Enterprise Focus"
Recipient Lists: [Whitepaper downloaders list]

Step 1: Action - Adjust Score
  → +5 points (list membership bonus)

Step 2: Send Email
  → Email: "Thank You for Downloading Our Whitepaper"
  → Wait 2 days

Step 3: Trigger - Email Open
  → If opened: +10 points (engagement bonus)
     → Wait 1 day
  → If not opened (max wait 14 days):
     → Go to Step 5

Step 4: Rule - Mid-Level Qualification
  Condition: Score >= 50
  If YES:
    → Send Email: "Deeper Dive: Industry Trends"
    → Wait 3 days
  If NO:
    → Send Email: "Quick Tip: Getting Started"
    → Wait 7 days

Step 5: Rule - Sales Handoff Gate
  Condition: Score >= 85 AND Job_Title IN ['VP', 'Director', 'C-Level']
  If YES:
    → Assign to User: [Sales Development Rep]
    → Adjust Score: +15 (assignment bonus)
    → Send Email: "Sales Team Connection"
  If NO:
    → Send Email: "Deeper Content Series"
    → Wait 5 days
    → Rule: Score >= 75?
      If YES: Assign to Group: Sales Development
      If NO: Exit to Continue Program
```

#### Step 3: Automation Flow (Optional)
If you want automatic Salesforce Lead creation when score ≥ 100:

```
Flow: Whitepaper_Score_Based_Sync
Trigger: Prospect record updated
Condition: Score >= 100 AND SalesforceLeadId IS NULL

Actions:
  1. Get Salesforce Lead by email
  2. If NOT found:
       Create Lead with prospect data
       Update prospect: SalesforceLeadId = [new Lead ID]
       Send notification to sales manager
```

#### Step 4: Monitor and Adjust
- **Week 1-2**: Observe how many prospects hit Score ≥ 85 threshold
- **Week 3**: If fewer than expected → Lower threshold to 75 OR adjust email content
- **Week 4**: Check sales team feedback ("Are these really qualified?")
- **Monthly**: Review score distribution; consider marketing → sales collaboration

### Metrics to Track
- % of downloaders reaching Score ≥ 50 (nurture effectiveness)
- % reaching Score ≥ 85 (MQL conversion)
- % reaching Score ≥ 100 (SQL conversion)
- Sales team feedback on quality of handed-off prospects

---

## Example 2: Multi-Touch Attribution with Score Decay

**User Story**: "Track contribution of multiple marketing touchpoints to lead quality, but weight recent engagement more heavily than old engagement."

### Setup Steps

#### Challenge
Default MCAE scoring is *accumulative* (all points persist forever). A prospect who engaged 12 months ago retains their score even if they're now inactive.

#### Solution: Engagement Studio + Annual Reassessment

```
Step 1: Engagement Program - Score Maintenance
  (Run monthly/quarterly as needed)
  
  → Trigger: Custom Field "Last Score Review Date" > 90 days ago
  
  → Action: Create Task for Admin
    "Review prospect {Name}: Last active {Last Activity Date}, 
     Current Score {Score}. Recommend reset if > 6 months inactive."
    
Step 2: Engagement Program - Re-Engagement Offer
  
  Condition: Last Activity > 6 months ago
  
  If YES:
    → Adjust Score: -50 (decay penalty for inactivity)
       OR reset to 0 for clean slate
    → Send Email: "We miss you! Here's what's new"
       
  If NO (actively engaged):
    → Continue normal nurture tracks
```

#### Alternative: Automation Flow for Decay
```
Flow: Score_Decay_Monthly
Trigger: Schedule (1st of month at 9 AM)

For each prospect:
  1. Get last engagement date
  2. Calculate months since engagement
  3. If > 6 months: Reduce score by 25%
  4. Update prospect record
  
This creates "fresher" scores that better reflect current engagement.
```

---

## Example 3: Behavioral Segmentation with Scoring

**User Story**: "Segment prospects by behavior type (researcher vs. buyer) and tailor engagement paths based on their demonstrated buying pattern."

### Setup Steps

#### Behavior Definition
Based on **which content they engage with**, not just engagement volume:

| Behavior Type | Indicators | Score Multiplier |
|---|---|---|
| **Researcher** (High POC) | 5+ page views, no form fills | 1x base score |
| **Buyer** (Decision maker) | Form fills, peer content, ROI content | 3x score adjustments |
| **Executive** (Influencer) | Case studies, webinars, email opens | 2x score adjustments |

#### Implementation

```
Engagement Program: "Behavioral Routing"

Step 1: Rule - Content Type Engagement Check
  
  If clicked: "ROI Calculator" or "Pricing Guide"
    → Adjust Score: +30 (buyer signal)
    → Flag: buyer_behavior__c = true
    
  Else if: page views > 5 AND no forms
    → Adjust Score: +5 (still learning)
    → Flag: researcher_behavior__c = true
    
  Else if: opened case study + webinar email
    → Adjust Score: +20 (executive signal)
    → Flag: executive_behavior__c = true

Step 2: Rule - Routing Based on Behavior
  
  If buyer_behavior__c = true AND Score >= 75:
    → Assign to Sales (Account Executive)
    → Send Email: "Pricing & Demos"
    
  If researcher_behavior__c = true:
    → Send Email: "Comparison Guide"
    → Wait 7 days
    → Rule: Score >= 60?
      If YES: Assign to Sales
      If NO: Continue nurture
    
  If executive_behavior__c = true AND Score >= 80:
    → Assign to Sales (Regional VP)
    → Notify: "Executive Prospect Ready for C-Level Conversation"
```

#### Expected Outcome
- **Researchers**: Longer nurture cycle, but higher close rates (more informed)
- **Buyers**: Faster sales cycles, immediate demo requests
- **Executives**: Higher-touch, account-based routing to leadership

---

## Example 4: Account-Based Scoring (ABM)

**User Story**: "Target high-value accounts; progress prospects from that account together as a unit."

### Setup Steps

#### Account-Level Scoring
MCAE supports company-level (account) scoring separate from prospect scoring:

```
Company Score = SUM(All Prospect Scores in Company)
        +
       BONUS: Multi-prospect engagement (3+ buyers engaged = +50)

Account Status:
  If CompanyScore >= 500: Account is HOT → Alert Account Executive
  If CompanyScore >= 300: Account is WARM → Schedule account review
  If CompanyScore < 300: Account is COLD → Continue general nurture
```

#### Implementation

```
Engagement Program: "Account-Based Nurture"

Step 1: Trigger - Form Submission (any prospect at target company)
  → Get all prospects at this company
  → Increment company_score__c
  → Adjust Score: +25 per prospect
  
Step 2: Rule - Company-Level Gate
  Condition: company_score__c >= 300
  
  If YES:
    → Send Alert Email: Account Executive
       "Account: {Company}, Total Score: {CompanyScore}, 
        Buying Groups Engaged: {ProspectCount}"
    
    → For all prospects in company:
      Add to List: "High-Value Account - Active"
      Assign to Account Executive (same user for all)
      Send Email: "We're aware of your company's interest"
  
  If NO:
    → Continue company nurturing

Step 3: Action - Milestone Tracking
  → Add all prospects to Salesforce Campaign: "ABM - {CompanyName}"
  → Campaign Status: tracking engagement by account
```

#### Expected Outcome
- Sales team focuses on entire buying group, not individual
- Coordinated outreach to multiple stakeholders
- Better deal closure rates

---

## Troubleshooting Common Issues

### Issue: Prospects stuck at score threshold
**Cause**: Rule condition too strict; no engagement happening to increase score
**Fix**: Lower threshold by 10 points, OR add "engagement bonus" email sends to drive activation

### Issue: Score inflates too quickly
**Cause**: Too many high-point adjustments (e.g., +50 per email open)
**Fix**: Audit point values; adjust to +5 or +10 for common activities; reserve +50 for high-intent actions (webinar attendance, demo request)

### Issue: Sales rejects all handed-off prospects as "not qualified"
**Cause**: Score threshold doesn't align with sales definition of "ready"
**Fix**: Schedule marketing-sales sync; define score = capability to engage, not qualification; add Grade field (A/B/C) for fit assessment

### Issue: Score doesn't update quickly enough for timely sales response
**Cause**: Using Engagement Studio rules (batch processing, wait periods)
**Fix**: Implement Salesforce Flow with Record-Triggered automation for immediate score updates and instant assignment
