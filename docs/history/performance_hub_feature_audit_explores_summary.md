# Performance Hub Feature Audit - Explores Summary

Created explores to replicate the Confluence Performance Hub Feature Audit analysis in Looker dashboards.

**Confluence Reference:** https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4205936693

**Branch:** `dev-performance-hub-feature-audit`

---

## Explores Created

### 1. `performance_hub_reach_analysis` (Q1)
**For: How many relevant suppliers is the Performance Hub reaching?**

**Purpose:** Calculate reach rate with proper denominator (relevant suppliers)

**Base View:** `dim_supplier_relevance` (relevant supplier universe)

**Joined Views:**
- `dim_supplier_summary` (segmentation: managed, connected, segment)
- `performance_hub_events` (PH page views and events)

**Key Metrics:**
- `count_relevant_suppliers` - Total relevant suppliers (denominator): 48,520
- `count_suppliers_post_rollout` - Suppliers who visited post rollout (numerator): 14,753
- Reach Rate = count_suppliers_post_rollout / relevant_suppliers = 30.4%

**Use Cases:**
- Overall reach rate (post full rollout: March 30 - April 17)
- Reach by managed/unmanaged (41.8% vs 28.4%)
- Reach by connected/non-connected (~30% both)
- BP vs PP visitor breakdown

---

### 2. `supplier_performance_hub_engagement` (Q4, Q7)
**For: Engagement depth and returning suppliers**

**Purpose:** Supplier-level engagement metrics (NOT event-level)

**Base View:** `agg_supplier_performance_hub_engagement` (derived table, one row per supplier)

**Joined Views:**
- `dim_supplier_summary` (segmentation)
- `dim_supplier_relevance` (relevance criteria)

**Key Metrics:**

**Q4 - Engagement Depth:**
- `avg_events_per_supplier` - Mean: 31.6 events
- `median_events_per_supplier` - Median: 13.0 events
- `avg_bp_page_views` - Mean: 15.4 page views
- `median_bp_page_views` - Median: 6.0 page views
- `avg_pp_page_views` - Mean: 10.2 page views
- `median_pp_page_views` - Median: 5.0 page views
- `avg_interactions_per_supplier` - Mean: 11.9 interactions
- `median_interactions_per_supplier` - Median: 5.0 interactions

**Q7 - Retention:**
- `march_cohort_early_access` - Cohort size: 1,303 suppliers
- `returned_in_april_count` - Returned: 1,019 suppliers
- `returning_rate` - 78.2%

**Use Cases:**
- Engagement depth distribution
- Engagement tiers (Light, Moderate, Active, Power User)
- Cohort retention (March → April)
- Interaction rate breakdowns

---

### 3. `performance_hub_usage` (Q2, Q3, Q5, Q6) **[Already Exists]**
**For: Activity, section usage, functionality, action-taking**

**Purpose:** Event-level analysis (one row per event)

**Base View:** `performance_hub_events`

**Key Metrics:**

**Q2 - Activity (MAU/WAU):**
- `mau` - Monthly active users
- Weekly aggregation via `date_week` dimension

**Q3 - Section Usage:**
- `bp_visitors` - Business Performance unique visitors: 15,377
- `pp_visitors` - Product Performance unique visitors: 8,352
- `total_page_views` - 320,813 (BP + PP)

**Q5 - Functionality:**
- `total_events` by `event_name`
- Most used: Date range change (114,290 events, 12,778 suppliers)

**Q6 - Action-Taking:**
- `suppliers_who_resolved_from_ph` - 691 suppliers
- `actions_resolved_from_ph` - 1,478 total resolves
- `resolve_rate_from_pp` - 8.3%

**Use Cases:**
- MAU/WAU trending
- Event volume by type
- Page view distribution (BP vs PP)
- Action-taking rates

---

## How to Build the Dashboard

### Q1: How many relevant suppliers is the Performance Hub reaching?

**Explore:** `Performance Hub - Reach Analysis`

**Tiles:**

**1. Top-line Reach Metrics (Single Value)**
- **Measures:**
  - `Dim Supplier Relevance > Count Relevant Suppliers` (48,520)
  - `Agg Supplier Performance Hub Engagement > Count Suppliers Post Rollout` (14,753)
- **Custom Field:** Reach Rate = `count_suppliers_post_rollout / count_relevant_suppliers`
- **Viz:** Single value showing 30.4%

