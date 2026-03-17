# Salesforce Marketing Ecosystem: Decision Framework

**Plattformübergreifende Lösungen - Entscheidungskriterien**

Basierend auf Salesforce Official Documentation (Sales_Core, Extend_Click_Automate, Cross-Cloud Products)

---

## 🎯 Quick Decision Matrix

Beantworte diese 3 Fragen, um die richtige Lösung zu finden:

| Frage | MCAE | Core | Cross-Cloud |
|-------|------|------|-----------|
| **Wer sind meine Zielgruppen?** | Prospects (vor CRM-Übergabe) | Leads/Contacts (in Salesforce) | Beides (Prospect → Lead Pipeline) |
| **Was ist meine primäre Aktion?** | Email Nurturing, Scoring, Segmentation | System Automation (Flows, Tasks) | Journey → CRM Handoff |
| **Wieviele Touchpoints?** | Multi-Step (5-20+ Emails) | Einfache/Komplexe Automation | Multi-Channel (Email + SMS + Workflows) |
| **Brauche ich ROI-Tracking?** | Teilweise (Score-basiert) | Voll (Campaign Influence) | Voll (beide kombiniert) |

---

## 📋 Entscheidungselemente nach Szenario

### Szenario 1: Lead Nurturing & Scoring

**Business Case:** "Wir wollen Prospects automatisch nurture, nach Score qualifizieren und an Sales übergeben."

#### ✅ MCAE-only Lösung
**Wann gut:**
- Targets sind **nicht in Salesforce** (reine Prospect DB)
- Score-basierte Qualifikation reicht aus
- Vereinfachte CRM-Übergabe akzeptabel

**Komponenten:**
- **Custom Fields:** Lead Score, Lead Grade, Engagement Level (Picklist)
- **Forms:** Landing Page Forms mit +10-20 Punkt Completion Actions
- **Engagement Studio:** Multi-Step Program mit Score-basierten Rule Steps
  - Trigger: Email Open → +5 Punkte
  - Rule: Score ≥ 50 → Send "Mid-Level Content"
  - Rule: Score ≥ 100 → Assign to User + Add to List
- **Dynamic Lists:** Segmente nach Score-Ranges (0-50, 50-100, ≥100)
- **Salesforce Connector:** Sync Prospects ≥ 100 Score als Leads

**Pros:**
- ✅ Schnell implementierbar (MCAE-Admin, kein Coding)
- ✅ Niedrige Komplexität
- ✅ Gute Email-Performance (MCAE-optimiert)
- ✅ Bessere Deliverability als Salesforce Email

**Cons:**
- ❌ Limited Automation (nur Engagement Studio-Logic)
- ❌ Keine Custom Fields in Rules (nur Standard Prospects)
- ❌ Score-Decay manuell (kein Auto-Reset)
- ❌ Wenig Pipeline-Visibilität in Salesforce

**ROI Tracking:** Campaign-Level via MCAE Reports (nicht Opportunity-linked)

---

#### ✅ Salesforce Core-only Lösung
**Wann gut:**
- Alle Contacts/Leads bereits in **Salesforce** existieren
- Complex Automation benötigt (nicht nur Email)
- Full CRM-Integration wichtig

**Komponenten:**
- **Lead/Contact Setup:** Custom Fields (Score, Grade, Status)
- **Campaign:** Salesforce Campaign mit Campaign Member Statuses
- **Flow (Record-Triggered):** 
  ```
  Trigger: Lead updated (Score field changes)
  IF Score >= 100:
    - Assign to Sales User
    - Create Task: "Follow up with lead"
    - Update Campaign Member Status
    - Notify Sales Manager
  ```
- **Process Builder / Flow:** Score-Updates basierend auf:
  - Opportunity created: +100 Score
  - Form submission: +20 Score
  - Manual adjustment: -50 Score
- **Campaign Influence:** Track which campaigns impact closed deals
  - Primary Campaign Source Model (100% to one campaign)
  - OR Custom Model (manual attribution to multiple campaigns)
- **Reports:** Campaign Revenue Report, Campaign ROI Analysis

**Pros:**
- ✅ Complex Automation möglich (Flows, Tasks, API calls)
- ✅ Full CRM Integration (Leads, Contacts, Opportunities)
- ✅ Campaign Influence & Multi-Touch Attribution
- ✅ Salesforce-native (Admin-freundlich für Sales)
- ✅ Lead Assignment Rules (auto-routing)

