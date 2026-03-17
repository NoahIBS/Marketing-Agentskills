# Marketing Architecture Decision Matrix

**Architecture guidance for Salesforce marketing implementations across MCAE and Salesforce Core**

This guide helps marketing architects and administrators decide **where marketing functionality should be built** when working with Marketing Cloud Account Engagement (MCAE) and Salesforce Core. It focuses exclusively on marketing-related architectural decisions.

---

## 1. Platform Decision: MCAE vs Salesforce Core

### Overview

The first architectural decision is **which platform owns a given marketing capability**. This decision determines where you build automation, store data, and manage processes.

- **MCAE** excels at prospect engagement, scoring, and multi-step nurturing
- **Salesforce Core** excels at CRM record management, complex system automation, and opportunity tracking
- **Cross-Cloud approaches** combine both for complete customer journeys

### Platform Decision Table

| Use Case | MCAE | Salesforce Core | Cross-Cloud | Justification |
|----------|------|-----------------|-------------|---------------|
| **Email Marketing & Nurturing** | ✅ Primary | ⚠️ Limited | ✅ Recommended | MCAE has superior deliverability, segmentation, and A/B testing. Salesforce email has strict rate limits. Use Cross-Cloud when sales needs inbox visibility. |
| **Lead Nurturing (Multi-Step)** | ✅ Primary | ❌ Not suitable | ✅ Recommended | MCAE's Engagement Studio is built for nurture workflows. Salesforce Flows are better for record automation, not nurture journeys. |
| **Prospect Scoring** | ✅ Primary | ❌ Not suitable | ✅ Recommended | MCAE scoring is dynamic and real-time. Lead scoring in Salesforce requires custom fields and flows. Use Cross-Cloud to sync scores to Salesforce. |
| **Lead Status Management** | ❌ Not suitable | ✅ Primary | ⚠️ Consider | Salesforce owns Lead/Contact records. MCAE can trigger status changes but shouldn't be system of record. |
| **Opportunity Automation** | ❌ Not suitable | ✅ Primary | ✅ Recommended | Opportunities exist only in Salesforce. Use Flows or Process Builder for automation. Connect MCAE for pre-opportunity nurturing. |
| **Sales Workflow & Task Management** | ❌ Not suitable | ✅ Primary | ✅ Recommended | Task creation, assignment, and escalation belong in Salesforce. MCAE can trigger them via Connector. |
| **Marketing Engagement Tracking** | ✅ Primary | ⚠️ Limited | ✅ Recommended | MCAE tracks email opens, clicks, form submissions. Salesforce has limited engagement visibility. Use Distributed Marketing for sales team visibility. |
| **Campaign Influence & Attribution** | ❌ Limited | ✅ Primary | ✅ Recommended | Salesforce Campaign Influence tracks which campaigns influenced won opportunities. MCAE can't see revenue. Use Cross-Cloud for complete attribution. |
| **Cross-Object Logic** | ⚠️ Limited | ✅ Primary | ✅ Recommended | Multi-object logic (Lead → Opportunity → Account) belongs in Salesforce Flows. MCAE can participate but not orchestrate. |
| **Marketing Segmentation** | ✅ Primary | ⚠️ Limited | ✅ Recommended | MCAE Dynamic Lists are far more flexible than Salesforce list views. Combine for comprehensive segmentation. |
| **Data Integration & Sync** | ⚠️ Limited | ✅ Primary | ✅ Recommended | Salesforce is the system of record for CRM data. Use Connectors to keep MCAE and Salesforce in sync. |

### Rule of Thumb: Platform Decision

> **MCAE owns prospect engagement; Salesforce owns CRM records.**
>
> - **Choose MCAE if:** You're nurturing prospects not yet in Salesforce, managing email engagement, or you need real-time scoring logic
> - **Choose Salesforce if:** You're updating CRM records, orchestrating opportunity processes, or managing sales workflows
> - **Choose Cross-Cloud if:** You need both prospect engagement AND CRM record management, or you want sales teams to see marketing metrics

---

## 2. Automation Decision: Engagement Studio vs Automation Rules vs Flow

### Overview

The second architectural decision is **which automation tool to use**. Three primary options exist:

- **Engagement Studio** – Prospect-focused, email-triggered, multi-step nurture workflows
- **Automation Rules** – Background MCAE processes triggered by record changes
- **Salesforce Flow** – CRM-focused, complex logic, multi-object automation

### Automation Tool Comparison

