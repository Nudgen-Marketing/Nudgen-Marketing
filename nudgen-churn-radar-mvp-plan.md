# Nudgen Churn Radar MVP Plan

## 1. Product Direction

Build **Nudgen Churn Radar**: a lightweight early churn alert product on top of Nudgen that detects customers likely to disengage soon and automatically creates the right save campaign before they fully churn.

### Core Positioning

> **Nudgen Churn Radar helps small SaaS and growing businesses detect churn risk early, understand why each customer is slipping away, and launch personalized retention emails automatically.**

This fits Nudgen better than becoming a heavy customer success platform.

Nudgen already focuses on retention email automation, AI-generated copy, audience tags, brand voice, and follow-up that stops when users engage. The churn product should become the **signal layer** before Nudgen’s current **campaign execution layer**.

---

## 2. Competitor Reading

### Flywheel

Flywheel’s positioning is:

> **Stop Losing Users To Preventable Churn**

They focus on predicting churn before obvious signs and saving users automatically. Their product appears to include churn probability score, MRR, activation score, lifetime value, automations, alerts, and tasks.

#### What Flywheel seems to focus on

- SaaS companies
- Predictive churn score
- Product usage and activation signals
- Automated save actions
- Customer-level dashboard

#### Opportunity for Nudgen

Flywheel looks more like a SaaS/customer success product. Nudgen can go simpler and more execution-focused:

> **You do not need a customer success team or complex dashboard. Connect your customer data, Nudgen tells you who is at risk, why, and launches the right email sequence.**

---

### ChurnDog

ChurnDog is more revenue recovery and payment-churn focused.

#### What ChurnDog seems to focus on

- Failed payment recovery
- Stripe/payment workflows
- Branded payment update portal
- Billing status dashboard
- Involuntary churn

#### Opportunity for Nudgen

Do not compete head-on with dunning first. Payment recovery is useful, but it is narrower and more infrastructure-heavy.

Nudgen should start with **behavioral churn**, then later add payment churn as one signal.

---

## 3. Best Product Angle

Do **not** build another churn analytics dashboard.

That market is crowded and harder to sell. Dashboards tell users there is a problem, but they still have to decide what to do.

Nudgen’s advantage is action.

The product should be:

> **Early churn alerts + AI-generated retention action.**

Not just:

> **Here is a churn score.**

Better promise:

> **Know who is slipping away, why they are at risk, and what message to send next.**

This connects directly to Nudgen’s current strengths:

- AI drafts
- brand voice
- behavior-driven follow-up
- audience preview
- auto-stop rules

---

## 4. Ideal Customer Profile for MVP

Start with **small B2B SaaS and subscription businesses**, not ecommerce.

### Why SaaS first

- Churn is painful and measurable.
- SaaS teams usually have product events like login, project created, invite sent, feature used.
- They may not have a dedicated customer success team.
- They already understand MRR, churn, activation, trial conversion, and retention.
- Email is still a natural save channel.

### Best first ICP

> **Founder-led SaaS teams from $1k to $50k MRR who know users are dropping off but do not have time to manually monitor usage and write follow-ups.**

Avoid enterprise customer success teams at first. They will expect Salesforce, Gainsight, health scoring, account hierarchy, playbooks, CSM workflows, permissions, and reporting.

That is too heavy for the MVP.

---

## 5. Product Concept

### Nudgen Churn Radar Workflow

1. User connects data source.
2. Nudgen detects churn signals.
3. Nudgen creates risk segments.
4. Nudgen explains why each user/account is at risk.
5. Nudgen recommends a save action.
6. User reviews or auto-launches a retention campaign.
7. Nudgen stops follow-up once user engages.

### Example Alert

```text
23 customers are showing churn risk this week.

8 stopped using the core feature.
6 did not finish onboarding.
5 have not logged in for 14 days.
4 are near renewal but usage dropped.

Launch save campaigns?
```

---

## 6. MVP Name

Recommended name:

> **Nudgen Churn Radar**

Other possible names:

- Nudgen Retention Radar
- Nudgen Save Signals
- Nudgen Early Churn Alerts

### Why Churn Radar is best

- Clear
- Easy to understand
- SEO-friendly
- Immediately communicates the product value

---

## 7. MVP Promise

> **Detect at-risk customers and launch personalized save emails before they churn.**

### Sub-header

