# Supplier Portal Feature Engagement Framework

## Product Creation Wizard (Smart Creation)

---

### Feature Overview

| Element | Description |
|---------|-------------|
| **Feature Purpose** | Enable suppliers to submit new products/tours to the GYG marketplace via a self-service, category-aware wizard |
| **Core Action** | Submit a product through the wizard |
| **Success Outcome** | Product approved by curation and goes live on marketplace |
| **Engagement Measured On** | Activation Success, Submission Frequency, Approval Quality, Business Value |

---

### Accountability Framework

**The Core Issue:** The wizard's purpose is to help suppliers create products, but success depends on factors the wizard doesn't directly control (curation approval, marketplace demand for bookings). How do we measure wizard success fairly?

**Solution:** Separate **accountability** (what the wizard controls) from **influence** (what it affects) and **tracking** (what predicts retention).

```
┌─────────────────────────────────────────────────────────────┐
│                    Wizard Accountability                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  ✅ DIRECT ACCOUNTABILITY (Wizard Controls)                │
│     • Feature discovery (% who find the wizard)            │
│     • Submission completion (% who submit)                 │
│     • Creation flow friction (dropoff points)              │
│     ➜ PRIMARY METRIC: Activation Rate                      │
│                                                             │
│  ⚠️ INFLUENCE (Wizard Affects Through Guidance)            │
│     • Approval rate (via quality guidance)                 │
│     • First booking rate (via content richness)            │
│     ➜ TRACKED AS: Quality Indicators                       │
│     ➜ WHY: Feedback on wizard effectiveness                │
│                                                             │
│  ❌ NO CONTROL (External Factors)                          │
│     • Curation decision speed                              │
│     • Marketplace ranking algorithms                       │
│     • Traveler demand for specific products                │
│     ➜ TRACKED AS: Context metrics only                     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Why Track Things We Don't Control?**
1. **Feedback loop:** Low approval rates signal poor wizard guidance → Action: Improve examples, quality checks
2. **Predict retention:** Approved suppliers return 2x more often → Informs Level 2 strategy
3. **Prioritize improvements:** Helps decide where to invest (better preview, category-specific guidance)

**Example:**
- **Bad:** "Wizard failed because only 45% of products got first booking" ← Not wizard's fault
- **Good:** "Wizard guidance is working: 70% approval rate, up from 60%" ← Wizard influence
- **Best:** "Improving wizard guidance from 60% → 70% approval increased retention from 35% → 40%" ← Shows wizard impact

**Principle:** The wizard is **accountable** for submissions, but should **optimize** for approval and booking success through better guidance and quality checks.

---

## How to Use This Framework

**This framework is a MEASUREMENT and DISCOVERY tool, not a prescription.**

### Purpose

1. **Discover baselines:** What's the current state? What are the distributions?
2. **Track trends:** Is it getting better or worse? Week-over-week? Month-over-month?
3. **Find patterns:** What behaviors predict success? What causes dropoff?
4. **Set targets:** AFTER you understand the data, then set realistic, data-driven targets

### DO NOT Start With Targets

❌ **Wrong:** "Our target is 60% activation in 30 days"
✅ **Right:** "Let's measure: What % activate at 7d/14d/30d/60d/90d? What's the distribution? Then we'll set a target."

### The Process

```
Step 1: MEASURE
├─ Implement tracking
├─ Collect 4-8 weeks of data
└─ Analyze distributions (P25/P50/P75)

Step 2: UNDERSTAND
├─ What's the baseline? (median behavior)
├─ What's the trend? (improving/declining/stable)
├─ What's the distribution? (wide variation? tight clustering?)
└─ What predicts success? (correlations, patterns)

Step 3: SET TARGETS
├─ Based on current P75 (top quartile)
├─ Based on best-performing cohort
├─ Based on improvement trajectory
└─ Realistic but aspirational

Step 4: ITERATE
├─ Track against targets
├─ Adjust targets as you learn
└─ Continuously improve
```

---

## Framework Structure

The framework measures engagement through **three views**:

```
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  COMBINED VIEW (Overall Platform Health)                │
│  └─ How quickly are suppliers creating products?        │
│  └─ Are they returning to create more?                  │
│  └─ What's the business value per product?              │
│                                                         │
└─────────────────────────────────────────────────────────┘
                            │
                            ├────────────────┬────────────────┐
                            ▼                ▼                ▼
              ┌─────────────────────┐  ┌─────────────────────┐
              │                     │  │                     │
              │  NEW SUPPLIERS      │  │  EXISTING SUPPLIERS │
              │  (Account < 90d)    │  │  (Account ≥ 90d)    │
              │                     │  │                     │
              │  Level 1: First     │  │  Level 1: Continue  │
              │  Level 2: Return    │  │  Level 2: Sustain   │
              │  Level 3: Value     │  │  Level 3: Value     │
              │                     │  │                     │
              └─────────────────────┘  └─────────────────────┘
