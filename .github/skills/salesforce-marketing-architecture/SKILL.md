---
name: salesforce-marketing-architecture
description: 'Architectural decision guidance for Salesforce marketing solutions spanning MCAE, Salesforce Core, and cross-cloud implementations. Use for: deciding whether to build in MCAE or Salesforce; choosing automation tools (Engagement Studio vs Flow vs Automation Rules); determining data ownership; evaluating platform capabilities. Answers: "MCAE or Salesforce?", "Flow or Automation Rules?", "Cross-cloud or single platform?"'
argument-hint: 'What marketing capability are you building? (e.g., "nurture automation", "campaign lead assignment", "prospect scoring")'
user-invocable: true
disable-model-invocation: false
---

# Salesforce Marketing Architecture

**Architectural decision guidance for MCAE, Salesforce Core, and cross-cloud marketing solutions.**

This skill helps marketing architects and administrators make informed decisions about where to build marketing capabilities across the Salesforce marketing ecosystem.

---

## When to Use

✅ **Use this skill for:**
- Deciding between MCAE, Salesforce Core, or cross-cloud implementation
- Choosing which automation tool to use (Engagement Studio, Automation Rules, Flow)
- Determining data ownership (MCAE vs Salesforce as system of record)
- Evaluating platform capabilities before building
- Comparing implementation approach options
- Assessing architectural trade-offs and anti-patterns

❌ **Don't use for:**
- Implementation details or step-by-step technical setup
- Fixing existing code or debugging errors
- General Salesforce questions outside marketing architecture
- Tool-specific how-to guidance (see individual tool documentation)

---

## Decision Workflow

Follow these steps to make an informed architectural decision:

### Step 1: Define the Business Requirement

Start by clearly defining what you're building:

```
Business Requirement:
└─ Use Case: [E.g., "Multi-step email nurturing for unqualified prospects"]
└─ Primary Actors: [E.g., "Prospects not yet in Salesforce"]
└─ Success Criteria: [E.g., "Real-time scoring, high email delivery"]
```

**Questions to ask:**
- What is the business outcome?
- Who are the target audience (prospects, leads, contacts)?
- What is the primary action or workflow?
- What metrics or KPIs matter?
- What time constraints exist?

### Step 2: Make Platform Decision

Use the **Platform Decision Matrix** to determine whether to build in MCAE, Salesforce Core, or cross-cloud.

**Key factors:**
1. **Who are your targets?** (Prospects only? Leads/Contacts? Both?)
2. **What's the primary tactic?** (Email nurturing? System automation? CRM record updates?)
3. **What level of complexity?** (Simple rules? Complex multi-object logic?)
4. **Do you need CRM integration?** (Sales visibility? Campaign Influence? Revenue attribution?)

**Baseline guidance:**
- 🔵 **Choose MCAE** if: Prospect nurturing, email-primary, scoring-based qualification, sales doesn't need deep visibility
- 🔵 **Choose Salesforce Core** if: All targets in CRM, complex system automation, Campaign Influence required, sales workflows
- 🔵 **Choose Cross-Cloud** if: Full journey (prospect → lead → opportunity), both email + automation needed, ROI tracking critical

**Reference:** See `marketing-architecture-decision-matrix.md` → Section 1: Platform Decision Table (11 scenarios with justifications)

### Step 3: Make Automation Decision

Once you've chosen the platform, select which automation tool to use.

**For MCAE capabilities:**
- 🟠 **Engagement Studio** – Multi-step nurture journeys, email-triggered workflows, real-time scoring
- 🟠 **Automation Rules** – Background prospect updates, segmentation logic, batch/scheduled processing

**For Salesforce capabilities:**
- 🟣 **Salesforce Flow** – CRM record automation, complex multi-object logic, external integrations, API calls
- 🟣 **Lead Assignment Rules** – Automatic lead routing and queue management (for lead assignment use only)
- 🟣 **Process Builder** – Legacy automation (use Flow for new implementations)

**Common scenarios:**
- 5+ email nurture sequence → **Engagement Studio**
- Prospect cleanup/hygiene tasks → **Automation Rules**
- Lead assignment logic → **Salesforce Flow** or **Lead Assignment Rules**
- Cross-object workflows → **Salesforce Flow**
- Email-based triggers → **Engagement Studio**

**Reference:** See `marketing-architecture-decision-matrix.md` → Section 2: Automation Decision Table (10 scenarios with decision logic)

