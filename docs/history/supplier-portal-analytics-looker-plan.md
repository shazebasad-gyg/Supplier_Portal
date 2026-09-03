# Supplier Portal Analytics: Looker Implementation Plan

## Executive Summary

Based on your Confluence analysis, we need to build **3 core explores** in Looker that consolidate supplier portal engagement, feature usage, and business outcomes. These explores will power the three-tier dashboard system outlined in your implementation plan.

---

## Data Sources Identified

### Core Tables from Your Analysis:

| Table | Schema | Purpose |
|-------|--------|---------|
| **dim_supplier_summary** | production.supply_analytics | Supplier master: login metrics, segment, managed/connected status, NR tiers |
| **fact_supplier_history** | production.supply_analytics | Daily supplier snapshots: login flags, counts, bookings by date |
| **dim_recommended_actions** | production.supply_analytics | Recommended Actions: action_type, status, timestamps, dismissal_reason |
| **tour_creation_funnel** | production.supply_analytics | Tour creation wizard steps: step_name, step_number, timestamps |
| **events** | production.events | Supplier portal events: Performance Hub interactions, all event types |
| **fact_booking** | production.dwh | Booking transactions: GMV, NR, customer_id |
| **dim_tour** | production.dwh | Activity/tour master: status, gyg_status, supplier_id |
| **dim_tour_history** | production.dwh | Activity history: is_online, update_timestamp |
| **catalog__tour_generated_content** | production.db_mirror_dbz | AI content generation: status, timestamps |
| **catalog__tour_business_category** | production.db_mirror_dbz | Business categories: level1, level2, level3 |
| **dim_activity_lookback_activation** | production.supply | Activation metrics: has_booking_in_preceding_28_days |

---

## Proposed Looker Explore Architecture

### **Explore 1: Supplier Engagement & Portal Usage**
**Base Table:** `fact_supplier_history` (daily grain)

**Purpose:** Track login behavior, engagement trends, MAU/WAU/DAU, cohort analysis

**Joins:**
- `dim_supplier_summary` (supplier attributes: segment, managed, connected, NR tier)
- `fact_booking` (aggregated to supplier level for GMV-weighted metrics)
- `dim_tour` via `fact_supplier_history.supplier_id` (count of active activities)

**Key Dimensions:**
- Date (partition key)
- Supplier ID, segment, managed status, connected status
- NR tier (€0-€346, €346-€1,627, €1,627-€8,958, €8,958+)
- Geography (country, region)
- Login recency (L7, L30, L90)

**Key Measures:**
- MAU, WAU, DAU (count distinct suppliers with login flag)
- GMV-weighted login rate (SUM(gmv WHERE logged_in) / SUM(gmv))
- Login frequency distribution (1-2, 3-5, 6-10, 10+ logins/month)
- Avg logins per supplier
- % suppliers by engagement tier

**Use Cases:**
- Executive Dashboard: Overall portal adoption, MAU trends, engagement by segment
- PM Dashboard: L7/L30 retention, power user identification
- Analytics Deep-Dive: Cohort analysis, engagement funnels

---

### **Explore 2: Feature Usage & Outcomes**
**Base Table:** `dim_recommended_actions`

**Purpose:** Track Recommended Actions and Performance Hub feature usage, measure feature adoption and impact

**Joins:**
- `dim_supplier_summary` (supplier attributes)
- `fact_supplier_history` (login behavior at time of action surfacing)
- `fact_booking` (supplier outcomes: GMV growth, booking volume)
- `dim_tour` (activity-level actions)
- `production.events.events` (Performance Hub events by supplier_id extracted from json_event)

**Key Dimensions:**
- Action type, status (resolved, expired, dismissed, active)
- Dismissal reason
- Surfaced date, resolved date (for time-to-resolution)
- Supplier segment, managed, connected
- Performance Hub event types (SupplierPerformancePageRequest, etc.)

**Key Measures:**
- Reach rate (% suppliers with ≥1 action surfaced)
- Resolution rate (overall, 28-day)
- Dismissal rate (dismissed / actioned)
- Expiry rate (expired / closed)
- Supplier conversion rate (% reached suppliers who resolved ≥1)
- Avg days to resolve
- Engagement tier distribution (Single-Use, Occasional, Regular, Power User)
- Performance Hub MAU/WAU
- PH page views, event counts by type
- % PH visitors who resolve actions

**Use Cases:**
- PM Dashboard: Feature adoption, resolution trends, drop-off analysis
- Executive Dashboard: Feature reach, supplier conversion
- Analytics Deep-Dive: Action type performance, dismissal reasons, cohort progression

---

### **Explore 3: Product Creation & Activation**
**Base Table:** `tour_creation_funnel`

**Purpose:** Track tour creation wizard performance, AI adoption, activation rates

**Joins:**
- `dim_supplier_summary` (supplier attributes)
- `catalog__tour_generated_content` (AI generation success/failure)
- `catalog__tour_business_category` (category-level submission rates)
- `dim_activity_lookback_activation` (1B30D activation metric)
- `fact_booking` (booking volume post-creation)

**Key Dimensions:**
- Step name, step number
- Creation path (AI vs Manual)
- Category (level1, level2, level3)
- AI generation status (completed, failed)
- Supplier segment, managed, connected
- Cohort (by month of creation start)