| Scenario | Engagement Studio | Automation Rules | Salesforce Flow | Decision |
|----------|------------------|------------------|-----------------|----------|
| **Multi-step nurture journeys (5+ emails)** | ✅ Ideal | ❌ Not suitable | ❌ Not suitable | ES is purpose-built for nurture workflows. Provides visual journey builder, prospect state management, and email integration. |
| **Background prospect automation** | ⚠️ Works | ✅ Better | ❌ Not suitable | Automation Rules run in background without user interaction. Use for prospect record cleanup, list management, status updates. |
| **CRM record updates (lead/contact/account)** | ❌ Limited | ❌ No access | ✅ Ideal | Flows are the native Salesforce automation. Use for complex record logic, field updates, and cross-object changes. |
| **Email-triggered workflows** | ✅ Ideal | ⚠️ Clunky | ⚠️ Limited | ES naturally triggers on email opens/clicks. Automation Rules can trigger but have limitations. Flows can't directly trigger on email events. |
| **Cross-object automation (Prospect → Lead → Opp)** | ❌ No access | ❌ No access | ✅ Ideal | Flows access all Salesforce objects. MCAE can't orchestrate cross-object logic. Use Cross-Cloud connectors instead. |
| **Marketing segmentation & list management** | ✅ Ideal | ✅ Good | ❌ Not suitable | ES and Automation Rules can add/remove prospects from lists. Flows can't directly manage MCAE lists. |
| **Real-time scoring rules** | ✅ Ideal | ⚠️ Slower | ❌ Not suitable | ES scores prospects in real-time as they engage. Automation Rules update existing scores. Flows can't access MCAE scoring engine. |
| **Lead assignment & routing** | ⚠️ Can trigger | ❌ No access | ✅ Ideal | ES/Automation Rules can trigger assignment. Salesforce Lead Assignment Rules and Flows handle actual routing and queuing. |
| **Conditional logic (if/then/else chains)** | ✅ Good | ✅ Good | ✅ Excellent | All support conditionals. Flow is more powerful for complex nested logic. ES and AR are simpler but sufficient for marketing. |
| **API & external integrations** | ⚠️ Limited | ⚠️ Limited | ✅ Excellent | Flows have native HTTP request actions. MCAE tools have limited outbound integration. Use Flows for external system updates. |
| **Scheduled/batch processing** | ⚠️ Limited | ✅ Good | ✅ Good | Automation Rules run on schedules. Flows can be scheduled. ES is event-driven, not batch. |

### Automation Tool Selection: Detailed Scenarios

#### Scenario A: Email Nurture Journey
**Business:** Send 5-email nurture series based on email engagement

**Best Tool:** Engagement Studio

**Why:** ES is purpose-built for multi-step email journeys. Provides:
- Visual workflow builder
- Email content library integration
- State management (prevents duplicate sends)
- Scoring integration
- Built-in wait/timer steps
- Prospect engagement tracking

---

#### Scenario B: Auto-Update Prospect Score
**Business:** When prospect opens marketing email, automatically add 5 points

**Best Tool:** Engagement Studio (primary) + Automation Rules (fallback)

**Why:** 
- ES naturally triggers on email open events
- Can score in real-time
- Automation Rules work for background scoring but less efficient
- Flows can't access email engagement events

---

#### Scenario C: Create Salesforce Lead When Score Reaches 100
**Business:** When prospect score reaches 100, automatically create Lead record in Salesforce

**Best Tool:** Cross-Cloud with Automation Rule → Salesforce Connector

**Why:**
- Automation Rule detects score change in MCAE
- Connector creates Lead in Salesforce
- Flows alone can't access MCAE score changes
- Pure Flow solution would require polling (inefficient)

---

#### Scenario D: Complex Lead Assignment Logic
**Business:** Assign newly created Leads to sales team based on region, product interest, and available capacity

**Best Tool:** Salesforce Flow + Lead Assignment Rules

**Why:**
- Flow handles complex multi-object logic
- Lead Assignment Rules handle capacity/queue management
- This logic is CRM-specific, not marketing-specific
- MCAE can trigger but shouldn't orchestrate

---

#### Scenario E: Background Prospect Cleanup
**Business:** Nightly job to mark prospects as "Inactive" if they haven't engaged in 90 days

**Best Tool:** Automation Rules

**Why:**
- Runs in background without user interaction
- Scheduled batch execution available
- Simpler than building a Flow
- Focused on prospect hygiene, not cross-object logic

---

### Rule of Thumb: Automation Decision

> **Engagement Studio for engagement; Automation Rules for background work; Flow for CRM logic.**
>
> - **Use Engagement Studio if:** You're building nurture journeys, email-triggered workflows, or real-time prospect scoring
> - **Use Automation Rules if:** You need background prospect record updates, segmentation logic, or scheduled batch processing
> - **Use Salesforce Flow if:** You're updating CRM records, orchestrating multi-object logic, or calling external APIs

---

## 3. Data Ownership Decision: Marketing Data vs CRM Data

### Overview

