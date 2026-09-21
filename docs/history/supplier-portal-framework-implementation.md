# Supplier Portal Analytics Framework - Implementation Plan

## Executive Summary

Based on your 4 Confluence analyses and the theoretical framework, here's how to build the complete 3-tier dashboard system using **available data sources**.

---

## Data Availability Mapping

### ✅ What We Have

| Theoretical Metric | Available Data | Source Table |
|-------------------|----------------|--------------|
| **MAU/DAU** | ✅ `has_login_l30`, `has_login` | `fact_supplier_history` |
| **Login frequency** | ❌ Not available (no login_count column) | - |
| **Portal adoption rate** | ✅ Calculated from `has_login_l30` / `is_active` | `fact_supplier_history` |
| **Segment breakdown** | ✅ `supplier_segment` | `dim_supplier_summary` |
| **Managed/Connected status** | ✅ `is_managed`, `is_connected` | `dim_supplier_summary` |
| **Geographic breakdown** | ✅ `country`, `region` | `dim_supplier_summary` |
| **Feature: Recommended Actions** | ✅ Full lifecycle tracking | `dim_recommended_actions` |
| **Feature: Performance Hub** | ✅ Event tracking | `production.events.events` |
| **Feature: Product Creation** | ✅ Funnel tracking | `tour_creation_funnel` |
| **Feature: Pricing** | ✅ Adoption & depth metrics | Analysis in Confluence (needs extraction) |
| **Supplier outcomes: GMV** | ✅ `gmv_l365` | `dim_supplier_summary` |
| **Supplier outcomes: Bookings** | ✅ `bookings`, `bookings_l30` | `fact_supplier_history` |
| **Supplier outcomes: Content quality** | ❌ Not in existing tables | - |
| **Supplier outcomes: Review ratings** | ❌ Not in existing tables | - |

### ❌ What We Don't Have (Yet)

- Login count per month (for frequency distribution)
- WAU (no L7 login flag)
- Session duration
- GMV at daily grain (only aggregated in dim_supplier_summary)
- Content quality scores
- Review ratings by supplier

---

## Phase 1: Dashboard Implementation Plan

### **Tier 1: Executive Dashboard** (Build This First)

**Available Now:**

| Tile | Data Source | Status |
|------|-------------|--------|
| **MAU Trend** | `fact_supplier_engagement.mau` by month | ✅ Ready |
| **Portal Adoption Rate (L30)** | `fact_supplier_engagement.l30_login_rate` | ✅ Ready |
| **MAU by Segment** | `mau` grouped by `dim_supplier_summary.supplier_segment` | ✅ Ready |
| **MAU by Country** | `mau` grouped by `dim_supplier_summary.country` | ✅ Ready |
| **Engagement by Status** | `mau` by `is_managed`, `is_connected` | ✅ Ready |
| **Feature Adoption Heatmap** | Needs Explore 2 (Recommended Actions) | 🔄 Need to build |

**Not Available (Workarounds):**

| Intended Tile | Limitation | Workaround |
|--------------|------------|------------|
| **GMV-Weighted Login Rate** | No daily GMV grain | Use `dim_supplier_summary.gmv_l365` with latest snapshot |
| **WAU/MAU Stickiness** | No L7 flag | Use L30/L60 ratio instead |

---

### **Tier 2: PM Dashboard** (Build After Tier 1)

**Available Now:**

| Metric Category | Tiles | Data Source | Status |
|----------------|-------|-------------|--------|
| **Activation** | Onboarding completion (tour creation submission rate) | `tour_creation_funnel` | ✅ Ready (Explore 3) |
| **Adoption** | RA reach rate, PH reach rate | `dim_recommended_actions`, `events.events` | 🔄 Need Explore 2 |
| **Engagement** | MAU/DAU, L30 login rate, bookings per supplier | `fact_supplier_engagement` | ✅ Ready |
| **Depth** | RA resolution rate, PH events per visit, wizard completion | `dim_recommended_actions`, `events`, `tour_creation_funnel` | 🔄 Need Explores 2 & 3 |
| **Pricing Adoption** | Individual pricing %, Multiple options %, API pricing % | Confluence analysis (static) | ⚠️ Manual reporting only |

