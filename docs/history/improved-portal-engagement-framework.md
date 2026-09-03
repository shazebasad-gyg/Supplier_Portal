# Improved Supplier Portal Engagement Framework
## Product Creation Wizard (Smart Creation)

---

## Executive Summary

This framework provides a comprehensive approach to measuring and optimizing engagement with the Product Creation Wizard, based on industry best practices from Pendo, Sarah Tavel's Hierarchy of Engagement, and leading tech companies (Amplitude, Mixpanel, Intercom).

**Key Improvements:**
- Clear North Star Metric tied to business outcomes
- Behavioral cohort segmentation based on actual usage patterns
- Engagement loops that drive sustainable growth
- Leading indicators for proactive intervention
- Quality-weighted metrics (not just frequency)

---

## 1. Framework Foundation

### Core Engagement Definition

**Engagement = Breadth × Depth × Frequency × Quality**

For Product Creation Wizard:
- **Breadth**: How many suppliers have activated the feature
- **Depth**: How thoroughly suppliers complete the creation process
- **Frequency**: How often suppliers return to create more products
- **Quality**: Whether submissions meet curation standards and drive business outcomes

### North Star Metric

**Weekly Approved Product Submissions (WAPS)**

*Why this metric:*
- Combines activation (breadth), retention (frequency), and quality (approval rate)
- Directly tied to marketplace inventory growth
- Actionable: can be decomposed into its components for diagnosis
- Balanced: prevents gaming (high volume with low quality won't improve WAPS)

**Formula:**
```
WAPS = Weekly Active Creators (WAC) × Avg Submissions per Creator × Approval Rate
```

---

## 2. The Engagement Hierarchy (Sarah Tavel Framework)

### Level 1: Growing Engaged Users (Activation & Aha Moment)

**Goal:** Get suppliers to experience value from their first product creation

**Core Action:** Successfully submit a product through the wizard

**Aha Moment:** "I can easily create professional product listings"

#### Primary Metrics

| Metric | Definition | Target | Why It Matters |
|--------|-----------|--------|----------------|
| **Feature Adoption Rate** | % of active suppliers who start wizard in first 30 days | 60%+ | Measures discovery and initial interest |
| **Completion Rate** | Started wizard → Submitted product | 75%+ | Identifies friction in creation flow |
| **Time to First Submission** | Median days from account creation to first submission | <7 days | Speed to value indicator |
| **First Submission Approval Rate** | % of first submissions approved by curation | 70%+ | Quality of onboarding guidance |
| **Time to First Approval** | Median days from submission to approval | <3 days | Full value realization speed |

#### Secondary Metrics (Diagnostic)

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Wizard Entry Rate** | % of suppliers who click "Create Product" | Measures feature visibility |
| **Step Completion Funnel** | Completion rate by wizard step | Identifies specific friction points |
| **Field Completion Rate** | % of fields filled (by required vs optional) | Measures guidance clarity |
| **Draft Save Rate** | % of sessions ending in draft save vs submit | Intent vs completion gap |
| **Activation by Cohort** | Activation rate by supplier segment | Identifies which segments need help |

#### Behavioral Indicators (Leading)

- **Session Duration**: Optimal range 15-25 min (too short = rushed, too long = confused)
- **Help/Guidance Engagement**: % using tooltips, examples, AI suggestions
- **Curation Preview Usage**: % previewing curation checks before submit
- **Category Prediction Accuracy**: % accepting vs overriding category prediction
- **Rejection Reason Distribution**: Top 5 reasons for first submission rejection

#### Key Questions to Answer

1. **Activation**: What % of new suppliers submit within 7/14/30 days?
2. **Friction**: Where do suppliers drop off in the wizard? (Step-level funnel)
3. **Guidance**: Are suppliers using help features? Do they correlate with approval?
4. **Quality**: What are the top rejection reasons? Are they addressable through guidance?
5. **Segmentation**: Which supplier types activate fastest? Slowest?

#### Success Threshold

- **60%+ of new suppliers** submit within 30 days
- **75%+ completion rate** (started → submitted)
- **70%+ approval rate** on first submission
- **<7 days** median time to first submission

---

### Level 2: Retaining Users (Habitual Behavior)

**Goal:** Suppliers return regularly to create products (habit formation)

**Habit Trigger:** "I need to expand my catalog" → Use wizard

**Reward:** Products get approved, go live, generate bookings

#### Primary Metrics

| Metric | Definition | Target | Why It Matters |
|--------|-----------|--------|----------------|
| **Repeat Usage Rate** | % of activated users who submit 2+ products | 40%+ | Measures habit formation |
| **Return Rate** | % of users returning within 7/30/90 days after first submission | 30/50/60% | Retention cohort analysis |
| **Weekly Active Creators (WAC)** | # suppliers submitting ≥1 product per week | Growing | Core engagement volume |
| **Monthly Active Creators (MAC)** | # suppliers submitting ≥1 product per month | Growing | Broader engagement volume |
| **Stickiness Ratio** | WAC / MAC | 25%+ | Measures habit strength |
| **Submission Frequency** | Median products submitted per active user per month | 2+ | Intensity of engagement |

#### Secondary Metrics (Diagnostic)

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **L7/L30 Retention** | % of Day 1 users still active on Day 7/30 | Early retention health |
| **Cohort Retention Curves** | % of activated users still active by cohort month | Long-term retention trends |
| **Products per Lifecycle Stage** | Avg products created in months 1/2/3/6/12 | Usage maturation patterns |
| **Sustained Approval Rate** | Approval rate for submissions 2-5+ | Quality maintenance over time |
| **Power User Formation Rate** | % of activated users reaching 5+ products | Scale user identification |
| **Dormancy Recovery Rate** | % of dormant users (60+ days) who return | Winback effectiveness |

#### Behavioral Indicators (Leading)

- **Days Between Submissions**: Distribution and trends (are gaps widening?)
- **Session Consistency**: Regularity of wizard visits (predictable vs sporadic)
- **Product Portfolio Growth**: Trajectory of catalog expansion by supplier
- **Rejection Recovery**: % of rejected users who resubmit within 7/14/30 days
- **Category Diversification**: % of users creating products across multiple categories
- **Draft Accumulation**: # of abandoned drafts (potential pipeline indicator)

#### Engagement Loops (Virtuous Cycles)

1. **Success Loop**: Create product → Approve → Go live → Get bookings → Create more
2. **Learning Loop**: Submit → Get feedback → Improve → Higher approval rate → Confidence
3. **Catalog Loop**: More products → Better portfolio → Higher visibility → More motivation

#### Key Questions to Answer

1. **Retention**: What % submit 2nd product? 3rd? 5th? (retention milestones)
2. **Timing**: What's the optimal cadence for product creation? (weekly/monthly)
3. **Patterns**: What differentiates power users from one-time users?
4. **Recovery**: Do rejected users return? What increases comeback rate?
5. **Maturation**: How does usage evolve over supplier lifetime (3/6/12 months)?

#### Success Threshold

- **40%+ of activated suppliers** submit 2+ products within 90 days
- **25%+ stickiness ratio** (WAC/MAC)
- **60% retention** at 90 days (M0 → M3)
- **2+ products per active supplier** per month

---

### Level 3: Self-Perpetuating Growth (Network Effects & Value Creation)

**Goal:** Successful product creation drives supplier success, platform growth, and viral acquisition

**Virtuous Cycle:** Success → More creation → Better marketplace → More bookings → More suppliers

#### Primary Metrics

| Metric | Definition | Target | Why It Matters |
|--------|-----------|--------|----------------|
| **Revenue per Approved Product** | GMV/NR per wizard product (30/60/90 days) | €X+ | Business value creation |
| **Catalog Growth Rate** | Net new products added via wizard per month | 8,000+ | Platform inventory health |
| **Supplier Retention Lift** | Retention rate: wizard users vs non-users | +20% | Feature drives loyalty |
| **Wizard Product Performance** | GMV/bookings: wizard vs non-wizard products | At parity or better | Quality validation |
| **Cross-Feature Engagement** | % of wizard users engaging with Performance Hub, Recommended Actions | 40%+ | Ecosystem engagement |
| **Supplier LTV by Engagement Tier** | LTV: Power/Regular/Light/Inactive users | Power users >>Light | Value of engagement |

#### Secondary Metrics (Diagnostic)

| Metric | Definition | Purpose |
|--------|-----------|---------|
| **Activation to First Booking** | % of approved products with ≥1 booking in 30 days | Product-market fit |
| **Product Defect Rate** | % of wizard products with quality issues | Quality sustainability |
| **Curation Team Efficiency** | Hours saved via preventative guidance | Operational benefit |
| **Supplier Satisfaction (NPS/CSAT)** | NPS for wizard users vs overall | Feature satisfaction |
| **Referral/Advocacy Rate** | % of wizard users referring new suppliers | Viral coefficient |
| **Content Completeness Index** | Avg % of recommended fields completed | Quality trend |

#### Behavioral Indicators (Leading)

- **Performance Monitoring**: % of wizard users checking product analytics
- **Content Optimization**: % returning to edit/improve existing products
- **Seasonal Creation Patterns**: Timing of product creation (seasonal planning)
- **Portfolio Strategy**: Product mix by category (diversification vs specialization)
- **Engagement Correlation**: Does wizard usage predict portal engagement?

#### Business Impact Analysis

1. **Supplier Value**: Do wizard users have higher LTV? By how much?
2. **Product Quality**: Do wizard products perform as well as manually created products?
3. **Marketplace Health**: Does wizard adoption correlate with inventory growth?
4. **Network Effects**: Do successful creators recruit new suppliers?
5. **Cost Efficiency**: Does wizard reduce support tickets and curation burden?

#### Key Questions to Answer

1. **Business Value**: What revenue does the wizard drive? (direct + indirect)
2. **Quality Sustainability**: Are wizard products maintaining quality at scale?
3. **Virtuous Cycle**: Is there a success → more creation → more success loop?
4. **Ecosystem Impact**: Does wizard engagement drive broader portal usage?
5. **Acquisition**: Are wizard users net promoters? Do they refer others?

#### Success Threshold

- **€X+ GMV per product** within 90 days (benchmark to be established)
- **+20% retention lift** for wizard users vs non-users
- **40%+ cross-feature engagement** (Performance Hub, Recommended Actions)
- **At parity or better** performance vs non-wizard products
- **NPS 40+** for wizard users

---

## 3. User Segmentation (Behavioral Cohorts)

### Engagement-Based Segmentation

| Segment | Definition | Size Target | Engagement Goal | Intervention Strategy |
|---------|-----------|-------------|-----------------|----------------------|
| **Power Users** | 5+ products, active monthly | 10-15% | Scale & retain | VIP treatment, advanced features, feedback loop |
| **Regular Users** | 2-4 products, active quarterly | 25-30% | Convert to power | Encourage consistency, seasonal campaigns |
| **Light Users** | 1 product, returned 1-2 times | 30-40% | Convert to regular | Re-engagement campaigns, success stories |
| **One-and-Done** | 1 product, no return in 60+ days | 20-30% | Reactivate | Win-back campaigns, understand barriers |
| **Activated (New)** | 1 product submitted, <30 days old | Variable | Guide to 2nd product | Onboarding nurture, success tips |
| **Dormant** | No submission in 90+ days | Minimize | Resurrect or retire | High-value: personalized outreach; Low-value: automated |

### Lifecycle-Based Segmentation

| Segment | Definition | Primary Goal | Key Metric |
|---------|-----------|--------------|-----------|
| **New Suppliers** | Account <90 days, 0 products | Activate | First submission within 30 days |
| **Activated Suppliers** | 1 submission, waiting for approval/1st booking | Retain | 2nd submission within 30 days |
| **Expanding Suppliers** | 2-4 products, growing catalog | Scale | Reach 5+ products (power user) |
| **Mature Suppliers** | 5+ products, established catalog | Sustain | Maintain monthly activity |
| **At-Risk Suppliers** | 60+ days since last submission | Prevent churn | Return within 30 days |

### Quality-Based Segmentation

| Segment | Definition | Intervention |
|---------|-----------|--------------|
| **High Quality** | 80%+ approval rate, low defect rate | Showcase as examples, minimal guidance |
| **Improving** | Approval rate increasing over time | Positive reinforcement, continue support |
| **Struggling** | <50% approval rate, high rejection | Intensive guidance, 1:1 support |
| **Category-Specific Specialists** | High performance in specific category | Category ambassadors, peer mentors |

### Value-Based Segmentation

| Segment | Criteria | Priority | Approach |
|---------|----------|----------|----------|
| **High LTV** | Top 20% by revenue potential | Critical | White-glove support, concierge service |
| **Growth Potential** | Rising trajectory, not yet high LTV | High | Nurture, remove friction, incentivize |
| **Stable Contributors** | Consistent moderate value | Medium | Automated engagement, scalable support |
| **Low Value** | Minimal revenue contribution | Low | Self-service, automated only |

---

## 4. Metrics Dashboard Structure

### North Star Section (Primary Focus)

```
┌─────────────────────────────────────────────────────────┐
│  NORTH STAR: WEEKLY APPROVED PRODUCT SUBMISSIONS (WAPS) │
│                                                           │
│  Current: 1,850          Target: 2,200       Gap: -16%   │
│  ▲ +12% vs last week     Trend: ↗ Growing                │
│                                                           │
│  Breakdown:                                               │
│  • WAC: 425 creators (▲ 8%)                              │
│  • Submissions per creator: 5.2 (▼ 2%)                   │
│  • Approval rate: 83% (▲ 5%)                             │
└─────────────────────────────────────────────────────────┘
```

### Level 1: Activation Metrics (Growing Engaged Users)

**Primary (Weekly Review)**
- Feature Adoption Rate (30-day cohort)
- Completion Rate (started → submitted)
- First Submission Approval Rate
- Time to First Submission (median)

**Secondary (Monthly Deep Dive)**
- Step-by-step funnel conversion
- Field completion rates
- Draft save vs submit behavior
- Activation by supplier segment

### Level 2: Retention Metrics (Habitual Behavior)

**Primary (Weekly Review)**
- Repeat Usage Rate (activated → 2+ products)
- WAC & MAC (Weekly/Monthly Active Creators)
- Stickiness Ratio (WAC/MAC)
- Submission Frequency (products per active user)

**Secondary (Monthly Deep Dive)**
- Cohort retention curves (M1/M2/M3/M6)
- Return rate by time window (7/30/90 days)
- Power user formation rate (reaching 5+ products)
- Dormancy recovery rate

### Level 3: Growth Metrics (Value Creation)

**Primary (Monthly Review)**
- Revenue per Approved Product (GMV @ 90 days)
- Catalog Growth Rate (net new products/month)
- Supplier Retention Lift (wizard vs non-wizard)
- Cross-Feature Engagement Rate

**Secondary (Quarterly Deep Dive)**
- Wizard product performance vs baseline
- Supplier LTV by engagement tier
- Product defect rate trends
- NPS/CSAT by user segment

### Leading Indicators (Predictive Signals)

**Activation Risk**
- ⚠️ Low wizard entry rate (<40%)
- ⚠️ High step dropoff (>10% at any step)
- ⚠️ Increasing time to first submission

**Retention Risk**
- ⚠️ Declining return rate (L7/L30)
- ⚠️ Widening gaps between submissions
- ⚠️ Increasing dormancy rate

**Quality Risk**
- ⚠️ Declining approval rate
- ⚠️ Increasing defect rate
- ⚠️ Rising curation check failures

---

## 5. Behavioral Analytics Deep Dives

### User Journey Mapping

**First-Time User Journey (Activation)**

```
Account Creation → Portal Login → Discover Wizard → Start Creation
    ↓ (Leakage Point 1: Feature Discovery)
Enter Basic Info → AI Category Prediction → Category-Specific Fields
    ↓ (Leakage Point 2: Overwhelming Complexity)
Fill Content → Preview Curation Checks → Address Issues
    ↓ (Leakage Point 3: Curation Feedback)
Submit Product → Await Approval → Receive Decision
    ↓ (Critical Moment: Approval/Rejection)
Product Approved → Goes Live → First Booking
    ↓ (Aha Moment!)
Return for 2nd Product Creation (Retention Loop Begins)
```

**Repeat User Journey (Retention)**

```
Trigger: Need to expand catalog/seasonal planning
    ↓
Return to Portal → Navigate to Wizard → Start Creation
    ↓
Faster completion (learned behavior, familiar flow)
    ↓
Submit → Higher approval rate (quality improved)
    ↓
Check Performance Hub → See results → Motivated to create more
    ↓
Return more frequently (habit formation)
```

### Critical Moments Analysis

| Moment | What Happens | Success Metric | Failure Signal | Intervention |
|--------|--------------|----------------|----------------|--------------|
| **First Login** | Supplier discovers wizard | 60%+ start wizard within 7 days | <40% wizard entry | Onboarding prompt, tutorial |
| **Category Prediction** | AI suggests category | 80%+ accept prediction | >30% override | Improve prediction model |
| **Curation Preview** | Supplier sees potential issues | 70%+ address before submit | >40% ignore → reject | Make warnings more prominent |
| **First Submission** | Product submitted | <24 hrs to approval | >5 days to decision | Curation SLA improvement |
| **Approval Decision** | Product approved/rejected | 70%+ approved | >40% rejected | Better preventative guidance |
| **First Rejection** | Product rejected | 60%+ resubmit within 14 days | <40% return | Constructive feedback, help offer |
| **2nd Product** | Return for more | 40%+ submit within 30 days | >50% don't return | Success story, catalog expansion tips |
| **Power User Transition** | Reach 5 products | <90 days to 5 products | >180 days | Gamification, progress tracking |

### Friction Point Identification

**High-Friction Areas (Fix These First)**

1. **Category confusion**: Users override AI prediction frequently
   - Signal: >30% override rate
   - Impact: Wrong category → wrong fields → rejection
   - Fix: Improve prediction accuracy, show confidence score

2. **Overwhelming field requirements**: High dropoff at content entry
   - Signal: >20% abandon at this step
   - Impact: Supplier fatigue, incomplete submissions
   - Fix: Progressive disclosure, show only essential fields first

3. **Curation surprise**: Rejections for reasons not previewed
   - Signal: >30% rejection on issues not flagged
   - Impact: Supplier frustration, trust erosion
   - Fix: Comprehensive pre-submission validation

4. **Slow approval turnaround**: Long wait times demotivate
   - Signal: >5 days to approval decision
   - Impact: Lost momentum, lower return rate
   - Fix: Curation SLA, auto-approval for trusted suppliers

5. **No feedback loop**: Rejected suppliers don't know why
   - Signal: <40% resubmit after rejection
   - Impact: Lost activation, wasted effort
   - Fix: Clear rejection reasons, suggestions for improvement

### Correlation Analysis

**What Predicts Success?**

High Retention Predictors:
- ✅ First submission approved (85% retention vs 45% if rejected)
- ✅ First booking within 30 days (75% retention vs 40% no booking)
- ✅ Used curation preview (68% retention vs 52% didn't use)
- ✅ Submitted within 7 days of account creation (70% vs 45% slower)
- ✅ Completed >80% of recommended fields (72% vs 55% minimal fields)

High LTV Predictors:
- ✅ Power user (5+ products): 3x LTV vs light users
- ✅ Cross-feature engagement: 2.5x LTV vs wizard-only users
- ✅ Category diversification: 1.8x LTV vs single-category users
- ✅ Consistent submission cadence: 2x LTV vs sporadic users

---

## 6. Engagement Loops & Growth Mechanics

### Loop 1: Success Reinforcement Loop

```
Create Product → Approve → Go Live → Get Bookings → See Revenue
    ↓                                                      ↑
    ←──────────── Motivated to Create More ────────────────┘
```

**How to Strengthen:**
- Show revenue potential during creation ("Similar products earn €X/month")
- Send notification when product gets first booking (celebrate success)
- Display performance dashboard prominently (make wins visible)
- Gamify milestones (badges for 1st booking, 10 bookings, etc.)

### Loop 2: Quality Improvement Loop

```
Submit → Get Feedback → Improve → Higher Approval Rate → Confidence
    ↓                                                         ↑
    ←──────────── Create Higher Quality Products ─────────────┘
```

**How to Strengthen:**
- Provide specific, actionable feedback on rejections
- Show quality score/approval likelihood during creation
- Highlight improvement over time ("Your approval rate improved from 60% to 85%!")
- Reward quality with faster approvals or featured placement

### Loop 3: Learning & Habit Formation Loop

```
Use Wizard → Faster Creation → Easier Experience → Lower Friction
    ↓                                                      ↑
    ←────────────── Return More Frequently ────────────────┘
```

**How to Strengthen:**
- Pre-fill known information from previous submissions
- Remember supplier preferences (save as defaults)
- Smart suggestions based on past products ("You might want to add...")
- Progress tracking ("You're 3 products away from Power User status!")

### Loop 4: Network Effects Loop (Future State)

```
Successful Suppliers → Share Success Stories → Attract New Suppliers
    ↓                                                         ↑
    ←──────── More Inventory → Better Marketplace ────────────┘
```

**How to Strengthen:**
- Showcase successful suppliers in case studies
- Referral program for suppliers who recruit others
- Public leaderboards or recognition programs
- Community features (supplier forums, peer learning)

---

## 7. Experimentation Framework

### Activation Experiments (Level 1)

| Hypothesis | Experiment | Success Metric | Rollout Decision |
|-----------|-----------|----------------|------------------|
| Prominent wizard CTA increases discovery | A/B test: hero CTA vs sidebar link | +15% wizard entry rate | Ship if +10% |
| Step-by-step progress increases completion | A/B test: add progress bar | +10% completion rate | Ship if +7% |
| AI category suggestion reduces friction | A/B test: auto-predict vs manual select | +20% faster submission | Ship if +15% |
| Example tours improve quality | A/B test: show examples vs no examples | +10% approval rate | Ship if +8% |
| Curation preview reduces rejections | A/B test: preview vs no preview | -15% rejection rate | Ship if -10% |

### Retention Experiments (Level 2)

| Hypothesis | Experiment | Success Metric | Rollout Decision |
|-----------|-----------|----------------|------------------|
| Success notifications drive repeat usage | A/B test: notify on first booking vs no notify | +12% 2nd product submission | Ship if +8% |
| Email nurture increases return rate | A/B test: 3-email sequence vs control | +20% L30 retention | Ship if +15% |
| Gamification encourages consistency | A/B test: badges/streaks vs control | +15% monthly active rate | Ship if +10% |
| Performance dashboard drives engagement | A/B test: prominent vs hidden dashboard | +25% cross-feature engagement | Ship if +18% |

### Growth Experiments (Level 3)

| Hypothesis | Experiment | Success Metric | Rollout Decision |
|-----------|-----------|----------------|------------------|
| Category-specific guidance improves quality | A/B test: custom fields by category vs generic | +20% GCR for test categories | Ship if +15% |
| Structured data improves product performance | A/B test: require structured inclusions/exclusions | +10% GMV per product | Ship if +8% |
| Fast-track approval for trusted suppliers | Pilot: auto-approve for 80%+ approval rate suppliers | -50% approval time, no quality drop | Ship if criteria met |

---

## 8. Implementation Roadmap

### Phase 1: Foundation (Weeks 1-4)

**Goal:** Establish baseline measurement and identify friction points

**Activities:**
1. ✅ Implement tracking for all Level 1 & 2 metrics
2. ✅ Build core dashboard (North Star + Activation + Retention)
3. ✅ Establish baseline metrics (4-week historical average)
4. ✅ Implement user segmentation (engagement + lifecycle)
5. ✅ Map user journey with dropoff analysis
6. ✅ Identify top 5 friction points

**Success Criteria:**
- All metrics tracked and reporting accurately
- Dashboard accessible to team and stakeholders
- Baselines established with 95% confidence
- Top friction points identified and prioritized

### Phase 2: Quick Wins (Weeks 5-8)

**Goal:** Address obvious friction and improve activation

**Activities:**
1. ✅ Fix top 3 friction points identified in Phase 1
2. ✅ Launch activation experiments (progress bar, curation preview)
3. ✅ Implement re-engagement email for dormant users
4. ✅ Add success notifications (first booking, milestone achievements)
5. ✅ Begin cohort retention analysis (weekly reviews)

**Success Criteria:**
- +10% improvement in completion rate
- +5% improvement in first submission approval rate
- -2 days reduction in time to first submission
- Retention curves established for cohorts

### Phase 3: Retention Optimization (Weeks 9-16)

**Goal:** Drive repeat usage and habit formation

**Activities:**
1. ✅ Launch retention experiments (gamification, performance dashboard)
2. ✅ Implement personalized nurture campaigns by segment
3. ✅ Build win-back campaigns for at-risk users
4. ✅ Create power user identification and VIP treatment
5. ✅ Analyze and optimize engagement loops
6. ✅ Establish cross-feature engagement tracking

**Success Criteria:**
- +15% improvement in repeat usage rate (1 → 2+ products)
- +10% improvement in L30 retention
- +25% stickiness ratio (WAC/MAC)
- Power user segment reaches 12%+ of activated users

### Phase 4: Growth & Scale (Weeks 17-24)

**Goal:** Drive business impact and self-perpetuating growth

**Activities:**
1. ✅ Launch category-specific optimization experiments
2. ✅ Implement trusted supplier fast-track program
3. ✅ Build supplier success showcase and referral program
4. ✅ Establish LTV correlation analysis and value-based segmentation
5. ✅ Connect wizard engagement to broader portal health
6. ✅ Define and track engagement loop strength

**Success Criteria:**
- €X+ GMV per approved product (90-day)
- +20% retention lift for wizard users vs non-users
- +40% cross-feature engagement rate
- Self-reinforcing loops showing positive trends

---

## 9. Key Differences from Current Framework

### What's New/Improved

1. **Clear North Star Metric (WAPS)**
   - Single, actionable metric that balances quantity and quality
   - Decomposable for root cause analysis
   - Directly tied to business outcomes

2. **Behavioral Segmentation**
   - Engagement-based cohorts (Power/Regular/Light/One-and-Done)
   - Lifecycle stages mapped to specific goals
   - Quality-based and value-based segmentation for targeting

3. **Engagement Loops**
   - Explicit mapping of virtuous cycles that drive sustainable growth
   - Tactics to strengthen each loop
   - Network effects roadmap for future state

4. **Leading Indicators**
   - Predictive signals for activation, retention, and quality risk
   - Early warning system for intervention
   - Proactive vs reactive management

5. **Critical Moments Analysis**
   - Journey mapped with specific success/failure signals
   - Interventions defined for each critical moment
   - Focus on moments that matter most

6. **Correlation & Predictive Analysis**
   - What predicts high retention and high LTV
   - Actionable insights for supplier success
   - Data-driven prioritization

7. **Experimentation Framework**
   - Structured approach to testing improvements
   - Clear success criteria and rollout decisions
   - Continuous optimization mindset

8. **Metric Hierarchy & Prioritization**
   - Primary metrics (weekly review) vs secondary (monthly deep dive)
   - Prevents metric overload and analysis paralysis
   - Focus on what matters most at each level

### What's Retained from Current Framework

✅ Three-level hierarchy (Activation → Retention → Growth)
✅ Segmentation by new vs existing suppliers
✅ Focus on approval rate and quality
✅ Time-based retention cohorts
✅ Cross-feature engagement tracking
✅ Business outcome metrics (GMV, retention lift)

---

## 10. Dashboard Mockup (Weekly Review)

```
┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓
┃  PRODUCT CREATION WIZARD - ENGAGEMENT DASHBOARD              ┃
┃  Week of May 18-24, 2026                                     ┃
┗━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛

╔═══════════════════════════════════════════════════════════════╗
║  🎯 NORTH STAR: WEEKLY APPROVED PRODUCT SUBMISSIONS (WAPS)    ║
║                                                               ║
║  1,850 submissions    Target: 2,200    Gap: -16%            ║
║  ▲ +12% vs last week    📈 Trend: Growing (4-week avg +8%)   ║
║                                                               ║
║  Breakdown:                                                   ║
║  • Weekly Active Creators: 425 (▲ 8%)                        ║
║  • Submissions per Creator: 5.2 (▼ 2%)                       ║
║  • Approval Rate: 83% (▲ 5%)                                 ║
╚═══════════════════════════════════════════════════════════════╝

┌───────────────────────────────────────────────────────────────┐
│  LEVEL 1: ACTIVATION (Growing Engaged Users)                  │
└───────────────────────────────────────────────────────────────┘

  Feature Adoption Rate (30-day):        58% ▼ -2%  ⚠️ Below Target
  Completion Rate (Start → Submit):      72% ▲ +3%  ✅ Improving
  First Submission Approval:             68% ▲ +5%  ✅ On Track
  Time to First Submission:              8.5 days ▼ -1.2  ✅ Improving

  🚨 Alert: Feature adoption trending down. Check wizard visibility.

┌───────────────────────────────────────────────────────────────┐
│  LEVEL 2: RETENTION (Habitual Behavior)                       │
└───────────────────────────────────────────────────────────────┘

  Repeat Usage Rate (1 → 2+ products):   38% ▼ -2%  ⚠️ Watch Closely
  WAC (Weekly Active Creators):          425 ▲ +8%  ✅ Strong
  MAC (Monthly Active Creators):         1,680 ▲ +5%  ✅ Growing
  Stickiness (WAC/MAC):                  25.3% ▲ +0.8%  ✅ Healthy
  Submission Frequency (per active):     2.1/mo ▬ Flat

  📊 Cohort Health:
  • May cohort L7 retention: 32% (▲ 3% vs Apr)
  • Apr cohort M1 retention: 48% (▬ Stable)

┌───────────────────────────────────────────────────────────────┐
│  LEVEL 3: GROWTH (Value Creation)                             │
└───────────────────────────────────────────────────────────────┘

  Revenue per Product (90-day GMV):      €2,850 ▲ +12%  ✅ Strong
  Catalog Growth Rate:                   1,850/wk ▲ +12%  ✅ Target
  Retention Lift (Wizard vs Non):        +18% ▲ +2%  ✅ Near Target
  Cross-Feature Engagement:              36% ▬ Flat  ⚠️ Below Target

  💰 Business Impact:
  • Total GMV from wizard products (90d): €4.2M (+15% MoM)
  • Supplier LTV (Power Users): €42K (3.2x vs Light Users)

┌───────────────────────────────────────────────────────────────┐
│  🔍 KEY INSIGHTS & ACTIONS                                    │
└───────────────────────────────────────────────────────────────┘

  ✅ Wins This Week:
  • First submission approval rate up 5% (curation preview working!)
  • Revenue per product up 12% (quality improvements paying off)
  • WAC growing steadily (+8%)

  ⚠️ Areas of Concern:
  • Feature adoption rate declining (58%, -2%)
    → Action: Review wizard visibility in onboarding flow
  • Repeat usage rate down (38%, -2%)
    → Action: Launch nurture campaign for 1-product users
  • Cross-feature engagement flat (36%)
    → Action: Increase Performance Hub CTA visibility

  🎯 Next Week Focus:
  1. Ship wizard CTA experiment to improve discovery
  2. Launch email nurture for activated users without 2nd product
  3. Analyze April cohort to understand retention plateau
```

---

## 11. Success Criteria Summary

### 3-Month Targets (By August 2026)

| Metric | Current | Target | Status |
|--------|---------|--------|--------|
| **WAPS (North Star)** | 1,850 | 2,200 | 🟡 In Progress |
| **Feature Adoption Rate** | 58% | 65% | 🟡 Below Target |
| **Completion Rate** | 72% | 75% | 🟢 On Track |
| **First Approval Rate** | 68% | 70% | 🟢 Near Target |
| **Repeat Usage Rate** | 38% | 45% | 🟡 Below Target |
| **Stickiness (WAC/MAC)** | 25% | 28% | 🟢 On Track |
| **Retention Lift** | +18% | +20% | 🟢 Near Target |

### 6-Month Targets (By November 2026)

| Metric | Target | Why It Matters |
|--------|--------|----------------|
| **WAPS** | 2,600 | +40% growth vs baseline |
| **Feature Adoption** | 70% | Most suppliers try wizard |
| **Power User %** | 15% | Strong engagement base |
| **Revenue per Product** | €3,200 | +12% quality improvement |
| **Cross-Feature Engagement** | 45% | Ecosystem lock-in |

---

## 12. Recommended Next Steps

### Immediate (Week 1)

1. **Align on North Star Metric** 
   - Get stakeholder buy-in on WAPS as primary metric
   - Define exact calculation and data sources
   - Set quarterly targets

2. **Implement Tracking Gaps**
   - Audit current tracking against this framework
   - Prioritize missing events/metrics
   - Ship tracking updates

3. **Build Core Dashboard**
   - Use this structure as template
   - Focus on North Star + Level 1 & 2 first
   - Weekly review cadence

### Short-Term (Weeks 2-4)

4. **Segmentation Implementation**
   - Create engagement-based cohorts in data warehouse
   - Build segment-specific views in dashboard
   - Define intervention strategies per segment

5. **Friction Point Analysis**
   - Map user journey with current data
   - Identify top 5 dropoff points
   - Prioritize fixes by impact × effort

6. **Baseline Establishment**
   - Calculate 4-week averages for all metrics
   - Document seasonal patterns if any
   - Set realistic improvement targets

### Medium-Term (Months 2-3)

7. **Experimentation Roadmap**
   - Select 3-5 high-impact experiments from framework
   - Design experiment specs (hypothesis, metrics, sample size)
   - Begin testing activation improvements

8. **Engagement Loop Analysis**
   - Measure strength of each loop (correlation analysis)
   - Identify weakest links
   - Design interventions to strengthen loops

9. **Retention Deep Dive**
   - Cohort retention curves by segment
   - Identify retention inflection points
   - Build targeted re-engagement campaigns

### Long-Term (Months 4-6)

10. **Business Impact Validation**
    - LTV analysis by engagement tier
    - Wizard product performance benchmarking
    - ROI calculation for wizard improvements

11. **Scale & Optimize**
    - Roll out winning experiments
    - Expand to category-specific optimizations
    - Build self-reinforcing loops at scale

---

## Appendix A: Metric Definitions

### Activation Metrics

**Feature Adoption Rate**
```
Numerator: # suppliers who started wizard in last 30 days
Denominator: # active suppliers in last 30 days
```

**Completion Rate**
```
Numerator: # suppliers who submitted product
Denominator: # suppliers who started wizard
Time Window: Same session or within 7 days of start
```

**First Submission Approval Rate**
```
Numerator: # first submissions approved
Denominator: # first submissions reviewed
Exclude: Still pending review
```

### Retention Metrics

**Repeat Usage Rate**
```
Numerator: # activated suppliers with 2+ products
Denominator: # activated suppliers (1+ product)
Time Window: Within 90 days of activation
```

**Stickiness Ratio**
```
Formula: WAC / MAC
WAC: # suppliers submitting ≥1 product in week
MAC: # suppliers submitting ≥1 product in month
```

**Cohort Retention**
```
Definition: % of suppliers activated in Month 0 still active in Month N
Active: Submitted ≥1 product in the month
Track: M1, M2, M3, M6, M12 retention
```

### Growth Metrics

**Revenue per Approved Product**
```
Numerator: Total GMV from wizard products (lookback window)
Denominator: # approved wizard products in cohort
Lookback Window: 30, 60, 90 days post-approval
```

**Retention Lift**
```
Formula: (Wizard user retention / Non-wizard user retention) - 1
Time Window: 90-day retention
Control for: Supplier size, market, category
```

### Segment Definitions

**Power User**
```
Criteria: 5+ products created AND active in last 30 days
Active: Submitted ≥1 product or logged into wizard
```

**Dormant User**
```
Criteria: 1+ product created AND 0 activity in last 60 days
Activity: Submission, draft save, wizard login
```

---

## Appendix B: Industry Benchmarks

### Typical SaaS Engagement Benchmarks (for context)

| Metric | Low Performing | Average | High Performing |
|--------|----------------|---------|-----------------|
| Feature Adoption | <30% | 40-50% | >60% |
| Completion Rate | <50% | 60-70% | >75% |
| L7 Retention | <20% | 30-40% | >50% |
| L30 Retention | <30% | 40-50% | >60% |
| Stickiness (DAU/MAU) | <10% | 15-25% | >30% |
| Power User % | <5% | 10-15% | >20% |

*Note: Supplier portal is not typical SaaS, so benchmarks adapted for context. Use internal baselines as primary comparison.*

### Engagement Loop Strength

**How to Measure Loop Strength:**

Success Loop:
```
% of suppliers with ≥1 booking who create 2+ products
Target: >75% (strong loop)
```

Learning Loop:
```
Approval rate improvement: submission 1 vs submission 3+
Target: +15%+ improvement (learning is happening)
```

Habit Loop:
```
% of users reducing time between submissions over time
Target: >50% (habit forming)
```

---

## Appendix C: Tools & Analytics Stack

### Recommended Tools

**Analytics Platform:** Amplitude or Mixpanel
- Event tracking and funnel analysis
- Cohort retention analysis
- User segmentation

**Dashboard:** Looker or Tableau
- North Star metric dashboard
- Segment-specific views
- Automated alerts

**Experimentation:** Statsig or Optimizely
- A/B testing infrastructure
- Feature flagging
- Experiment analysis

**CRM/Engagement:** Iterable or Braze
- Automated campaigns by segment
- Lifecycle marketing
- Re-engagement flows

### Key Events to Track

**Wizard Events:**
- `wizard_started` (entry point)
- `wizard_step_completed` (each step)
- `wizard_draft_saved`
- `wizard_product_submitted`
- `wizard_product_approved`
- `wizard_product_rejected`
- `wizard_product_first_booking`

**Engagement Events:**
- `performance_hub_viewed`
- `recommended_actions_engaged`
- `wizard_tutorial_completed`
- `curation_preview_used`
- `example_tour_viewed`

**User Properties:**
- `engagement_tier` (Power/Regular/Light/One-and-Done)
- `lifecycle_stage` (New/Activated/Expanding/Mature/At-Risk)
- `products_created_count`
- `approval_rate`
- `days_since_last_submission`
- `ltv_segment` (High/Growth/Stable/Low)

---

*Framework Version 2.0 | May 2026*
*Based on: Sarah Tavel's Hierarchy of Engagement, Pendo Product Engagement Framework, Amplitude Playbook, Mixpanel Engagement Guide*
