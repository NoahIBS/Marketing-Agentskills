# Decision Framework - Content Coverage & Gaps Analysis

**Datum:** 15. März 2026  
**Ziel:** Vollständige Analyse, welche Informationen verfügbar sind und was fehlt für ein funktionierendes Entscheidungswerkzeug

---

## 📊 TEIL 1: WAS IST VORHANDEN (Coverage Analysis)

### A. Verfügbare Dateien (In 2 Ordnern)

#### Salesforce Marketing Ecosystem Advisor/ (4 Dateien)
1. ✅ **decision_framework.md** - MAIN TARGET (Das Tool selbst)
2. ✅ **sales_core.md** - Campaign, Lead/Contact, Campaign Influence, ROI
3. ✅ **extend_click_automate.md** - Flow Types, Decision Elements, Orchestration, Flow Limits
4. ✅ **mc_cross-cloud_products.md** - Distributed Marketing, Journey Builder, Campaign Connect

#### MCAE/ (16 Dateien)
1. ✅ **Account Engagement Setup.md** - AppExchange Install, Business Unit, Connector, User Sync
2. ✅ **Engagement Studio.md** - Program Steps, Triggers, Rules, Actions, Wait Periods, Limits
3. ✅ **Automate_Business.md** - Flow types, Orchestration, Approval Processes, Flow Limits
4. ✅ **pardot_sf_connector_setup_implementation_guide.md** - Connector v1 & v2, Field Mapping, Sync Logic
5. ✅ **pardot_b2bma_implementation_guide.md** - B2B Marketing Analytics, Dashboards, Datasets
6. ✅ **pardot_einstein_implementation_guide.md** - Einstein Scoring, LeadScoring
7. ✅ **pardot_engagement_studio_implementation_guide-2.md** - ES Programs, Versioning, Best Practices
8. ✅ **Implementation Guide.md** - Enhanced Landing Pages
9. ✅ **Implementation Guide: Email.md** - Email Setup & Configuration
10. ✅ **Account Engagement Lightning.md** - Lightning App UI, Lightning App Features
11. ✅ **Account Engagement: Data.md** - Data Architecture, Objects, Fields
12. ✅ **Engagement History.md** - Activity Tracking, History Dashboard
13. ✅ **Account Engagement Sandbox.md** - Sandbox Setup & Testing
14. ✅ **Upgrade Account Engagement.md** - Versioning, Upgrades
15. ✅ **Marketing Cloud Advertising.md** - Advertising Integration
16. ✅ **Financial Services Cloud.md** - FSC Specific Features

#### Additional Context (Related Skills - not directly analyzed)
- .github/skills/mcae-solution-architect/SKILL.md
- .github/skills/mcae-functional-consultant/SKILL.md
- Various reference guides in each skill folder

---

## 📋 TEIL 2: WHAT IS COVERED BY TOPIC

### Topic 1: MCAE vs. Salesforce Core Comparison
**Status:** ✅ **70% COVERED**

✅ **Vorhanden:**
- Email capabilities (MCAE: deliverability, segmentation, personalization vs. Salesforce: limited)
- Automation types (MCAE: Engagement Studio vs. Salesforce: Flows)
- Lead scoring (MCAE: native scoring with Rules vs. Salesforce: custom formula)
- Analytics (MCAE: engagement reports vs. Salesforce: campaign influence)
- MCAE Prospects vs. Salesforce Leads/Contacts distinction

❌ **Teilweise/Fehler:**
- Edition-based limits (Growth/Plus/Advanced/Premium) - erwähnt in decide_framework aber nicht umfassend
- Feature availability nach Edition - fehlt systematische Übersicht
- Pricing/Lizenzierung - nicht berücksichtigt
- Compliance/Data Security unterschiede - nicht erwähnt

---

### Topic 2: Cross-Cloud Architecture
**Status:** ✅ **60% COVERED**

✅ **Vorhanden:**
- Salesforce Connector architecture (v1 & v2 unterschiede)
- Field mapping (Lead → Contact auto-conversion)
- Sync timing (all 2 minutes möglich)
- Distributed Marketing workflows (Campaign Send vs. Quick Send)
- Journey Builder integration with connected campaigns
- Multi-touch attribution via Campaign Influence

