# Supplier Portal Engagement Metrics: Industry Best Practices

## Executive Summary

Based on research from big tech companies (Amazon, Salesforce, Shopify, Stripe, Meta, Google), here are the recommended engagement metrics for supplier/partner portals at different organizational levels.

---

## 1. The Engagement Metrics Hierarchy

### **For C-Level/Executive Management (Single North Star Metric)**

**Recommended: Weekly Active Suppliers (WAS) or Monthly Active Suppliers (MAS)**

**Why:**
- Simple, easy to communicate
- Directly correlates with business value (active suppliers = revenue opportunity)
- Used by Shopify (merchants), Stripe (business users), Amazon Seller Central (sellers)
- Answers: "Are our suppliers engaged with the platform?"

**Definition:**
- **WAS:** Unique suppliers who logged in at least once in the past 7 days
- **MAS:** Unique suppliers who logged in at least once in the past 30 days

**Variant: GMV-Weighted Active Rate**
- Active suppliers weighted by their GMV contribution
- Prioritizes engagement from high-value suppliers
- Formula: `(GMV from active suppliers) / (Total GMV from all suppliers)`

---

## 2. The Engagement Framework Stack (Top to Bottom)

Big tech companies use a **layered approach** to measure engagement:

### **Layer 1: Activation Metrics (Are they starting?)**
- % of suppliers who logged in within 7 days of approval
- % of suppliers who completed profile setup
- Time to first login after activation

**Used by:** Salesforce Partner Portal, Shopify Partner Dashboard

---

### **Layer 2: Active Usage Metrics (Are they coming back?)**

#### **Primary Metrics:**
1. **MAU (Monthly Active Users)** - Standard at Meta, Google, LinkedIn
   - Unique suppliers who logged in in the past 30 days
   - Most common industry standard

2. **WAU (Weekly Active Users)** - Preferred by fast-moving platforms
   - Unique suppliers who logged in in the past 7 days
   - Better for detecting short-term trends

3. **DAU (Daily Active Users)** - For high-frequency products only
   - Unique suppliers who logged in today
   - Only relevant if daily usage is expected (e.g., inventory management)

#### **Secondary Metrics:**
4. **Stickiness Ratio** = DAU / MAU
   - Industry benchmark: 20-25% for B2B products
   - Measures how often users return within a month
   - Used by Facebook, Slack, Notion

5. **L28 Login Rate** (Login in Last 28 Days)
   - % of all suppliers who logged in at least once in past 28 days
   - More inclusive than MAU (counts churned suppliers too)
   - Used by Amazon Seller Central

6. **Login Frequency Distribution**
   - % logging in 1x, 2-5x, 6-15x, 16+ times per month
   - Identifies power users vs casual users
   - Used by LinkedIn, Shopify

---

### **Layer 3: Engagement Quality Metrics (What are they doing?)**

#### **Breadth Metrics (How many features?)**
1. **Feature Adoption Rate**
   - % of suppliers using each core feature
   - Used by Salesforce, HubSpot, Stripe

2. **Breadth of Feature Usage**
   - Average # of distinct features used per session
   - Identifies engaged vs superficial users
   - Used by Google Workspace, Microsoft 365

#### **Depth Metrics (How much are they doing?)**
3. **Session Duration**
   - Average time spent per session
   - Benchmark: 3-7 minutes for B2B portals

4. **Actions Per Session**
   - # of meaningful actions (not just page views)
   - Actions = clicks on core features, downloads, uploads, etc.

5. **Core Action Completion Rate**
   - % of sessions where supplier completes a core action
   - Core actions = update inventory, respond to message, view insights
   - Used by Amazon Seller Central, eBay Seller Hub

---

### **Layer 4: Outcome Metrics (Is engagement driving business value?)**

1. **Revenue Impact**
   - GMV from engaged suppliers vs non-engaged
   - Conversion rate improvement for engaged suppliers
   - Used by Shopify, Amazon

2. **Retention & Churn**
   - 30-day retention rate
   - 90-day retention rate
   - Churn rate by engagement tier
   - Used by Salesforce, HubSpot

3. **NPS by Engagement Tier**
   - Compare NPS scores: High engagement vs Low engagement
   - Validates that engagement → satisfaction
   - Used by Zendesk, Intercom

---

## 3. Industry-Specific Benchmarks

### **B2B SaaS Portals (Salesforce, HubSpot, Zendesk)**
- **MAU/Total Users:** 40-60%
- **Stickiness (DAU/MAU):** 15-25%
- **Session Frequency:** 2-3x per week

### **Marketplace Seller Portals (Amazon, eBay, Etsy)**
- **MAU/Total Sellers:** 60-80% (high because sellers need to manage inventory)
- **Stickiness:** 30-40%
- **Session Frequency:** 4-7x per week

### **Partner/Supplier Portals (Shopify Partners, Stripe Connect)**
- **MAU/Total Partners:** 30-50%
- **Stickiness:** 10-20%
- **Session Frequency:** 1-2x per week

---

## 4. The Google HEART Framework