```

**Why This Structure:**
- **Combined View:** Executive summary, overall platform health
- **New Suppliers:** Acquisition funnel, getting started
- **Existing Suppliers:** Retention and expansion, sustained usage

---

## Primary Metrics Summary

### Combined View

| Level | Primary Metric | What to Track |
|-------|---------------|---------------|
| **Level 1** | Submission Rate + Completion Rate + Approval Rate + 30D Booking Rate | Core action: Submit product. Track completion, quality, success |
| **Level 2** | Return Rate Distribution | % returning by time window (30d/60d/90d/180d), median days between submissions |
| **Level 3** | Revenue per Product | Distribution (P25/P50/P75), trend over time |

### New Suppliers Segment

| Level | Primary Metric | What to Track |
|-------|---------------|---------------|
| **Level 1** | Activation Rate + Completion Rate + First Approval Rate + 30D Booking Rate | Core action: Submit first product. Track completion, quality, success |
| **Level 2** | 2nd Product Creation Rate | Cumulative % by days since 1st, time distribution (1st→2nd) |
| **Level 3** | Early Value Creation | Revenue distribution, products per supplier in first 90d |

### Existing Suppliers Segment

| Level | Primary Metric | What to Track |
|-------|---------------|---------------|
| **Level 1** | Monthly Submission Rate + Completion Rate + Approval Rate + 30D Booking Rate | Core action: Submit products. Track completion, quality, success |
| **Level 2** | Creation Frequency | Days between submissions (P25/P50/P75), consistency patterns |
| **Level 3** | Long-term Value | LTV distribution by engagement tier, revenue contribution |

**Key Principle:** Track distributions and trends FIRST, then set targets based on what you learn from the data.

---

## Engagement Framework

---

# COMBINED VIEW (Overall Platform Health)

This view provides the executive summary of wizard engagement across all suppliers.

### Level 1: Product Creation (Core Engagement)

**Definition:** Growing engaged users - getting suppliers to submit products

**Core Action:** Submit a product

#### Primary Metrics

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|----------------|---------------------|
| **Submission Rate** | % of suppliers who submit ≥1 product | Monthly rate, trend over time (MoM), by segment | Are suppliers submitting? Trend? |
| **Completion Rate** | % of started wizard sessions that result in submission | Overall rate, by step (funnel), trend over time | Where do suppliers drop off? Improving? |
| **Approval Rate** | % of submissions approved by curation | Overall rate, by supplier segment, trend | Is quality good? Improving? |
| **30D Booking Rate** | % of approved products with ≥1 booking in 30 days | By segment, trend over time | Are products successful? |

---

### Level 2: Retention (Habitual Use)

**Definition:** Do suppliers return to create more products?

**Goal:** Understand return behavior, identify patterns, optimize for repeat creation

#### Primary Metrics

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|----------------|---------------------|
| **Return Rate by Time Window** | % of suppliers who submit another product within X days of last submission | Track cumulative: 30d/60d/90d/180d/365d return rates | What's the natural cadence? When do most return? |
| **Days Between Submissions** | Time between consecutive submissions (submission N → N+1) | Distribution (P25/P50/P75), histogram, trend over time | How fast do they return? Is it speeding up or slowing? |

---

### Level 3: Growth (Value Creation)

**Definition:** What business value does product creation drive?

**Goal:** Understand value creation patterns, quantify engagement impact on business

#### Primary Metrics

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|----------------|---------------------|
| **Revenue per Product** | GMV generated per product at 30/60/90/180 days | Distribution (P25/P50/P75), by category, trend over time | What's typical product value? Improving? Varies by category? |
| **Supplier LTV by Engagement Tier** | Compare LTV: Power (5+) vs Regular (2-4) vs Light (1) | Calculate multiplier, correlation with creation frequency | How much more valuable are engaged suppliers? Causal or correlation? |

---

# NEW SUPPLIERS SEGMENT (Account < 90 Days)

This segment measures how new suppliers progress through the product creation funnel for the first time.

### Level 1: First Product Creation

**Definition:** Getting new suppliers to submit their first product

**Core Action:** Submit first product

#### Primary Metrics

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|----------------|---------------------|
| **Activation Rate** | % of new suppliers who submit first product within 30 days | Rate by cohort, trend over time | Are new suppliers submitting? |
| **Completion Rate** | % of started wizard sessions that result in submission | Overall rate, by wizard step (funnel), trend over time | Where are suppliers dropping off? Improving? |
| **First Approval Rate** | % of first submissions approved by curation | Rate over time, rejection reason distribution | Is quality good for first submissions? |
| **30D Booking Rate** | % of approved first products with ≥1 booking in 30 days | By cohort, trend over time | Are first products successful? |

#### Quality Indicators

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|--------|----------------|
| **First Submission Approval Rate** | % of first submissions approved by curation | Rate over time, rejection reason distribution | Is wizard guidance effective? What causes rejections? |
| **First Product Booking Rate** | % of first approved products getting ≥1 booking by days (7d/14d/30d/60d) | Cumulative curve, time to first booking distribution | Do first products get traction? How long does it take? |

---

### Level 2: Return for More

**Definition:** Getting new suppliers to create additional products after their first

**Goal:** Understand early retention patterns, identify what drives repeat behavior

#### Primary Metrics

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|----------------|---------------------|
| **2nd Product Creation - Time Distribution** | % of new suppliers creating 2nd product by days since 1st | Cumulative curve: 7d/14d/30d/60d/90d/180d | When do they return? What's the pattern? |
| **Time Between 1st and 2nd** | Days from 1st submission to 2nd submission | Distribution (P25/P50/P75), histogram | What's typical cadence? Fast vs slow returners? |
| **Retention Cohort Curves** | % of new suppliers still active after X days (by cohort month) | Track 7d/14d/30d/60d/90d/180d retention, compare cohorts | Are cohorts improving? Where's the biggest dropoff? |

---

### Level 3: New Supplier Value

**Definition:** Business value generated by new suppliers in their early days

**Goal:** Understand value creation trajectory, identify successful vs struggling new suppliers

#### Primary Metrics

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|----------------|---------------------|
| **Early Revenue Distribution** | GMV generated by new supplier at 30/60/90 days | Distribution (P25/P50/P75), by products created | What's typical early value? What drives higher value? |
| **Products per New Supplier** | # products created by new suppliers in first 30/60/90 days | Distribution, correlation with revenue | How many products do successful new suppliers create? |
| **New Supplier Booking Success** | % of new suppliers getting ≥1 booking by days (30/60/90) | Cumulative curve, factors predicting success | What% experience value? What predicts success? |

---

# EXISTING SUPPLIERS SEGMENT (Account ≥ 90 Days)

This segment measures how existing suppliers continue to create products over time.

### Level 1: Ongoing Product Creation

**Definition:** Getting existing suppliers to continue submitting products

**Core Action:** Submit additional products

#### Primary Metrics

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|----------------|---------------------|
| **Monthly Submission Rate** | % of existing suppliers who submit ≥1 product in the month | Trend over time (MoM), by supplier tenure | Are existing suppliers submitting? |
| **Completion Rate** | % of started wizard sessions that result in submission | Overall rate, by wizard step, trend over time | Friction points? Improving? |
| **Approval Rate** | Approval rate for existing suppliers | Track by submission number (1st vs 5th vs 10th), trend | Is quality good? Improving over time? |
| **30D Booking Rate** | % of approved products with ≥1 booking in 30 days | By engagement tier, trend over time | Are products successful? |

#### Quality Indicators

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|--------|----------------|
| **Sustained Approval Rate** | Approval rate for existing suppliers (by submission #) | Track by submission number (1st vs 5th vs 10th), trend | Are suppliers learning? Quality improving over time? |
| **Product Performance** | Booking rate for products by submission number | Compare early products vs later products | Do suppliers get better at creating successful products? |

---

### Level 2: Consistent Activity

**Definition:** Getting existing suppliers to create products consistently (habit)

**Goal:** Understand consistency patterns, identify factors that sustain engagement

#### Primary Metrics

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|--------|---------------------|
| **Return Rate for Existing** | % of existing suppliers who submit again by days since last | Cumulative curve: 7d/14d/30d/60d/90d | What's typical return cadence for existing? |
| **Time Between Submissions** | Days between consecutive submissions for existing suppliers | Distribution (P25/P50/P75), trend over time, by tier | How fast do they return? Getting faster or slower? |
| **Submission Frequency Distribution** | Days between submissions over rolling 180-day window | Histogram, P25/P50/P75, identify consistent vs sporadic patterns | Are suppliers consistent or sporadic? Pattern changes over time? |

---

### Level 3: Existing Supplier Value

**Definition:** Cumulative business value generated by existing suppliers

**Goal:** Understand long-term value patterns, quantify impact of sustained engagement

#### Primary Metrics

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|----------------|---------------------|
| **LTV Distribution** | GMV generated by existing supplier (lifetime) | Distribution (P25/P50/P75), by tenure, by engagement tier | What's typical LTV? Top performers? |
| **Revenue Contribution** | % of total GMV from existing vs new suppliers | Trend over time, by segment | How much value comes from existing? Sustainable? |
| **LTV by Engagement Tier** | Compare LTV: Power (5+) vs Regular (2-4) vs Light (1) | Calculate multiplier, correlation analysis, trend | How much more valuable are power users? Growing gap? |

---

# DETAILED SECTIONS (Original Content)

### Level 1: Core Action (Submit A Product)

**Definition:** Getting suppliers to submit products through the wizard

**Goal:** Suppliers successfully submit, get approved, and get bookings

**Core Action:** Submit a product

**Applies To:**
- ✅ New suppliers submitting their first product
- ✅ Existing suppliers submitting additional products (2nd, 5th, 10th, etc.)
- ✅ Every product submission event

**Wizard Accountability:** The wizard is **directly responsible** for submissions and completion. It is **not responsible** for approval (curation's decision) or bookings (marketplace dynamics), but it should **influence** approval through better guidance and quality checks.

---

#### Primary Metrics

These measure engagement across ALL submissions:

| Metric | Definition | How to Analyze | Insights to Look For |
|--------|-----------|----------------|---------------------|
| **Submission Rate** | % of suppliers who submit ≥1 product | Monthly rate, trend over time (MoM) | Are suppliers submitting? |
| **Completion Rate** | % of started wizard sessions that result in submission | Overall rate, by wizard step (funnel), trend over time | Where do suppliers drop off? Improving? |
| **Approval Rate** | % of submissions approved by curation | Overall rate, by supplier segment, trend | Is quality good? Improving? |
| **30D Booking Rate** | % of approved products with ≥1 booking in 30 days | By segment, trend over time | Are products successful? |

#### Supporting Metrics

These provide context for the primary metrics:

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Time to Submission** | Days from trigger to submission | Distribution (P25/P50/P75), histogram, trend | How quickly do suppliers submit? |
| **Time to Approval** | Median days from submission to approval decision | Affects supplier momentum - not wizard control |
| **Time to First Booking** | Median days from product going live to first booking | Success signal - not wizard control |

**Key Insight:** 
- **Level 1 = Core Action: Submit**
- Track 4 metrics: Submission + Completion + Approval + 30D Booking
- Booking metrics predict Level 2 return behavior

---

#### Secondary Metrics (Diagnostic)

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Step-by-Step Dropoff** | Completion rate at each wizard step | Identifies specific friction points in creation flow |
| **Draft Save Rate** | % of sessions ending in draft vs submission | Shows intent vs completion gap |
| **Category Prediction Accuracy** | % accepting vs overriding AI category suggestion | AI guidance effectiveness |
| **Rejection Reason Distribution** | Top reasons for submission rejection | Guides wizard improvement priorities |
| **Resubmission Rate After Rejection** | % of rejected users who submit again within 14 days | Resilience and learning |

#### Key Questions

**Core Action Funnel (Direct Accountability):**
1. What's the product creation rate distribution? (7d/14d/30d/60d/90d cumulative)
2. What % of new suppliers submit their first product within 30 days?
3. What's the median time to product creation? Trending faster or slower?
4. Where do suppliers drop off in the wizard? (Step-level funnel - all submissions)
5. What's the completion rate: started → submitted? Improving?
6. Where should we focus improvements to increase completion rate and reduce time to creation?

**Quality Indicators (Wizard Influence - Feedback on Effectiveness):**
7. What % of all submissions get approved vs rejected?
8. What are the top rejection reasons? **Are they preventable through better wizard guidance?**
9. Do rejected suppliers resubmit? What increases comeback rate?
10. What % of approved products get their first booking within 30 days?
11. How long from going live to first booking?
12. **Does improving wizard guidance increase approval rates across all submissions?**

**Loop Effectiveness (Inform Level 2 Strategy):**
13. What predicts return behavior? (Approval status? Booking success? Submission experience?)
14. How much more likely are suppliers with approved products to submit again?
15. How much more likely are suppliers with bookings to submit again?
16. Does submission experience quality (approval, booking) affect how quickly suppliers return for next submission?

#### Segmentation (Applies to All Submissions)

| Segment | Definition | Level 1 Goal | Intervention Strategy |
|---------|-----------|--------------|----------------------|
| **New Suppliers** | 0 products submitted | Submit first product within 30 days | Onboarding prompts, tutorials, success stories |
| **Active Creators** | Submitted in last 30 days | Submit next product | Success notifications, performance insights |
| **Returning Creators** | Last submission 30-90 days ago | Submit again | Seasonal prompts, catalog expansion ideas |
| **Dormant Creators** | Last submission 90+ days ago | Reactivate | Win-back campaigns, what's new in wizard |
| **Stalled Sessions** | Started wizard but didn't complete | Complete submission | Re-engagement email, barrier removal |

**By Experience:**
| Segment | Definition | Strategy |
|---------|-----------|----------|
| **High Success** | 80%+ approval rate, products getting bookings | Showcase as examples, ask for feedback |
| **Struggling** | <50% approval rate, frequent rejections | Intensive guidance, identify barriers |
| **Rejected Last Submission** | Most recent submission rejected | Specific feedback, guide resubmission |

**By Priority:**
| Segment | Definition | Strategy |
|---------|-----------|----------|
| **High-Value Suppliers** | Top 20% by revenue potential | White-glove support, priority curation |
| **Power Users** | 5+ products, active monthly | VIP treatment, early access to features |

---

### Level 2: Habit Formation (Return & Submit More)

**Definition:** Getting suppliers to return and submit again after each submission (the loop)

**Goal:** Suppliers develop a habit of regularly submitting products

**The Loop:** After completing Level 1 (submit a product), suppliers should return to Level 1 again (submit another product). Level 2 measures how quickly and how often this loop repeats.

**Key Insight:** Every supplier is continuously cycling between Level 1 (submit) and Level 2 (return to submit more). This is not a one-time journey.

#### Key Metrics

| Metric | Definition | Target | Why It Matters |
|--------|-----------|--------|----------------|
| **Return Rate by Time Window** | % of suppliers who submit another product within X days of last submission | Track cumulative: 30d/60d/90d/180d | When do they return? Pattern? |
| **Days Between Submissions** | Time between consecutive submissions | Distribution (P25/P50/P75), trend | How fast do they return? Speeding up/slowing? |
| **Sustained Quality** | Approval rate by submission number (1st vs 5th vs 10th) | Trend over time | Are suppliers learning and improving? |

#### Secondary Metrics (Diagnostic)

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Return Rate (L7/L30)** | % of activated users returning within 7/30 days after first submission | Early habit formation signal |
| **Days Between Submissions** | Median days between 1st and 2nd, 2nd and 3rd submissions | Usage cadence patterns |
| **Power User Formation Rate** | % of activated users reaching 5+ products within 90 days | Identifies scaling engagement |
| **Dormancy Recovery Rate** | % of dormant users (60+ days) who return within 30 days | Winback effectiveness |
| **Post-Rejection Return Rate** | % of rejected users who resubmit within 14/30 days | Resilience and learning |

#### Key Questions

1. **The Loop:** What % of suppliers return to submit another product within 30/60/90 days?
2. **Loop Speed:** How long between submissions? (1st→2nd, 2nd→3rd, 5th→6th)
3. **Loop Sustainability:** Does the time between submissions increase, decrease, or stay stable?
4. **Success Impact:** Do approved products drive faster return than rejected ones?
5. **Booking Impact:** Do products with bookings drive faster return than those without?
6. **Power User Patterns:** What makes suppliers submit frequently vs infrequently?
7. **Dormancy:** What breaks the loop? Why do suppliers stop returning?
8. **Reactivation:** What brings dormant suppliers back into the loop?
9. **Cadence:** What's the natural submission rhythm? Weekly? Monthly? Seasonal?

#### Segmentation (Behavioral)

| Segment | Definition | Size Target | Retention Goal | Intervention Strategy |
|---------|-----------|-------------|----------------|----------------------|
| **Power Users** | 5+ products created, active monthly | 10-15% | Sustain monthly activity | VIP treatment, advanced features, early access |
| **Regular Users** | 2-4 products, active quarterly | 25-30% | Convert to power users | Encourage consistency, catalog expansion tips |
| **Light Users** | 1 product, returned 1-2 times | 30-40% | Convert to regular users | Success stories, seasonal campaigns |
| **One-and-Done** | 1 product, no return in 60+ days | <25% (minimize) | Reactivate within 90 days | Win-back campaigns, understand barriers |
| **Dormant** | Previously active, 90+ days inactive | Monitor & minimize | Return within 30 days | High-value: personalized outreach; Low-value: automated |

---

### Level 3: Growth (Value Creation)

**Definition:** Product creation drives measurable supplier success, platform growth, and network effects

**Goal:** Creating products (via the wizard) drives supplier success, platform inventory growth, and ecosystem engagement

**Context:** The wizard is the ONLY way to create products on the platform, so we measure how product creation frequency correlates with business value.

#### Key Metrics

| Metric | Definition | Target | Why It Matters |
|--------|-----------|--------|----------------|
| **Revenue per Approved Product** | GMV generated per product at 90 days | €X+ (TBD) | PRIMARY - Business value of feature |
| **Supplier Retention by Creation Frequency** | 90-day retention: Suppliers creating 5+ products vs 1-2 products | High creators +30% retention | Does creating more products drive loyalty? |
| **Cross-Feature Engagement** | % of product creators engaging with Performance Hub, Recommended Actions | 40%+ | Does product creation drive ecosystem engagement? |
| **Supplier LTV by Engagement Tier** | LTV: Power users (5+ products) vs Regular (2-4) vs Light (1) | Power ≥3x Light | Value of encouraging more product creation |
| **Product Quality at Scale** | Avg defect rate, approval rate, booking rate over time | Stable or improving | Is quality maintained as volume grows? |

#### Secondary Metrics (Diagnostic)

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Product Defect Rate** | % of products with quality issues flagged post-launch | Quality sustainability as volume scales |
| **Curation Efficiency** | Avg time saved per product via preventative guidance | Operational benefit of wizard guidance |
| **Resubmission After Rejection** | % of rejected users who submit again within 30 days | Learning and persistence |
| **Category Completion Index** | % of category-specific fields completed (avg across categories) | Content richness trend over time |
| **Supplier Satisfaction (NPS/CSAT)** | NPS for suppliers actively creating products | Feature satisfaction |
| **Revenue Concentration** | % of total GMV from top 20% of creators vs bottom 50% | Is value creation concentrated or distributed? |

#### Key Questions

1. **Business Value:** What revenue do products generate? (30/60/90 day cohorts)
2. **Creation Frequency & Value:** Do suppliers who create more products have higher LTV? By how much?
3. **Product Quality at Scale:** Is quality maintained as catalog grows? (approval rate, defect rate trends)
4. **Retention Impact:** Does creating more products correlate with higher supplier retention?
5. **Ecosystem Engagement:** Does product creation drive engagement with other portal features (Performance Hub, Recommended Actions)?
6. **Virtuous Cycle:** Is there evidence of: Create → Get bookings → Create more → Success?
7. **Supplier Success:** Do suppliers who create products see business growth on the platform? (GMV, bookings)
8. **Engagement Tiers:** What's the LTV difference between power users (5+ products) vs light users (1 product)?
9. **Network Effects:** Do successful creators recruit new suppliers? (referral data)
10. **Platform Health:** Are suppliers maintaining product creation frequency over time? Is quality stable as frequency increases?

#### Segmentation (Value-Based)

| Segment | Definition | Business Impact | Strategy |
|---------|-----------|-----------------|----------|
| **High LTV (Top 20%)** | Highest revenue contributors | Critical business value | White-glove support, priority features |
| **Growth Potential** | Rising trajectory, not yet high LTV | Future high-value | Nurture, remove friction, incentivize |
| **Stable Contributors** | Consistent moderate value | Reliable base | Scalable support, automated engagement |
| **Low Value** | Minimal revenue contribution | Limited resources | Self-service only |

---

## Measurement Dashboard Structure

### Primary Dashboard (Weekly Review)

```
┌─────────────────────────────────────────────────────────────┐
│              PRODUCT CREATION WIZARD DASHBOARD              │
│                    Week of May 26, 2026                     │
└─────────────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════════
                      COMBINED VIEW
