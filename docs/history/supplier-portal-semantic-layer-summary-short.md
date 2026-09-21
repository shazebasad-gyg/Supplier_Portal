# Supplier Portal Semantic Layer - Quick Summary

**What:** New data foundation for analyzing supplier engagement on the Supplier Portal  
**Status:** Merged and live (PR #2788 / BOI-2951)

---

## 🎯 What Can You Analyze?

### Engagement Metrics
- **Active suppliers** (daily/weekly/monthly)
- **Stickiness** (DAU/MAU - how often suppliers return)
- **Active sessions** (supplier and browser level)
- **Feature adoption** (who's using what features for the first time)
- **Time-to-feature** (how quickly suppliers find features)

### Breakdowns Available
- Supplier: segment, country, size, tenure, managed/self-serve, contract type
- Device: platform (web/iOS/Android), device type, OS
- Portal: feature, location in portal (header/modal/settings)
- Language, account manager

---

## 📊 12 Metrics Ready to Use

| Category | Metrics |
|----------|---------|
| **Volume** | supplier_portal_events, active_suppliers, active_logins, active_sessions, active_browser_sessions |
| **Time-based** | dau, wau, mau, stickiness |
| **Adoption** | n_suppliers_first_use, median/p10/p90 time-to-event |

---

## 💡 Example Questions

✅ "How many suppliers are active weekly?"  
✅ "Which features are being adopted fastest?"  
✅ "Are mobile users as engaged as desktop users?"  
✅ "How quickly do suppliers find the export bookings button?"  
✅ "Which account managers have the most engaged suppliers?"

❌ "Did portal changes increase bookings?" (out of scope - needs custom model)  
❌ "What's the conversion rate from portal visit to booking?" (out of scope)

---

## 🚧 Known Gaps

- **Feature names are still technical codes** (e.g., `UIClick:export_button`) — business taxonomy coming soon
- **Supplier attributes show current values**, not historical (except size tier/tenure)
- **No commercial outcomes** (bookings/revenue) — use for engagement analysis only

---

## 🔍 How to Access

- **Analysts:** MetricFlow CLI (`mf query --metrics active_suppliers --group-by event_date`)
- **Looker:** Coming soon via dbt2looker integration
- **Stakeholders:** Request reports from BOI team

---

**Questions?** Contact BOI team | [Jira BOI-2951](https://getyourguide.atlassian.net/browse/BOI-2951)
