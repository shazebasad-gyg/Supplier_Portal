# Supplier Portal Engagement Metrics - Executive Summary

## The Answer: What Metric Should GYG Use?

### **For C-Level/Management: Monthly Active Suppliers (MAU)**

**Definition:** Unique suppliers who logged in at least once in the past 30 days

**Why this metric:**
- ✅ **Industry standard** - Used by Amazon Seller Central, Shopify, Stripe
- ✅ **Simple to communicate** - One number executives understand
- ✅ **Actionable** - Shows if suppliers are engaged or drifting away
- ✅ **You already have it** - In your `fact_supplier_engagement` view

**Target:** 60-70% of total active suppliers (adjust based on your baseline)

---

## The Problem with "Just Login Rates"

Login rates are a **starting point**, but insufficient alone because:

❌ **Login ≠ Value** - Supplier might login and leave frustrated  
❌ **Doesn't show depth** - 1 login vs 20 logins look the same  
❌ **Misses the "why"** - Are they using features? Getting value?

**Big tech companies never use just login rates alone.**

---

## The Complete Framework (What Big Tech Actually Uses)

### **Level 1: North Star Metric** (Board/C-Suite)
→ **Monthly Active Suppliers (MAU)**

### **Level 2: Supporting Engagement Metrics** (VP/Director)
→ **Stickiness** = DAU/MAU (how often they return)  
→ **GMV-Weighted Active Rate** (engagement from high-value suppliers)  
→ **Login Frequency Distribution** (1x vs 5x vs 20x per month)

### **Level 3: Feature Adoption Metrics** (Product Team)
→ % using Performance Hub  
→ % interacting with Recommended Actions  
→ Average # of features used per session

### **Level 4: Outcome Metrics** (Business Value)
→ GMV from engaged vs non-engaged suppliers  
→ Retention rate by engagement tier  
→ NPS by engagement tier

---

## How Google Does It: The HEART Framework

| Dimension | Metric |
|-----------|--------|
| **H**appiness | NPS, satisfaction scores |
| **E**ngagement | MAU, session duration, actions per session |
| **A**doption | % using each feature |
| **R**etention | 30-day retention rate |
| **T**ask Success | % completing core actions |

**All Google products report on HEART, not just login rates.**

---

## The 3 Metrics Management Should Track

### 1. **MAU (Monthly Active Suppliers)** 
   - Primary metric, track MoM trend
   - Segment by: Managed vs Non-Managed, Connected vs Non-Connected

### 2. **GMV-Weighted Active Rate**
   - % of GMV from suppliers who logged in past 30 days
   - Ensures you're engaging high-value suppliers

### 3. **Feature Adoption Rate**
   - % using Performance Hub, Recommended Actions
   - Shows engagement quality, not just login

---

## What Your Explores Already Support

✅ **You have the right data structure:**

**From `supplier_engagement` explore:**
- MAU, WAU, DAU ← **Primary engagement metrics**
- Stickiness (DAU/MAU) ← **Engagement quality**
- Login rates (L28, L30, L60) ← **Alternative views**
- GMV-weighted metrics ← **Business value**
- Login frequency distribution ← **Segmentation**

**From `feature_usage_outcomes` explore:**
- Performance Hub usage ← **Feature adoption**
- Recommended Actions adoption ← **Feature adoption**
- Resolution rates ← **Task success**

**You're already aligned with big tech best practices!**

---

## Quick Decision Guide

### "Which login rate metric should we use?"

| Metric | When to Use |
|--------|-------------|
| **L7 Login Rate** | Fast-moving products (daily usage expected) |
| **L28 Login Rate** | **← RECOMMENDED for GYG** (industry standard) |
| **L90 Login Rate** | Seasonal/infrequent products |
| **Monthly Login Frequency** | Understanding power users vs casual users |

**Our recommendation: L28 Login Rate = MAU / Total Active Suppliers**

---

## Recommended Dashboard

```
┌─────────────────────────────────────────────────────┐
│ SUPPLIER PORTAL ENGAGEMENT (April 2026)             │
├─────────────────────────────────────────────────────┤
│                                                      │
│ 📊 Monthly Active Suppliers                         │
│    12,450 suppliers (62% of total) ▲ 8% MoM        │
│                                                      │
│ 💰 GMV-Weighted Active Rate                         │
│    78% of GMV from active suppliers ▲ 3% MoM       │
│                                                      │
│ 🎯 Feature Adoption                                 │
│    • Performance Hub: 65% of active suppliers       │
│    • Recommended Actions: 42% of active suppliers   │
│                                                      │
│ 📈 Engagement Quality                               │
│    • Stickiness (DAU/MAU): 18%                      │
│    • Avg logins per supplier: 4.2x per month        │
│    • Avg actions per session: 3.8                   │
│                                                      │
│ 💡 Business Impact                                  │
│    • GMV from engaged: €125M (82% of total)         │
│    • GMV from non-engaged: €28M (18% of total)      │
│    • Retention (engaged): 72% vs 45% (non-engaged)  │
│                                                      │
└─────────────────────────────────────────────────────┘
```

---

## What to Tell Management

**"We recommend using Monthly Active Suppliers (MAU) as our primary engagement metric, following industry best practices from Amazon, Shopify, and Stripe."**

**"This is better than just login rates because it combines:**
- Who is engaged (login rate)
- How often they engage (stickiness)
- What they do (feature adoption)
- Business value (GMV-weighted metrics)"

**"We'll report MAU monthly with a trend line, segmented by supplier type, and show the GMV impact."**

---

## Implementation Timeline

**Week 1-2:** Establish MAU baseline, set targets  
**Week 3-4:** Build executive dashboard with MAU + GMV-weighted rate  
**Month 2:** Add stickiness and feature adoption metrics  
**Month 3:** Add outcome metrics (retention, GMV impact)  
**Month 4:** Build comprehensive HEART framework dashboard

---

## Bottom Line

✅ **Use MAU (Monthly Active Suppliers) as your North Star**  
✅ **Supplement with GMV-weighted rate for business value**  
✅ **Add feature adoption to show engagement quality**  
✅ **Track outcomes (retention, GMV) to prove impact**

**You already have the data. You already have the explores. Just need to decide on the primary metric and build the dashboard.**

**Recommended: Start with MAU.**
