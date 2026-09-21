# Supplier Portal Engagement Framework
## Product Creation Wizard

---

## What is an Engagement Framework?

An **engagement framework** is a structured approach to measuring, understanding, and improving how users interact with a product feature over time. Rather than tracking isolated metrics, it provides a holistic view of the user journey from first use to long-term value creation.

### Purpose of This Framework

**Primary Purpose:** Determine if the Product Creation Wizard is driving sustainable long-term business value.

**Secondary Purposes:**
1. **Diagnose** where the feature is failing (Level 1? Level 2? Level 3?)
2. **Prioritize** what to optimize (fix broken levels first, then optimize working ones)
3. **Measure Impact** to justify continued investment in the feature

### What Determines Success?

**Success = Level 3 shows positive business impact:**
- Wizard users have higher LTV than non-users
- Platform inventory is growing sustainably through wizard submissions
- Quality is maintained at scale (approval rates stable or improving)
- Wizard usage drives broader ecosystem engagement

**You cannot reach Level 3 success without Level 1 and Level 2 working:**
- If Level 1 is broken (low submission rate) → Fix engagement first
- If Level 2 is broken (low return rate) → Fix retention first
- If Level 1 & 2 work but Level 3 doesn't → Feature isn't delivering business value

### Three Questions This Framework Answers

1. **Level 1: Growing Engaged Users** - Are suppliers discovering and using the wizard?
2. **Level 2: Retaining Users** - Are they coming back to create more products?
3. **Level 3: Value Creation** - Is the wizard driving sustainable business value?

---

## The Three-Level Engagement Hierarchy

This framework is based on **Sarah Tavel's Hierarchy of Engagement** and best practices from leading product analytics companies (Amplitude, Pendo, Mixpanel):

