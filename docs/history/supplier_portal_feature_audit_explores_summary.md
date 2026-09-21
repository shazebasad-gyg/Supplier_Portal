# Supplier Portal Feature Audit - Explores Summary

Created explores to replicate the Confluence Feature Audit analysis in Looker dashboards.

**Confluence Reference:** https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4197253805

---

## Explores Created

### 1. `recommended_actions_reach_analysis` 
**For Q1: How many suppliers is the feature reaching?**

**Purpose:** Calculate reach rate with proper denominator (relevant suppliers)

**Base View:** `dim_supplier_relevance` (relevant supplier universe)

**Joined Views:**
- `dim_supplier_summary` (segmentation: managed, connected, segment)
- `dim_recommended_actions` (actions surfaced)

**Key Metrics:**
- `count_relevant_suppliers` - Total relevant suppliers (denominator)
- `total_suppliers_reached` - Suppliers who received ≥1 action (numerator)
- Reach Rate = suppliers_reached / relevant_suppliers

**Use Cases:**
- Reach rate by managed/unmanaged
- Reach rate by connected/non-connected  
- Reach by action type
- Reach trending over time

**Always Filtered:** Only relevant suppliers (is_relevant = yes)

---

### 2. `supplier_engagement_recommended_actions`
**For Q3, Q5, Q7: Conversion, repeat engagement, cohort progression**

**Purpose:** Supplier-level engagement analysis (NOT action-level)

**Base View:** `supplier_engagement_metrics` (derived table, one row per supplier)

**Joined Views:**
- `dim_supplier_summary` (segmentation)
- `dim_supplier_relevance` (relevance criteria)

**Key Metrics:**

**Q3 - Conversion:**
- `count_suppliers` - Total suppliers reached
- `count_converting_suppliers` - Suppliers who resolved ≥1
- `supplier_conversion_rate` - % of reached who converted

**Q5 - Repeat Engagement:**
- `engagement_tier` - Single-Use, Occasional, Regular, Power User
- `repeat_user_rate` - % of converters who resolved >1
- `avg_actions_resolved_per_supplier` - Mean resolved count
- `median_actions_resolved` - Median resolved count

**Q7 - Cohort Progression:**
- `was_q3_2025_single_use` - Flag for Q3 2025 single-use suppliers
- `q1_2026_engagement_tier` - Tier by end of Q1 2026
- `progressed_from_q3_single_use` - Flag for progression
- `cohort_progression_rate` - % who moved to higher tier

**Use Cases:**
- Supplier conversion rate by segment
- Engagement tier distribution
- Repeat behavior patterns
- Cohort progression tracking (Q3 2025 → Q1 2026)

---

### 3. `feature_usage_outcomes` (existing, enhanced)
**For Q2, Q4, Q6: Resolution rates, trending, timing**

**Purpose:** Action-level analysis (one row per action instance)

**Base View:** `dim_recommended_actions`

**Key Metrics:**

**Q2 - Resolution Analysis:**
- `total_actions` - Actions surfaced
- `actions_resolved` - Actions resolved
- `resolution_rate` - Overall resolution %
- `resolution_rate_28d` - 28-day resolution % (benchmark: 30%)
- `dismissal_rate_over_actioned` - % dismissed (benchmark: <10%)
- `expiry_rate_over_closed` - % expired

**Q4 - Trending:**
- `surfaced_at_month` - Time dimension
- All metrics above by month

**Q6 - Action Lifecycle Timing:**
- `time_to_resolve_tier` - Same day, 1-3 days, 4-7, 8-14, 15-30, 31-60, 60+
- `days_to_resolve` - Numeric days
- `avg_days_to_resolve` - Mean resolution time

**Use Cases:**
- Resolution rates by action type
- Monthly trends
- Time-to-resolution distribution
- Dismissal reason analysis
- Status funnel (resolved, dismissed, expired, active)

---

## How to Build the Dashboard

### Q1: Reach Analysis

**Explore:** `recommended_actions_reach_analysis`

**Tiles:**
1. **Top-line Reach Metrics**
   - Dimensions: None
   - Measures: `count_relevant_suppliers`, `total_suppliers_reached`
   - Calculation: Reach Rate = suppliers_reached / relevant_suppliers