**Not Available:**

- Login frequency distribution (1-2, 3-5, 6-10, 10+ logins/month)
- Session duration
- Actions per session

---

### **Tier 3: Analytics Deep-Dive** (Build Last)

**Available Now:**

| Analysis Type | Capability | Data Source | Status |
|--------------|-----------|-------------|--------|
| **Cohort Analysis** | Compare engagement by segment, NR tier, managed status | `fact_supplier_engagement` + `dim_supplier_summary` | ✅ Ready |
| **Funnel Analysis** | RA lifecycle, wizard drop-offs | `dim_recommended_actions`, `tour_creation_funnel` | 🔄 Need Explores 2 & 3 |
| **Time-Lagged** | Login in Month N → GMV change in Month N+1 | `fact_supplier_history` + `fact_booking` | 🔄 Need custom derived table |
| **Feature Interaction** | RA dismissal reasons, wizard abandonment points | `dim_recommended_actions`, `tour_creation_funnel` | 🔄 Need Explores 2 & 3 |

---

## Phase 2: Connecting Engagement to Outcomes

### Available Outcome Metrics

| Outcome Category | Metric | Source | Grain |
|-----------------|--------|--------|-------|
| **Revenue** | GMV per supplier | `dim_supplier_summary.gmv_l365` | Supplier-level (L365 rolling) |
| **Revenue** | Bookings per supplier | `fact_supplier_history.bookings`, `bookings_l30` | Daily |
| **Operational** | Online tours count | `fact_supplier_history.online_tours` | Daily |
| **Content** | Pricing feature adoption | Confluence analysis | Supplier-level (static) |

### Causal Analysis Methods - Feasibility

| Method | Feasible? | Requirements | Status |
|--------|-----------|--------------|--------|
| **Correlation Analysis** | ✅ Yes | Engagement metrics + outcome metrics | Ready now |
| **Propensity Score Matching** | ✅ Yes | Supplier attributes for matching (segment, tenure, size) | Need to add `tenure` field |
| **Difference-in-Differences** | ⚠️ Limited | Feature rollout dates + pre/post data | Only for recent features (PH, RA) |
| **Regression with Controls** | ✅ Yes | Engagement + supplier attributes + outcomes | Ready now |
| **Time-Lagged Analysis** | ✅ Yes | Historical engagement + future outcomes | Need derived table joining history over time |

---

## Implementation Roadmap (Revised for Available Data)

### **Quarter 1 (Now): Build Core Dashboards**

**Week 1-2:**
- ✅ Explore 1: Supplier Engagement (DONE)
- 🔄 Explore 2: Feature Usage (Recommended Actions + Performance Hub)
- 🔄 Explore 3: Product Creation

**Week 3:**
- Build Tier 1 Executive Dashboard (6 tiles)
- Build Tier 2 PM Dashboard (10 tiles)

**Week 4:**
- Test dashboards with stakeholders
- Iterate based on feedback
- Document limitations

### **Quarter 2: Establish Descriptive Linkages**

**Month 1:**
- Correlation analysis: Login rate vs GMV growth
- Correlation analysis: RA resolution vs GMV growth
- Correlation analysis: Tour creation completion vs activation rate

**Month 2:**
- Build outcome tracking derived tables
- Add time-lagged views (Month N engagement → Month N+1 outcomes)
- Create visualizations

**Month 3:**
- Document relationships
- Identify high-priority features for causal analysis
- Present findings to leadership

### **Quarter 3: Implement Causal Methods**

**Month 1:**
- Propensity score matching: RA resolvers vs non-resolvers
- Control for: segment, NR tier, tenure, managed status

**Month 2:**
- Difference-in-differences: Performance Hub early adopters vs late adopters
- Use rollout date (March 30, 2026) as treatment timing

