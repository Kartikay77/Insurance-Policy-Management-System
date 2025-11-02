# Insurance-Policy-Management-System
Mini insurance policy management system simulating policy issuance, renewals, and claims. Includes BRD, SRS, data dictionary, BPMN workflows, RTM, and UAT test cases. Demonstrates requirements gathering, process mapping, SLA-based ticket handling, gap analysis, and business rules validation for BA roles.

# workflow diagram
## BPMN 1: Policy Issuance Workflow
[Customer Onboarding] → (Start Event)
      ↓
[Enter Customer Details]
      ↓
[Validate Eligibility]
      ├─(Invalid Age <18?)─→ [Reject Policy] → (End)
      ↓
[Select Policy Type & Coverage]
      ↓
[Calculate Premium]
      ↓
[Underwriting Review]
      ├─Manual Review Required?─→ [Risk Assessment] → [Approve/Reject]
      ↓
[Generate Policy Number]
      ↓
[Issue Policy Document]
      ↓
[Activate Policy]
      ↓
(End)

Swimlanes
Customer Service Agent
Underwriter
System
Gateways
Eligibility rule check
Underwriting risk-assessment branch
Business Rules
Policy cannot be issued if client is under 18
High-risk profiles trigger manual underwriting

## BPMN 2: Policy Renewal Workflow
[Policy Expiry Timer Event (-30 days)]
      ↓
[Send Renewal Reminder]
      ↓
[Customer Accepts Renewal?]
      ├─No→[Policy Expires]→(End)
      ↓
[Recalculate Premium]
      ↓
[Payment Collection]
      ↓
[Generate Updated Terms]
      ↓
[Renew Policy]
      ↓
(End)


Gateways
Customer acceptance decision
Rules Applied
Renewal premium increase: +10–20% based on risk profile
Grace period flag enabled if payment delayed
Service Level Indicators
Response SLA: 72 hours
Notification retries: 3 attempts

## BPMN 3: Claims Processing Workflow
(Start)
  ↓
[Submit Claim + Evidence]
  ↓
[Verify Policy Status]
  ├─Expired?→[Reject Claim]→(End)
  ↓
[Validate Documentation]
  │
  ├─Incomplete?→[Request Additional Info]→return back
  ↓
[Coverage Check]
  ├─Coverage Limit Exceeded?→[Auto-Escalation]→[Manager Review]
  ↓
[Fraud Flags?]
  ├─Yes→[Investigate Claim]→decision
  ↓
[Adjuster Review]
  ├─Approve→[Calculate Payout]→[Trigger Payment]→(End)
  ├─Reject→[Communicate Decision]→(End)


Swimlanes
Customer Portal
Claims Adjuster
Risk/Fraud Team
System

## BPMN 3: Claims Processing Workflow
(Start)
  ↓
[Submit Claim + Evidence]
  ↓
[Verify Policy Status]
       ├─ Expired? → [Reject Claim] → (End)
  ↓
[Validate Documentation]
       ├─ Incomplete? → [Request Additional Info] → (Loop back)
  ↓
[Coverage Check]
       ├─ Limit Exceeded? → [Auto-Escalate to Manager Review]
  ↓
[Fraud Flags Detected?]
       ├─ Yes → [Investigate Claim] → Decision
  ↓
[Adjuster Review]
      ├─ Approve → [Calculate Payout] → [Trigger Payment] → (End)
      ├─ Reject  → [Communicate Decision] → (End)


Swimlanes
Customer Portal
Claims Adjuster
Risk/Fraud Team
System
Escalation Conditions
High-value claims
Fraud-risk scoring threshold exceeded
Loops
Documentation completeness loop until all evidence submitted

## BA Concepts Demonstrated
| BA Concept                | Demonstrated via                           |
| ------------------------- | ------------------------------------------ |
| Requirements Gathering    | Eligibility, premium rules, fraud logic    |
| Process Mapping           | BPMN workflows & decisioning               |
| SLA-based Handling        | Renewal response windows, reminder retries |
| Gap Analysis              | Manual vs automated underwriting           |
| Business Rules Validation | Age checks, coverage limitations           |
| Traceability              | Decision gateways map to requirements      |