```
┌─────────────────────────────────────────────────────────────┐
│                                                             │
│  LEVEL 3: VALUE CREATION                                    │
│  └─ Does engagement drive business outcomes?                │
│     (Revenue, LTV, Platform Growth)                         │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  LEVEL 2: RETAINING USERS                                   │
│  └─ Do users return and form habits?                        │
│     (Repeat Usage, Frequency, Retention)                    │
│                                                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  LEVEL 1: GROWING ENGAGED USERS                             │
│  └─ Do users complete the core action successfully?         │
│     (Submission, Completion, Approval, Success)             │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Level 1: Growing Engaged Users (Activation)
**Question:** Are suppliers successfully submitting products?

**Goal:** Submit a product through the wizard

**Why This is the Goal:** Submission is the only action suppliers control. They cannot control approval (curation decides) or bookings (marketplace decides).

**Why Track Outcomes?**
- **Approval Rate:** Low rate = Wizard guidance isn't working → Won't return
- **Booking Rate:** Low rate = Products aren't marketplace-ready → Won't return
- Both outcomes predict Level 2 retention

**Key Metrics:** 
- **Engagement Goal:** Submission Rate, Completion Rate (what users do - under their control)
- **Outcome Metrics:** Approval Rate, 30D Booking Rate (not under user control, but predict retention)

### Level 2: Retaining Users (Habit Formation)
**Question:** Do suppliers return to create more products?

**Habit Loop:** Submit → Approve → Go Live → Get Bookings → Submit More

**Why It Matters:** One-time usage doesn't drive sustainable value. This level measures whether suppliers form a habit of regularly creating products through the wizard.

**Key Metrics:** Return Rate, Days Between Submissions, Repeat Usage Rate, Retention Cohorts

### Level 3: Value Creation (Business Impact)
**Question:** Does the wizard drive sustainable long-term business value?

**THIS IS THE SUCCESS CRITERIA:** If Level 3 doesn't work, the feature is failing - even if Level 1 & 2 are good.

**Virtuous Cycle:** More products → More revenue → More engagement → Platform growth

**What We're Proving:**
- Wizard users have higher LTV than non-users
- Platform inventory grows sustainably through wizard
- Quality is maintained at scale
- Wizard drives broader ecosystem engagement

**Key Metrics:** Revenue per Product, LTV by Engagement Tier, Retention Lift, Product Performance, Cross-Feature Engagement

---

## How to Use This Framework

### 1. Measurement-Driven Approach

This framework follows a **"measure first, set targets later"** philosophy:

**Step 1: MEASURE (Weeks 1-4)**
- Implement tracking for all Level 1 & Level 2 metrics
- Collect 4-8 weeks of baseline data
- Build initial dashboard

**Step 2: UNDERSTAND (Weeks 5-6)**
- Analyze distributions (P25/P50/P75)
- Identify trends (improving/declining/stable)
- Find patterns (what predicts success?)
- Understand segmentation differences

**Step 3: SET TARGETS (Week 7)**
- Based on current P75 (top quartile)
- Based on best-performing cohort
- Based on improvement trajectory
- Realistic but aspirational

**Step 4: ITERATE (Ongoing)**
- Track against targets
- Test interventions
- Adjust targets as you learn
- Continuously improve

### 2. Read the Framework by Level

Each level has:
- **Primary Metrics** - What to track to understand that level
- **Secondary Metrics** - Diagnostic metrics for deeper investigation
- **Key Questions** - What you're trying to answer
- **Targets** - Example benchmarks (establish your own through measurement)

### 3. Segment by Supplier Lifecycle

The framework tracks **New Suppliers** (<90 days) and **Existing Suppliers** (≥90 days) separately because they have different behavior patterns:

- **New Suppliers:** Focus on activation (first product) and early retention (2nd product)
- **Existing Suppliers:** Focus on ongoing engagement and long-term value

### 4. Progressive Focus (Optimization Waterfall)

**The framework shows you WHERE to focus improvements:**

```
┌─────────────────────────────────────────────────────────┐
│ Is Level 1 working? (Are suppliers submitting?)        │
│ No → FIX LEVEL 1 FIRST (improve discovery, reduce      │
│      friction, improve guidance)                        │
│ Yes → Move to Level 2                                   │
└─────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────┐
│ Is Level 2 working? (Are suppliers returning?)         │
│ No → FIX LEVEL 2 (improve success rates, nurture,      │
│      notifications, win-back campaigns)                 │
│ Yes → Move to Level 3                                   │
└─────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────┐
│ Is Level 3 working? (Driving business value?)          │
│ No → FEATURE ISN'T SUCCESSFUL - Consider pivot/sunset  │
│ Yes → FEATURE IS SUCCESSFUL - Optimize & scale         │
└─────────────────────────────────────────────────────────┘
```

**Key Principle:** You cannot fix Level 3 if Level 1 or 2 is broken. Fix foundational levels first.

### 5. Weekly Review Cadence

Use the dashboard structure (see "Measurement Dashboard" section) for weekly reviews:
- **Level 1:** Are suppliers engaging? (Weekly check)
- **Level 2:** Are they returning? (Weekly check)
- **Level 3:** Is it driving value? (Weekly check)
- **Insights:** What changed? What should we do?

---

## Determining Feature Success

**The feature is SUCCESSFUL if Level 3 shows positive business impact:**

| Success Indicator | What to Look For | Why It Matters |
|-------------------|------------------|----------------|
| **LTV Lift** | Wizard users have 20%+ higher LTV than non-users | Proves feature drives supplier value |
| **Inventory Growth** | Consistent catalog growth through wizard submissions | Proves feature drives platform value |
| **Quality Sustainability** | Approval rates stable/improving as volume scales | Proves feature maintains quality at scale |
| **Ecosystem Engagement** | 40%+ of wizard users engage with other features | Proves feature drives broader engagement |
| **Retention Lift** | Wizard users have higher retention than non-users | Proves feature drives loyalty |

**The feature is FAILING if:**
- Level 3 metrics show no business impact (even if Level 1 & 2 are good)
- LTV of wizard users = LTV of non-users (feature not driving value)
- Quality declining as volume grows (not sustainable)
- High cost to maintain with low business return

**Decision Framework:**

```
Level 1 + Level 2 + Level 3 = FEATURE SUCCESS
  ✓       ✓         ✓      → Optimize & scale
  ✓       ✓         ✗      → Feature not delivering value → Pivot or sunset
  ✓       ✗         ?      → Fix retention first → Then measure Level 3
  ✗       ?         ?      → Fix engagement first → Then measure Level 2 & 3
