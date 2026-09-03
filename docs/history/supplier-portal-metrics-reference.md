# Supplier Portal Metrics - Quick Reference

## Metrics Catalog

| Metric Name | Label | What It Measures | When to Use |
|-------------|-------|------------------|-------------|
| **supplier_portal_events** | Supplier Portal Events | Total raw events on the portal | Overall activity volume |
| **active_suppliers** | Active Suppliers | Distinct supplier businesses active | "How many suppliers used the portal?" |
| **active_logins** | Active Logins | Distinct user accounts active | "How many people logged in?" (lower than suppliers when one person manages multiple) |
| **active_sessions** | Active Sessions | Supplier-session pairs | Per-supplier engagement tracking |
| **active_browser_sessions** | Active Browser Sessions | Browser sessions only | Browser-level traffic (accounts for account-switching) |
| **dau** | Daily Active Suppliers | Daily unique suppliers | Day-to-day engagement |
| **wau** | Weekly Active Suppliers | 7-day rolling window | Weekly trends |
| **mau** | Monthly Active Suppliers | 30-day rolling window | Monthly trends |
| **stickiness** | Portal Stickiness (DAU/MAU) | Engagement quality ratio | How often suppliers return (higher = better) |
| **n_suppliers_first_use** | Suppliers First-Using Feature | Count of first-time feature uses | Feature adoption tracking |
| **median_time_to_event_in_session_seconds** | Median Time-to-Event (s) | p50 seconds to find feature | Typical user experience |
| **p10_time_to_event_in_session_seconds** | p10 Time-to-Event (s) | Fast users (10th percentile) | Best-case user experience |
| **p90_time_to_event_in_session_seconds** | p90 Time-to-Event (s) | Slow users (90th percentile) | Worst-case user experience |

---

## Dimensions (Filters & Breakdowns)

### Time
- `event_date` - Daily granularity

### Supplier Attributes
- `supplier_segment` - Strategic, core, tail, etc.
- `supplier_country_name` - Supplier's country
- `supply_geo_area` - Regional grouping
- `is_managed` - Has account manager (true/false)
- `is_connected` - Connected to GYG systems (true/false)
- `size_tier` - Based on L365 revenue and bookings
- `tenure_bucket` - How long they've been a supplier
- `is_relevant` - Active/relevant flag
- `contract_type` - T&Cs, Individual Agency, Tours & Tickets, etc.
- `gyg_status` - Operational status
- `account_manager` - AM responsible for supplier
- `parent_supplier_id` - For multi-account hierarchies

### Device & Platform
- `platform` - web, iOS, Android
- `os` - Operating system
- `device` - mobile, tablet, desktop

### Portal Features
- `event_identifier` - Which feature/button/action (technical key)
- `container_name` - Portal location (header, modal, settings)
- `is_feature_first_use` - First-time usage flag

### Language
- `language_id` - Language ID
- `language_name` - Language name
- `language_iso_code` - ISO code

---

## Session Measures Explained

**Why two session metrics?**

The Supplier Portal has an **account-switcher** feature that lets one user manage multiple supplier accounts in the same browser session.

- **active_sessions** (`supplier_id × session_id`) - Counts **supplier-sessions**  
  Use when analyzing per-supplier engagement: "How many sessions did Supplier X have?"

- **active_browser_sessions** (`session_id` only) - Counts **browser sessions**  
  Use when analyzing browser-level traffic: "How many browser sessions hit the portal?"

**Example:**  
A user logs in, manages Supplier A, switches accounts to Supplier B, all in one browser session.
- `active_browser_sessions` = 1 (one browser session)
- `active_sessions` = 2 (Supplier A session + Supplier B session)

---

## Usage Examples

### Example 1: Weekly Active Suppliers by Segment
```
Metric: wau
Breakdown: event_date, supplier_segment
Result: Time series showing WAU for strategic, core, tail segments
```

### Example 2: Feature Adoption - Export Bookings
```
Metric: n_suppliers_first_use
Filter: event_identifier = 'export_bookings'
Breakdown: event_date
Result: Daily count of suppliers using export for first time
```

### Example 3: Mobile Engagement Quality
```
Metric: stickiness
Filter: device = 'mobile'
Breakdown: event_date
Result: Mobile DAU/MAU ratio over time
```

### Example 4: Time to Find Edit Availability Button
```
Metric: median_time_to_event_in_session_seconds
Filter: event_identifier = 'edit_availability'
Breakdown: platform (web vs iOS vs Android)
Result: Median seconds by platform
```

### Example 5: Account Manager Performance
```
Metric: active_suppliers, stickiness
Breakdown: account_manager
Result: AM-level engagement comparison
```

---

## Quick Tips

✅ **For volume questions** → Use `active_suppliers` or `active_sessions`  
✅ **For engagement quality** → Use `stickiness` (higher is better)  
✅ **For adoption tracking** → Use `n_suppliers_first_use`  
✅ **For UX analysis** → Use time-to-event percentiles  
✅ **Avoid `n_events`** → Inflated by auto-fired page views; use distinct measures instead

❌ **Don't use for revenue/booking questions** → This mart has no commercial data  
❌ **Feature names are technical** → Wait for business taxonomy or ask BOI for mapping

---

**Owner:** BOI Team  
**Data Location:** `production.core_supply.agg_supplier_portal_events_session_daily`  
**Updated:** Daily via `sde_supply_semantic_transformations` Airflow DAG