═══════════════════════════════════════════════════════════════

LEVEL 1: Product Submission (Core Action)
  Submission Rate: 58% of supplier base submitted this month
  Completion Rate: 72% (started → submitted)
  Approval Rate: 71% (submitted → approved)
  30D Booking Rate: 48% (approved → bookings)
  
  Trend: Submission ▼ -2% MoM | Completion ▲ +1% | Approval ▬ stable
  
LEVEL 2: Return Rate Distribution
  30 days: 25% | 60 days: 35% | 90 days: 42%
  Median time to next: 58 days
  
  Trend: ▲ +2% MoM (90d rate)

LEVEL 3: Revenue per Product (90d)
  P25: €850 | P50: €2,850 | P75: €6,200
  
  Trend: ▲ +12% MoM (median)


═══════════════════════════════════════════════════════════════
                    NEW SUPPLIERS (< 90 days)
                    2,100 new accounts this month
═══════════════════════════════════════════════════════════════

LEVEL 1: First Product Submission (Core Action)
  Activation Rate: 58% submit first product in 30d
  Completion Rate: 72% (started → submitted)
  First Approval Rate: 68%
  30D Booking Rate: 45%
  
  Time to First Submission: P25: 12d | P50: 28d | P75: 48d
  
  Trend: Activation ▼ -2% vs prior cohort | Completion ▬ stable