```

---

## Key Principles

1. **Success = Level 3 Impact:** The feature is only successful if it drives long-term business value
2. **Engagement = What Users Control:** The Level 1 goal is **Submit a product** - the only action suppliers control
3. **Outcomes ≠ Goals:** Approval and bookings are OUTCOMES, not goals. Suppliers cannot control curation decisions or marketplace demand
4. **Why Track Outcomes:** Low approval/booking rates predict low Level 2 retention → tells us wizard guidance needs improvement
5. **Funnel, Not Just Count:** Track the journey (submit → approve → booking), not just totals
6. **Distributions Over Averages:** Use P25/P50/P75 to understand the full picture, not just mean
7. **Trends Over Snapshots:** Track MoM/WoW changes to see if things are improving
8. **Segments Matter:** New vs Existing suppliers behave differently - analyze separately
9. **Measure to Learn:** Don't start with arbitrary targets - measure first, then set informed goals

---

## Framework Overview

This framework measures engagement with the Product Creation Wizard using the three-level hierarchy:

1. **Level 1: Growing Engaged Users** - Getting suppliers to submit products and experience success
2. **Level 2: Retaining Users** - Getting suppliers to return and submit more products
3. **Level 3: Value Creation** - Products drive supplier success and platform growth

---

## Segmentation

We segment suppliers into **New** (<90 days) and **Existing** (≥90 days) to understand different behavior patterns:

| Segment | Definition | Level 1 Focus | Level 2 Focus | Level 3 Focus |
|---------|-----------|---------------|---------------|---------------|
| **New Suppliers** | Account age <90 days | First product submission | 2nd product submission | Early revenue (first 90d) |
| **Existing Suppliers** | Account age ≥90 days | Ongoing submissions | Return frequency | Long-term LTV |

**Behavioral Tiers (within each segment):**

| Tier | Definition | Size Target | Goal |
|------|-----------|-------------|------|
| **Power Users** | 5+ products, active monthly | 10-15% | Sustain & scale |
| **Regular Users** | 2-4 products, active quarterly | 25-30% | Convert to power |
| **Light Users** | 1 product, occasional | 30-40% | Convert to regular |
| **One-and-Done** | 1 product, 60+ days inactive | <25% | Minimize this segment |

---

## Level 1: Growing Engaged Users

**Goal:** Get suppliers to submit products

**Why This is the Goal:** Submission is the only action suppliers control. They cannot control approval (curation decides) or bookings (marketplace decides).

**Core Action:** Submit a product through the wizard

**What We Measure:**

**1. Engagement Metrics (What Suppliers DO - Under Their Control):**
- Discover and enter the wizard
- Complete the wizard steps
- Submit the product ✓ ← **LEVEL 1 GOAL**

**2. Outcome Metrics (Value Delivered - NOT Under Supplier Control):**
- Product gets approved (curation decides, wizard influences through guidance)
- Product gets bookings within 30 days (marketplace decides)

**Why Track Outcomes?**
- **Low approval rate** → Wizard guidance isn't working → Suppliers won't return
- **Low booking rate** → Products aren't marketplace-ready → Suppliers won't return
- Both outcomes predict Level 2 retention behavior

### Engagement Metrics (Level 1 Goal - What Users DO)

These measure the core action suppliers control:

| Metric | Definition | New Suppliers | Existing Suppliers | Why It Matters |
|--------|-----------|---------------|-------------------|----------------|
| **Submission Rate** | % who submit ≥1 product | % submitting first product in 30d | % submitting in the month | **LEVEL 1 GOAL** - are they completing the core action? |
| **Completion Rate** | % of started sessions → submitted | % completing first submission | % completing submissions | Identifies friction in creation flow |

### Outcome Metrics (Value Delivered - NOT Under User Control)

These measure if the wizard delivers value. Low rates predict low Level 2 retention:

| Metric | Definition | New Suppliers | Existing Suppliers | Why Track It |
|--------|-----------|---------------|-------------------|----------------|
| **Approval Rate** | % of submissions → approved | First approval rate | Sustained approval rate | Low rate = wizard guidance isn't working → won't return |
| **30D Booking Rate** | % of approved → ≥1 booking in 30d | First product booking rate | Product booking rate | Low rate = products aren't marketplace-ready → won't return |

### Secondary Metrics (Diagnostic)

**Engagement Diagnostics:**

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Time to First Submission** | Days from account creation to first submission (new suppliers only) | Speed to completing core action |
| **Days Between Submissions** | Time between consecutive submissions (existing suppliers only) | Engagement cadence |
| **Step-by-Step Dropoff** | Completion rate at each wizard step | Identifies specific friction points |
| **Draft Save Rate** | % of sessions ending in draft vs submission | Intent vs completion gap |

**Outcome Diagnostics:**

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Rejection Reason Distribution** | Top reasons for submission rejection | Guides wizard guidance improvements |
| **Resubmission Rate** | % of rejected users who submit again within 14 days | Measures resilience after rejection |
| **Time to First Booking** | Days from approved → first booking | How fast do products generate value? |

### Key Questions

1. **Engagement Goal:** What % of new suppliers submit first product in 30d? What % of existing submit monthly?
2. **Completion:** Where do suppliers drop off in the wizard? Is completion improving?
3. **Outcomes (Predict Level 2):**
   - What % of submissions get approved? (Low = wizard guidance not working)
   - What % of approved products get bookings in 30d? (Low = products not marketplace-ready)
   - Do these outcomes predict Level 2 return rate?
4. **Improvement:** What are top rejection reasons? Can we prevent them through better wizard guidance?

### Targets (Discover First, Then Set)

Start by measuring for 4-8 weeks to establish baselines. Example targets based on industry benchmarks:

**Engagement Targets (Level 1 Goal - What Suppliers Control):**
- **New Suppliers:** 60%+ submit first product in 30 days
- **Existing Suppliers:** 40-50% submit each month
- **Completion Rate:** 75%+ (started → submitted)

**Outcome Targets (Value Delivered - Predicts Level 2 Return):**
- **Approval Rate:** 70%+ (low = wizard guidance not working → fix guidance)
- **30D Booking Rate:** 45%+ (low = products not marketplace-ready → improve quality/content guidance)

---

## Level 2: Retaining Users

**Goal:** Get suppliers to return and submit more products (habit formation)

**Habit Loop:** Submit product → Approve → Go live → Get bookings → Submit more

**Success Indicators:**
- Suppliers return to create 2nd, 3rd, 5th product
- Days between submissions stays stable or decreases
- Consistent monthly activity

### Primary Metrics

| Metric | Definition | New Suppliers | Existing Suppliers | Why It Matters |
|--------|-----------|---------------|-------------------|----------------|
| **Return Rate** | % who submit another product within X days | % submitting 2nd product within 30/60/90 days | % returning within 30/60/90 days of last submission | Core retention metric |
| **Days Between Submissions** | Time between consecutive submissions | Days from 1st → 2nd product | Median days between submissions | Engagement cadence |
| **Repeat Usage Rate** | % who reach milestone submissions | % reaching 2nd, 3rd, 5th product | % submitting 2+ products per month | Habit formation |
| **Retention Cohorts** | % still active after X days | % still active at 30/60/90 days | % active in 3/6/12 months | Long-term retention health |

### Secondary Metrics

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Power User Formation Rate** | % reaching 5+ products within 90 days | Identifies scaling engagement |
| **Dormancy Recovery Rate** | % of dormant users (90+ days) who return | Win-back effectiveness |
| **Consistency Patterns** | # of months active out of last 6 months | Identifies sporadic vs consistent users |
| **Post-Rejection Return Rate** | % of rejected users who resubmit within 14/30 days | Resilience indicator |
| **Submission Frequency** | Products per active supplier per month | Distribution (P25/P50/P75) | Intensity of usage |

### Engagement Loops

These self-reinforcing cycles drive sustainable retention:

1. **Success Loop:** Create product → Approve → Go live → Get bookings → Create more
2. **Learning Loop:** Submit → Get feedback → Improve → Higher approval rate → Confidence grows
3. **Catalog Loop:** More products → Better portfolio → Higher visibility → More motivation to create

### Key Questions

1. **New Suppliers:** What % create 2nd product? When? What predicts 2nd product creation?
2. **Existing Suppliers:** What % return each month? Is frequency stable or declining?
3. **Patterns:** What differentiates power users from one-time users?
4. **Recovery:** Do rejected users return? What increases comeback rate?
5. **Cadence:** What's the natural submission rhythm? Weekly? Monthly? Seasonal?

### Targets (Discover First, Then Set)

Example targets based on industry benchmarks:

- **New Suppliers:** 40%+ submit 2nd product within 90 days
- **Existing Suppliers:** 55%+ return within 90 days of last submission
- **Power User Formation:** 10-15% of activated suppliers reach 5+ products
- **90D Retention:** 60%+ of activated suppliers still active at 90 days
- **Median Days Between:** <60 days (target cadence)

---

## Level 3: Value Creation (ULTIMATE SUCCESS MEASURE)

**Goal:** Prove the wizard drives sustainable long-term business value

**THIS IS WHAT DETERMINES FEATURE SUCCESS:**
- If Level 3 works → Feature is successful → Optimize & scale
- If Level 3 doesn't work → Feature is failing → Pivot or sunset

**Virtuous Cycle:** Create products → Generate revenue → More motivation → Create more → Platform grows

**What We Must Prove:**
- Wizard users have higher LTV than non-users (20%+ lift)
- Platform inventory grows sustainably through wizard
- Quality is maintained at scale (approval rates stable/improving)
- Wizard drives broader ecosystem engagement (40%+ engage with other features)

**Why This Matters:** Level 1 & 2 measure engagement and retention, but Level 3 measures if that engagement translates to actual business value. Without Level 3 success, the feature isn't worth maintaining.

### Primary Metrics

| Metric | Definition | New Suppliers | Existing Suppliers | Why It Matters |
|--------|-----------|---------------|-------------------|----------------|
| **Revenue per Product** | GMV generated per product at 90 days | First 90 days revenue distribution | LTV by product | Business value of feature |
| **LTV by Engagement Tier** | LTV: Power vs Regular vs Light | Early LTV (first 90d) | Lifetime LTV | Value of driving engagement |
| **Product Performance** | Booking rate, revenue trend over time | First product performance | Product portfolio performance | Quality sustainability |
| **Cross-Feature Engagement** | % engaging with Performance Hub, other features | % engaging in first 90d | % engaging overall | Ecosystem engagement |

### Secondary Metrics

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Supplier Retention by Creation Frequency** | 90-day retention: 5+ products vs 1-2 products | Does creating more drive loyalty? |
| **Product Defect Rate** | % of products with quality issues post-launch | Quality sustainability at scale |
| **Category Diversification** | % creating products across multiple categories | Portfolio strategy insights |
| **Curation Efficiency** | Time saved per product via preventative guidance | Operational benefit |
| **Supplier Satisfaction (NPS)** | NPS for active creators | Feature satisfaction |
| **Revenue Contribution** | % of total GMV from new vs existing suppliers | Platform health |

### Key Questions (Proving Feature Success)

1. **LTV Lift:** Do wizard users have higher LTV than non-users? By how much? (Need 20%+ to prove value)
2. **Engagement Tiers:** Do suppliers who create more products have higher LTV? (Proves more engagement = more value)
3. **Retention Lift:** Do wizard users have higher retention than non-users? (Proves feature drives loyalty)
4. **Quality at Scale:** Is approval rate stable/improving as submission volume grows? (Proves sustainability)
5. **Inventory Growth:** Is the wizard driving consistent catalog growth? (Proves platform impact)
6. **Ecosystem Impact:** Does wizard usage drive engagement with other features? (Proves broader value)

**If answers to these questions are "NO" or "MINIMAL" → Feature is not successful, even if Level 1 & 2 are good**

### Success Thresholds (What Proves Feature Value)

**These thresholds determine if the feature is successful:**

| Success Metric | Threshold | What It Proves |
|----------------|-----------|----------------|
| **LTV Lift** | Wizard users have 20%+ higher LTV than non-users | Feature drives supplier value |
| **LTV by Engagement** | Power users (5+) have 3x LTV vs Light (1) | More engagement = more value |
| **Retention Lift** | Wizard users have +20% retention vs non-users | Feature drives loyalty |
| **Quality at Scale** | Approval rate stable or improving as volume grows | Feature is sustainable |
| **Inventory Growth** | Consistent month-over-month catalog growth | Feature drives platform value |
| **Ecosystem Engagement** | 40%+ engage with other features | Feature drives broader engagement |

**Decision Criteria:**
- **All thresholds met** → Feature is successful → Invest & scale
- **Most thresholds missed** → Feature is failing → Pivot or sunset
- **Mixed results** → Investigate which segments/use cases work → Double down or cut

---

## Measurement Dashboard Structure

### Weekly Review Dashboard

```
┌─────────────────────────────────────────────────────────────┐
│              PRODUCT CREATION WIZARD DASHBOARD              │
│                    Week of May 26, 2026                     │
└─────────────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════════
                LEVEL 1: GROWING ENGAGED USERS (GOAL: SUBMIT)