> Connect customer activity, define churn signals, and let Nudgen create behavior-based retention campaigns that stop when customers come back.

---

## 8. MVP Features

## Feature 1: Event Tracking

Start with three ways to import events.

### Option A: JavaScript Tracking Snippet

For SaaS/web apps.

```html
<script>
  nudgen.identify("user_123", {
    email: "customer@example.com",
    name: "Sarah",
    plan: "Pro",
    mrr: 49
  });

  nudgen.track("project_created");
  nudgen.track("invite_sent");
  nudgen.track("login");
</script>
```

### Option B: Server-side API

For developers.

```bash
curl -X POST https://api.nudgen.net/events \
  -H "Authorization: Bearer NUDGEN_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "userId": "user_123",
    "email": "customer@example.com",
    "event": "login",
    "timestamp": "2026-05-09T10:00:00Z"
  }'
```

### Option C: CSV Upload

For non-technical users.

```csv
email,name,plan,last_login,last_purchase,last_active,renewal_date,mrr
```

For the MVP, CSV upload can be the fastest way to validate the idea.

---

## Feature 2: Churn Signal Builder

Let users define simple rules first.

| Signal | Rule |
|---|---|
| Inactive user | No login in 14 days |
| Onboarding stuck | Signed up but did not complete setup in 3 days |
| Feature drop-off | Used key feature 5 times last week, 0 times this week |
| Trial risk | Trial ends in 3 days but no activation event |
| Renewal risk | Renewal in 14 days and usage dropped 50% |
| High-value risk | MRR above $100 and inactive for 7 days |
| Expansion risk | Team plan but no invite sent after 5 days |

Do not start with complex ML.

Start with rule-based scoring because it is:

- explainable
- fast to build
- easier for customers to trust

---

## Feature 3: Churn Risk Score

Each customer gets a score from 0 to 100.

### Example Scoring

| Risk factor | Points |
|---|---:|
| No login for 14 days | +25 |
| Did not complete onboarding | +30 |
| Usage dropped more than 50% | +25 |
| Trial ending in 3 days | +20 |
| No campaign/email engagement | +10 |
| Open support issue | +15 |
| High MRR account | Multiplier |

### Risk Levels

| Score | Status |
|---:|---|
| 0-29 | Healthy |
| 30-59 | Watch |
| 60-79 | At Risk |
| 80-100 | Critical |

Important: show the reason, not only the score.

Bad:

> Churn risk: 78%

Good:

> Churn risk: High  
> Reason: No login in 12 days, trial ends in 3 days, did not invite team members.

---

## Feature 4: At-risk Customer Inbox

This should be the core dashboard.

| Customer | Risk | Reason | Value | Recommended Action |
|---|---:|---|---:|---|
| Sarah | High | No login 14 days | $49 MRR | Send reactivation email |
| Acme Co | Critical | Renewal soon + usage drop | $299 MRR | Send founder check-in |
| Minh | Medium | Onboarding incomplete | Trial | Send setup help |

Each row should have:

- customer name
- email
- plan/MRR
- risk level
- top 3 risk reasons
- recommended campaign
- button: **Create save campaign**

---

## Feature 5: AI Save Campaign Generator

When a user clicks **Create save campaign**, Nudgen generates a campaign based on the churn reason.

### For onboarding stuck

Subject:

> Need help getting your first result?

Message angle:

> Helpful, supportive, educational.

Campaign:

- Day 1: offer quick setup help
- Day 3: show one simple use case
- Day 6: ask what blocked them

### For inactive paid user

Subject:

> Still want to keep this running?

Message angle:

> Gentle reminder + value recap.

Campaign:

- Day 1: remind them what they can do
- Day 4: share shortcut/tip
- Day 7: offer help or pause option

### For renewal risk

Subject:

> Before your renewal

Message angle:

> Human, transparent, value-focused.

Campaign:

- Day 1: usage/value recap
- Day 3: ask if anything is missing
- Day 6: offer call or support

This is where Nudgen can win.

Competitors may show churn risk. Nudgen should turn risk into ready-to-send personalized messages.

---

## Feature 6: Auto-stop Rules

This should become a major advantage.

For Churn Radar, stop campaigns when:

- user logs back in
- user completes activation event
- user replies
- user clicks CTA
- user renews
- user updates payment
- user unsubscribes
- user books a call

