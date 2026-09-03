# Supplier Portal Engagement Dashboard Design

## Dashboard Layout

```
┌─────────────────────────────────────────────────────────────────┐
│  Supplier Portal Engagement Dashboard                           │
│  Filters: [Date Range] [Is Relevant: Yes ▼]                    │
└─────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│  SECTION 1: KEY METRICS (Single Value Tiles)                     │
├─────────────┬─────────────┬─────────────┬──────────────┬────────┤
│ Total       │ L7 Login    │ L30 Login   │ L90 Login    │  MAU   │
│ Suppliers   │ Rate        │ Rate        │ Rate         │ (MTD)  │
│  48,807     │  67.9%      │  81.2%      │  90.2%       │ 38,240 │
└─────────────┴─────────────┴─────────────┴──────────────┴────────┘

┌──────────────────────────────────────────────────────────────────┐
│  SECTION 2: ENGAGEMENT BY COHORT                                 │
├───────────────────────────────┬──────────────────────────────────┤
│  Table: Login Rates by Cohort │  Bar Chart: Login Rate Comparison│
│                               │                                  │
│  Cohort      | L7  | L30 | L90│  [Chart showing relevant vs not] │
│  ─────────────────────────────│                                  │
│  Relevant    | 68% | 81% | 90%│                                  │
│  Not relevant|  3% |  7% | 13%│                                  │
└───────────────────────────────┴──────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│  SECTION 3: ENGAGEMENT TRENDS                                    │
├──────────────────────────────────────────────────────────────────┤
│  Line Chart: MAU Growth Over Time (Apr 2025 - Mar 2026)         │
│  [Line trending from 29k to 38k]                                │
│                                                                  │
│  With secondary axis: GMV-Weighted Login Rate (flat at 95%)     │
└──────────────────────────────────────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│  SECTION 4: SEGMENTATION ANALYSIS                                │
├───────────────────────────────┬──────────────────────────────────┤
│  Table: Login Rates by Segment│  Table: By Managed/Connected     │
│                               │                                  │
│  Segment          | L7  | L30 │  Status              | L7  | L30 │
│  ──────────────────────────── │  ──────────────────────────────  │
│  Scale Seeker     | 75% | 86% │  Managed+Connected   | 80% | 90% │
│  Leisure Brand    | 60% | 77% │  Managed+Non-Conn    | 80% | 89% │
│  Independent Cr.  | 59% | 74% │  Non-Managed+Conn    | 65% | 79% │
│  Heritage Pres.   | 51% | 69% │  Non-Managed+Non-Conn| 66% | 80% │
└───────────────────────────────┴──────────────────────────────────┘

┌──────────────────────────────────────────────────────────────────┐
│  SECTION 5: LOGIN FREQUENCY (if login_count exists)             │
├──────────────────────────────────────────────────────────────────┤
│  Heatmap: Login Frequency by NR Tier                            │
│                                                                  │
│  NR Tier    | No Login | 1-2 | 3-5 | 6-10 | 10+                │
│  ─────────────────────────────────────────────────────────────  │
│  €8,958+    |   [2%]  | [12%]| [10%]| [13%]| [64%] ← Darkest   │
│  €1,627-€8k |   [6%]  | [23%]| [16%]| [16%]| [39%]             │
│  €346-€1,627|  [13%]  | [33%]| [17%]| [16%]| [21%]             │
│  €1-€346    |  [22%]  | [37%]| [17%]| [14%]| [10%]             │
│  No NR      |  [23%]  | [29%]| [24%]| [18%]|  [7%] ← Lightest  │
└──────────────────────────────────────────────────────────────────┘
```

---

## Tile-by-Tile Build Guide

### SECTION 1: Key Metrics

#### Tile 1.1: Total Suppliers
- **Visualization:** Single Value
- **Explore:** Supplier Engagement & Portal Usage
- **Measure:** `Dim Supplier Summary > Count Suppliers`
- **Filter:** `Dim Supplier Relevance > Is Relevant` = Yes
- **No date filter** (snapshot)