**2. Reach by Managed Status (Bar Chart)**
- **Dimensions:** `Dim Supplier Summary > Is Managed`
- **Measures:** `Count Suppliers Post Rollout`, `Count Relevant Suppliers`
- **Table Calculation:** Reach Rate by segment
- **Viz:** Bar chart (Managed: 41.8%, Non-Managed: 28.4%)

**3. Reach by Connected Status (Bar Chart)**
- **Dimensions:** `Dim Supplier Summary > Is Connected`
- **Measures:** `Count Suppliers Post Rollout`, `Count Relevant Suppliers`
- **Table Calculation:** Reach Rate by segment
- **Viz:** Bar chart (both ~30%)

**4. BP vs PP Visitors (Table)**
- **Dimensions:** None
- **Measures:**
  - `Agg Supplier Performance Hub Engagement > Count BP Visitors` (15,377)
  - `Agg Supplier Performance Hub Engagement > Count PP Visitors` (8,352)
  - `Agg Supplier Performance Hub Engagement > PP Navigation Rate` (54.3%)
- **Viz:** Single-row table

---

### Q2: How active are suppliers with the Performance Hub?

**Explore:** `Performance Hub Usage`

**Tiles:**

**1. Monthly Active Suppliers (MAU) Trend (Table)**
- **Dimensions:** `Performance Hub Events > Date Month`
- **Measures:**
  - `Performance Hub Events > MAU`
  - `Performance Hub Events > Total Page Views`
- **Filters:** `Date Date >= 2026-03-01`
- **Viz:** Table
  - March 2026: 1,162 MAU (early access only)
  - April 2026 (1-17): 15,129 MAU

**2. Weekly Active Suppliers (WAU) Post Full Rollout (Table)**
- **Dimensions:** `Performance Hub Events > Date Week`
- **Measures:**
  - `Performance Hub Events > MAU` (overall WAU)
  - `Performance Hub Events > BP Visitors`
  - `Performance Hub Events > PP Visitors`
  - `Performance Hub Events > Total Events`
- **Filters:** `Date Date` between `2026-03-30` and `2026-04-17`
- **Viz:** Table showing weekly progression:
  - Week 1 (Mar 30 - Apr 5): 5,142 WAU
  - Week 2 (Apr 6-12): 11,119 WAU
  - Week 3 (Apr 13-17, partial): 8,331 WAU

---

### Q3: How are suppliers using each section of the Performance Hub?

**Explore:** `Performance Hub Usage`

**Tiles:**

**1. Usage Summary by Page Type (Table)**
- **Dimensions:** `Performance Hub Events > Page Type`
- **Measures:**
  - `Performance Hub Events > MAU` (unique suppliers)
  - `Performance Hub Events > Total Page Views`
- **Table Calculation:** Avg Page Views per Visitor
- **Filters:** Post rollout window (Mar 30 - Apr 17)
- **Viz:** Table:
  - Business Performance: 15,377 suppliers, 236,448 views, 15.4 avg
  - Product Performance: 8,352 suppliers, 84,365 views, 10.1 avg

**2. PP Navigation Rate (Single Value)**
- **Measures:**
  - `Performance Hub Events > BP Visitors`
  - `Performance Hub Events > PP Visitors`
- **Table Calculation:** `pp_visitors / bp_visitors`
- **Filters:** Post rollout window
- **Viz:** Single value: 54.3%

---

### Q4: How deeply do suppliers engage per visit?

**Explore:** `Supplier Performance Hub Engagement`

**Tiles:**

**1. Per-User Engagement Depth (Table)**
- **Dimensions:** None
- **Measures:**
  - `Agg Supplier Performance Hub Engagement > Avg BP Page Views` (15.4)
  - `Agg Supplier Performance Hub Engagement > Median BP Page Views` (6.0)
  - `Agg Supplier Performance Hub Engagement > Avg PP Page Views` (10.2)
  - `Agg Supplier Performance Hub Engagement > Median PP Page Views` (5.0)
  - `Agg Supplier Performance Hub Engagement > Avg Interactions per Supplier` (11.9)
  - `Agg Supplier Performance Hub Engagement > Median Interactions per Supplier` (5.0)
  - `Agg Supplier Performance Hub Engagement > Avg Events per Supplier` (31.6)
  - `Agg Supplier Performance Hub Engagement > Median Events per Supplier` (13.0)
