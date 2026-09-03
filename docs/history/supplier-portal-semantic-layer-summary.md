# Supplier Portal Semantic Layer - Stakeholder Summary

**PR:** BOI-2951 (#2788) - Merged  
**Purpose:** First core data mart for Supplier Portal engagement analysis (Q2 2026 Semantic Layer Initiative)

---

## What Is This?

A new data foundation that makes it easy to analyze **how suppliers use the Supplier Portal**. Instead of writing complex SQL queries, anyone can now ask questions about supplier engagement using simple metric names and get accurate answers automatically.

Think of it as a "question-answering engine" for Supplier Portal analytics.

---

## What Questions Can We Answer?

### 📊 **Engagement & Activity**
- How many suppliers are active daily/weekly/monthly?
- How engaged are our suppliers? (stickiness = DAU/MAU ratio)
- Which features are suppliers using most?
- How many login accounts vs. supplier businesses are active?
- How many sessions are happening on the portal?

### 🆕 **Feature Adoption**
- How many suppliers used a feature for the first time?
- Which features are being adopted fastest?
- How quickly do suppliers find specific features in a session?

### 🔍 **Segmentation**
All metrics can be broken down by:
- **Supplier attributes:** segment, country, size tier, tenure, managed vs. self-serve, connected status, contract type
- **Device/Platform:** desktop vs. mobile, iOS vs. Android, browser type
- **Portal surface:** which part of the portal (header, modal, settings page)
- **Language:** which language the supplier is using
- **Account manager:** for AM-level adoption analysis

---

## Available Metrics (12 Total)

### Core Engagement Metrics

| Metric | What It Measures | Use Case |
|--------|------------------|----------|
| **supplier_portal_events** | Total raw events on the portal | Overall portal activity volume |
| **active_suppliers** | Distinct supplier businesses active | "How many suppliers used the portal?" |
| **active_logins** | Distinct user accounts active | "How many people logged in?" (lower than suppliers when one person manages multiple businesses) |
| **active_sessions** | Supplier-session pairs | Per-supplier engagement tracking |
| **active_browser_sessions** | Browser sessions only | Browser-level traffic (accounts for account-switching) |

### Time-Based Engagement

| Metric | What It Measures | Use Case |
|--------|------------------|----------|
| **dau** | Daily Active Suppliers | Day-to-day engagement |
| **wau** | Weekly Active Suppliers (7-day rolling) | Weekly engagement trends |
| **mau** | Monthly Active Suppliers (30-day rolling) | Monthly engagement trends |
| **stickiness** | DAU / MAU ratio | Engagement quality (higher = more frequent usage) |

### Feature Adoption

| Metric | What It Measures | Use Case |
|--------|------------------|----------|
| **n_suppliers_first_use** | Suppliers using a feature for the first time | Feature adoption tracking |
| **median_time_to_event_in_session_seconds** | p50 seconds from session start to feature use | How quickly suppliers find features |
| **p10_time_to_event_in_session_seconds** | p10 time-to-event | Fastest 10% of users |
| **p90_time_to_event_in_session_seconds** | p90 time-to-event | Slowest 10% of users |

---

## Available Dimensions (Filters & Breakdowns)

### 📅 Time
- Event date (daily granularity)

### 🏢 Supplier Attributes
- **Supplier segment** (e.g., strategic, core, tail)
- **Country** (supplier's country)
- **Supply geo area** (regional grouping)
- **Is managed** (has dedicated account manager)
- **Is connected** (connected to GYG systems)
- **Size tier** (based on last 365-day revenue and bookings)
- **Tenure bucket** (how long they've been a supplier)
- **Is relevant** (active/relevant supplier flag)
- **Contract type** (T&Cs, Individual Agency, Tours & Tickets, etc.)
- **GYG status** (operational status)
- **Account manager** (who manages the supplier)
- **Parent supplier ID** (for multi-account hierarchies)

### 💻 Device & Platform
- **Platform** (web, iOS, Android)
- **Operating system** (iOS, Android, Windows, Mac, etc.)
- **Device** (mobile, tablet, desktop)

### 🌐 Language
- **Language ID**
- **Language name**
- **Language ISO code**

### 🎯 Portal Features
- **Event identifier** (which feature/button/action)
- **Container name** (which part of the portal: header, modal, settings, etc.)
- **Is feature first use** (flag for first-time usage)

---

## Example Questions & How to Answer Them

### "How many suppliers are actively using the portal each week?"
**Metric:** `wau` (Weekly Active Suppliers)  
**Breakdown:** By `event_date`  
**Result:** Time-series chart showing weekly active suppliers

### "Which supplier segments are most engaged with the portal?"
**Metric:** `active_suppliers` or `stickiness`  
**Breakdown:** By `supplier_segment`  
**Result:** Comparison of engagement by segment

### "How many suppliers used the 'export bookings' feature for the first time this month?"
**Metric:** `n_suppliers_first_use`  
**Filter:** `event_identifier = 'export_bookings'` AND `event_date` in last 30 days  
**Result:** Count of suppliers adopting the feature

### "How quickly do mobile users find the 'edit availability' button?"
**Metric:** `median_time_to_event_in_session_seconds`  
**Filter:** `event_identifier = 'edit_availability'` AND `device = 'mobile'`  
**Result:** Median seconds from session start

### "Which account managers' suppliers are most engaged?"
**Metric:** `stickiness` or `dau`  
**Breakdown:** By `account_manager`  
**Result:** Engagement ranking by AM

---

## Data Scope & Coverage

### ✅ What's Included
- Supplier user events only (not admin or GYG internal staff)
- Real supplier accounts (excludes internal GYG-owned suppliers)
- Real engagement (excludes office IP addresses)
- Meaningful events (filters out ~30 auto-fired noise events like performance tracking)
- Data from **May 2026 onwards** (when tracking began)

### 📊 Data Volume
- ~4.2 million rows per week (compressed from 15.3M raw events)
- 3.6× compression ratio (one row = ~3.6 raw events on average)
- Updated daily via the `sde_supply_semantic_transformations` Airflow DAG

---

## Known Limitations

### 🚧 Feature Taxonomy
- **Event identifier is still a raw technical key** (e.g., `UIClick:export_button_header`) — not yet mapped to business-friendly feature names
- A governed event-to-feature mapping table is planned as a follow-up
- Use `container_name` alongside `event_identifier` to distinguish the same UI element on different portal surfaces

### 📸 Point-in-Time Snapshots
- **Supplier attributes are current-value** (segment, country, is_managed, is_connected, supplier_type)
- Not historical "as-of" values — if a supplier's segment changed in the past, historical events show their current segment
- Exception: `size_tier` and `tenure_bucket` are date-aligned (correctly show the value on the event date)

### 🌙 Session Splitting
- Sessions reset at midnight (browser-scoped `attribution_session_id`)
- A real user session crossing midnight appears as two separate sessions
- One browser session can have multiple `supplier_id` values due to the account-switcher feature (expected behavior)

### 📈 Page-View Inflation
- The `n_events` metric includes auto-fired page-view events alongside click events
- For engagement volume, prefer **distinct-supplier** or **distinct-session** metrics instead

### 🎯 Out of Scope
This data mart tracks **engagement only** — it does **NOT** include:
- Commercial outcomes (bookings, revenue, conversion)
- Causal impact of portal changes on business results
- Links between portal actions and downstream sales

**For those questions:** A custom model is needed that joins this mart to booking/revenue tables.

---

## How to Access This Data

### For Analysts
- **MetricFlow CLI:** Query metrics directly via `mf query --metrics active_suppliers --group-by event_date,platform`
- **Looker (coming soon):** Metrics will be exposed via dbt2looker integration
- **AI Agents:** Semantic models are AI-ready with synonyms, sample queries, and metadata

### For Stakeholders
- Request reports from the **BOI (Business Operations Intelligence)** team
- Metrics will be available in self-service dashboards once Looker integration is complete

---

## Technical Details (For Data Teams)

**Data Models Created:**
- `int_supplier_portal_feature_engagement` — cleaned event-level intermediate
- `int_supplier_attributes_daily` — date-aligned supplier attributes (size tier, tenure)
- `agg_supplier_portal_events_session_daily` — core mart (session × event × day grain)
- `sem_supplier_portal_events` — semantic model for MetricFlow
- `sem_dim_supplier` — supplier dimension semantic model (auto-joins via MetricFlow)

**Airflow DAG:** `sde_supply_semantic_transformations`  
**Catalog:** `production.core_supply`  
**Owner:** BOI team

---

## Next Steps

1. **Feature taxonomy mapping** — create business-friendly feature names
2. **Looker integration** — expose metrics in self-service dashboards via dbt2looker
3. **Historical alignment** — investigate feasibility of date-aligned supplier attributes
4. **Commercial outcomes** — build downstream models linking portal engagement to bookings/revenue

---

## Questions?

Contact the **BOI (Business Operations Intelligence)** team or the semantic layer initiative stakeholders.

**Jira Ticket:** [BOI-2951](https://getyourguide.atlassian.net/browse/BOI-2951)  
**PR:** [#2788](https://github.com/getyourguide/dap-dbt-transformations/pull/2788)