❌ **Fehlendes:**
- Real-time sync vs. batch sync trade-offs - nicht detailliert
- Sync latency impact on decision-making - nicht behandelt
- Error handling & sync failure recovery - nicht erwähnt
- Duplicate prospect matching logic - nur oberflächlich
- Data quality issues (invalid emails, duplicates) - nicht behandelt
- Cost implications of cross-cloud syncing - nicht erwähnt

---

### Topic 3: Lead Nurturing & Scoring Scenario
**Status:** ✅ **75% COVERED**

✅ **Vorhanden (aus decision_framework.md):**
- MCAE-only: Form → Completion Actions → Engagement Studio → Dynamic Lists → Connector Sync
- Core-only: Campaign → Flow → Lead Assignment → Task Creation → Campaign Influence
- Cross-Cloud: MCAE + Distributed Marketing + Salesforce Campaign + Flow automation

✅ **Detaillierter Info in anderen Dateien:**
- Engagement Studio step types (sales_core.md, Engagement Studio.md)
- Flow trigger types (extend_click_automate.md, Automate_Business.md)
- Campaign Influence models (sales_core.md)

❌ **Fehlendes Kontext:**
- Score decay/reset policies - nicht dokumentiert detailliert
- Score ranges interpretation (0-50 vs 50-100) - Best practices fehlen
- When to re-engage old prospects - nicht erwähnt
- Unsubscribe/opt-out handling in scoring - nicht behandelt
- Integration with sales waterfall/pipeline stages - nicht detailliert
- Lead scoring best practices overview - nicht vorhanden

---

### Topic 4: Account-Based Marketing (ABM) Scenario
**Status:** ✅ **50% COVERED**

✅ **Vorhanden (aus decision_framework.md):**
- MCAE-only: Company Score → Engagement Studio aggregation → Dynamic Lists
- Core-only: Account Object → Opportunity Contact Roles → Campaign → Flow
- Cross-Cloud: MCAE company scoring + Engagement Studio + Distributed Marketing + SF Campaign + Flow

❌ **Kritisch Fehlendes:**
- Named account selection criteria - nicht behandelt
- Account hierarchy handling (Parent/Child) - nicht documented
- Multi-persona buying committee orchestration - nicht erwähnt
- Account engagement scoring aggregation logic - nicht detailliert
- Cross-account influence tracking - nicht behandelt
- Account health scoring - nicht erwähnt (vs. prospect scoring)
- Firmographic data integration - nicht behandelt

---

### Topic 5: Event Management Scenario
**Status:** ✅ **40% COVERED**

✅ **Vorhanden (aus decision_framework.md):**
- MCAE-only: Form registration → Email series → Score increment → Export
- Core-only: Campaign → Lead creation → Event attendance tracking
- Cross-Cloud: Registration + nurture + attendance + import + assignment

❌ **Kritisch Fehlendes:**
- Event registration workflows - keine detaillierte Anleitung
- Attendee vs. Non-attendee follow-up branching - nicht behandelt
- Post-event engagement cadence - nicht dokumentiert
- Event ROI calculation - nicht detailliert (nur kurzer Verweis)
- Webinar platform integration (GoToWebinar, Zoom, Marketo) - nicht erwähnt
- Lead scoring adjustments post-event - nicht behandelt
- Attendee list upload/match logic - nicht documented

---

### Topic 6: Engagement Studio Deep Dive
**Status:** ✅ **85% COVERED**

✅ **In Engagement Studio.md & pardot_engagement_studio_implementation_guide-2.md:**
- Trigger types (Email Open, Link Click, Form, Landing Page, Custom Redirect, File Download)
- Rule types (Score, Grade, List, Campaign, Email Status)
- Action types (Send Email, Adjust Score, Create Task, Add to List)
- Wait periods (maximum, triggers override)
- Program limits (20-200 programs, 10-15 repeating, max 300 steps)
- Versioning (Pausing creates versions)
- Program design patterns (linear, branching)

❌ **Fehlendes:**
- Re-entry logic for repeating programs - erwähnt aber nicht detailliert
- Segment/List management - grundlagen vorhanden aber nicht strategy
- Program performance optimization - nicht vorhanden
- Static list vs. dynamic list in ES context - nicht klar differenziert
- Error handling in programs - nicht behandelt
- Program pause/resume impact - erwähnt aber nicht umfassend