2. **Reach by Managed Status**
   - Dimensions: `is_managed`
   - Measures: `total_suppliers_reached`
   - Visualization: Bar chart

3. **Reach by Connected Status**
   - Dimensions: `is_connected`  
   - Measures: `total_suppliers_reached`
   - Visualization: Bar chart

4. **Reach by Action Type**
   - Dimensions: `action_type`
   - Measures: `total_suppliers_reached`, `total_actions`
   - Visualization: Bar chart, sorted by suppliers reached desc

---

### Q2: Resolution Analysis

**Explore:** `feature_usage_outcomes`

**Tiles:**
1. **Overall Status Funnel**
   - Dimensions: `status`
   - Measures: `total_actions`
   - Visualization: Column chart

2. **Key Performance Metrics**
   - Dimensions: None
   - Measures: `total_actions`, `resolution_rate`, `resolution_rate_28d`, `dismissal_rate_over_actioned`, `expiry_rate_over_closed`
   - Visualization: Table with conditional formatting (28d rate benchmark 30%)

3. **Resolution Rate by Action Type**
   - Dimensions: `action_type`
   - Measures: `total_actions`, `resolution_rate`, `resolution_rate_28d`, `dismissal_rate_over_actioned`, `expiry_rate_over_closed`, `avg_days_to_resolve`
   - Visualization: Table, sorted by 28d rate desc
   - Conditional formatting: Highlight 28d rate ≥30% green

4. **Top Dismissal Reasons**
   - Dimensions: `action_type`, `dismissal_reason`
   - Measures: `actions_dismissed`
   - Filters: `is_dismissed = yes`
   - Sorts: Count desc
   - Limit: 10

---

### Q3: Supplier Conversion

**Explore:** `supplier_engagement_recommended_actions`

**Tiles:**
1. **Supplier Conversion Metrics**
   - Dimensions: None
   - Measures: `count_suppliers`, `count_converting_suppliers`, `supplier_conversion_rate`
   - Visualization: Single value (conversion rate), with comparison (suppliers reached)

2. **Conversion by Managed Status**
   - Dimensions: `is_managed`
   - Measures: `count_suppliers`, `count_converting_suppliers`, `supplier_conversion_rate`
   - Visualization: Column chart

3. **Conversion by Connected Status**
   - Dimensions: `is_connected`
   - Measures: `count_suppliers`, `count_converting_suppliers`, `supplier_conversion_rate`
   - Visualization: Column chart

---

### Q4: Trending Over Time

**Explore:** `feature_usage_outcomes`

**Tiles:**
1. **Monthly Resolution Rate Trend**
   - Dimensions: `surfaced_at_month`
   - Measures: `total_actions`, `total_suppliers_reached`, `resolution_rate_28d`
   - Visualization: Line chart (resolution rate) + column chart (volume)
   - Reference line: 30% benchmark

2. **Monthly Metrics Table**
   - Dimensions: `surfaced_at_month`
   - Measures: `total_actions`, `total_suppliers_reached`, `resolution_rate_28d`, `resolution_rate`, `expiry_rate_over_closed`, `dismissal_rate_over_actioned`
   - Visualization: Table with conditional formatting
   - Sort: Month desc

---

### Q5: Repeat Engagement

**Explore:** `supplier_engagement_recommended_actions`

**Tiles:**
1. **Engagement Tier Distribution**
   - Dimensions: `engagement_tier`
   - Measures: `count_suppliers`, percent of total
   - Filters: `is_converter = yes` (only converting suppliers)
   - Visualization: Donut chart or column chart

2. **Repeat User Rate**
   - Dimensions: None
   - Measures: `count_converting_suppliers`, `count_repeat_users`, `repeat_user_rate`
   - Visualization: Single value

3. **Engagement Depth Metrics**
   - Dimensions: None
   - Measures: `avg_actions_resolved_per_supplier`, `median_actions_resolved`
   - Filters: `is_converter = yes`
   - Visualization: Table

---

### Q6: Action Lifecycle Timing

**Explore:** `feature_usage_outcomes`

