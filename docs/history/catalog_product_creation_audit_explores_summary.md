# Catalog Feature Audit: Product Creation - Explores Summary

Created explores to replicate the Confluence Product Creation analysis in Looker dashboards.

**Confluence Reference:** https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4206461002/Catalog+Feature+Audit+-+Product+Creation

**Branch:** `dev-catalog-product-creation-audit`

---

## Explores Created

### 1. `tour_creation_overview` (Q1, Q2, Q5, Q7)
**For: Volume trends, AI adoption, category performance, anomalies**

**Purpose:** High-level creation analytics

**Base View:** `agg_tour_creation_session` (tour-level aggregations)

**Joined Views:**
- `ai_content_generation` (optional, for AI backend validation)

**Key Metrics:**
- `tours_started` - Total tours reaching Activity Creation Start
- `tours_submitted` - Tours reaching Activity Submitted
- `submission_rate` - % of started tours submitted
- `ai_adoption_rate` - % using AI Content Creator
- `submission_rate_ai` - Submission rate for AI path (76.5%)
- `submission_rate_manual` - Submission rate for manual path (69.7%)

**Use Cases:**
- Q1: Monthly/weekly volume trends
- Q2: AI adoption and submission by path
- Q5: Submission rates by category
- Q7: Weekly anomaly detection

---

### 2. `tour_creation_funnel_analysis` (Q3)
**For: Funnel drop-off analysis**

**Purpose:** Step-by-step wizard funnel

**Base View:** `tour_creation_funnel` (step-level data)

**Key Metrics:**
- `tours_reached_step` - Distinct tours reaching each step
- Step dimensions: `step_name`, `step_number`, `step_category`

**Use Cases:**
- Q3: Identify where suppliers drop off in wizard
- Step-by-step conversion rates
- Time-based drop-off trends

---

### 3. `tour_activation_analysis` (Q6)
**For: 30-day booking activation**

**Purpose:** Activation rate (first booking within 30 days)

**Base View:** `agg_tour_activation` (tour submission + 30-day lookback)

**Key Metrics:**
- `tours_submitted_observable` - Tours with complete 30-day window
- `tours_activated` - Tours with ≥1 booking in 30 days
- `activation_rate` - Overall 30-day activation rate (16.0%)
- `activation_rate_ai` - AI path activation (15.2%)
- `activation_rate_manual` - Manual path activation (18.7%)

**IMPORTANT:** Always filter `Observation Complete = Yes` (already set as always_filter)

---

## Dashboard Build Guide

### Q1: What is the overall creation volume and trend?

**Explore:** `Tour Creation - Overview`

**Tile 1: Monthly Volume Summary (Table)**
- **Dimensions:** `Agg Tour Creation Session > Creation Start Month`
- **Measures:**
  - `Tours Started`
  - `Tours Submitted`
  - `Submission Rate`
- **Viz:** Table
- **Expected Results:**
  - Jan 2026: 27,307 started, 21,696 submitted, 79.5%
  - Feb 2026: 26,947 started, 21,247 submitted, 78.9%
  - Mar 2026: 33,416 started, 25,875 submitted, 77.4%
  - Apr 2026 (1-14): 14,818 started, 11,317 submitted, 76.4%

**Tile 2: Monthly Trend Line Chart**
- **Viz:** Line Chart
- **X-axis:** `Creation Start Month`
- **Y-axis:** `Tours Started`, `Tours Submitted`
- Shows growth momentum over time

---

### Q2: How widely is the AI Content Creator being used?

**Explore:** `Tour Creation - Overview`

**Tile 1: AI vs Manual Submission Rate (Table)**
- **Dimensions:** `Agg Tour Creation Session > Creation Path`
- **Measures:**
  - `Tours Started`
  - `Tours Submitted`
  - `Submission Rate`
- **Viz:** Table
- **Expected Results:**
  - AI Content Creator: 77,582 started, 59,338 submitted, **76.5%**
  - Manual (No AI): 24,906 started, 17,368 submitted, **69.7%**