**Month 3:**
- Regression models: Predict GMV growth from engagement metrics
- Controls: supplier size, segment, geography, historical performance
- Time-lagged: L30 login in Month N → GMV change in Month N+1

### **Quarter 4: Operationalize Insights**

**Month 1:**
- Build predictive models: Early engagement → long-term success
- Identify at-risk suppliers (low engagement + declining GMV)

**Month 2:**
- Create intervention workflows
- Build A/B testing framework for portal features

**Month 3:**
- Automated reporting
- Document learnings
- Plan Phase 2 extensions

---

## Explore Requirements

### **Explore 1: Supplier Engagement** ✅ DONE
- Base: `fact_supplier_history`
- Join: `dim_supplier_summary`
- Metrics: MAU, DAU, L30/L60 login rates, bookings, online tours
- **Status: Live in Looker**

### **Explore 2: Feature Usage & Outcomes** 🔄 NEXT
- Base: `dim_recommended_actions`
- Joins:
  - `dim_supplier_summary` (supplier attributes)
  - `fact_supplier_history` (engagement at time of action)
  - `production.events.events` (Performance Hub events, filter: `event_name LIKE '%Supplier%'`)
- Metrics:
  - RA: Reach rate, resolution rate (28-day), dismissal rate, expiry rate, supplier conversion, engagement tiers
  - PH: MAU, page views, event counts by type, % who resolve actions from PH
- **Status: Need to build**

### **Explore 3: Product Creation & Activation** 🔄 NEXT
- Base: `tour_creation_funnel`
- Joins:
  - `dim_supplier_summary` (supplier attributes)
  - `catalog__tour_generated_content` (AI success/failure)
  - `catalog__tour_business_category` (category-level submission rates)
  - `dim_activity_lookback_activation` (1B30D activation)
- Metrics:
  - Tours started, submitted, submission rate
  - AI adoption rate, AI success rate
  - Funnel drop-offs by step
  - Activation rate (1B30D)
  - Time to submit (median, P75)
- **Status: Need to build**

---

## Dashboard Tile Specifications

### **Executive Dashboard - Detailed Spec**

**Tile 1: MAU Trend**
```
Explore: supplier_engagement
Dimension: Fact Supplier Engagement > Date > Month
Measure: Fact Supplier Engagement > MAU
Filter: Date = last 12 months
Viz: Line chart
```

**Tile 2: Portal Adoption Rate**
```
Explore: supplier_engagement
Measure: Fact Supplier Engagement > L30 Login Rate
Filter: Date = last 30 days
Viz: Single value with % format
```

**Tile 3: MAU by Segment**
```
Explore: supplier_engagement
Dimension: Dim Supplier Summary > Supplier Segment
Measure: Fact Supplier Engagement > MAU
Filter: Date = last 30 days
Viz: Horizontal bar chart
Sort: MAU descending
```

**Tile 4: MAU by Country (Top 15)**
```
Explore: supplier_engagement
Dimension: Dim Supplier Summary > Country
Measure: Fact Supplier Engagement > MAU
Filter: Date = last 30 days
Limit: 15
Viz: Map or horizontal bar chart
Sort: MAU descending
```

**Tile 5: Engagement Breakdown Table**
```
Explore: supplier_engagement
Dimensions:
  - Dim Supplier Summary > Supplier Segment
  - Dim Supplier Summary > Is Managed
  - Dim Supplier Summary > Is Connected
Measures:
  - Fact Supplier Engagement > Total Suppliers
  - Fact Supplier Engagement > MAU
  - Fact Supplier Engagement > L30 Login Rate
Filter: Date = last 30 days
Viz: Table
```

**Tile 6: Feature Adoption Heatmap** (Needs Explore 2)
```
Explore: feature_usage_outcomes
Dimensions:
  - Dim Supplier Summary > Supplier Segment (rows)
  - Feature Name (columns: RA, PH, Product Creation)
Measure: % Suppliers Reached
Filter: Date = last 30 days
Viz: Heatmap
```

---

## PM Dashboard - Detailed Spec

