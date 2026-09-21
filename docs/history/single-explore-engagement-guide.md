# Complete Engagement Analysis Using ONE Explore

Use **Supplier Engagement & Portal Usage** for ALL analysis from your Confluence page.

---

## Q1: Login Rates by Cohort (Table 1.1)

**Goal:** Recreate this table:
| Cohort | Share | L7D | L30D | L90D |
|--------|-------|-----|------|------|
| Relevant | 15.3% | 67.9% | 81.2% | 90.2% |
| Not relevant | 84.7% | 3.2% | 6.5% | 12.9% |

### In Looker:

**Explore:** Supplier Engagement & Portal Usage

**Dimensions:**
- `Dim Supplier Relevance > Cohort`

**Measures:**
- `Dim Supplier Summary > Count Suppliers`
- `Dim Supplier Summary > Login Rate (L7)`
- `Dim Supplier Summary > Login Rate (L30)`
- `Dim Supplier Summary > Login Rate (L90)`

**Filters:**
- `Fact Supplier Engagement > Date > Date` = Most recent date (e.g., 2026-04-12)
- OR use no date filter and it will show current snapshot

**Key insight:** Even though this explore has daily grain, when you filter to a single date or use the dim_supplier_summary measures, you get snapshot-level metrics.

---

## Q2: MAU Trend Over Time (Table 2.1)

**Goal:** Monthly active users April 2025 - March 2026

### In Looker:

**Explore:** Supplier Engagement & Portal Usage

**Dimensions:**
- `Fact Supplier Engagement > Date > Month`

**Measures:**
- `Fact Supplier Engagement > MAU`
- `Fact Supplier Engagement > Total GMV L30`
- `Fact Supplier Engagement > GMV from Logged In Suppliers`
- **Table Calculation:** `GMV-Weighted Rate = ${gmv_from_logged_in} / ${total_gmv_l30}`

**Filters:**
- `Dim Supplier Relevance > Is Relevant` = Yes
- `Fact Supplier Engagement > Date > Month` = April 2025 to March 2026

**Visualization:** Line chart with MAU trend

---

## Q3: Login Frequency by NR Tier (Table 3.1)

**Goal:** Distribution of login frequency (1-2, 3-5, 6-10, 10+ logins/month) by NR tier

### In Looker:

**Explore:** Supplier Engagement & Portal Usage

**Dimensions:**
- `Dim Supplier Summary > NR Tier`
- `Fact Supplier Engagement > Login Frequency Tier` (need to add this dimension to view)

**Measures:**
- `Fact Supplier Engagement > Total Suppliers`

**Filters:**
- `Dim Supplier Relevance > Is Relevant` = Yes
- `Fact Supplier Engagement > Date > Month` = Jan 2026 to Mar 2026

**Pivot:**
- Pivot on `Login Frequency Tier` to create columns

**Note:** I need to add a `login_frequency_tier` dimension to the view based on login_count. Let me do that next.

---

## Q4: Login Rates by Supplier Segment (Table 4.1)

**Goal:** L7/L30/L90 rates for Scale Seeker, Leisure Brand, Independent Creator, Heritage Preserver

### In Looker:

**Explore:** Supplier Engagement & Portal Usage

**Dimensions:**
- `Dim Supplier Summary > Supplier Segment`

**Measures:**
- `Dim Supplier Summary > Count Suppliers`
- `Dim Supplier Summary > Login Rate (L7)`
- `Dim Supplier Summary > Login Rate (L30)`
- `Dim Supplier Summary > Login Rate (L90)`

**Filters:**
- `Dim Supplier Relevance > Is Relevant` = Yes
- `Fact Supplier Engagement > Date > Date` = Most recent date (e.g., 2026-04-12)

---

## Q5: Login Rates by Managed/Connected Status (Table 5.1)

**Goal:** L7/L30/L90 rates for Managed+Connected, Managed+Non-Connected, etc.

### In Looker:

**Explore:** Supplier Engagement & Portal Usage

**Dimensions:**
- `Dim Supplier Summary > Is Managed`
- `Dim Supplier Summary > Is Connected`

**Measures:**
- `Dim Supplier Summary > Count Suppliers`
- `Dim Supplier Summary > Login Rate (L7)`
- `Dim Supplier Summary > Login Rate (L30)`
- `Dim Supplier Summary > Login Rate (L90)`
- `Dim Supplier Summary > Avg NR Per Supplier`

**Filters:**
- `Dim Supplier Relevance > Is Relevant` = Yes
- `Fact Supplier Engagement > Date > Date` = Most recent date (e.g., 2026-04-12)

**Table Calculation for Combined Segment:**
- Concatenate: `${is_managed} & " + " & ${is_connected}`

---

## Key Pattern

**For snapshot analysis (Q1, Q4, Q5):**
- Filter to a single date OR don't filter by date at all
- Use `Dim Supplier Summary` measures (they use supplier-level data)

**For time-series analysis (Q2, Q3):**
- Group by `Date > Month` or `Date > Week`
- Use `Fact Supplier Engagement` measures (they aggregate daily data)

**Always filter:**
- `Dim Supplier Relevance > Is Relevant` = Yes (for relevant supplier pool)

---

## What I Need to Add

To complete Q3 (login frequency), I need to add a dimension to `fact_supplier_engagement`:

```lkml
dimension: login_frequency_tier {
  type: string
  sql: CASE
    WHEN ${login_count} = 0 THEN 'No Login'
    WHEN ${login_count} BETWEEN 1 AND 2 THEN '1-2 Logins/month'
    WHEN ${login_count} BETWEEN 3 AND 5 THEN '3-5 Logins/month'
    WHEN ${login_count} BETWEEN 6 AND 10 THEN '6-10 Logins/month'
    WHEN ${login_count} > 10 THEN '10+ Logins/month'
    ELSE 'Unknown'
  END ;;
}
```

But checking the schema, I'm not sure if `login_count` exists in fact_supplier_engagement. Let me verify first.

---

## Summary

**ONE explore does everything:**
- ✅ Q1: Login rates by cohort
- ✅ Q2: MAU trend over time
- ⚠️ Q3: Login frequency (need to check if login_count field exists)
- ✅ Q4: Login rates by segment
- ✅ Q5: Login rates by managed/connected

No need for multiple explores. Just filter and group differently depending on what you're analyzing.