**Tile 2: AI Adoption Rate Over Time (Line Chart)**
- **Dimensions:** `Creation Start Month` or `Creation Start Week`
- **Measures:**
  - `AI Adoption Rate`
  - `Tours Started`
- **Viz:** Line Chart (or combo chart)
- Shows AI adoption trending ~75-80% baseline

**Tile 3: Time to Submit by Path (Table)**
- **Dimensions:** `Creation Path`
- **Measures:**
  - `Median Hours to Submit`
  - `P25 Hours to Submit`
  - `P75 Hours to Submit`
- **Viz:** Table
- **Expected Results:**
  - Both paths: Median < 1 hour
  - AI path: P75 = 6 hours
  - Manual path: P75 = 3 hours

---

### Q3: Where are suppliers dropping off in the creation wizard?

**Explore:** `Tour Creation - Funnel Drop-offs`

**Tile 1: Funnel Visualization (Table)**
- **Dimensions:**
  - `Agg Tour Creation Funnel > Step #`
  - `Agg Tour Creation Funnel > Step Name`
- **Measures:** `Tours Reached Step`
- **Sort:** By `Step #` ascending (automatically sorts by funnel order 1→16)
- **Viz:** Table showing Confluence step numbers (1, 4, 5, 6, 7, 8, 13, 14, 16, 17, 18, 21, 22, 26, 27, 28)
- **Table Calculations (to match Confluence):**
  
  **% of Starts:**
  - Formula: `${tours_reached_step} / ${tours_reached_step:first_value}`
  - Format: Percentage (1 decimal)
  
  **Drop from Previous Step:**
  - Formula: `if(${tours_reached_step} < ${tours_reached_step:previous_value}, (${tours_reached_step:previous_value} - ${tours_reached_step}) / ${tours_reached_step:previous_value}, null)`
  - Format: Percentage (1 decimal)
  - Shows "∅" when tours increase (steps 17, 21, 27, 28) matching Confluence "—"

**Expected Results (matching Confluence Table 3.1):**
- Funnel Sequence 1 (Activity Creation Start): 91,199 tours
- Funnel Sequence 2 (Activity Title): 81,760 tours (–10.4% from start)
- Funnel Sequence 11 (Activity Availability Schedule): 63,709 tours (–12.9% from Availability & Pricing)
- Funnel Sequence 14 (Activity Itinerary): 51,004 tours (–28.2% from previous, optional step)
- Funnel Sequence 16 (Activity Submitted): 71,360 tours

**Key Drop-offs to Highlight:**
1. Creation Start → Title: –10.4% (91,199 → 81,760)
2. Availability & Pricing → Schedule: –12.9% (73,124 → 63,709)
3. Addons → Itinerary: –28.2% (expected, itinerary is optional)

**Tile 2: Funnel by Step Category (Bar Chart)**
- **Dimensions:** `Step Category`
- **Measures:** `Tours Reached Step`
- **Viz:** Horizontal bar chart showing volume by category
- Categories: Onboarding, AI Generation, Content, Options, Logistics, Availability & Pricing, Review & Submit

---

### Q4: How reliable is the AI content generation system?

**Explore:** `Tour Creation - Overview`

**Tile 1: AI Generation Success Rate by Month (Table)**
- **Dimensions:** None (or use `AI Content Generation > Update Timestamp Month` if you join)
- **Measures:**
  - `AI Content Generation > Total Generations`
  - `AI Content Generation > Successful Generations`
  - `AI Content Generation > Failed Generations`
  - `AI Content Generation > Success Rate`
- **Viz:** Table
- **Expected Results:**
  - Jan 2026: 15,765 total, 99.6% success
  - Feb 2026: 14,293 total, **98.4% success** (anomaly)
  - Mar 2026: 17,807 total, 99.6% success
  - Apr 2026 (1-14): 8,200 total, 99.4% success

**Alternative (without join):**
- Use `Tour Creation - Overview` explore
- Filter to `Used AI = Yes`
- Show tours started by month
- Note: This shows AI step reach, not backend generation success
- For backend success rate, join `ai_content_generation` view

---

### Q5: How does creation performance vary by category?