LEVEL 2: 2nd Product Creation Time Distribution  
  7d: 5% | 14d: 12% | 30d: 22% | 60d: 30% | 90d: 35%
  Median time 1st→2nd: 52 days
  
  Trend: 90d rate ▼ -3% vs prior cohort

LEVEL 3: Early Value (First 90 Days)
  Revenue P25: €200 | P50: €1,200 | P75: €3,500
  Avg products created: 1.8
  % with ≥1 booking: 48%

📊 Insight: Only 58% of new suppliers create first product in 
           30d. Bigger issue: Only 35% create 2nd product ever.
           Those who do activate create ~€1,200 in 90d.


═══════════════════════════════════════════════════════════════
                  EXISTING SUPPLIERS (≥ 90 days)
                  6,250 existing suppliers
═══════════════════════════════════════════════════════════════

LEVEL 1: Ongoing Product Submission (Core Action)
  Monthly Submission Rate: 48% (3,000 of 6,250 suppliers)
  Completion Rate: 76% (started → submitted)
  Approval Rate: 75% (vs 68% for new)
  30D Booking Rate: 52%
  
  Days Between Submissions: P25: 18d | P50: 38d | P75: 72d
  
  Trend: Submission Rate ▬ stable | Approval ▬ stable

LEVEL 2: Return Patterns
  Return rate: 30d: 35% | 60d: 48% | 90d: 55%
  Time between submissions: P25: 18d | P50: 38d | P75: 72d
  Submission frequency distribution: Consistent (<30d): 35% | Sporadic (30-90d): 42% | Infrequent (>90d): 23%
  
  Trend: Return rate (90d) ▲ +2% MoM
  Trend: Time between submissions ▬ stable