**Key Measures:**
- Tours started, tours submitted
- Submission rate (submitted / started)
- AI adoption rate (tours with AI step / tours started)
- AI generation success rate (completed / total)
- Funnel drop-off by step
- Activation rate (1B30D): % submitted tours with booking in 30 days
- Median/P75 time to submit
- Category-specific submission rates

**Use Cases:**
- PM Dashboard: Wizard funnel optimization, AI feature performance
- Executive Dashboard: Creation volume trends, activation rates
- Analytics Deep-Dive: Step-by-step drop-offs, category/segment performance

---

## Dashboard Tier Mapping

### **Executive Dashboard** (High-level health metrics)
**Data Sources:** Explores 1, 2, 3

**Key Tiles:**
- Total active suppliers (MAU from Explore 1)
- Overall portal adoption rate (% relevant suppliers logged in L30)
- Engagement trends (MAU/WAU over time)
- Feature adoption heatmap (% suppliers using RA, PH, Product Creation)
- GMV-weighted login rate (business coverage)
- Geographic breakdown (suppliers by country/region)

---

### **Product Manager Dashboard** (Actionable insights)
**Data Sources:** Explores 1, 2, 3

**Key Tiles:**
- Onboarding completion rates (creation submission rate from Explore 3)
- Feature-level adoption rates (RA reach, PH reach from Explore 2)
- Stickiness metrics (WAU/MAU ratio, login frequency from Explore 1)
- Power user identification (engagement tiers from Explore 2)
- Workflow completion rates (RA resolution rate, wizard submission rate)
- Session frequency & depth (logins per month, PH events per visit)
- Time to first value (1B30D activation from Explore 3)

---

### **Analytics Deep-Dive** (Detailed investigation)
**Data Sources:** Explores 1, 2, 3

**Key Capabilities:**
- Cohort analysis (compare engagement patterns by segment, NR tier, managed status)
- Funnel analysis (RA lifecycle, wizard drop-offs)
- User journey mapping (login → feature usage → outcome)
- Feature interaction patterns (RA dismissal reasons, PH event sequences)
- Behavioral clustering (engagement tiers, login frequency distribution)

---

## Phase 2: Connecting Engagement to Supplier Outcomes

Once Phase 1 explores are built, Phase 2 adds outcome metrics by extending Explore 2:

**Additional Joins to Explore 2:**
- `fact_booking` aggregated to supplier-month level (GMV growth, booking volume growth)
- Activity-level metrics from `dim_tour` (listing completeness, update frequency)
- Review ratings, complaint rates (if available in existing tables)
- Operational metrics (booking acceptance rate, cancellation rate, response time)

**New Measures:**
- GMV per supplier (this month vs last month, % growth)
- Booking acceptance rate
- Avg response time
- Cancellation rate
- Review rating avg
- Listing completeness score
- Content update frequency

**Analytical Use Cases:**
- Correlation analysis: Does RA resolution rate correlate with GMV growth?
- Propensity score matching: Compare suppliers who use PH vs similar suppliers who don't
- Regression: Predict GMV growth based on engagement metrics + controls (size, geography, category)
- Time-lagged: Does L30 login frequency in month N predict GMV growth in month N+1?

---

## Implementation Steps

### Step 1: Build Base Views (Week 1-2)
1. Create `fact_supplier_history.view.lkml` (daily grain, supplier_id + date)
2. Create `dim_supplier_summary.view.lkml` (supplier attributes)
3. Create `dim_recommended_actions.view.lkml` (action-level grain)
4. Create `tour_creation_funnel.view.lkml` (step-level grain)
5. Create `supplier_portal_events.view.lkml` (derived from production.events.events, filtered to supplier portal event types)

### Step 2: Build Explores (Week 2-3)
1. Create `supplier_engagement.explore.lkml` (Explore 1)
2. Create `feature_usage_outcomes.explore.lkml` (Explore 2)
3. Create `product_creation_activation.explore.lkml` (Explore 3)

### Step 3: Build Dashboards (Week 3-4)
1. Executive Dashboard (via Looker UI, save to folder)
2. Product Manager Dashboard (via Looker UI, save to folder)
3. Analytics Deep-Dive (via Looker UI, save to folder)

### Step 4: Phase 2 - Outcomes (Quarter 2-3)
1. Extend Explore 2 with outcome joins
2. Create derived tables for cohort analysis, propensity matching
3. Build statistical analysis views (correlation, regression coefficients)

---

## Key Decisions Needed

1. **Do you want LookML dashboards or User-Defined Dashboards?**
   - User-Defined (UI-based) is simpler and faster
   - LookML (code-based) is version-controlled but harder to iterate

2. **Which Looker model should these explores live in?**
   - Options: `getyourguide`, `supply_operations`, or create new `supplier_portal` model

3. **Should we start with just Explore 1, or build all 3 in parallel?**
   - Recommend: Start with Explore 1, validate, then build 2 & 3

4. **Access control: Who should see these dashboards?**
   - Supply team only? Product team? Data team? Execs?

---

## Next Steps

**Option A: I build the explores in gyg-looker for you**
- I'll create the view files and explore files
- You review and test in Looker dev mode
- We iterate until it works
- Then you build dashboards via UI

**Option B: You give me a specific explore to start with**
- Tell me which of the 3 explores to prioritize
- I'll build just that one first
- Faster iteration, lower risk

**Which option do you prefer?**