This makes the product feel intelligent and less spammy.

---

## Feature 7: Weekly Churn Alert Email

Send the business owner a weekly summary.

### Example

Subject:

> 18 customers need attention this week

Body:

```text
Your churn radar found 18 at-risk customers.

Critical:
- 3 paid customers inactive for 14+ days
- 2 renewals coming up with usage drop

Medium:
- 7 trial users did not activate
- 6 users opened emails but did not return

Recommended next action:
Launch 3 save campaigns:
1. Trial activation rescue
2. Inactive paid user check-in
3. Renewal risk founder note
```

This can become a strong habit loop.

---

## 9. MVP Integration Priority

## Phase 1: CSV + Manual Rules

Fastest validation.

Users upload:

- customer list
- last active date
- plan
- MRR
- signup date
- renewal date
- key event count

Then Nudgen calculates risk.

Good for demos, early users, and onboarding without engineering friction.

---

## Phase 2: Stripe

Add Stripe after behavioral MVP, not before.

### Why Stripe matters

- MRR
- subscription status
- failed payment
- renewal date
- trial end date
- canceled subscription

ChurnDog focuses heavily here, so Nudgen can use Stripe as a signal but not make it the whole product.

---

## Phase 3: Segment / PostHog / Amplitude

These are powerful for product events.

For early MVP, PostHog is probably the best integration because many indie SaaS and technical founders use it.

---

## Phase 4: Shopify / WooCommerce

Later, if you want to extend beyond SaaS into ecommerce retention.

### Possible ecommerce signals

- no purchase in X days
- abandoned cart
- category interest
- purchase frequency drop
- high-LTV customer inactive

Start with SaaS because **churn alert** is more urgent there.

---

## 10. Data Model

### customers

```ts
Customer {
  id
  workspaceId
  externalId
  email
  name
  plan
  mrr
  status
  createdAt
  lastSeenAt
  metadata
}
```

### events

```ts
Event {
  id
  workspaceId
  customerId
  eventName
  timestamp
  properties
}
```

### churn_signals

```ts
ChurnSignal {
  id
  workspaceId
  name
  description
  ruleType
  ruleConfig
  points
  enabled
}
```

### customer_risk_scores

```ts
CustomerRiskScore {
  id
  workspaceId
  customerId
  score
  level
  reasons
  calculatedAt
}
```

### save_recommendations

```ts
SaveRecommendation {
  id
  workspaceId
  customerId
  riskScoreId
  campaignType
  suggestedSubject
  suggestedAngle
  suggestedSteps
  status
}
```

---

## 11. Risk Scoring MVP Logic

Start with deterministic scoring.

```ts
function calculateRisk(customer, events, rules) {
  let score = 0;
  const reasons = [];

  if (daysSince(customer.lastSeenAt) > 14) {
    score += 25;
    reasons.push("No activity in 14+ days");
  }

  if (
    customer.trialEndsAt &&
    daysUntil(customer.trialEndsAt) <= 3 &&
    !hasEvent(events, "activation_completed")
  ) {
    score += 30;
    reasons.push("Trial ending soon without activation");
  }

  if (usageDropped(events, 0.5)) {
    score += 25;
    reasons.push("Usage dropped more than 50%");
  }

  if (customer.mrr >= 100 && score >= 40) {
    score += 10;
    reasons.push("High-value account");
  }

  return {
    score: Math.min(score, 100),
    level: getRiskLevel(score),
    reasons
  };
}
```

No need for AI prediction first.

Use AI for:

- explanation
- campaign angle
- message personalization
- segment naming
- suggested next best action

This is more reliable than claiming **AI predicts churn** too early.

---

## 12. MVP Screens

## Screen 1: Churn Radar Overview

Cards:

- At-risk customers
- Critical customers
- Revenue at risk
- Campaigns launched
- Customers recovered

Example:

```text
Churn Radar

42 customers at risk
$3,420 revenue at risk
11 critical accounts
7 recovered this month
```

---

## Screen 2: Risk Inbox

Table of customers and reasons.

Primary CTA:

> Create save campaign

Secondary CTA:

> Mark as handled

---

## Screen 3: Signal Settings

Simple templates:

```text
Choose your churn signals:

[ ] No login in 14 days
[ ] Trial ending soon without activation
[ ] Usage dropped 50%
[ ] Renewal coming soon with low activity
[ ] Failed payment
[ ] No response to previous campaign
```