### Activation Section

**Tile 1: Tour Creation Submission Rate**
```
Explore: product_creation_activation
Dimension: Tour Creation Funnel > Date > Month
Measures:
  - Tours Started
  - Tours Submitted
  - Submission Rate
Filter: Date = last 6 months
Viz: Line chart (2 lines + calculated field)
```

**Tile 2: AI Adoption Rate**
```
Explore: product_creation_activation
Measure: AI Adoption Rate
Filter: Date = last 30 days
Viz: Single value with %
```

### Adoption Section

**Tile 3: Feature Reach Rates**
```
Explore: feature_usage_outcomes
Dimension: Feature Type (RA, PH, Product Creation)
Measure: Reach Rate
Filter: Date = last 30 days
Viz: Bar chart
```

**Tile 4: RA Resolution Rate (28-day)**
```
Explore: feature_usage_outcomes
Dimension: Date > Month
Measure: Resolution Rate (28-day)
Filter: Date = last 12 months
Viz: Line chart with target line at 30%
```

### Engagement Section

**Tile 5: MAU/DAU Trends**
```
Explore: supplier_engagement
Dimension: Date > Week
Measures:
  - MAU
  - DAU
Filter: Date = last 13 weeks
Viz: Dual-axis line chart
```

**Tile 6: L30 Login Rate by Segment**
```
Explore: supplier_engagement
Dimension: Dim Supplier Summary > Supplier Segment
Measure: L30 Login Rate
Filter: Date = last 30 days
Viz: Bar chart
Sort: L30 Login Rate descending
```

### Depth Section

**Tile 7: RA Supplier Conversion Rate**
```
Explore: feature_usage_outcomes
Measure: Supplier Conversion Rate (% reached who resolved ≥1)
Filter: Date = last 30 days
Viz: Single value with %
```

**Tile 8: Product Creation Wizard Funnel**
```
Explore: product_creation_activation
Dimension: Step Name
Measure: Tours Reached
Filter: Date = last 30 days
Viz: Funnel chart
```

**Tile 9: RA Engagement Tier Distribution**
```
Explore: feature_usage_outcomes
Dimension: Engagement Tier (Single-Use, Occasional, Regular, Power User)
Measure: Count Suppliers
Filter: Date = all time (cumulative)
Viz: Pie chart
```

**Tile 10: Avg Bookings per Supplier**
```
Explore: supplier_engagement
Dimension: Dim Supplier Summary > Supplier Segment
Measure: Avg Bookings per Supplier (L30)
Filter: Date = last 30 days
Viz: Bar chart
```

---

## Next Steps

**Immediate (This Week):**
1. Build Explore 2: Feature Usage & Outcomes
   - View: `dim_recommended_actions`
   - View: `supplier_portal_events` (derived from `production.events.events`)
   - Explore: Join them with `dim_supplier_summary`

2. Build Explore 3: Product Creation
   - View: `tour_creation_funnel` (may already exist)
   - Joins: AI content, categories, activation

3. Build Executive Dashboard
   - Create 6 tiles using Explore 1 (already working)

**Next Week:**
4. Build PM Dashboard
   - Create 10 tiles using all 3 explores

5. Stakeholder review
   - Present dashboards
   - Gather feedback
   - Iterate

**Month 2:**
6. Start Phase 2: Correlation analysis
   - Login rate vs GMV
   - RA resolution vs GMV
   - Document relationships

---

## Limitations to Document

1. **No login frequency distribution** - Cannot build "10+ logins/month" power user metric
2. **No session duration** - Cannot measure time spent in portal
3. **No WAU** - No L7 flag available, using L30/L60 instead
4. **No daily GMV** - GMV only available as L365 rolling in `dim_supplier_summary`
5. **Pricing metrics are static** - From Confluence analysis, not live in dashboards
6. **No content quality scores** - Cannot track listing completeness, photo quality
7. **No review ratings** - Cannot link engagement to customer satisfaction

---

**Ready to build Explore 2 and Explore 3?**