The third architectural decision is **which system owns which data**. Data ownership determines:
- Where data is created and updated
- Which system is the source of truth
- How data syncs between systems
- Reporting and analytics location

### Data Ownership Comparison Table

| Data Type | MCAE (System of Record) | CRM (System of Record) | Sync Strategy | Justification |
|-----------|------------------------|----------------------|-----------------|---------------|
| **Email Engagement (opens, clicks, bounces)** | ✅ Owner | ❌ Reference | One-way: MCAE → Salesforce (via Connector) | Email events are native to MCAE. Salesforce receives summary metrics only. MCAE is authoritative. |
| **Prospect Score** | ✅ Owner | ⚠️ Synced copy | One-way: MCAE → Salesforce | MCAE calculates scores in real-time. Prospects are MCAE objects. Sync score to Lead for visibility, but MCAE is source of truth. |
| **Lead Score** | ⚠️ Synced copy | ✅ Owner | Two-way: MCAE ↔ Lead (via Connector) | Lead is Salesforce object. Lead score can originate in Salesforce (manual or Flow-calculated) or be synced from MCAE prospects. Define single source per org. |
| **Lead/Contact Status** | ❌ Not owner | ✅ Owner | One-way or Two-way | Status (Active, Inactive, Deleted) is a CRM concept. MCAE syncs prospect status but shouldn't update it. Flows/automation own lead status changes. |
| **Opportunity Stage & Status** | ❌ Not owner | ✅ Owner | One-way: Salesforce only | Opportunities exist only in Salesforce. MCAE can't own or update. MCAE can see opportunities read-only via Connector for context. |
| **Campaign Membership** | ⚠️ Owns prospects | ✅ Owns leads | Bi-directional: MCAE journey → SF Campaign | MCAE owns prospect campaign membership in Engagement Studio. Salesforce owns Lead/Contact campaign membership. Use Distributed Marketing to link both. |
| **Email Engagement History** | ✅ Owner | ❌ Reference only | One-way: MCAE → Salesforce (summary only) | MCAE stores detailed email engagement (opens, clicks, unsubscribes). Salesforce receives aggregated metrics. Full history lives in MCAE. |
| **Form Submissions & Custom Fields** | ✅ Owner | ⚠️ Synced copy | One-way: MCAE → Salesforce (select fields) | Form submissions are MCAE events. Custom field values originate in forms. Only sync relevant fields to Salesforce; not all form data needs to cross. |
| **List/Segment Membership** | ✅ Owner | ⚠️ Reference | One-way: MCAE → Salesforce (via dynamic segments) | Dynamic Lists are MCAE. Salesforce can see list membership via Connector but shouldn't be source of truth. Use MCAE lists for engagement, Salesforce lists for sales. |
| **Sales Task & Activity Records** | ❌ Not owner | ✅ Owner | One-way: Salesforce only | Tasks and activity records are CRM objects. MCAE can trigger task creation but doesn't own tasks. All task management in Salesforce. |
| **Account Information** | ❌ Not owner | ✅ Owner | One-way: Salesforce → MCAE (for context) | Accounts are Salesforce objects. MCAE can sync account data for reporting/context but shouldn't modify. Use for ABM targeting only. |
| **Campaign Attribution & ROI** | ⚠️ Engagement metrics | ✅ Revenue attribution | Two-way reporting | MCAE tracks engagement attribution (which campaigns led to form submission). Salesforce tracks revenue attribution (which campaigns influenced won deals). Both needed for full picture. |
| **Prospect vs Lead Distinction** | ✅ Owner | ✅ Owner | Manual handoff (not bidirectional) | Prospects are MCAE objects. Leads are Salesforce objects. Keep separate until explicit handoff. One prospect can create multiple leads (multi-step sales process). |

### Data Architecture Patterns

#### Pattern 1: MCAE is System of Record
**Used for:** Email engagement, prospect scoring, nurture state, prospect records

**Flow:**
```
MCAE (create & update) → Connector syncs → Salesforce (read-only reference)
```

**Example:** Prospect engagement score is calculated and stored in MCAE. Score synced to Salesforce Lead via Connector. Sales team sees score but can't edit in Salesforce.

---

#### Pattern 2: Salesforce is System of Record
**Used for:** Lead/Contact records, opportunity data, sales activities, revenue attribution

**Flow:**
```
Salesforce (create & update) → Connector syncs → MCAE (read-only reference)
```

**Example:** Lead records created in Salesforce by sales or via lead upload. Lead data synced to MCAE for email targeting. MCAE doesn't modify lead record.

---

#### Pattern 3: Dual Systems of Record (Handoff)
**Used for:** Prospect → Lead transitions, journey → CRM handoff

**Flow:**
```
MCAE owns Prospect → Connector transfers selected fields → Salesforce owns Lead
```