LEVEL 3: Long-term Value Distribution
  LTV by tier:
    • Power (5+): P50 €18,500 (n=625, 10% of existing)
    • Regular (2-4): P50 €8,200 (n=1,875, 30%)
    • Light (1): P50 €5,800 (n=3,750, 60%)
  
  Revenue contribution: 82% of platform GMV
  Power user multiplier: 3.2x vs Light

📊 Insight: Existing suppliers create products every 38 days (median). 
           35% return within 30 days, 55% within 90 days. Power 
           users (5+ products) have 3.2x higher LTV than light users.


═══════════════════════════════════════════════════════════════
                       KEY INSIGHTS
═══════════════════════════════════════════════════════════════

📊 What We Learned This Week:

1. NEW SUPPLIER CHALLENGE: 
   • 58% create first product in 30d (down from 60%)
   • Only 35% ever create 2nd product
   • Biggest dropoff: after 1st product
   
2. EXISTING SUPPLIER PATTERNS:
   • Return every 38 days (median), 55% within 90 days
   • 35% return within 30 days (fast returners)
   • Power users (5+) have 3.2x LTV vs light users
   
3. MEDIAN BEHAVIORS:
   • New suppliers take 28 days to first product
   • Take 52 days from 1st to 2nd product
   • Existing suppliers submit every 38 days (median)
   • Products generate €2,850 at 90 days (median)

