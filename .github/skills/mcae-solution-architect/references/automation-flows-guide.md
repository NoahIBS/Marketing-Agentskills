# Salesforce Flows for MCAE Score-Based Automation

## When to Use Flows (Beyond Engagement Studio)

Engagement Studio handles most nurture workflows. Use **Salesforce Flows** when:

1. **Score changes should trigger immediate actions** (not just for future prospects)
2. **Complex logic** beyond 5 conditions needed
3. **External system integration** required (API callouts, third-party webhooks)
4. **Batch operations** on existing prospects (e.g., recalculate all prospects with certain criteria)
5. **Auto-creation/update of Salesforce records** based on score thresholds

## Flow Types for MCAE

### 1. Record-Triggered Flows
**Trigger**: When a prospect record is created or updated

**Use Case**: Auto-sync qualified prospects to Salesforce CRM when score crosses threshold

```
Trigger: Prospect - After Update
Condition: NEW score ≥ 100 AND OLD score < 100
          (prospect just became sales-qualified)

Actions:
  Decision: Is there a Salesforce Lead for this prospect?
    Yes → Update Lead (set Status = "Sales Qualified")
    No → Create Lead (populate from prospect fields)
         Send Email to Sales Manager
         Create Task: "Follow up with new SQL"
```

### 2. Schedule-Triggered Flows
**Trigger**: Runs on a schedule (daily, weekly, monthly)

**Use Case**: Regular batch scoring adjustments or bulk status updates

```
Schedule: Daily at 9 AM
Batch: All prospects where Score is null

Actions:
  For each prospect:
    Calculate engagement score from email opens + form submissions
    Update Score field
```

### 3. Decision Element
Evaluate conditions on score or other prospect attributes

```
Decision: Is this a sales-qualified prospect?
Condition: score ≥ 100 AND company ≠ null AND lead_status = null

Output:
  SQL (Yes) → Create Salesforce Lead
  MQL (No, but score ≥ 85) → Add to Salesforce Campaign
  Cold (No, score < 85) → Continue nurturing
```

## Key Flow Elements for Score-Based Workflows

### Get Records
Retrieve prospect records matching criteria before taking action

```
Get Prospects:
  Where score >= 85 AND assigned_user IS NULL
  
Output: List of prospects ready for assignment
```

### Update Records
Modify prospect field values based on score thresholds

```
Update Prospect:
  Set status = "Marketing Qualified" if score ≥ 85
  Set assigned_user = [Available Sales Rep] if score ≥ 100
```

### Create Records
Auto-create Salesforce records when MCAE prospects become sales-ready

```
Create Salesforce Lead:
  First Name = Prospect.first_name
  Last Name = Prospect.last_name
  Company = Prospect.company
  Lead Status = "SQL" (if prospect.score ≥ 100)
  Phone = Prospect.phone
```

### Email Alert/Notification
Send structured alerts when score milestones are reached

```
Send Email:
  To: Sales Manager
  Subject: New Sales-Qualified Prospect
  Body: {Prospect.Name} reached score {Prospect.Score}
        Click here to assign to sales rep
```

## Example: Complete Score-Based Flow

**Scenario**: When a prospect's score exceeds 100, auto-create a Salesforce Lead and notify the sales manager.

```yaml
Flow Name: Score_Based_Lead_Creation
Trigger: Prospect - Record Triggered (After Update)
Trigger Condition:
  - Prospect.Score >= 100
  - Prospect.SalesforceLeadId__c IS NULL

Elements:
  1. Get Records: Query Salesforce Lead by Email
     Conditions: Email = triggering prospect email
     
  2. Decision: Does a Lead already exist?
     Yes → Go to "Notify Manager" (don't create duplicate)
     No → Continue to "Create Lead"
     
  3. Create Records: Create Salesforce Lead
     Field Values:
       - FirstName = {!prospectFirstName}
       - LastName = {!prospectLastName}
       - Company = {!prospectCompany}
       - Phone = {!prospectPhone}
       - LeadSource = "Marketing Cloud Account Engagement"
       - Status = "SQL"
     
  4. Update Records: Update original prospect
     Set SalesforceLeadId__c = [newly created Lead ID]
     Set LastSyncDate__c = TODAY()
     
  5. Send Email Alert: Notify Sales Manager
     To: {!SalesManagerEmail}
     Template: New SQL notification
     Record ID: [newly created Lead]
```

## Connector Configuration

The **Salesforce Connector** (not a flow, but configuration) handles ongoing sync:

- MCAE prospects with `Score >= [configured threshold]` sync to Salesforce as Leads
- Updates to prospect score sync back to Salesforce Lead
- Opportunity creation in MCAE can auto-trigger opportunity creation in SF

**When to use Flow instead of Connector**:
- Connector syncs continuously; Flow gives you precise control over *when* sync happens
- Connector follows standard field mapping; Flow allows custom transformations
- Flow can call external APIs or trigger downstream systems

## Best Practices

1. **Avoid Flow-Engagement Studio Overlap**: 
   - Engagement Studio for nurture workflows (emails, assignments, wait periods)
   - Flows for integration and one-time bulk operations
   
2. **Use Safe Updates**:
   - Check if Salesforce Lead exists before creating (avoid duplicates)
   - Use prospect email as unique key for lookups
   
3. **Error Handling**:
   - Add fault paths if API callouts fail
   - Log errors for admin review
   
4. **Performance**:
   - Batch operations; avoid triggering a flow for every single record update
   - Use schedule-triggered flows for bulk recalculations (nightly)
   
5. **Testing**:
   - Test flows in Sandbox first
   - Use flow debug feature to trace execution
   - Verify field mappings before going live