**Example:** Prospect reaches 100 score in MCAE. Connector creates Lead record in Salesforce with prospect details (email, company, score). MCAE drops prospect from marketing list. Lead now owned by Salesforce.

---

#### Pattern 4: MCAE for Engagement, Salesforce for Revenue
**Used for:** Full attribution and ROI

**Flow:**
```
MCAE (engagement attribution) ↔ Connector ↔ Salesforce (revenue attribution)
```

**Example:** 
- MCAE tracks: Which campaign/email drove form submission
- Salesforce tracks: Which campaign influenced won deal
- Combined view = full customer journey ROI

---

### Data Ownership Rules by Persona

#### MCAE Owns:
- ✅ Prospect records (person objects not yet in Salesforce)
- ✅ Email engagement history (opens, clicks, bounces)
- ✅ Prospect scores and grades (calculated and updated in real-time)
- ✅ Engagement Studio state (witch list, journey membership)
- ✅ Marketing forms and form submissions
- ✅ Dynamic list/segment membership
- ✅ Prospect custom fields
- ✅ Email templates and content
- ✅ Engagement metrics and reports

#### Salesforce Owns:
- ✅ Lead and Contact records (people in CRM)
- ✅ Account records
- ✅ Opportunity records and stages
- ✅ Sales activities (tasks, events, calls)
- ✅ Lead assignment and routing
- ✅ Campaign membership for leads/contacts
- ✅ Campaign Influence models and revenue attribution
- ✅ Custom CRM fields on standard objects
- ✅ Permission and security model for CRM data

#### Both Own (Synced):
- ⚠️ Email address (master in both, kept in sync)
- ⚠️ Company name (synced from Salesforce → MCAE for segmentation)
- ⚠️ Score fields (calculated in MCAE, synced to Salesforce for visibility)
- ⚠️ Campaign participation (MCAE journey + SF campaign = complete picture)

---

### Rule of Thumb: Data Ownership Decision

> **MCAE is the engagement system; Salesforce is the record system.**
>
> - **Store in MCAE if:** It's engagement data (email events, prospect behavior, nurture state), it's about what prospects do, or it only matters for marketing
> - **Store in Salesforce if:** It's a CRM record (Lead, Contact, Account, Opportunity), it matters to sales, or it needs business process integration
> - **Sync between systems if:** Data needs visibility in both systems, but define one as the source of truth and sync one-way or bi-directional based on ownership
> - **Never assume data exists in Salesforce if created in MCAE** – Always explicitly sync via Connector to increase visibility

---

## Summary: Three Decisions for Marketing Architecture

### Decision 1: Platform
> **Where does this marketing capability belong?**
- MCAE for engagement, segmentation, and scoring
- Salesforce for CRM records and business processes

### Decision 2: Automation
> **Which automation tool should orchestrate this workflow?**
- Engagement Studio for nurture journeys
- Automation Rules for background prospect work
- Salesforce Flow for CRM logic and multi-object automation

### Decision 3: Data
> **Which system owns this data?**
- MCAE owns engagement and prospect data
- Salesforce owns CRM records and revenue data
- Sync strategically between systems

---

## Quick Reference Checklist

Use this checklist when designing a new marketing capability:

### Before You Build

- [ ] **Platform Decision:** Should this live in MCAE or Salesforce? (Use Table 1)
- [ ] **Automation Decision:** What tool should execute this? (Use Table 2)
- [ ] **Data Decision:** Which system owns this data? (Use Table 3)
- [ ] **Integration Decision:** Does data need to sync between systems?
- [ ] **Reporting Decision:** Where will metrics be reported (MCAE Reports, Salesforce Dashboards, or both)?
- [ ] **Ownership Decision:** Who maintains this in production (MCAE Admin, Salesforce Admin, or both)?

### Red Flags

🚨 **Stop if you see these patterns:**

- MCAE trying to manage Lead assignment (belongs in Salesforce)
- Salesforce Flow trying to manage email nurture (belongs in Engagement Studio)
- Data stored in only one system when both need visibility
- Unclear which system is the source of truth for shared data
- Complex multi-object logic built in Engagement Studio (use Flow instead)
- Email delivery processed through Salesforce at scale (use MCAE instead)

---

## Additional Resources

- **Related:** See `decision_framework.md` for business scenario decision logic
- **Implementation:** Reference `sales_core.md` for Salesforce automation patterns
- **Engagement:** Reference MCAE skill files for Engagement Studio implementation details
- **Integration:** Reference cross-cloud documentation for Connector and Distributed Marketing patterns

---

**Version:** 1.0  
**Last Updated:** March 2026  
**Based on:** Salesforce Spring '26 Platform Architecture Best Practices