- **Filters:** None (full availability window)
- **Viz:** Two-column table (Mean | Median)

**2. Engagement Tier Distribution (Column Chart)**
- **Dimensions:** `Agg Supplier Performance Hub Engagement > Engagement Tier`
- **Measures:** `Agg Supplier Performance Hub Engagement > Count Suppliers`
- **Viz:** Column chart showing distribution:
  - Light (1-5 events)
  - Moderate (6-15 events)
  - Active (16-50 events)
  - Power User (50+ events)

---

### Q5: What functionality is most used?

**Explore:** `Performance Hub Usage`

**Tiles:**

**1. Event Volume Breakdown (Table)**
- **Dimensions:**
  - `Performance Hub Events > Event Name`
  - `Performance Hub Events > Event Category` (optional, for grouping)
- **Measures:**
  - `Performance Hub Events > MAU` (unique suppliers)
  - `Performance Hub Events > Total Events`
- **Filters:** Full availability window (Mar 2 - Apr 17)
- **Sort:** By `Total Events` descending
- **Viz:** Table showing:
  - SupplierPerformancePageRequest: 15,384 suppliers, 237,255 events
  - SupplierBusinessPerformanceDateRangeChange: 12,778 suppliers, 114,290 events
  - SupplierProductPerformancePageRequest: 8,363 suppliers, 85,230 events
  - SupplierPerformanceTopActionsVisible: 12,060 suppliers, 40,542 events
  - etc.

---

### Q6: Are suppliers taking action from the Performance Hub?

**Explore:** `Performance Hub Usage` or `Supplier Performance Hub Engagement`

**Tiles:**

**1. Action-Taking From Performance Hub (Table)**
- **Dimensions:** None
- **Measures:**
  - `Performance Hub Events > PP Visitors` (8,352)
  - `Performance Hub Events > Suppliers Who Resolved from PH` (691)
  - `Performance Hub Events > Resolve Rate from PP` (8.3%)
  - `Performance Hub Events > Actions Resolved from PH` (1,478)
- **Filters:** Post rollout window (Mar 30 - Apr 17)
- **Viz:** Single-row table

**Alternative (using engagement explore):**
- **Measures:**
  - `Agg Supplier Performance Hub Engagement > Count PP Visitors`
  - `Agg Supplier Performance Hub Engagement > PP Resolve Rate`
- **Filters:** `Visited Post Rollout = Yes`

**2. Interaction Rates (Table)**
- **Explore:** `Supplier Performance Hub Engagement`
- **Measures:**
  - `Agg Supplier Performance Hub Engagement > Date Range Change Rate` (83.1%)
  - `Agg Supplier Performance Hub Engagement > RA Widget Scroll Rate` (78.4%)
  - `Agg Supplier Performance Hub Engagement > RA Widget Click Rate` (22.3%)
  - `Agg Supplier Performance Hub Engagement > PP Resolve Rate` (8.3%)
- **Filters:** `Visited Post Rollout = Yes`
- **Viz:** Single-row table

---

### Q7: Are suppliers returning to the Performance Hub?

**Explore:** `Supplier Performance Hub Engagement`

**Tiles:**

**OPTION A: N-Month Retention Curves (Recommended - Comparable Across Cohorts)**

**1. Retention Rates by Cohort Month (Table)**
- **Dimensions:** `Agg Supplier Performance Hub Engagement > First Visit Month Month`
- **Measures:**
  - `Agg Supplier Performance Hub Engagement > Cohort Size`
  - `Agg Supplier Performance Hub Engagement > 1-Month Retention Rate`
  - `Agg Supplier Performance Hub Engagement > 2-Month Retention Rate`
  - `Agg Supplier Performance Hub Engagement > 3-Month Retention Rate`
- **Viz:** Table showing retention curves for each cohort
- **Note:** All cohorts measured with same time windows (1, 2, 3 months after first visit)
- **Interpretation:**
  - March cohort 1-month = % who returned in April
  - March cohort 2-month = % who returned in April OR May
  - March cohort 3-month = % who returned in April, May, OR June