🎯 Questions to Investigate:

1. Why did new supplier 30d activation drop 2%? (58% → 60%)
2. Why do 65% of new suppliers never create 2nd product?
3. Can we move more suppliers from Light → Power tier?
4. Can we reduce median time between submissions from 38d to 30d?


```

---

## Segmentation Summary

### Primary Segmentation (New vs Existing)

| Segment | Definition | Size | Focus Area |
|---------|-----------|------|-----------|
| **New Suppliers** | Account age < 90 days | ~2,100/month | Getting started, first products |
| **Existing Suppliers** | Account age ≥ 90 days | ~6,250 total | Sustained engagement, return frequency |

### Behavioral Segmentation (Within Each Primary Segment)

**For New Suppliers:**

| State | Definition | Goal | Intervention |
|-------|-----------|------|--------------|
| **Inactive** | 0 products submitted | Create first product | Onboarding, tutorials |
| **Activated** | 1 product submitted | Create 2nd product | Success stories, next steps |
| **Expanding** | 2-4 products | Reach 5+ products | Catalog expansion tips |
| **Power User (Early)** | 5+ products in first 90 days | Sustain momentum | VIP treatment |

**For Existing Suppliers:**

| State | Definition | Goal | Intervention |
|-------|-----------|------|--------------|
| **Active** | Last submission <30 days | Keep creating | Performance insights |
| **Occasional** | Last submission 30-90 days | Increase frequency | Seasonal prompts |
| **Dormant** | Last submission 90+ days | Reactivate | Win-back campaigns |
| **Power User** | 5+ products, monthly active | Sustain | VIP treatment, early access |

### Engagement Segmentation (Behavioral Tiers)

| Tier | Definition | Size Target | Engagement Goal |
|------|-----------|-------------|-----------------|
| **Power Users** | 5+ products, active monthly | 10-15% | Scale & sustain |
| **Regular Users** | 2-4 products, active quarterly | 25-30% | Convert to power |
| **Light Users** | 1 product, returned 1-2 times | 30-40% | Convert to regular |
| **One-and-Done** | 1 product, 60+ days inactive | <25% | Minimize this segment |

### Quality Segmentation

| Tier | Definition | Approach |
|------|-----------|----------|
| **High Quality** | 80%+ approval rate, low defect rate | Showcase as examples, minimal guidance |
| **Improving** | Approval rate increasing over time | Positive reinforcement, continue support |
| **Struggling** | <50% approval rate, frequent rejections | Intensive guidance, identify barriers |

### Value Segmentation

| Tier | Criteria | Priority | Resource Allocation |
|------|----------|----------|-------------------|
| **High LTV** | Top 20% by revenue potential | Critical | White-glove, dedicated support |
| **Growth Potential** | Rising trajectory, not yet high LTV | High | Proactive nurture, remove friction |
| **Stable Contributors** | Consistent moderate value | Medium | Scalable, automated support |
| **Low Value** | Minimal revenue | Low | Self-service only |

---

## Implementation Priorities

### Phase 1: Foundation (Weeks 1-4)

**Objective:** Establish baseline measurement

**Activities:**
1. ✅ Implement tracking for all Level 1 & 2 metrics
2. ✅ Build core dashboard (3 levels + segmentation)
3. ✅ Establish 4-week baseline averages
4. ✅ Map user journey and identify dropoff points
5. ✅ Create supplier segments in data warehouse

**Success Criteria:**
- All metrics tracked and reporting accurately
- Dashboard accessible and updated weekly
- Baselines established with statistical confidence
- Segments defined and populated

### Phase 2: Activation Optimization (Weeks 5-8)

**Objective:** Improve Level 1 metrics (activation)

**Activities (Direct Accountability):**
1. ✅ Fix top 3 friction points in wizard flow → Increase activation rate
2. ✅ Improve wizard visibility in onboarding → Increase discovery
3. ✅ Improve submission flow UX → Increase completion rate

**Activities (Improve Wizard Influence):**
4. ✅ Enhance curation preview functionality → Help suppliers fix issues before submit
5. ✅ Test category-specific guidance → Improve approval rate through better quality
6. ✅ Add quality check warnings during creation → Reduce rejection rate

**Activities (External - Not Wizard Team):**
7. ❌ Reduce time to approval (curation SLA) → Curation team responsibility

**Success Criteria:**
- **Direct Accountability:** +10% improvement in activation rate (58% → 64%)
- **Wizard Influence:** +5% improvement in first approval rate (68% → 71%)
- **Speed:** -2 days reduction in time to first submission (8.5d → 6.5d)

### Phase 3: Retention Optimization (Weeks 9-16)

**Objective:** Improve Level 2 metrics (retention)

**Activities:**
1. ✅ Launch email nurture campaigns by segment
2. ✅ Implement success notifications (first booking, milestones)
3. ✅ Build win-back campaigns for dormant users
4. ✅ Test gamification elements (badges, progress)
5. ✅ Analyze and document power user patterns

**Success Criteria:**
- +15% improvement in repeat usage rate
- +10% improvement in L30 retention
- Power user segment reaches 12%+

### Phase 4: Growth & Business Impact (Weeks 17-24)

**Objective:** Improve Level 3 metrics (growth)

**Activities:**
1. ✅ Validate LTV correlation by engagement tier (Power vs Regular vs Light)
2. ✅ Launch category-specific optimization experiments
3. ✅ Implement cross-feature engagement prompts (Performance Hub CTAs)
4. ✅ Build supplier success showcase (motivate more creation)
5. ✅ Analyze product quality trends as volume scales

**Success Criteria:**
- €X+ GMV per approved product (90-day)
- +30% retention for high-frequency creators (5+ products) vs low (1-2)
- +40% cross-feature engagement
- Quality maintained at scale (stable approval rate, defect rate)
- Power users LTV ≥3x Light users

---

## Key Questions by Stakeholder

### Product Team

**Combined View:**
- What's the product creation rate distribution? (7d/14d/30d/60d/90d)
- What's the median time to product creation? Improving or declining?
- What's the return rate distribution? (30d/60d/90d)

**New Suppliers:**
- Where are new suppliers dropping off in the wizard?
- What causes first submission rejections? Can we prevent through better guidance?
- Why aren't more new suppliers creating a 2nd product?
- How can we improve 30-day activation rate?

**Existing Suppliers:**
- Why do existing suppliers stop creating? (Dormancy reasons)
- What makes power users (5+ products) different from occasional users?
- How can we reduce time between submissions for existing suppliers?
- Are we maintaining quality as suppliers create more products?

### Business / Leadership

**Combined View:**
- What's the product creation rate? (cumulative % by 7d/14d/30d/60d/90d)
- What's the return rate distribution? (30d/60d/90d)
- What's the revenue per product? Trending?

**New Suppliers:**
- What % of new suppliers activate (create first product)?
- What % become regular creators (2+ products)?
- What's the avg LTV of new suppliers in first 90 days?

**Existing Suppliers:**
- What's the return rate for existing suppliers? (30d/60d/90d)
- What's the revenue distribution by engagement tier? (Power vs Regular vs Light)
- Are we retaining our best creators?

### Data / Analytics Team

**Combined View:**
- What's the overall funnel: suppliers → active creators → repeat creators?
- What predicts high engagement? (Approval? Bookings? Content quality?)

**New Suppliers:**
- What predicts successful activation? (Time to first submission? First approval?)
- What predicts 2nd product creation? (First product success? Booking?)
- What's the 30/60/90 day retention curve for new supplier cohorts?

**Existing Suppliers:**
- What predicts sustained engagement? (Product performance? Past success?)
- What's the causal relationship between creation frequency and LTV?
- What differentiates power users from dormant users?

### Segmentation Questions

- How different are new vs existing supplier behaviors?
- Should we have different targets for each segment?
- What's the optimal path: new → activated → power user?
- Where is the biggest leakage in the funnel? (New activation vs existing retention)

---

## Appendix: Metric Calculation Details

### Level 1: Core Action Metrics

**Product Creation Rate by Time**
```
Numerator: # suppliers who create product within X days (7d/14d/30d/60d/90d)
Denominator: # suppliers in cohort
Time Window: Days from cohort start (new: account creation, existing: period start)
Analysis: Cumulative distribution, trend over time
```

**New Supplier Activation Rate**
```
Numerator: # new suppliers who submitted their first product in first 30 days
Denominator: # new suppliers who created account 30+ days ago
Target: 60%+
Note: Measures getting new suppliers into the loop
```

**Completion Rate**
```
Numerator: # wizard sessions that resulted in submission
Denominator: # wizard sessions started (any supplier, any submission)
Time Window: Same session or within 7 days of start
Target: 75%+
```

**Overall Approval Rate (Quality Indicator)**
```
Numerator: # all submissions approved by curation
Denominator: # all submissions reviewed (exclude pending)
Target: 70%+
Note: Predicts if suppliers will return (the loop)
```

**Product Activation Rate (Quality Indicator)**
```
Numerator: # approved products with ≥1 booking within 30 days
Denominator: # approved products that have been live for 30+ days
Target: 45%+
Note: Products with bookings drive faster return to submission
```

### Level 2: Retention Metrics

**Return Rate (PRIMARY)**
```
Numerator: # suppliers who submitted another product within 90 days of their last submission
Denominator: # suppliers who submitted a product 90+ days ago
Note: Measures the loop - how many come back after each submission
Example: If supplier submitted on Jan 1, did they submit again by Apr 1?
```

**Time to Next Submission**
```
Calculate: Days between consecutive submissions (submission N → submission N+1)
Report: Median across all suppliers
Example: Supplier submits on Jan 1 (1st product), then Feb 15 (2nd product) = 45 days
Target: <60 days median
Note: Measures loop speed - how fast do they come back
```

**30/60/90-Day Retention**
```
Numerator: # suppliers activated in Month 0 still active in Month 1/2/3
Denominator: # suppliers activated in Month 0
Active: Submitted ≥1 product in the month
```

### Level 3: Growth Metrics

**Revenue per Approved Product (90-day)**
```
Numerator: Total GMV from products created 90+ days ago
Denominator: # approved products in that cohort
Cohort: Products approved 90 days ago (rolling)
Note: All products created through wizard (only creation method)
```

**Supplier Retention by Creation Frequency**
```
Formula: 90d retention rate for suppliers creating 5+ products vs 1-2 products
Segments: 
  - Power: 5+ products
  - Regular: 2-4 products
  - Light: 1 product
Control for: Supplier size, market, account age
Method: Cohort retention analysis
```

**Cross-Feature Engagement**
```
Numerator: # product creators who also used Performance Hub OR Recommended Actions
Denominator: # product creators (≥1 product submitted)
Time Window: Within 90 days of first product creation
```

**Supplier LTV by Engagement Tier**
```
LTV = Total GMV generated by supplier over lifetime
Tiers:
  - Power users: 5+ products created
  - Regular users: 2-4 products created
  - Light users: 1 product created
Calculate: Avg LTV per tier, compare Power/Light ratio
Target: Power users ≥3x Light users
```

---

*Framework Version 2.0 - Simplified & Structured*
*Last Updated: May 2026*