### Step 4: Make Data Ownership Decision

Determine which system is the authoritative source for each type of data.

**MCAE owns (source of truth):**
- ✔️ Prospect records and prospect fields
- ✔️ Email engagement (opens, clicks, bounces)
- ✔️ Prospect scores and dynamic list membership
- ✔️ Form submissions and form-generated data
- ✔️ Engagement Studio journey state

**Salesforce owns (source of truth):**
- ✔️ Lead/Contact records
- ✔️ Account and Opportunity records
- ✔️ Sales activities (tasks, events, calls)
- ✔️ Lead assignment and routing decisions
- ✔️ Campaign Influence and revenue attribution

**Synced data (define one as source):**
- ⚠️ Email address, company, score, status fields
- ⚠️ Campaign membership (MCAE journey + SF campaign)

**Sync strategy:**
- **One-way sync** if one system is clearly the source (most common)
- **Two-way sync** if both systems need to write and read (risky, requires careful conflict resolution)
- **Event-driven sync** via Connectors rather than batch jobs (more reliable)

**Reference:** See `marketing-architecture-decision-matrix.md` → Section 3: Data Ownership Table (12 data types with ownership and sync patterns)

### Step 5: Evaluate Trade-offs

For each option, assess:

| Factor | MCAE | Salesforce Core | Cross-Cloud |
|--------|------|-----------------|-------------|
| **Implementation Speed** | ⚡ Fast | ⏱️ Medium | 🐢 Complex |
| **Email Performance** | ⭐⭐⭐⭐⭐ | ⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Automation Flexibility** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **CRM Integration** | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Sales Visibility** | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **ROI Tracking** | ⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Team Skill Required** | 👤 MCAE Admin | 👤 SF Admin | 👥 Both |
| **Maintenance Burden** | Low | Medium | High |

---

## Reference Architecture Patterns

### Pattern 1: MCAE-Only
**Best for:** Prospect database, email nurturing, low CRM complexity

```
MCAE → Email nurturing, Scoring, Segmentation
  └─ Connector syncs high-value prospects → Salesforce (one-way)
     └─ Salesforce receives prospects as Leads for sales follow-up
```

**Characteristics:**
- ✅ Fast to implement
- ✅ High email delivery quality
- ✅ Simple audience model
- ❌ Limited CRM integration
- ❌ Limited ROI tracking
- ❌ No sales visibility into nurture activity

---

### Pattern 2: Salesforce-Only
**Best for:** All audiences in CRM, complex automation, CRM-driven workflows

```
Salesforce → Lead management, Flows, Campaign Influence
  └─ Connector syncs limited data → MCAE (one-way, read-only)
     └─ MCAE receives Lead data for reporting context only
```

**Characteristics:**
- ✅ Full CRM integration
- ✅ Complex automation possible
- ✅ Campaign Influence + attribution
- ❌ Poor email delivery at scale
- ❌ Limited personalization
- ❌ Lead assignment complexity

---

### Pattern 3: Cross-Cloud (Recommended)
**Best for:** Full customer journeys, email + automation both critical, ROI tracking essential

```
MCAE ←→ Salesforce
  ├─ MCAE: Email nurturing, Scoring, Segmentation
  ├─ Salesforce: Lead management, Flows, Campaign Influence
  └─ Connectors: Bi-directional sync
     ├─ Prospect score → Lead score (one-way: MCAE source)
     ├─ Lead status → Prospect record (one-way: Salesforce source)
     └─ Campaign membership (both systems participate)
     
Result: Prospect → Nurturing → Scoring → Lead Handoff → Opportunity → Won Deal
```

**Characteristics:**
- ✅ Best email + automation
- ✅ Full pipeline visibility
- ✅ Complete attribution
- ✅ Sales team engagement
- ⚠️ More complex to setup
- ⚠️ Requires data sync discipline
- ⚠️ Higher maintenance

---

## Quick Reference: Decision Trees

### "MCAE or Salesforce?"