**Cons:**
- ❌ Email Delivery schlecht (nicht optimiert)
- ❌ Email Scale-Limits (Salesforce hat strikte Rate-Limits)
- ❌ No Advanced Segmentation (nur Campaign + Lists/Reports)
- ❌ Prospect vs. Lead Confusion (2 separate objects)

**ROI Tracking:** Full Pipeline (Lead → Opportunity → Won Deal)

---

#### ✅ Cross-Cloud Lösung (EMPFOHLEN)
**Wann gut:**
- Full Customer Journey wichtig (Prospect → Lead → Opportunity)
- Email + System Automation beide benötigt
- Best-of-both-worlds Performance

**Komponenten:**

**MCAE Side:**
- **Engagement Studio:** Nurture Program (Score ≥ 75 = Marketing Qualified)
  - Score-based Rules (Email, Scoring, List Management)
  - Prospect → Lead Handoff Logic

**Salesforce Core Side:**
- **Campaign:** Linked via Distributed Marketing to MCAE Journey
  - Campaign Members track MCAE sends
  - Campaign Influence measures downstream impact
  
**Cross-Cloud Connectors:**
- **Salesforce Connector:** Auto-sync Prospects ≥ 100 Score → Lead
- **Distributed Marketing:** Link MCAE Campaign to Sales Cloud Campaign
  - Sales reps can see MCAE journey metrics in Salesforce
  - Quick Send: Sales reps send MCAE content directly from Salesforce

**Automation Flow (optional):**
```
Trigger: Prospect Score reaches 100
Actions:
  1. Get/Create Salesforce Lead
  2. Update Lead: Score = Prospect Score
  3. Assign to Sales User
  4. Add to Salesforce Campaign
  5. Create Task in Salesforce
  6. Add to List: "Sales Handoff"
```

**Pros:**
- ✅ Best email delivery (MCAE) + Best automation (Core)
- ✅ Full pipeline visibility (MCAE metrics + SF Analytics)
- ✅ Sales team can engage with MCAE content
- ✅ Campaign Influence + MCAE engagement history = complete attribution
- ✅ Score is source of truth (MCAE), Opportunity is destination

**Cons:**
- ⚠️ More Complex setup (requires MCAE + Salesforce Connector + Distributed Marketing)
- ⚠️ Data sync latency (Prospects → Leads not instant)
- ⚠️ Needs clear handoff rules (at what score?)

**ROI Tracking:** MCAE Score Stages + Salesforce Campaign Influence (multi-touch)

---

### Szenario 2: Account-Based Marketing (ABM)

**Business Case:** "Wir wollen 10 Target Accounts auf Buyer Committee Level tracken und koordiniert nurture."

#### ✅ MCAE-only Lösung
**Wenn:** Budget-Budget, kleine ABM Program (< 50 Accounts)

**Komponenten:**
- **Company Score:** Custom field on prospect (company_score__c)
- **Engagement Studio:** Multi-prospect logic
  - Track ALL prospects from target company
  - Aggregate score: SUM of all prospects at company
- **Dynamic List:** "ABM Hot Accounts" - company_score ≥ 500
- **Form Tracking:** Identify all buying stakeholders via forms
- **Email:** Coordinated sends (all stakeholders get same email theme)

**Pros:** Simple, no Sales involvement needed yet
**Cons:** Limited insight into Account health; no unified sales view

---

#### ✅ Salesforce Core-only Lösung
**Wenn:** ABM im Sales Focus (Account Executive führt ABM)

**Komponenten:**
- **Account Object:** Target Account list
- **Opportunity Contact Roles:** Multiple decision makers
- **Campaign:** ABM Campaign per account + stakeholder emails
- **Flow:** Auto-detect new contacts at target account + assign to Account Executive
- **Campaign Influence:** Custom model to track which campaigns influenced deal

**Pros:** Sales team controls; Opportunity-linked
**Cons:** Email scale issues; MCAE insights lost

---

#### ✅ Cross-Cloud Lösung (EMPFOHLEN)
**Komponenten:**
- **MCAE:** Score all prospects per company (company_score_c)
- **Engagement Studio:** "High-Value Account" Program triggered when company_score ≥ 500
- **Distributed Marketing:** Campaigns linked to journeys; Sales reps can see prospect engagement history
- **Salesforce Campaign:** ABM Campaign tracks all account-level metrics
- **Flow:** When company_score ≥ 500
  - Alert Account Executive
  - Create ABM Task in Salesforce
  - Add all prospects to "Alert – Hot Account" List in MCAE

**Result:** Sales sees "Account Momentum" via MCAE engagement + Campaign metrics

