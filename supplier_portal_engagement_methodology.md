# Supplier Portal Engagement Score — Methodology

---

## What the metric is

### Definition

The share of the 8 portal features each active supplier used in a given month, averaged across all active suppliers.

---

### Formula

```
Supplier score  =  Features used by supplier  ÷  8  (fixed — total features in current version)

Headline score  =  Average supplier score across all active suppliers
```

The denominator is always **8** — not the number of features a supplier is eligible for. Non-eligible features score 0 in the numerator but do not reduce the denominator. This means the metric is stable: adding a new feature in the future cannot silently drop scores for suppliers who didn't change their behaviour.

---

### Worked example

| Supplier | Features used | Score |
|---|---|---|
| Supplier A (8 eligible, uses 4) | 4 | 4 ÷ 8 = **50%** |
| Supplier B (4 eligible, uses 3) | 3 | 3 ÷ 8 = **37.5%** |
| Supplier C (8 eligible, uses 2) | 2 | 2 ÷ 8 = **25%** |

**Headline score = (50% + 37.5% + 25%) ÷ 3 = 37.5%**

> **Note:** A Pre-Activated supplier eligible for only 4 features who uses all 4 scores 4 ÷ 8 = **50%** — not 100%. This correctly reflects that half the portal is not yet available to them.

---

### The 8 features (v1)

| # | Feature | Eligible suppliers | Counts as "used" when… |
|---|---|---|---|
| F1 | Product Content Editing | ≥ 1 live product | Supplier saves any step in the product editor or creation wizard |
| F2 | Option & Pricing Configuration | ≥ 1 live product | Supplier saves an option or creates / updates a pricing rule |
| F3 | Performance Views | ≥ 1 booking in last 365 days | Supplier opens the Performance tab and interacts (filters, drills into a product) |
| F4 | Availability Management | ≥ 1 live product | Supplier makes any confirmed save on dates, capacity, cut-off, or schedule |
| F5 | Special Offers | ≥ 1 live product | Supplier applies a one-click deal, enters the deal creation flow, or deletes an offer |
| F6 | Bookings Management | ≥ 1 booking in last 365 days | Supplier takes any booking action (confirm, cancel, no-show, bulk manage) |
| F7 | Review Responses | ≥ 1 booking in last 365 days | Supplier submits at least one review reply |
| F8 | Customer Messaging | ≥ 1 booking in last 365 days | Supplier sends or replies to a customer message |

---
---

## Methodology

### Who is included

Active suppliers only: **Pre-Activated** and **Activated** lifecycle stage at the last day of the reporting month.  
GYG staff accounts, internal IPs, and GYG-owned supplier accounts are excluded from all event data.

---

### Why the denominator is fixed at 8

Each supplier scores their features reached out of **8**, regardless of eligibility. Adding F9 in the future cannot silently drop the score of suppliers who didn't change their behaviour — the denominator only changes via a deliberate version bump (see below).

---

### When new features are added to the metric

The denominator changes (e.g. 8 → 9). This requires a one-time deliberate restatement — it does not happen automatically.

| Step | What happens |
|---|---|
| 1 | New feature confirmed instrumented and reliable (at least one full clean month of data) |
| 2 | Supply Analytics recalculates the **last 3 months** of scores using the new denominator |
| 3 | The current target is adjusted proportionally: `new_target = old_target × (new_score_this_month / old_score_this_month)` |
| 4 | All future reporting uses the new denominator. Historical data beyond the 3-month window is labelled **v1 (÷8 basis)** |
| 5 | This document and the Confluence page are updated: denominator, feature table, restated numbers, and adjusted target |

**Why adjust the target rather than reset it?** Adding F9 changes the scale — every supplier's score is now out of 9. A supplier who hasn't used F9 yet scores slightly lower by construction, not because they engaged less. The proportional adjustment corrects for this scale change while preserving the underlying ambition.

---

### Current baseline

The v1 metric is fully instrumented from **March 2026**.  
January and February are excluded from trend comparisons because three features (F2, F3, F4) had events that went live during that period. Data before March exists but is partial — it understates reach and must not be used as a baseline.

---

### Version history

| Version | Since | Features | Denominator | Mar 2026 baseline |
|---|---|---|---|---|
| **v1 — CURRENT** | Aug 2026 | F1 – F8 | ÷ 8 | 23.4% |

---

## Results: Jan–Jul 2026

> ⚠️ **Jan and Feb = partial instrumentation.** F2's primary event went live late Jan, F3's container launched Feb 17, F4's pricing-path events launched Feb–Mar, F8's Inbox events launched Mar. Clean trend starts **March 2026**.

### Headline engagement score

Clean trend (Mar–Jul): **23.4% → 31.0%** · **+7.6pp in 5 months** · **Target: 38% by Dec 2026**

| Month | Active suppliers | Engagement score | MoM change | Note |
|---|---|---|---|---|
| Jan 2026 ⚠️ | 50,301 | 18.2% | — | Partial — F2, F3, F4, F8 not fully tracked |
| Feb 2026 ⚠️ | 52,230 | 19.0% | +0.8pp | Partial — F3 container live Feb 17 only |
| **Mar 2026 ✦ baseline** | **54,892** | **23.4%** | +4.4pp | First fully instrumented month |
| Apr 2026 | 57,244 | 27.7% | +4.3pp | F3 ramps to full adoption |
| May 2026 | 60,668 | 28.4% | +0.7pp | |
| Jun 2026 | 63,942 | 29.3% | +0.9pp | F5 spike from one-click deal campaign |
| **Jul 2026** | **66,006** | **31.0%** | +1.7pp | F6 jump — summer peak + Bookings surface expansion |

### Per-feature reach rate (% of eligible suppliers who used the feature)

| Month | F1 Content | F2 Pricing | F3 Perf | F4 Avail | F5 Offers | F6 Bookings | F7 Reviews | F8 Messaging |
|---|---|---|---|---|---|---|---|---|
| Jan 2026 ⚠️ | 29.5% | 8.3% ⚠️ | 0.0% ⚠️ | 38.6% ⚠️ | 5.4% | 31.9% | 11.2% | 32.5% ⚠️ |
| Feb 2026 ⚠️ | 25.0% | 19.5% ⚠️ | 0.0% ⚠️ | 40.3% ⚠️ | 5.3% | 31.8% | 11.4% | 30.2% ⚠️ |
| Mar 2026 ✦ | 22.3% | 29.2% | 2.0% | 44.6% | 5.7% | 34.9% | 14.2% | 50.1% |
| Apr 2026 | 21.9% | 28.6% | 40.2% | 44.5% | 6.1% | 36.8% | 16.3% | 48.6% |
| May 2026 | 22.8% | 28.8% | 40.4% | 44.8% | 7.2% | 37.8% | 17.6% | 50.2% |
| Jun 2026 | 23.8% | 28.3% | 42.6% | 43.8% | 13.4% | 37.1% | 18.6% | 49.1% |
| Jul 2026 | 22.6% | 28.0% | 41.7% | 44.8% | 13.0% | 48.3% | 19.3% | 51.4% |