---

## Screen 4: Campaign Recommendation

Show:

- audience
- reason
- generated email sequence
- stop rules
- preview contacts

CTA:

> Launch campaign

---

## Screen 5: Results

Metrics:

- emails sent
- opens
- clicks
- replies
- users returned
- revenue recovered
- campaigns auto-stopped

---

## 13. MVP Campaign Templates

Start with 5 churn playbooks.

## 1. Trial Activation Rescue

Trigger:

- Trial user has not completed activation event
- Trial ends in 1-3 days

Goal:

- Help user reach first value

Email angle:

> Can I help you get this set up?

---

## 2. Inactive Paid User

Trigger:

- Paid user no activity for 14+ days

Goal:

- Bring user back before cancellation

Email angle:

> Still want to get value from this?

---

## 3. Feature Drop-off

Trigger:

- Previously used key feature, then stopped

Goal:

- Understand blocker and remind value

Email angle:

> Noticed you stopped using X. Anything missing?

---

## 4. Renewal Risk

Trigger:

- Renewal date within 14 days
- Usage is low or declining

Goal:

- Save renewal

Email angle:

> Before your renewal, want help getting more value?

---

## 5. Failed Payment Recovery

Trigger:

- Stripe payment failed

Goal:

- Recover involuntary churn

Email angle:

> Quick billing update needed

This overlaps with ChurnDog, but should be a later playbook, not the core wedge.

---

## 14. What Makes Nudgen Different

| Product | Main wedge | Gap |
|---|---|---|
| Flywheel | Predictive churn prevention for SaaS | May feel like a customer success/analytics tool |
| ChurnDog | Failed payment and revenue recovery | More payment/dunning focused |
| Nudgen Churn Radar | Early churn signals + personalized save campaigns | Easier, lighter, built for action |

### Nudgen’s Unique Angle

> **From signal to send.**

Most products stop at:

> This customer is at risk.

Nudgen should continue to:

1. explain why,
2. generate the message,
3. launch the campaign,
4. stop when the user comes back,
5. report recovered revenue.

That is more practical for small teams.

---

## 15. Pricing Idea

## Option A: Add-on Pricing

### Churn Radar Add-on

```text
$29/month

Up to 1,000 tracked customers
Weekly churn alerts
Risk inbox
5 churn playbooks
AI save campaigns
```

### Churn Radar Pro

```text
$79/month

Up to 10,000 tracked customers
Stripe integration
Custom signals
Revenue-at-risk dashboard
Advanced stop rules
```

---

## Option B: Bundle Into Nudgen Plans

| Plan | Churn Radar Access |
|---|---|
| Free / Trial | Manual CSV scan |
| Starter | Basic churn signals |
| Growth | Stripe + event tracking |
| Pro | Custom playbooks + revenue-at-risk |

For early traction, offer:

> **Free churn audit**

User uploads customer CSV, then Nudgen shows:

- how many users are at risk
- estimated revenue at risk
- recommended save campaigns

Then upsell to launch the campaign.

---

## 16. GTM Strategy

## Best Landing Page Headline

> **Find customers before they churn. Win them back with AI.**

Sub-headline:

> Nudgen Churn Radar detects inactive, stuck, and renewal-risk customers, then creates personalized retention campaigns that stop when customers return.

---

## Stronger Version for SaaS Founders

> **Your customers usually churn quietly. Nudgen alerts you before they leave.**

Sub-headline:

> Connect customer activity, spot risk signals, and launch AI-personalized save campaigns in minutes.

---

## Lead Magnet

Create a free tool:

> **Free Churn Risk Scanner**

Upload CSV:

- email
- signup date
- plan
- last active
- renewal date
- MRR

Output:

```text
You have 37 at-risk customers.
Estimated revenue at risk: $2,840/month.
Top churn reason: 21 users have not logged in for 14+ days.
Recommended action: Launch inactive paid user campaign.
```

This fits Nudgen’s current SEO/free-tool strategy.

---

## 17. 6-week MVP Build Plan

## Week 1: Product Foundation

Build:

- Churn Radar page
- CSV upload
- customer import
- last active / trial / MRR fields
- basic customer table

Deliverable:

> User can upload customers and see a customer list.

---