═══════════════════════════════════════════════════════════════

COMBINED VIEW
  ENGAGEMENT (what users do - LEVEL 1 GOAL):
    Submission Rate: 58% submitted this month ← GOAL
    Completion Rate: 72% (started → submitted)
  
  OUTCOMES (value delivered - predicts Level 2 return):
    Approval Rate: 71% (low = guidance not working)
    30D Booking Rate: 48% (low = products not marketplace-ready)
  
  Trend: Submission ▼ -2% MoM | Completion ▲ +1% | Approval ▬ stable

NEW SUPPLIERS (<90 days): 2,100 new accounts this month
  ENGAGEMENT (GOAL): Activation: 58% submit first product in 30d
  ENGAGEMENT: Completion: 72%
  
  OUTCOMES (predict Level 2 return):
    Approval: 68% (low = guidance not working)
    30D Booking: 45% (low = not marketplace-ready)
  
  Time to First: P25: 12d | P50: 28d | P75: 48d
  Trend: Activation ▼ -2% vs prior cohort

EXISTING SUPPLIERS (≥90 days): 6,250 total
  ENGAGEMENT (GOAL): Monthly Submission: 48% (3,000 suppliers)
  ENGAGEMENT: Completion: 76%
  
  OUTCOMES (predict Level 2 return):
    Approval: 75% (better than new suppliers)
    30D Booking: 52% (better than new suppliers)
  
  Days Between: P25: 18d | P50: 38d | P75: 72d
  Trend: Submission ▬ stable