**Tiles:**
1. **Time from Surfaced to Resolved**
   - Dimensions: `time_to_resolve_tier`
   - Measures: `actions_resolved`, percent of resolved
   - Filters: `is_resolved = yes`
   - Visualization: Column chart

2. **Cumulative Resolution by Days**
   - Dimensions: `time_to_resolve_tier`
   - Measures: `actions_resolved` (cumulative)
   - Filters: `is_resolved = yes`
   - Visualization: Area chart

---

### Q7: Engagement Depth & Cohort Progression

**Explore:** `supplier_engagement_recommended_actions`

**Tiles:**
1. **Engagement Tier Distribution (Current)**
   - Dimensions: `engagement_tier`
   - Measures: `count_suppliers`
   - Filters: `is_converter = yes`
   - Visualization: Column chart

2. **Q3 2025 Single-Use Cohort Progression**
   - Dimensions: `q1_2026_engagement_tier`
   - Measures: `count_suppliers`
   - Filters: `was_q3_2025_single_use = yes`
   - Visualization: Column chart showing progression

3. **Cohort Progression Metrics**
   - Dimensions: None
   - Measures: `count_q3_single_use_cohort`, `count_progressed_from_single_use`, `cohort_progression_rate`
   - Visualization: Single value (progression rate)

4. **Cohort Progression by Segment**
   - Dimensions: `is_managed` or `supplier_segment`
   - Measures: `count_q3_single_use_cohort`, `cohort_progression_rate`
   - Filters: `was_q3_2025_single_use = yes`
   - Visualization: Table

---

## Dashboard Filters

Add these dashboard-level filters:

1. **Date Range** (surfaced_at_date)
   - Default: "after 2025-05-15" (feature launch)
   - Type: date_filter

2. **Action Type** (action_type)
   - Default: all
   - Type: field_filter (tag_list)

3. **Supplier Segment** (supplier_segment)
   - Default: all
   - Type: field_filter (tag_list)

4. **Managed Status** (is_managed)
   - Default: all
   - Type: field_filter

5. **Connected Status** (is_connected)
   - Default: all  
   - Type: field_filter

---

## Key Tables Used

From Databricks (per Confluence analysis):

- **production.supply_analytics.dim_recommended_actions** - Primary action data
- **production.supply_analytics.dim_supplier_summary** - Supplier attributes
- **production.dwh.dim_tour** - Activity data
- **production.dwh.dim_tour_history** - Activity lifecycle
- **production.dwh.fact_booking** - Booking transactions

---

## Notes

1. **Reach Rate Denominator:** Always use `recommended_actions_reach_analysis` explore for Q1 to get proper denominator (relevant suppliers)

2. **Action-level vs Supplier-level:**
   - Use `feature_usage_outcomes` for action-level analysis (Q2, Q4, Q6)
   - Use `supplier_engagement_recommended_actions` for supplier-level (Q3, Q5, Q7)

3. **Performance:** All explores have aggregate tables defined for common query patterns

4. **Cohort Analysis:** Q3 2025 cohort is hardcoded (July-Sept 2025). For dynamic cohorts, create parameters

5. **Always Filters:**
   - `recommended_actions_reach_analysis`: Only relevant suppliers
   - `feature_usage_outcomes`: surfaced_at >= 2025-05-15 (feature launch)

---

## Files Created

```
gyg-looker/
├── explores/supply_operations/
│   ├── recommended_actions_reach_analysis.explore.lkml (NEW)
│   └── supplier_engagement_recommended_actions.explore.lkml (NEW)
├── views/supply_analytics/
│   ├── supplier_engagement_metrics.view.lkml (NEW)
│   ├── dim_recommended_actions.view.lkml (existing)
│   ├── dim_supplier_summary.view.lkml (existing)
│   └── dim_supplier_relevance.view.lkml (existing)
└── models/
    └── supply_operations.model.lkml (updated to include new explores)
```

Branch: `feature/supplier-portal-analytics`

Committed: Yes (commit eb8746bb1)

---

## Next Steps

1. Switch to your Looker dev branch
2. Pull the latest from `feature/supplier-portal-analytics`
3. Verify explores appear in Looker UI
4. Create dashboard manually using the tiles above
5. Test with filters and drill-downs
6. Deploy to production when validated