**Explore:** `Tour Creation - Overview`

**Tile 1: Submission Rate by Category (Table)**
- **Dimensions:** `Agg Tour Creation Session > Category`
- **Measures:**
  - `Tours Started`
  - `Tours Submitted`
  - `Submission Rate`
- **Sort:** By `Tours Started` descending (to show top categories first)
- **Viz:** Table
- **Expected Results:**
  - Bus Tours: 17,202 started, 85.2%
  - Walking Tours: 17,754 started, 81.3%
  - Day Trips: 15,240 started, 84.3%
  - Adventure Tours: 11,718 started, 85.0%
  - **Transfers: 3,185 started, 66.1%** (below average)
  - **City Cards: 730 started, 60.0%** (below average)

**Tile 2: Submission Rate by Category (Bar Chart)**
- **Viz:** Horizontal bar chart
- **X-axis:** `Submission Rate`
- **Y-axis:** `Category`
- Color-code bars below 70% in red to highlight problem categories

---

### Q6: What share of newly submitted tours receive a first booking within 30 days?

**Explore:** `Tour Creation - 30-Day Activation`

**IMPORTANT:** The explore has `always_filter: observation_complete = yes` already applied. This ensures only tours with complete 30-day windows are included.

**Tile 1: Activation Rate by Creation Path (Table)**
- **Dimensions:** `Agg Tour Activation > Creation Path`
- **Measures:**
  - `Tours Submitted (Observable)`
  - `Tours Activated`
  - `Activation Rate (1B30D)`
- **Filters:** (Already applied: `Observation Complete = Yes`)
- **Additional Filter:** `Submission Month = 2026-01-01` (for Jan cohort, to match Confluence analysis)
- **Viz:** Table
- **Expected Results (January 2026 submissions):**
  - AI Content Creator: 15,933 submitted, 2,425 activated, **15.2%**
  - Manual (No AI): 5,763 submitted, 1,079 activated, **18.7%**
  - Overall: 21,696 submitted, 3,465 activated, **16.0%**

**Tile 2: Activation Rate by Category (Table)**
- **Dimensions:** `Category`
- **Measures:**
  - `Tours Submitted (Observable)`
  - `Activation Rate (1B30D)`
- **Filters:** `Submission Month = 2026-01-01`
- **Viz:** Table showing activation by category
- Identifies which categories activate faster/slower

**Tile 3: Activation Rate Over Time (Line Chart)**
- **Dimensions:** `Submission Month`
- **Measures:** `Activation Rate (1B30D)`
- **Viz:** Line chart tracking activation trends
- **Note:** Only shows months with complete 30-day observation windows

---

### Q7: Weekly Performance Monitoring (Anomaly Detection)

**Explore:** `Tour Creation - Overview`

**Purpose:** Monitor week-over-week trends to detect platform issues, AI system degradation, or unusual supplier behavior patterns.

**Tile 1: Weekly Performance Metrics (Table)**
- **Dimensions:** `Agg Tour Creation Session > Creation Start Week`
- **Measures:**
  - `Tours Started`
  - `Tours Submitted`
  - `Submission Rate`
  - `AI Adoption Rate`
- **Filters:** `Creation Start Date >= 2026-01-01` (adjust as needed for ongoing monitoring)
- **Viz:** Table
- **What to watch for:**
  - Submission rate drops below 75%
  - AI adoption rate drops more than 5-10 pp from baseline (~75-80%)
  - Sudden volume spikes or drops (>20% week-over-week)

**Tile 2: Weekly Trends (Line Chart)**
- **Viz:** Line chart with dual axis
- **X-axis:** `Creation Start Week`
- **Y-axis (left):** `Submission Rate`
- **Y-axis (right):** `AI Adoption Rate`
- **Purpose:** Visual trend monitoring - deviations from baseline indicate potential issues