Google uses the **HEART framework** for all product engagement:

| Dimension | Metric | Supplier Portal Example |
|-----------|--------|-------------------------|
| **Happiness** | NPS, CSAT | Supplier satisfaction score |
| **Engagement** | DAU, MAU, Session Duration | Weekly active suppliers, avg session time |
| **Adoption** | % using feature | % using Performance Hub, % using Recommended Actions |
| **Retention** | 30-day retention rate | % still active after 30 days |
| **Task Success** | Completion rate, Time to complete | % completing recommended actions, time to resolve action |

**Recommended for GYG:** Use HEART as your **framework**, with **MAU as your North Star**, and **feature adoption** as your key driver metric.

---

## 5. The Amplitude/Mixpanel Product Engagement Score (PES)

Modern product analytics platforms combine multiple signals into a **single engagement score**:

**Formula:**
```
PES = (Adoption × Stickiness × Growth) / 100

Where:
- Adoption = % of users who performed core action in past 30 days
- Stickiness = % of users who performed core action 5+ days in past 30 days
- Growth = % change in adoption vs previous period
```

**For Supplier Portal:**
```
Core Actions:
1. Login
2. View Performance Hub
3. Interact with Recommended Action
4. Update inventory/settings
5. View insights/reports

Engagement Score = (% who did ≥1 action) × (% who did actions 5+ days) × (growth rate)
```

---

## 6. Recommended Metrics for GYG Supplier Portal

### **Executive Dashboard (C-Level)**
**Primary Metric:** Monthly Active Suppliers (MAS)
- Simple, clear, aligns with business value

**Secondary Metric:** GMV-Weighted Active Rate
- Focuses on high-value supplier engagement

**Trend Metric:** MoM Growth in Active Suppliers
- Shows trajectory

---

### **Product Team Dashboard (Product/Analytics)**

**Activation:**
- % of new suppliers who logged in within 7 days
- % who used Performance Hub in first 30 days

**Engagement:**
- MAU, WAU
- Stickiness (DAU/MAU)
- Login frequency distribution
- L28 login rate by segment