```
START: "Where should I build this?"
│
├─ Is this about nurturing PROSPECTS (not yet in Salesforce)?
│  └─ YES → MCAE (or Cross-Cloud if complex)
│  └─ NO → Continue...
│
├─ Is EMAIL the primary tactic?
│  └─ YES → MCAE (or Cross-Cloud if CRM integration needed)
│  └─ NO → Continue...
│
├─ Do I need COMPLEX SYSTEM AUTOMATION (Flows, APIs, multi-object logic)?
│  └─ YES → Salesforce Core (or Cross-Cloud for both)
│  └─ NO → Continue...
│
├─ Do I need CAMPAIGN INFLUENCE or Revenue Attribution?
│  └─ YES → Salesforce Core (or Cross-Cloud)
│  └─ NO → Continue...
│
├─ Do SALES need visibility into this process?
│  └─ YES → Salesforce Core (or Cross-Cloud recommended)
│  └─ NO → MCAE is sufficient
│
END: If any YES above → Consider Cross-Cloud for flexibility
```

### "Flow, Automation Rules, or Engagement Studio?"

```
START: "What automation tool should I use?"
│
├─ Is this PROSPECT-related (not CRM records)?
│  └─ YES → Engagement Studio or Automation Rules → Continue A
│  └─ NO → Salesforce Flow → END
│
BRANCH A (MCAE):
├─ Is this a MULTI-STEP EMAIL JOURNEY (5+ emails)?
│  └─ YES → Engagement Studio → END
│  └─ NO → Continue...
│
├─ Is this RUN IN BACKGROUND (no user interaction)?
│  └─ YES → Automation Rules → END
│  └─ NO → Engagement Studio → END
│
BRANCH B (Salesforce):
├─ Is this LEAD ASSIGNMENT?
│  └─ YES → Lead Assignment Rules (or Flow for complex logic) → END
│  └─ NO → Salesforce Flow → END
```

### "Where should this data live?"

```
START: "Which system owns this data?"
│
├─ Is this EMAIL ENGAGEMENT (opens, clicks)?
│  └─ YES → MCAE owns, sync summary to Salesforce
│  └─ NO → Continue...
│
├─ Is this a PROSPECT RECORD or prospect-specific (field)?
│  └─ YES → MCAE owns
│  └─ NO → Continue...
│
├─ Is this a SALESFORCE CRM OBJECT (Lead, Contact, Account, Opportunity)?
│  └─ YES → Salesforce owns
│  └─ NO → Continue...
│
├─ Is this REVENUE or SALES-related?
│  └─ YES → Salesforce owns
│  └─ NO → Continue...
│
├─ Is this SHARED (both need to see)?
│  └─ YES → Define source system, sync one-way
│  └─ NO → Single system owns (from above logic)
│
END: Implement sync strategy (one-way, two-way, or event-triggered)
```

---

## Evaluation Checklist

Use this before finalizing your architectural decision:

### Platform Choice
- [ ] **Audience Clarity:** Do I know if targets are prospects-only or include existing CRM records?
- [ ] **Primary Tactic:** Is the primary action email, system automation, or workflow/orchestration?
- [ ] **Complexity Assessment:** Am I aware of complex automation needs (multi-object, APIs, integrations)?
- [ ] **Sales Visibility:** Do I know if sales teams need visibility or if this is marketing-only?
- [ ] **Revenue Tracking:** Do I need to track revenue impact or is engagement metrics sufficient?

### Automation Tool Choice
- [ ] **Workflow Type:** Have I identified if this is email-journey, background-task, or CRM-automation?
- [ ] **Scalability:** Do I know the volume and frequency (real-time vs batch vs scheduled)?
- [ ] **Integration Needs:** Do I need external system integration or API calls?
- [ ] **Team Capability:** Does my team have the required skills for the tool (admin vs dev)?

### Data Ownership
- [ ] **Source Identification:** Have I identified which system creates/updates this data?
- [ ] **Reference Fields:** Do other systems need to see this data (read-only or updatable)?
- [ ] **Sync Strategy:** Am I clear on one-way vs two-way vs event-triggered sync?
- [ ] **Conflict Resolution:** If two-way, do I have a conflict resolution strategy?

### Implementation Readiness
- [ ] **Resource Plan:** Do I have budget/team to implement this model?
- [ ] **Timeline:** Is my implementation timeline compatible with architecture (Cross-Cloud is longer)?
- [ ] **Maintenance:** Do I have operational capability to maintain this (data sync, connectors, sync delays)?
- [ ] **Documentation:** Will I document data ownership and sync flows for team?

---

## Anti-Patterns to Avoid

🚨 **Red flags – stop if you see:**