---

### Szenario 3: Event Management (Webinar/Conference)

**Business Case:** "Registration → Pre-Event Nurture → Event → Post-Event Follow-up + ROI"

#### ✅ MCAE-only
Form-submit → Email series → Score increment → Prospect list export to event platform

#### ✅ Salesforce Core-only
Campaign → Lead records → Event attendance tracked → Opportunity creation

#### ✅ Cross-Cloud (EMPFOHLEN)
1. **Registration:** MCAE Form → Completion Action: Score +50
2. **Pre-Event:** MCAE Engagement Studio 3-email series → Attendee confirmation
3. **Event Day:** Attendee list uploaded to event platform
4. **Post-Event:** 
   - MCAE: Thank you email, feedback form, score +100
   - Salesforce: Import attendance list, create Leads, add to Campaign, assign to Sales
5. **ROI:** 
   - MCAE metrics: Email engagement, form submissions, score distribution
   - Salesforce metrics: Leads created, Opportunities influenced, Revenue sourced (Campaign Influence)

---

## 🎓 Decision Criteria Checklist

Use this to pick **MCAE vs. Core vs. Cross-Cloud**:

### Choose MCAE-only if:
- [ ] Prospects NOT yet in Salesforce
- [ ] Email nurturing is PRIMARY tactic
- [ ] Score-based qualification sufficient
- [ ] Limited budget / simple automation needs
- [ ] Sales doesn't need deep CRM integration

### Choose Salesforce Core-only if:
- [ ] All Leads/Contacts already in Salesforce
- [ ] Complex system automation (Flows, integrations) needed
- [ ] Campaign Influence is critical metric
- [ ] Sales team manages their own pipeline
- [ ] Limited email volume (< 100k/month)

### Choose Cross-Cloud if:
- [ ] FULL customer journey required (Prospect → Lead → Opportunity)
- [ ] BOTH email nurturing + complex automation needed
- [ ] ROI tracking is critical (multi-touch attribution)
- [ ] Sales wants visibility into MCAE engagement
- [ ] Budget/complexity acceptable for best-of-both

---

## 📊 Feature Comparison

### Email: MCAE vs. Salesforce

| Feature | MCAE | Salesforce |
|---------|------|-----------|
| Deliverability | ⭐⭐⭐⭐⭐ (optimized) | ⭐⭐ (limited infra) |
| List Segmentation | ⭐⭐⭐⭐⭐ (dynamic) | ⭐⭐⭐ (lists/campaigns) |
| A/B Testing | ⭐⭐⭐⭐ | ⭐ (manual) |
| Personalization | ⭐⭐⭐⭐⭐ (AMPscript) | ⭐⭐ (merge fields) |
| Volume/Hour | ⭐⭐⭐⭐⭐ (1000s) | ⭐⭐ (limited) |
| Bounce Handling | ⭐⭐⭐⭐⭐ | ⭐⭐ |

### Automation: MCAE vs. Salesforce

| Feature | MCAE | Salesforce |
|---------|------|-----------|
| Engagement Studio | ⭐⭐⭐⭐⭐ | ❌ |
| Flows/Workflows | ⭐⭐ (limited) | ⭐⭐⭐⭐⭐ |
| Multi-Step Logic | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| External Integrations | ⭐⭐⭐ | ⭐⭐⭐⭐ |
| API/Webhooks | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| Lead Assignment | ⭐⭐ | ⭐⭐⭐⭐⭐ |

### Analytics/ROI: MCAE vs. Salesforce

| Feature | MCAE | Salesforce |
|---------|------|-----------|
| Engagement Reports | ⭐⭐⭐⭐⭐ | ⭐⭐ |
| Campaign Influence | ⭐ | ⭐⭐⭐⭐⭐ |
| Multi-Touch Attribution | ⭐ | ⭐⭐⭐⭐ |
| Revenue Attribution | ❌ | ⭐⭐⭐⭐⭐ |
| Prospect Velocity | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |

---

## 🚀 Next Steps

1. **Pick a Szenario** (Lead Nurturing, ABM, Event, etc.)
2. **Answer the 3 Quick Questions** (above)
3. **Use this Framework** to decide MCAE / Core / Cross
4. **Check Feature Comparison** (email, automation, analytics)
5. **Review Scenario Deep-Dive** (pros/cons, components, ROI)
6. **Build it step-by-step** (implementation guides in reference files)

---

**Version:** 1.0 | **Based on:** Salesforce Spring '26 Official Documentation