#### Tile 1.2: L7 Login Rate
- **Visualization:** Single Value
- **Explore:** Supplier Engagement & Portal Usage
- **Measure:** `Dim Supplier Summary > Login Rate (L7)`
- **Filter:** `Dim Supplier Relevance > Is Relevant` = Yes
- **Format:** Add comparison to previous period

#### Tile 1.3: L30 Login Rate
- Same as Tile 1.2, but use `Login Rate (L30)`

#### Tile 1.4: L90 Login Rate
- Same as Tile 1.2, but use `Login Rate (L90)`

#### Tile 1.5: MAU (Month-to-Date)
- **Visualization:** Single Value
- **Explore:** Supplier Engagement & Portal Usage
- **Dimension:** `Fact Supplier Engagement > Date > Month`
- **Measure:** `Fact Supplier Engagement > MAU`
- **Filter:** 
  - `Dim Supplier Relevance > Is Relevant` = Yes
  - `Date > Month` = Current month

---

### SECTION 2: Engagement by Cohort

#### Tile 2.1: Login Rates by Cohort (Table)
- **Visualization:** Table
- **Explore:** Supplier Engagement & Portal Usage
- **Dimensions:** `Dim Supplier Relevance > Cohort`
- **Measures:**
  - `Dim Supplier Summary > Count Suppliers`
  - `Dim Supplier Summary > Login Rate (L7)`
  - `Dim Supplier Summary > Login Rate (L30)`
  - `Dim Supplier Summary > Login Rate (L90)`
- **Table Calculation:** `Share = ${count_suppliers} / sum(${count_suppliers})`
- **No date filter**

#### Tile 2.2: Login Rate Comparison (Bar Chart)
- **Visualization:** Column Chart
- **Explore:** Supplier Engagement & Portal Usage
- **Dimensions:** `Dim Supplier Relevance > Cohort`
- **Measures:** `Dim Supplier Summary > Login Rate (L7/L30/L90)`
- **Series:** Group bars by L7/L30/L90
- **Colors:** Green for Relevant, Gray for Not Relevant

---

### SECTION 3: MAU Growth Trend

#### Tile 3.1: MAU Over Time
- **Visualization:** Line Chart
- **Explore:** Supplier Engagement & Portal Usage
- **Dimensions:** `Fact Supplier Engagement > Date > Month`
- **Measures:**
  - `Fact Supplier Engagement > MAU` (primary axis)
  - Optional: `Fact Supplier Engagement > Total GMV L30` (secondary axis)
- **Filter:**
  - `Dim Supplier Relevance > Is Relevant` = Yes
  - `Date > Month` = Last 12 months
- **Trend Line:** Add linear trend

---

### SECTION 4: Segmentation

#### Tile 4.1: Login Rates by Supplier Segment (Table)
- **Visualization:** Table
- **Explore:** Supplier Engagement & Portal Usage
- **Dimensions:** `Dim Supplier Summary > Supplier Segment`
- **Measures:**
  - `Dim Supplier Summary > Count Suppliers`
  - `Dim Supplier Summary > Login Rate (L7)`
  - `Dim Supplier Summary > Login Rate (L30)`
  - `Dim Supplier Summary > Login Rate (L90)`
- **Filter:** `Dim Supplier Relevance > Is Relevant` = Yes
- **Sort:** By L7 descending

#### Tile 4.2: Login Rates by Managed/Connected (Table)
- **Visualization:** Table
- **Explore:** Supplier Engagement & Portal Usage
- **Dimensions:**
  - `Dim Supplier Summary > Is Managed`
  - `Dim Supplier Summary > Is Connected`
- **Measures:**
  - `Dim Supplier Summary > Count Suppliers`
  - `Dim Supplier Summary > Login Rate (L7)`
  - `Dim Supplier Summary > Login Rate (L30)`
  - `Dim Supplier Summary > Login Rate (L90)`
  - `Dim Supplier Summary > Avg NR Per Supplier`