**Tile 3: AI Generation Success Rate by Week (Line Chart)**
- **Explore:** `Tour Creation - Overview` (with `ai_content_generation` join)
- **Dimensions:** `AI Content Generation > Update Timestamp Week`
- **Measures:** `Success Rate`
- **Filters:** `AI Content Generation > Update Timestamp Date >= 2026-01-01`
- **Viz:** Line chart
- **X-axis:** `Update Timestamp Week`
- **Y-axis:** `Success Rate`
- **What to watch for:** Success rate drops below 99% (indicates AI backend issues)

---

## Dashboard Filters

Add these cross-dashboard filters:

1. **Date Range Filter (Creation Start Date)**
   - Default: `>= 2026-01-01` (analysis start)
   - Allow users to select custom ranges for ongoing tracking

2. **Creation Path Filter**
   - Field: `Creation Path`
   - Options: AI Content Creator, Manual (No AI), All
   - Default: All

3. **Category Filter**
   - Field: `Category`
   - Options: All categories
   - Default: All

---

## Key Dates & Windows

| Period | Dates | Description |
|--------|-------|-------------|
| Full Analysis Window | Jan 1 - Apr 14, 2026 | Initial Confluence analysis period |
| Funnel Analysis Window | Jan 15 - Apr 14, 2026 | Step-level funnel tracking baseline |
| Activation Cohort | January 2026 | First submissions with complete 30-day observation window |
| Dashboard Date Range | Ongoing | Set filters to track current periods (e.g., last 3 months, last 30 days) |

---

## Summary: Which Explore for Which Question?

| Question | Explore | Focus |
|----------|---------|-------|
| Q1: Volume & Trend | `tour_creation_overview` | Monthly/weekly creation volume |
| Q2: AI Adoption | `tour_creation_overview` | AI vs Manual submission rates |
| Q3: Funnel Drop-offs | `tour_creation_funnel_analysis` | Step-by-step wizard conversion |
| Q4: AI Reliability | `tour_creation_overview` (with AI join) | AI generation success rate |
| Q5: Category Performance | `tour_creation_overview` | Submission rate by category |
| Q6: 30-Day Activation | `tour_activation_analysis` | First booking within 30 days |
| Q7: Weekly Performance Monitoring | `tour_creation_overview` | Weekly anomaly detection, AI health monitoring |

---

## Files Created

```
gyg-looker/
├── explores/supply_operations/
│   ├── tour_creation_overview.explore.lkml (NEW)
│   ├── tour_creation_funnel_analysis.explore.lkml (NEW)
│   └── tour_activation_analysis.explore.lkml (NEW)
├── views/supply_analytics/
│   ├── agg_tour_creation_session.view.lkml (NEW)
│   ├── tour_creation_funnel.view.lkml (NEW)
│   ├── ai_content_generation.view.lkml (NEW)
│   └── agg_tour_activation.view.lkml (NEW)
└── models/
    └── supply_operations.model.lkml (updated)
```

Branch: `dev-catalog-product-creation-audit`

Committed: Yes (commit 511d76608)

---

## Next Steps

1. **Switch to your Looker dev branch:** `dev-catalog-product-creation-audit`
2. **Verify explores appear** in Looker UI under Supply Operations model
3. **Create dashboard manually** using the tiles above
4. **Test with filters** and drill-downs
5. **Deploy to production** when validated

---

## Data Sources

| Table | Catalog / Schema | Purpose |
|-------|-----------------|---------|
| `tour_creation_funnel` | `production.supply_analytics` | Wizard step tracking |
| `catalog__tour_generated_content` | `production.db_mirror_dbz` | AI generation backend |
| `catalog__tour_business_category` | `production.db_mirror_dbz` | Category assignments |
| `dim_activity_lookback_activation` | `production.supply` | 30-day booking activation |

---

## Known Limitations

1. **Category assignment timing:** 16.7% of tours show as "Other / Unclassified" because category is assigned post-creation
2. **AI backend vs. funnel gap:** ~22K difference between funnel AI step reach (78,487) and backend generation calls (56,178). Use funnel-based AI adoption rate (75.7%) as the conservative metric.
3. **Activation window:** Only January 2026 cohort has complete 30-day observation window as of April 15, 2026. Filter to observable cohorts only.
4. **Time zone:** All timestamps in UTC