---

### Topic 7: Salesforce Flow Deep Dive
**Status:** ✅ **80% COVERED**

✅ **In extend_click_automate.md & Automate_Business.md:**
- Flow trigger types (Record-triggered, Schedule-triggered, Screen, Autolaunched, Platform Event)
- Decision elements & branching logic
- Orchestration (multi-user, multi-step processes)
- Flow limits (per-transaction, per-org)
- Best practices (batch DML, wait elements for transaction separation)
- Approval processes

❌ **Fehlendes:**
- Flow governor limits in context of bulk operations - kurz erwähnt, nicht detailliert
- Subflow patterns (user context vs. system context) - erwähnt aber nicht praktisch
- Error handling & fault paths - erwähnt aber nicht in decision context
- Asynchronous paths & scheduled paths - nicht behandelt im decision framework
- Flow version management strategy - nicht vorhanden
- Integration with external systems (Webhooks, REST) - nicht behandelt

---

### Topic 8: Campaign Influence & Attribution
**Status:** ✅ **65% COVERED**

✅ **In sales_core.md:**
- Campaign Influence 1.0 vs. Customizable Campaign Influence
- Attribution models (Primary Campaign Source, First-Touch, Even-Distribution, Last-Touch, Custom)
- Multi-touch attribution concept
- Campaign metrics (Budgeted Cost, Actual Cost, Revenue)
- ROI calculation formula

❌ **Fehlendes:**
- B2B Marketing Analytics Multi-Touch Attribution dashboard - nur oberflächlich erwähnt
- Campaign Influence vs. B2BMA attribution differences - nicht erläutert
- Influence model selection criteria - nicht dokumentiert
- Handling long sales cycles (>6 months) - nicht treated
- E-Signature/Contract signing as attribution touchpoint - nicht mentioned
- Custom attribution data sources - nicht discussed

---

### Topic 9: B2B Marketing Analytics
**Status:** ✅ **50% COVERED**

✅ **In pardot_b2bma_implementation_guide.md:**
- Dashboard types (Engagement, Pipeline, Marketing Manager, ABM, Multi-Touch Attribution)
- Datasets (pdCampaign, pdEmail, pdForm, pdLandingPage, pdOpportunity, pdProspect, pdVisitor)
- Connected Campaigns setup
- Field-level security configuration
- Permissions & licensing

❌ **Fehlendes aus Decision Framework Perspektive:**
- When to implement B2BMA vs. MCAE reports alone - nicht documented
- B2BMA data refresh latency - nicht treated (nur "alle 24 Stunden" erwähnt)
- Custom lens/dashboard creation - only setup documented, not strategy
- B2BMA vs. standard Salesforce reports trade-offs - not compared
- B2BMA limitations (data row limits, etc.) - erwähnt aber nicht praktisch
- Integration with Einstein Analytics - not treated

---

### Topic 10: Connector & Field Mapping
**Status:** ✅ **75% COVERED**

✅ **In pardot_sf_connector_setup_implementation_guide.md:**
- Connector v1 vs. v2 setup differences
- User assignment mapping (MCAE user → SF user)
- Lead/Contact field mapping rules
- Sync behavior (auto-create leads, match logic)
- Opportunity sync (scoring changes)
- Marketing Data Sharing configuration

❌ **Fehlendes:**
- Best practices for handling field conflicts - not documented
- Custom field mapping patterns - Theory covered, pattern library missing
- What happens to orphaned prospects - nicht treated
- Sync speed optimization - not discussed
- Testing connector before production - not covered
- Connector troubleshooting - not in decision context
- Account syncing (if enabled) - barely mentioned

---

### Topic 11: Edition-Based Feature Matrix
**Status:** ❌ **0% - CRITICAL GAP**

❌ **COMPLETELY MISSING:**
- Growth Edition: 20 programs, 10 repeating, basic features
- Plus Edition: 100 programs, 10 repeating, multi-touch, B2BMA
- Advanced Edition: 200 programs, 10 repeating
- Premium Edition: 200 programs, 15 repeating, B2BMA included
- Feature availability by edition (Orchestration, Einstein, etc.)