- **Filter:** `Dim Supplier Relevance > Is Relevant` = Yes
- **Pivot Table:** Create cross-tab with Managed (rows) x Connected (columns)

---

### SECTION 5: Login Frequency (Conditional)

**Note:** Only build this if `login_count` field exists in fact_supplier_history

#### Tile 5.1: Login Frequency Distribution by NR Tier (Heatmap)
- **Visualization:** Heatmap
- **Explore:** Supplier Engagement & Portal Usage
- **Dimensions:**
  - `Dim Supplier Summary > NR Tier` (rows)
  - `Login Frequency Tier` (columns) — needs to be created
- **Measure:** `Fact Supplier Engagement > Total Suppliers`
- **Filter:**
  - `Dim Supplier Relevance > Is Relevant` = Yes
  - `Date > Month` = Last 3 months
- **Color:** Gradient from light (low) to dark (high)

---

## Step-by-Step: Building the Dashboard in Looker UI

### 1. Create New Dashboard

1. Go to **Dashboards** → **+ New Dashboard**
2. Name: "Supplier Portal Engagement"
3. Add description: "Portal login rates, MAU trends, and cohort analysis. Filter to relevant suppliers by default."

### 2. Add Dashboard-Level Filters

1. Click **Edit Dashboard** → **Filters**
2. Add filter:
   - **Field:** `Dim Supplier Relevance > Is Relevant`
   - **Default:** Yes
   - **Allow multiple values:** No
3. Add filter:
   - **Field:** `Fact Supplier Engagement > Date > Month`
   - **Default:** Last 12 months
   - **Allow multiple values:** Yes

### 3. Build Tiles

**For each tile:**
1. Click **+ Tile** → **From Explore**
2. Select **Supplier Engagement & Portal Usage**
3. Add dimensions and measures as specified above
4. Configure visualization
5. Click **Save**
6. Drag to position in dashboard layout

### 4. Format Dashboard

1. **Layout:** Use grid with 4 columns
2. **Section Headers:** Add text tiles for each section
3. **Colors:**
   - Relevant cohort: Green (#34A853)
   - Not relevant: Gray (#9AA0A6)
   - MAU trend: Blue (#4285F4)
4. **Conditional Formatting:**
   - Login rates >80%: Green
   - Login rates 60-80%: Yellow
   - Login rates <60%: Red

### 5. Add Dashboard Description

Add this to the top:
```
This dashboard tracks supplier portal engagement across key dimensions:
- Login rates for relevant suppliers (active, >1 booking L365 or recent launch)
- MAU growth trends
- Engagement by segment, managed status, and connectivity

Default filter: Relevant suppliers only (48,807 as of Apr 2026)
```

---

## Advanced: Add Cross-Filtering

Enable users to click on a segment and filter the entire dashboard:

1. **Edit Dashboard** → **Dashboard Settings**
2. Enable **Cross-Filtering**
3. Now clicking "Scale Seeker" in Tile 4.1 will filter all tiles to that segment

---

## Dashboard Variants

### Executive Dashboard (Simplified)
- Only Sections 1, 2, 3
- Larger fonts, fewer details
- Focus on headline metrics

### PM Dashboard (Full Detail)
- All 5 sections
- Add drill-down links to supplier lists
- Include comparison to previous period

### Analyst Dashboard (Raw Data)
- Add "View SQL" and "Explore from Here" links
- Include data quality indicators
- Add last refresh timestamp

---

## Next Steps

1. **Build Section 1** (Key Metrics) first - these are quick wins
2. **Build Section 3** (MAU Trend) - validates the data pipeline
3. **Build Sections 2 & 4** (Cohort & Segmentation) - core analysis
4. **Build Section 5** (Login Frequency) - if data available

Should I walk you through building the first tile step-by-step in the Looker UI?