**2. Retention Curve Line Chart**
- **Viz:** Line Chart
- **X-axis:** `Agg Supplier Performance Hub Engagement > First Visit Month Month`
- **Y-axis (3 series):**
  - `1-Month Retention Rate`
  - `2-Month Retention Rate`
  - `3-Month Retention Rate`
- **Shows:** How retention evolves over time for different cohorts

**3. Retention by Segment (Pivot Table)**
- **Dimensions:**
  - `Agg Supplier Performance Hub Engagement > First Visit Month Month`
  - `Dim Supplier Summary > Is Managed`
- **Measures:**
  - `Agg Supplier Performance Hub Engagement > Cohort Size`
  - `Agg Supplier Performance Hub Engagement > 1-Month Retention Rate`
- **Viz:** Pivot table (cohort months as rows, managed status as columns)

---

**OPTION B: Legacy March → April Analysis (Specific)**

**1. Early Cohort Returning Rate (Single Value)**
- **Measures:**
  - `Agg Supplier Performance Hub Engagement > March Cohort Early Access` (1,303)
  - `Agg Supplier Performance Hub Engagement > Returned in April Count` (1,019)
  - `Agg Supplier Performance Hub Engagement > Returning Rate` (78.2%)
- **Viz:** Single value showing returning rate
  - Comparison label: "March Cohort Size"

**2. Retention by Segment (Table)**
- **Dimensions:** `Dim Supplier Summary > Is Managed`
- **Measures:**
  - `Agg Supplier Performance Hub Engagement > March Cohort Early Access`
  - `Agg Supplier Performance Hub Engagement > Returned in April Count`
  - `Agg Supplier Performance Hub Engagement > Returning Rate`
- **Viz:** Table showing retention by managed status

---

## Dashboard Filters

Add these cross-dashboard filters:

1. **Date Range** (applies to date_date)
   - Default: `is on or after 2026-03-30` (post full rollout)
   - For Q4: Remove filter (use full availability window)

2. **Supplier Segment** (field filter on supplier_segment)
   - Default: All

3. **Managed Status** (field filter on is_managed)
   - Default: All

4. **Connected Status** (field filter on is_connected)
   - Default: All

---

## Key Dates & Windows

| Period | Dates | Description |
|--------|-------|-------------|
| Early Access | March 2-29, 2026 | Before full homepage widget |
| Full Rollout | March 30-31, 2026 | Homepage widget deployed to all suppliers |
| **Post Rollout Window** | **March 30 - April 17, 2026** | **Primary analysis period (19 days)** |
| Full Availability | March 2 - April 17, 2026 | All data since PH launched |

---

## Summary: Which Explore for Which Question?

| Question | Explore | Focus |
|----------|---------|-------|
| Q1: Reach | `performance_hub_reach_analysis` | Reach rate with relevant supplier denominator |
| Q2: Activity (MAU/WAU) | `performance_hub_usage` | Monthly and weekly active users |
| Q3: Section Usage | `performance_hub_usage` | BP vs PP page views, navigation rate |
| Q4: Engagement Depth | `supplier_performance_hub_engagement` | Per-supplier event/interaction averages |
| Q5: Functionality | `performance_hub_usage` | Event volume by type |
| Q6: Action-Taking | `performance_hub_usage` or `supplier_performance_hub_engagement` | Resolve rates from PP |
| Q7: Returning Suppliers | `supplier_performance_hub_engagement` | March → April cohort retention |

---

## Files Created

```
gyg-looker/
├── explores/supply_operations/
│   ├── performance_hub_reach_analysis.explore.lkml (NEW)
│   └── supplier_performance_hub_engagement.explore.lkml (NEW)
├── views/supply_analytics/
│   ├── agg_supplier_performance_hub_engagement.view.lkml (NEW)
│   ├── performance_hub_events.view.lkml (existing)
│   ├── dim_supplier_summary.view.lkml (existing)
│   └── dim_supplier_relevance.view.lkml (existing)
└── models/
    └── supply_operations.model.lkml (updated to include new explores)
```

Branch: `dev-performance-hub-feature-audit`

Committed: Yes (commit 08afdd81a)

---

## Next Steps

1. **Switch to your Looker dev branch:** `dev-performance-hub-feature-audit`
2. **Verify explores appear** in Looker UI under Supply Operations model
3. **Create dashboard manually** using the tiles above
4. **Test with filters** and drill-downs
5. **Deploy to production** when validated