**Impact:** Users cannot make decisions about scalability, must check Edition later

---

### Topic 12: Prerequisites & Setup Foundation
**Status:** ❌ **30% - MAJOR GAP**

✅ **Parcially Mentioned:**
- AppExchange installation (in Account Engagement Setup.md)
- Connector requirements (in pardot_sf_connector_setup_implementation_guide.md)
- User Sync setup (in Account Engagement Setup.md)

❌ **NOT IN DECISION CONTEXT:**
- Equipment/Infrastructure requirements
- Pre-implementation checklist
- Data preparation requirements
- Timeline estimates for each solution
- Resource allocation (FTE/hours)
- Training requirements
- Governance/Approval process setup
- Data privacy/compliance preparation

**Impact:** Users can't assess feasibility before starting decision process

---

## 🎯 TEIL 3: WHAT IS COMPLETELY MISSING (Critical Gaps)

### Gap 1: **Implementation Timeline & Effort Estimates**
Currently NOT in any file:
- MCAE-only setup: X hours
- Core-only setup: Y hours
- Cross-Cloud setup: Z hours
- Per-scenario implementation times

**Why Needed:** Users need to compare not just capabilities but effort required

---

### Gap 2: **Cost Comparison & ROI Modeling**
Currently NOT documented:
- MCAE licensing costs
- Salesforce licensing multipliers
- Integration/consulting costs
- Ongoing maintenance costs
- Total Cost of Ownership (TCO) by solution

**Why Needed:** Budget is often the primary decision factor

---

### Gap 3: **Risk Assessment & Mitigation**
Currently NOT covered:
- MCAE implementation risks (lead quality, sync failures)
- Core implementation risks (flow complexity, governor limits)
- Cross-Cloud risks (latency, data consistency)
- Common failure patterns
- Risk mitigation strategies

**Why Needed:** Risk tolerance drives solution selection

---

### Gap 4: **Real-World Scenario Constraints**
Currently NOT treated:
- Large enterprise (1M+ prospects) constraints
- Small business (< 10k prospects) constraints
- Mid-market specific patterns
- Industry-specific considerations (B2B, B2C, SaaS, Services)
- Multi-subsidiary/Multi-brand scenarios

**Why Needed:** "One size fits all" doesn't apply

---

### Gap 5: **Change Management & Adoption Strategy**
Currently NOT documented:
- Sales team adoption approaches (MCAE vs. Core vs. Cross)
- Marketing ops training requirements
- Executive reporting & stakeholder management
- Process changes required by solution type
- Data governance policy implications

**Why Needed:** Even perfect solution fails if team doesn't adopt it

---

### Gap 6: **Vendor/Tool-Specific Integrations**
Currently NOT covered:
- Webinar platform integrations (Zoom, GoToWebinar, WebEx)
- Email platform options (MCAE vs. Marketing Cloud Email vs. 3rd party)
- CRM add-on integrations (Slack, Teams, Salesforce Mobile)
- Analytics/BI tool connections
- CDP/Data warehouse integration

**Why Needed:** Existing tool stack influences decision

---

### Gap 7: **Performance Benchmarks & KPIs**
Currently NOT documented:
- Expected email open rates by solution
- Lead-to-opportunity conversion expectations
- Sales cycle impact by nurture type
- Attribution accuracy by model
- System performance metrics (latency, throughput)

**Why Needed:** Users need baseline expectations

---

### Gap 8: **Data Migration & Historical Data Handling**
Currently NOT treated:
- Prospect database migration from other systems
- Lead/Contact deduplication strategies
- Historical engagement data import
- Scoring recalculation on existing database
- Data cleanup requirements

**Why Needed:** Greenfield ≠ Migration scenarios

---

### Gap 9: **Compliance & Data Privacy Specific**
Currently NOT documented:
- GDPR implications by solution (MCAE prospect data storage)
- CCPA opt-out handling differences
- SOC 2 / Data security by solution type
- Audit trail requirements
- Data residency options

**Why Needed:** Regulatory requirements drive decisions

---