═══════════════════════════════════════════════════════════════
                      LEVEL 2: RETENTION
═══════════════════════════════════════════════════════════════

NEW SUPPLIERS
  2nd Product Rate: 35% create 2nd product within 90d
  Time 1st→2nd: P25: 22d | P50: 52d | P75: 95d
  
  90D Retention: 35% still active at 90 days
  Trend: ▼ -3% vs prior cohort

EXISTING SUPPLIERS
  Return Rate: 30d: 35% | 60d: 48% | 90d: 55%
  Days Between: P25: 18d | P50: 38d | P75: 72d
  
  Consistency: 18% always active (6/6 months) | 40% frequently (4-5/6)
  Trend: Return rate (90d) ▲ +2% MoM


═══════════════════════════════════════════════════════════════
                      LEVEL 3: VALUE
═══════════════════════════════════════════════════════════════

REVENUE PER PRODUCT (90d)
  Overall: P25: €850 | P50: €2,850 | P75: €6,200
  New Suppliers: P50: €1,200 (first 90d)
  Existing: P50: €3,200
  
  Trend: ▲ +12% MoM (median)

LTV BY ENGAGEMENT TIER (Existing Suppliers)
  Power (5+): P50: €18,500 (n=625, 10%)
  Regular (2-4): P50: €8,200 (n=1,875, 30%)
  Light (1): P50: €5,800 (n=3,750, 60%)
  
  Multiplier: Power users 3.2x vs Light