| Anti-Pattern | Why It's Wrong | Fix |
|-------------|-----------------|-----|
| Building email nurture in Salesforce Flow | Email at scale fails; Flows not optimized | Use MCAE Engagement Studio |
| Using Salesforce email for high-volume sends | Strict rate limits; poor deliverability | Use MCAE instead |
| MCAE managing Lead assignment | MCAE can't access lead routing; no queue mgmt | Use Salesforce Lead Assignment Rules |
| Complex multi-object logic in Engagement Studio | ES can't access non-prospect objects | Use Salesforce Flow; have ES trigger it |
| Not syncing prospect score to Lead | Sales can't see MQL status | Use Connector to sync score field |
| Two-way sync without conflict strategy | Data corruption; sync loops | Define source system; use one-way sync |
| Storing all prospect data in Salesforce | Violates prospect/lead distinction; costs $ | Keep prospect records in MCAE; sync strategically |
| Engagement Studio trying to create Tasks | ES has limited native integration | Use Automation Rule → Connector → Flow |

---

## Related Documentation

📖 **Core References:**

- **[marketing-architecture-decision-matrix.md](../../../Salesforce%20Marketing%20Ecosystem%20Advisor/marketing-architecture-decision-matrix.md)** – Detailed decision tables, 30+ scenarios, feature comparisons
- **[decision_framework.md](../../../Salesforce%20Marketing%20Ecosystem%20Advisor/decision_framework.md)** – Business scenario examples (lead nurturing, ABM, events)
- **MCAE Skill Files:**
  - `mcae-functional-consultant/SKILL.md` – Forms, dynamic lists, custom fields, completion actions
  - `mcae-solution-architect/SKILL.md` – Score-based lead qualification, handoff workflows
- **Salesforce Flow Documentation** – [Salesforce Help](https://help.salesforce.com/s/articleView?id=sf.flow_concepts_create_configure.htm)

---

## Example: Decision Workflow in Action

**Scenario: "We want to nurture 50,000 prospects with a 10-email series, score them, and hand off leads at 100 points."**

### Step 1: Business Requirement
```
- Use Case: Multi-step nurture + auto-qualification
- Audience: Prospects (50k, not in Salesforce)
- Success: High email delivery, real-time scoring, automatic CRM handoff
```

### Step 2: Platform Decision
```
- Targets: Prospects only ✅ → MCAE capable
- Primary tactic: Email nurturing ✅ → MCAE ideal
- Complexity: Scoring + handoff ✅ → MCAE can do, but also needs CRM
- Sales visibility: "Yes, wants to see when leads qualify" ✅ → Cross-Cloud recommended

DECISION: Cross-Cloud (MCAE owns nurture + scoring; Salesforce owns lead + handoff)
```

### Step 3: Automation Decision
```
- Multi-step email series (10 emails) → Engagement Studio ✅
- Background scoring updates → Engagement Studio rule steps ✅
- Lead creation at threshold → Automation Rule + Connector + Flow
- Lead assignment → Salesforce Flow (complex logic) ✅

DECISION:
  1. Engagement Studio: Main nurture program (10 emails, scoring)
  2. Automation Rule: Trigger when score ≥ 100
  3. Salesforce Connector: Sync prospect to Lead
  4. Salesforce Flow: Complex lead assignment logic
```

### Step 4: Data Ownership Decision
```
- Prospect records: MCAE owns ✅
- Prospect score: MCAE owns, synced to Lead ✅
- Lead records: Salesforce owns ✅
- Email engagement: MCAE owns, summary to Salesforce ✅
- Lead assignment: Salesforce owns ✅

SYNC STRATEGY:
  - Prospect score → Lead score (one-way, MCAE source, real-time)
  - Prospect details → Lead (one-time, at handoff)
  - Lead status → Salesforce (never back to MCAE)
  - Email engagement summary → Salesforce (nightly batch)
```

### Step 5: Trade-offs
```
✅ Best email delivery (MCAE optimized)
✅ Best automation flexibility (Cross-Cloud)
✅ Full sales visibility (CRM integrated)
✅ Real-time scoring (MCAE engine)
⚠️ More complex setup (3 tools: ES + Rules + Flow)
⚠️ Data sync maintenance (Connector dependency)
⚠️ 2-3 week implementation (vs 1 week for MCAE-only)

RECOMMENDATION: Proceed → Complexity justified by business value
```

---

## Version & Attribution

**Version:** 1.0  
**Created:** March 2026  
**Based on:** Salesforce Spring '26 Marketing Architecture Best Practices  
**Reference Architecture:** Salesforce Marketing Ecosystem Advisor (multi-platform strategy)