### Gap 10: **Maintenance & Evolution Costs**
Currently NOT covered:
- Program/Flow maintenance overhead
- Upgrade/versioning strategy
- Skill building/analyst hiring
- Technical debt accumulation
- Scaling challenges after 1-3 years

**Why Needed:** Long-term TCO differs significantly

---

### Gap 11: **Success Metrics & KPI Selection**
Currently NOT documented:
- How to measure MCAE-only success
- How to measure Core-only success
- How to measure Cross-Cloud success
- When to declare a solution "working"
- When/how to pivot to different solution

**Why Needed:** Without clear metrics, organizations drift

---

### Gap 12: **Decision Support Tools**
Currently NOT provided:
- Interactive decision tree/flowchart
- Self-assessment questionnaire
- TCO calculator
- Feature requirement checklist
- Implementation readiness assessment

**Why Needed:** Framework is conceptual; tool should be operational

---

## 📈 TEIL 4: COVERAGE SUMMARY TABLE

| Topic | Coverage | Severity | Notes |
|-------|----------|----------|-------|
| MCAE vs. Core comparison | 70% | 🟡 Medium | Edition limits missing |
| Cross-Cloud architecture | 60% | 🔴 **High** | Sync latency, error handling missing |
| Lead Nurturing scenario | 75% | 🟡 Medium | Score decay policies missing |
| ABM scenario | 50% | 🔴 **High** | Account hierarchy, multi-persona missing |
| Event Management scenario | 40% | 🔴 **High** | Event ROI, attendee logic missing |
| Engagement Studio | 85% | 🟢 Low | Re-entry logic could be clearer |
| Salesforce Flow | 80% | 🟢 Low | Governor limits could be more practical |
| Campaign Influence | 65% | 🟡 Medium | B2BMA comparison missing |
| B2B Marketing Analytics | 50% | 🟡 Medium | When to use not documented |
| Connector & Mapping | 75% | 🟡 Medium | Troubleshooting missing |
| **Edition-Based Features** | **0%** | **🔴 CRITICAL** | **Completely missing** |
| **Prerequisites & Setup** | **30%** | **🔴 CRITICAL** | **Effort estimates missing** |
| Implementation Timeline | 0% | 🔴 CRITICAL | Completely missing |
| Cost/ROI Modeling | 0% | 🔴 CRITICAL | Completely missing |
| Risk Assessment | 0% | 🔴 CRITICAL | Completely missing |
| Real-World Constraints | 0% | 🔴 CRITICAL | Completely missing |
| Change Management | 0% | 🔴 CRITICAL | Completely missing |
| Tool Integrations | 0% | 🔴 CRITICAL | Completely missing |
| Performance Benchmarks | 0% | 🔴 CRITICAL | Completely missing |
| Data Migration | 0% | 🔴 CRITICAL | Completely missing |
| Compliance/Privacy | 0% | 🔴 CRITICAL | Completely missing |
| Maintenance/Evolution | 0% | 🔴 CRITICAL | Completely missing |
| Success Metrics | 0% | 🔴 CRITICAL | Completely missing |
| Decision Support Tools | 0% | 🔴 CRITICAL | Completely missing |

---

## 🎯 SUMMARY

**Total Coverage:** ~45% of what's needed for a complete decision framework

**Available information sufficient for:** 
- High-level capability comparison
- Scenario walkthrough (at macro level)
- Feature checklist

**Missing for real-world decision-making:**
- Practical constraints & trade-offs
- Cost/effort/risk assessment
- Implementation timeline & resource planning
- Ongoing maintenance & evolution paths
- Success metrics & measurement
- Vendor ecosystem & integration options
- Industry/size-specific guidance
- Compliance & governance implications

---

## 🚀 RECOMMENDED NEXT STEPS

To make decision_framework.md a **fully functional tool**, add:

1. **Edition-based feature matrix** (10 minutes work, highest impact)
2. **Setup effort estimates** (per scenario: Quick/Medium/Complex)
3. **Implementation checklist** (prerequisites, timeline)
4. **Cost implications** (licensing, consulting, ongoing)
5. **Risk matrix** (per solution type: High/Medium/Low risks)
6. **Real-world constraint scenarios** (SMB, Mid-Market, Enterprise)
7. **Success metrics template** (what success looks like)
8. **Tool/integration reference** (common stack patterns)