ECOSYSTEM ENGAGEMENT
  Cross-Feature: 42% use Performance Hub or other features
  Revenue Contribution: 82% of platform GMV from existing suppliers


═══════════════════════════════════════════════════════════════
                       KEY INSIGHTS
═══════════════════════════════════════════════════════════════

📊 Level 1 (Growing Engaged Users - Goal: Submit):
   • GOAL: 58% of new suppliers submit in 30d (down 2%)
   • GOAL: 48% of existing submit monthly (stable)
   • ENGAGEMENT: 72-76% completion rate (improving +1%)
   • OUTCOME: 68-75% approval rate (wizard guidance working)
   • OUTCOME: 45-52% get bookings in 30d (products marketplace-ready)
   • These outcomes predict Level 2 return behavior

📊 Level 2 (Retention):
   • Only 35% of new suppliers create 2nd product (biggest dropoff)
   • Existing suppliers: 55% return within 90 days
   • Median time between: 38 days (stable)

📊 Level 3 (Value):
   • Products generate €2,850 at 90d (median, up 12%)
   • Power users (5+) have 3.2x LTV vs light users (1 product)
   • 82% of GMV comes from existing suppliers

🎯 Focus Areas:
   1. Increase new supplier 2nd product rate (35% → 45%)
   2. Maintain existing supplier submission rate (48%)
   3. Move suppliers from Light → Regular → Power tiers