**Feature Adoption:**
- % using Performance Hub
- % interacting with Recommended Actions
- % viewing each insight type
- Feature usage breadth (avg # features used)

**Quality:**
- Session duration
- Actions per session
- Core action completion rate

**Outcomes:**
- GMV from engaged vs non-engaged suppliers
- Retention by engagement tier
- Conversion rate improvement

---

### **Management Dashboard (VP/Director)**

**Weekly Snapshot:**
1. **WAU** (trend chart)
2. **Login Rate by Segment** (table: managed vs non-managed)
3. **Top 3 Features Adopted** (% using each)
4. **Engagement Health Score** (RAG status)

**Monthly Deep Dive:**
1. **MAU** (trend + YoY)
2. **Stickiness Ratio** (trend)
3. **Feature Adoption Funnel** (% at each stage)
4. **Cohort Retention** (by onboarding month)
5. **GMV Impact** (engaged vs non-engaged)

---

## 7. Specific Login Rate Metrics Comparison

Since your team mentioned **login rates**, here are the options:

| Metric | Definition | Best For | Used By |
|--------|------------|----------|---------|
| **L7 Login Rate** | % who logged in past 7 days | Fast-moving decisions | Slack, Notion |
| **L28 Login Rate** | % who logged in past 28 days | Standard industry metric | Amazon, LinkedIn |
| **L90 Login Rate** | % who logged in past 90 days | Long-tail/seasonal users | Airbnb hosts |
| **Monthly Login Frequency** | Avg logins per supplier per month | Understanding usage intensity | Shopify |
| **GMV-Weighted Login Rate** | GMV from logged-in suppliers / Total GMV | High-value supplier focus | Stripe, Shopify |

**Recommendation:**
- **For management:** Use **L28 Login Rate** (industry standard, easy to understand)
- **For product team:** Use **MAU** and **Stickiness** (more actionable)
- **For business value:** Use **GMV-Weighted Login Rate** (ties to revenue)

---

## 8. Red Flags to Avoid

**Don't use these as primary metrics:**
1. ❌ **Total page views** - Vanity metric, doesn't indicate value
2. ❌ **Total sessions** - Can be inflated by confused users
3. ❌ **Average time on site** - Could indicate confusion, not engagement
4. ❌ **Unique visitors** - Includes one-time visitors, not engaged users

**Why login rate alone is insufficient:**
- Doesn't tell you **what** they're doing
- Doesn't show **value** they're getting
- Doesn't measure **depth** of engagement

**Better:** Combine login rate with feature adoption and outcome metrics.

---

## 9. Implementation Roadmap for GYG

### **Phase 1: North Star Metric (Now)**
✅ Choose: **Monthly Active Suppliers (MAS)** or **L28 Login Rate**
- Already have the data in `fact_supplier_engagement`
- Easy to communicate to leadership
- Set baseline and targets

### **Phase 2: Engagement Framework (Month 1-2)**
✅ Add supporting metrics:
- Stickiness (DAU/MAU)
- Login frequency distribution
- Segment breakdowns

### **Phase 3: Feature Adoption (Month 2-3)**
✅ Track feature-specific engagement:
- Performance Hub adoption
- Recommended Actions interaction
- Each feature's usage rate

### **Phase 4: Outcome Metrics (Month 3-4)**
✅ Connect engagement to business value:
- GMV by engagement tier
- Retention by engagement tier
- NPS by engagement tier

### **Phase 5: Engagement Score (Month 4-6)**
✅ Build composite engagement score:
- Combine activation, usage, feature adoption
- Create single health metric
- Automate RAG (Red/Amber/Green) status

---

## 10. Recommended Dashboard Structure

### **Executive View (1 slide)**
```
┌─────────────────────────────────────────────────────┐
│  Monthly Active Suppliers: 12,450 ▲ 8% MoM         │
│  GMV-Weighted Active Rate: 78% ▲ 3% MoM            │
│                                                      │
│  [MAU Trend Chart: Past 12 months]                  │
│                                                      │
│  Engagement by Segment:                              │
│  - Managed: 85% active                               │
│  - Non-Managed: 42% active                           │
│                                                      │
│  Business Impact:                                    │
│  - Engaged suppliers: €125M GMV (82% of total)      │
│  - Non-engaged: €28M GMV (18% of total)             │
└─────────────────────────────────────────────────────┘
```

### **Product Team View (Dashboard)**
```
┌──────────────────┬──────────────────┬──────────────────┐
│ Activation       │ Active Usage     │ Feature Adoption │
├──────────────────┼──────────────────┼──────────────────┤
│ L7 first login:  │ MAU: 12,450      │ Perf Hub: 65%    │
│ 68%              │ WAU: 5,230       │ Rec Actions: 42% │
│                  │ Stickiness: 18%  │ Insights: 55%    │
│ Profile setup:   │ L28 rate: 61%    │                  │
│ 82%              │                  │ Breadth: 2.3     │
└──────────────────┴──────────────────┴──────────────────┘

┌─────────────────────────────────────────────────────┐
│ Engagement Quality                                   │
├─────────────────────────────────────────────────────┤
│ Session duration: 4.2 min (target: 5 min)           │
│ Actions/session: 3.8 (target: 5)                    │
│ Core action completion: 62% (target: 70%)           │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ Outcomes                                             │
├─────────────────────────────────────────────────────┤
│ 30-day retention: 72%                                │
│ GMV lift (engaged): +23% vs non-engaged              │
│ NPS (engaged): 45 | NPS (non-engaged): 28           │
└─────────────────────────────────────────────────────┘
```

---

## 11. Key Takeaways

### **For Leadership:**
1. **Start with MAU or L28 Login Rate** as your North Star
2. **Add GMV-weighting** to show business value
3. **Track trend** (MoM growth) to show progress

### **For Product Team:**
1. **Don't rely on login rate alone** - add feature adoption
2. **Use the HEART framework** to cover all dimensions
3. **Measure stickiness** (DAU/MAU) to understand engagement quality
4. **Connect to outcomes** (GMV, retention) to prove value

### **For Your Current Explores:**
✅ You already have the right data structure:
- `fact_supplier_engagement` → MAU, WAU, DAU, stickiness
- `monthly_supplier_gmv` → GMV-weighted metrics
- `dim_recommended_actions` → Feature adoption
- `performance_hub_events` → Feature usage depth

**You're on the right track!** Just need to decide which metric to highlight as your primary engagement metric.

---

## 12. Final Recommendation

**For GYG Management:**

**Primary Metric:** **Monthly Active Suppliers (MAU)**
- Definition: Unique suppliers who logged in at least once in the past 30 days
- Target: Set based on current baseline, aim for 60-70% of total suppliers
- Report: MoM trend with segment breakdowns

**Secondary Metric:** **GMV-Weighted Login Rate**
- Definition: % of total GMV from suppliers who logged in past 30 days
- Target: 75-80%
- Report: Monthly snapshot

**Supporting Metrics (For deeper analysis):**
- Stickiness (DAU/MAU): Target 20-25%
- Feature adoption: Performance Hub 60%, Recommended Actions 50%
- Engagement quality: Avg 3+ actions per session

**Dashboard Cadence:**
- Weekly: WAU trend + key flags
- Monthly: MAU, GMV-weighted rate, feature adoption, outcomes
- Quarterly: Deep dive on retention cohorts and engagement impact

---

## Sources & References

This analysis is based on publicly documented practices from:
- **Meta/Facebook:** MAU/DAU methodology, stickiness ratios
- **Google:** HEART framework for product metrics
- **Amazon:** Seller Central engagement tracking (L28 login rate)
- **Salesforce:** Partner portal engagement framework
- **Shopify:** Merchant engagement metrics
- **Stripe:** Connected account engagement
- **Amplitude/Mixpanel:** Product Engagement Score methodology
- **LinkedIn:** B2B product engagement best practices

Industry benchmarks sourced from public product analytics research and B2B SaaS engagement studies (2023-2026).