## Week 2: Rule-based Churn Scoring

Build:

- default risk rules
- risk score calculation
- risk reason generation
- risk level labels
- revenue-at-risk calculation

Deliverable:

> User can see who is healthy, watch, at risk, or critical.

---

## Week 3: Risk Inbox

Build:

- risk customer table
- filters by risk level
- filters by reason
- sort by revenue at risk
- customer detail drawer

Deliverable:

> User can review at-risk customers and understand why they are at risk.

---

## Week 4: AI Campaign Recommendation

Build:

- campaign template mapping by churn reason
- AI subject/body generation
- brand voice integration
- preview campaign
- create Nudgen campaign from risk segment

Deliverable:

> User can turn a churn segment into a ready-to-send campaign.

---

## Week 5: Auto-stop and Results

Build:

- stop when click/reply/login/event occurs
- basic recovered-user metric
- campaign result page
- weekly churn summary email

Deliverable:

> User can launch campaigns and see who returned.

---

## Week 6: Stripe Beta

Build:

- Stripe customer import
- subscription status
- failed payment signal
- trial ending signal
- renewal date signal
- MRR sync

Deliverable:

> User can connect Stripe and monitor payment/subscription-related churn risk.

---

## 18. MVP Success Metrics

## Activation

- % users who upload CSV or connect Stripe
- % users who create first churn signal
- % users who generate first save campaign

## Product Value

- number of at-risk customers detected
- revenue at risk identified
- campaigns launched from Churn Radar
- customers who returned after campaign
- recovered MRR

## Business

- free churn scan to signup conversion
- signup to campaign launch conversion
- campaign launch to paid conversion
- retention of Nudgen users who enable Churn Radar vs. those who do not

### Main North Star

> **Recovered customers per workspace per month**

### Secondary Metric

> **Revenue at risk acted on**

---

## 19. What Not To Build In MVP

Avoid these early:

- complex machine learning churn prediction
- full customer success CRM
- account hierarchy
- health score customization like enterprise CS tools
- Slack task workflow
- NPS/survey product
- advanced cohort analytics
- multi-channel outreach beyond email
- payment portal like ChurnDog
- deep BI dashboard

These are useful later, but they slow down validation.

---

## 20. Best MVP Wedge

The fastest wedge is:

> **CSV Churn Scan → AI Save Campaign**

Flow:

1. Upload customer CSV.
2. Nudgen finds churn risk.
3. Nudgen shows revenue at risk.
4. Nudgen generates save campaign.
5. User launches campaign.
6. Nudgen stops when customer engages.

This is simple, demo-friendly, and directly connected to revenue.

You can sell it as:

> **Send us your customer list. In 2 minutes, Nudgen shows who might churn and gives you the exact campaign to win them back.**

---

## 21. Suggested Landing Page Structure

## Hero

# Find customers before they churn. Win them back with AI.

Nudgen Churn Radar detects inactive, stuck, and renewal-risk customers, then creates personalized save campaigns that stop when customers return.

CTA:

> Scan my customers

Secondary CTA:

> See example report

---

## Section 1: Problem

Your customers rarely announce they are leaving.

They just:

- stop logging in
- stop using key features
- ignore onboarding
- approach renewal with low usage
- fail payment
- quietly disappear

---

## Section 2: How It Works

1. Connect customer data or upload CSV
2. Nudgen detects churn signals
3. Review customers at risk
4. Launch AI-personalized save campaign
5. Stop follow-up when they engage

---

## Section 3: Example Alerts

```text
Critical: 8 paid users inactive for 14+ days
High: 12 trial users did not activate
Medium: 5 renewals coming up with low usage
```

---

## Section 4: Campaign Examples

- Trial rescue
- Inactive paid user
- Renewal risk
- Feature drop-off
- Failed payment

---

## Section 5: CTA

> Run a free churn scan

---

# Final Recommendation

Build **Nudgen Churn Radar** as a simple, action-first churn prevention layer.

Do **not** start as a pure analytics product.

Do **not** start as a payment recovery product.

Start with the problem Nudgen is already designed to solve:

> **Businesses already have customer signals, but they do not act on them fast enough.**

The MVP should be:

> **Upload customer data → detect churn risk → generate save campaign → auto-stop when customer comes back.**

That gives Nudgen a clear expansion path from retention email automation into proactive customer lifecycle automation.