```

---

## Implementation Priorities

### Phase 1: Foundation (Weeks 1-4)
1. Implement tracking for all Level 1 & 2 metrics
2. Build core dashboard (3 levels + segmentation)
3. Establish 4-8 week baseline averages
4. Map user journey and identify dropoff points

### Phase 2: Level 1 Optimization (Weeks 5-8)
1. Fix top 3 friction points in wizard flow → Increase completion rate
2. Enhance curation preview → Improve approval rate
3. Test category-specific guidance → Reduce rejection rate
4. Improve onboarding → Increase activation rate

**Success Criteria:**
- +10% improvement in activation rate (58% → 64%)
- +5% improvement in first approval rate (68% → 71%)
- Completion rate maintained or improved

### Phase 3: Level 2 Optimization (Weeks 9-16)
1. Launch email nurture campaigns by segment
2. Implement success notifications (first booking, milestones)
3. Build win-back campaigns for dormant users
4. Analyze and document power user patterns

**Success Criteria:**
- +15% improvement in 2nd product rate (35% → 40%)
- +10% improvement in 90d retention
- Power user segment reaches 12%+

### Phase 4: Level 3 Optimization (Weeks 17-24)
1. Validate LTV correlation by engagement tier
2. Launch category-specific optimization experiments
3. Implement cross-feature engagement prompts
4. Build supplier success showcase

**Success Criteria:**
- €2,850+ GMV per product (90-day median)
- +30% retention for power users vs light users
- +40% cross-feature engagement
- Quality maintained at scale

---

## Key Takeaways

1. **Level 1 = Growing Engaged Users:** Focus on submission, completion, approval, and booking success
2. **Level 2 = Retaining Users:** Focus on return rate, frequency, and habit formation
3. **Level 3 = Value Creation:** Focus on revenue, LTV, and ecosystem engagement
4. **Segmentation:** New vs Existing suppliers have different patterns and needs
5. **Measure First:** Establish baselines before setting targets
6. **Iterate:** Continuously test, learn, and improve based on data

---

*Framework Version 3.0 - Clean & Focused*
*Last Updated: May 2026*
