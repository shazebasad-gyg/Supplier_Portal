# Supplier Portal Engagement Score — v1 Full Definition, Results, and Validation

**Version:** v1 | **Baseline:** March 2026 | **Active suppliers (baseline):** 47,181 | **Owner:** Supply Analytics
**Source:** `production.core_supply.agg_supplier_portal_events_session_daily`

---

## Why we measure Optimization Tools Engagement

We are choosing to measure how suppliers engage with the optimization tools we build for them: the discretionary tools they use to compete better on pricing, content and availability. This is a leading, behavioral signal, and for now that is deliberately where we set the goal. We are measuring whether suppliers use what we build, not yet claiming a direct line to GMV.

This is a deliberate choice, not a vanity measure. Our approach to supplier optimization is product-first and self-serve: for the large majority of suppliers who will never have an account manager, these tools are how we support their growth. If we invest in them as the core of our offer, we have to know whether suppliers actually adopt and use them. Engagement is the earliest read on that, and it is something we can steer now.

The bridge to GMV is where we are heading, not where we start. Connecting tool engagement to supplier growth, and ultimately to GMV, is an aspirational validation layer we build toward. We are honest that this link has to be earned, not assumed, so we begin at the leading surface.

It is also a direct read on our 2027 Supplier Value Proposition. USP #2 is the tools to act on content, pricing, availability and monetization, and our target Scale Seeker is defined by valuing exactly these growth tools. So engagement with them is the proof we are delivering the value prop.

---

## Principle: how features count toward the Optimization Engagement

A feature counts only if it is discretionary: the supplier chooses to use it to compete better on pricing, content, or availability. Table-stakes and one-time setup are excluded. Test: could a supplier skip it and still operate normally? If yes, it counts. If they must do it to function, it does not.

**Keep:** Content editing, Pricing, Performance Hub, Availability management, Special offers, Review responses

**Exclude:** Booking management and Customer messaging (both reactive and non-negotiable), Product creation (setup), and helpers like verification and profile.

This keeps the score a clean signal of Scale Seekers using what we built to grow, not baseline operations every supplier does anyway.

*This initial set is an assumption, not settled. The line between proactive optimization and non-negotiable operations is a judgment call, and several features sit near the boundary. Availability is the clearest example: you could argue loading availability is table-stakes to run at all, and a baseline of it is. But how much a supplier opens, how far ahead, and whether they act on sell-out signals is a proactive lever to compete and capture more demand, so we count it. The point is that many tools have both a mandatory floor and a proactive layer, and we are measuring the proactive layer. We will refine the set as we learn.*

---

## What the metric is

### Definition

The share of the 6 scored portal features each active supplier used in a given month, averaged across all active suppliers.

An **active supplier** is any supplier with at least one live product (`bookable_activity_count > 0`) AND booking history in the last 365 days (`bookings_l365 > 0`) on any day within the reporting month. No lifecycle stage filter.

Each feature is scored on a **binary basis per calendar month**: a supplier scores **1** if they triggered the relevant event at least once during the month, and **0** if not.

### Formula

```
Supplier score           =  Features used by supplier  ÷  6
Supplier Portal Engagement  =  Average supplier score across all active suppliers
```

The denominator is fixed at **6** — the total number of scored features in v1.

### Worked example

| Supplier | Features used (of 6) | Supplier score |
|---|---|---|
| Supplier A | 4 | 4 ÷ 6 = **67%** |
| Supplier B | 2 | 2 ÷ 6 = **33%** |
| Supplier C | 1 | 1 ÷ 6 = **17%** |

**Supplier Portal Engagement = (67% + 33% + 17%) ÷ 3 = 39%**

---

## The 6 scored features and what counts as a use

F6 (Bookings Management) and F8 (Customer Messaging) are excluded from scoring as reactive features. The numbering reflects the original feature taxonomy.

| # | Feature | Eligibility gate | Counts as used when... | Containers |
|---|---|---|---|---|
| F1 | **Product Content Editing** | `bookable_activity_count > 0` | Supplier saves a content step in the existing product editor, manages keywords or addresses, or edits the option setup or meeting point tab in the option panel and saves in the same session | `ProductDetails` |
| F2 | **Pricing Configuration** | `bookable_activity_count > 0` | Supplier saves option pricing or availability configuration, or creates or updates an additional pricing rule | `ProductDetails`, `availability-and-pricing` |
| F3 | **Performance Views** | `bookings_l365 > 0` | Supplier lands on the Performance tab AND fires at least one depth interaction event | `SupplierPerformance`, `SupplierProductPerformance` |
| F4 | **Availability Management** | `bookable_activity_count > 0` | Supplier makes any confirmed save on dates, capacity, cut-off, or schedule, or edits the availability, cut-off, or duration tab in the option panel and saves in the same session | `SupplierAgenda`, `SupplierCalendar`, `availability-and-pricing`, `ProductDetails` |
| F5 | **Special Offers** | `bookable_activity_count > 0` | Supplier enters the deal creation flow or deletes an existing offer. One-click deal CTA click is excluded. | `SupplierSpecialOffers` |
| F7 | **Review Responses** | `bookings_l365 > 0` | Supplier submits at least one review reply | `SupplierReviews` |

---

## Methodology

### Who is included

- **Active supplier definition:** any supplier with `bookable_activity_count > 0` AND `bookings_l365 > 0` on at least one day within the reporting month. No lifecycle stage filter.
- **Exclusions:** GYG staff accounts, internal IPs, and GYG-owned supplier accounts are removed from all event data before any calculation.

### Why the denominator is fixed at 6

All suppliers in scope satisfy both entry conditions by construction, so all 6 features are relevant for every in-scope supplier. The denominator is always 6, unless a new feature is introduced and added to the engagement metric.

### When a new feature is added to the metric

Adding a new feature increases the denominator (e.g. 6 to 7). Without a deliberate restatement, every supplier's score would drop even if their behaviour had not changed.

| Step | What happens |
|---|---|
| 1 | New feature confirmed instrumented and reliable (at least one full clean month of data) |
| 2 | Supply Analytics recalculates the **last 3 months** of scores using the new denominator (e.g. ÷7). This is the published restatement. |
| 3 | The current target is adjusted proportionally: `new_target = old_target × (new_score_this_month / old_score_this_month)` |
| 4 | All future reporting uses the new denominator. Historical data beyond the 3-month restatement window is labelled **v1 (÷6 basis)**. |
| 5 | This document is updated: denominator, feature table, restated numbers, and adjusted target. |
| 6 | In the results table, the restatement month MoM change is labelled as a restatement, not organic movement. Format: **-Xpp (restatement: ÷6 to ÷7)**. |

### Current baseline

**Trend window starts March 2026.** January and February 2026 are excluded from trend comparisons. Three features (F1, F2, F3) had signal events that went live during that period. Data before March 2026 understates reach and is not comparable. 2025 figures reflect only the features that were instrumented at the time (F4, F5, F7 for most of the year).

### Version history

| Version | Since | Features | Denominator | Mar 2026 baseline |
|---|---|---|---|---|
| **v1 — CURRENT** | Aug 2026 | F1, F2, F3, F4, F5, F7 | ÷ 6 | 19.08% |
| v2 — PENDING | TBD | TBD | ÷ 7 | Restated at that time |

---

## Results: January 2025 – July 2026

**2025 scores are understated.** F1, F2, and F3 were not instrumented for most of 2025. Scores reflect only F4, F5, and F7 — three of the six features. Use 2025 data for directional context only, not as a performance baseline. Clean baseline starts **March 2026**.

**Jan and Feb 2026 = partial instrumentation.** F1 and F2 events went live December 2025 and ramped through Q1 2026. F3 container launched February 17. Clean trend starts **March 2026**.

### Headline engagement score — January 2025 to July 2026

Clean trend (March to July 2026): **19.08% to 29.56%**, +10.5pp in 5 months.

Months marked ⚠ are excluded from trend comparisons due to missing instrumentation.

| Month | Active suppliers | Engagement score | MoM change | Notes |
|---|---|---|---|---|
| Jan 2025 ⚠ | 36,558 | 5.42% | n/a | F1, F2, F3 not instrumented. Score reflects F4+F5+F7 only. |
| Feb 2025 ⚠ | 36,065 | 5.66% | +0.2pp | F1, F2, F3 not instrumented. |
| Mar 2025 ⚠ | 36,498 | 6.49% | +0.8pp | F1, F2, F3 not instrumented. |
| Apr 2025 ⚠ | 36,543 | 7.57% | +1.1pp | F1, F2, F3 not instrumented. |
| May 2025 ⚠ | 37,506 | 9.14% | +1.6pp | F1, F2, F3 not instrumented. |
| Jun 2025 ⚠ | 38,508 | 9.87% | +0.7pp | F1, F2, F3 not instrumented. |
| Jul 2025 ⚠ | 39,418 | 10.14% | +0.3pp | F1, F2, F3 not instrumented. |
| Aug 2025 ⚠ | 40,451 | 10.13% | 0.0pp | F1, F2, F3 not instrumented. |
| Sep 2025 ⚠ | 41,361 | 9.96% | -0.2pp | F1, F2, F3 not instrumented. |
| Oct 2025 ⚠ | 41,255 | 9.95% | 0.0pp | F1, F2, F3 not instrumented. |
| Nov 2025 ⚠ | 41,715 | 8.99% | -1.0pp | F1, F2, F3 not instrumented. |
| Dec 2025 ⚠ | 43,009 | 9.68% | +0.7pp | F1 and F2 events go live. |
| Jan 2026 ⚠ | 43,902 | 11.54% | +1.9pp | F1/F2 ramp. F3 not yet live. |
| Feb 2026 ⚠ | 44,927 | 14.85% | +3.3pp | F3 container launched Feb 17. |
| **Mar 2026 (baseline)** | **47,181** | **19.08%** | +4.2pp | First fully instrumented month. |
| Apr 2026 | 49,322 | 27.88% | +8.8pp | F1 proxy events go live. F3 ramps to full adoption. |
| May 2026 | 52,098 | 29.29% | +1.4pp | |
| Jun 2026 | 55,005 | 29.75% | +0.5pp | F5 increase from deal campaign. |
| **Jul 2026** | **58,045** | **29.56%** | -0.2pp | |

### Per-feature reach rate: January 2025 – July 2026

Percentage of active suppliers who used each feature in the month. Cells marked ⚠ are partial due to missing instrumentation.

| Month | F1 Content | F2 Pricing | F3 Perf | F4 Avail | F5 Offers | F7 Reviews |
|---|---|---|---|---|---|---|
| Jan 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 23.8% | 3.5% | 5.2% |
| Feb 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 24.2% | 4.1% | 5.6% |
| Mar 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 27.2% | 4.8% | 6.9% |
| Apr 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 29.9% | 5.6% | 9.9% |
| May 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 35.1% | 5.9% | 13.8% |
| Jun 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 39.6% | 6.0% | 13.6% |
| Jul 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 40.2% | 6.0% | 14.6% |
| Aug 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 39.9% | 5.6% | 15.3% |
| Sep 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 39.6% | 5.9% | 14.2% |
| Oct 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 40.4% | 5.5% | 13.9% |
| Nov 2025 | 0.0% ⚠ | 0.0% ⚠ | 0.0% ⚠ | 37.4% | 5.2% | 11.3% |
| Dec 2025 ⚠ | 1.1% ⚠ | 2.9% ⚠ | 0.0% ⚠ | 38.3% | 5.5% | 10.3% |
| Jan 2026 ⚠ | 4.3% ⚠ | 8.3% ⚠ | 0.0% ⚠ | 39.9% | 5.8% | 10.9% |
| Feb 2026 ⚠ | 10.7% ⚠ | 19.0% ⚠ | 0.0% ⚠ | 42.4% | 5.7% | 11.3% |
| **Mar 2026** | 16.0% | 29.4% | 2.0% | 46.8% | 6.2% | 14.0% |
| Apr 2026 | 27.6% | 28.8% | 39.7% | 48.4% | 6.7% | 16.0% |
| May 2026 | 33.2% | 28.5% | 39.9% | 49.1% | 7.7% | 17.4% |
| Jun 2026 | 33.8% | 27.7% | 42.0% | 48.2% | 8.5% | 18.4% |
| **Jul 2026** | 32.7% | 27.3% | 41.1% | 48.7% | 8.4% | 19.1% |

---

## Validation and stress tests — July 2026

All tests use July 2026 as the reference month (58,045 active suppliers).

### 5.1 Score distribution

**Why:** The headline is an average. If the distribution is heavily skewed, the average is misleading.

| Features reached | Suppliers | % of total | Cumulative % |
|---|---|---|---|
| 0 | 21,739 | 37.5% | 37.5% |
| 1 | 10,104 | 17.4% | 54.9% |
| 2 | 6,575 | 11.3% | 66.2% |
| 3 | 6,378 | 11.0% | 77.2% |
| 4 | 7,109 | 12.2% | 89.4% |
| 5 | 4,710 | 8.1% | 97.5% |
| 6 | 1,430 | 2.5% | 100% |

**Percentiles:** p10 = 0%, p50 = 16.7% (1 feature), p90 = 83.3% (5 features). Mean = 29.56%.

**Verdict: flag.** 37.5% of active suppliers used zero scored features in July. The mean is well above the median, meaning a smaller engaged group is pulling the average up. Always pair the headline with the zero-feature share. The 37.5% who use nothing are the primary opportunity.

---

### 5.2 Engagement by GMV tier

**Why:** If engagement is random with respect to GMV, the metric is not measuring anything commercially meaningful.

| GMV tier (last 365 days) | Suppliers | % of base | Avg engagement score |
|---|---|---|---|
| No GMV (€0) | 145 | 0.2% | 4.1% |
| €1 to €10K | 36,133 | 62.2% | 23.4% |
| €10K to €50K | 11,470 | 19.8% | 35.0% |
| €50K to €100K | 3,614 | 6.2% | 40.6% |
| €100K+ | 6,683 | 11.5% | 48.3% |

**Verdict: pass.** Engagement is monotonically higher at every GMV tier. The metric correlates with commercial value.

---

### 5.3 Managed vs non-managed

**Why:** Managed suppliers have a dedicated account manager driving portal activity. We need to know if this distorts the headline.

| Status | Suppliers | % of base | Avg engagement score |
|---|---|---|---|
| Non-managed | 52,300 | 90.1% | 28.2% |
| Managed | 5,745 | 9.9% | 42.1% |

**Verdict: flag.** +13.9pp gap. Managed suppliers add roughly +1.4pp to the headline (9.9% × 13.9pp). Not a large distortion but the headline should not be used to evaluate the self-serve portal in isolation. Use 28.2% as the non-managed baseline for any self-serve initiative.

---

### 5.4 Engagement by size tier

**Why:** If the metric is driven entirely by XL suppliers it is less useful as a company-wide signal.

| Size tier | Suppliers | % of base | Avg engagement score |
|---|---|---|---|
| S | 50,901 | 87.9% | 27.0% |
| M | 6,128 | 10.6% | 47.0% |
| L | 735 | 1.3% | 58.8% |
| XL | 135 | 0.2% | 68.9% |

**Verdict: pass.** The headline is driven by S-tier suppliers (87.9% of base). Not distorted by large accounts.

---

### 5.5 Feature co-usage matrix

**Why:** If two features always move together they are the same signal counted twice.

F2 (Pricing) and F4 (Availability) share the same primary event (`AvailabilityAndPricingSaveAndContinueButton`). Every supplier who fires that event is counted in both. All other feature pairs are measured by distinct events with no forced co-occurrence.

**Verdict: flag (F2 and F4 only).** The overlap does not invalidate the score but means F2 and F4 together contribute less incremental coverage than two fully independent features would. They are genuinely different optimization levers — pricing is what you charge, availability is when you are open. The overlap is an instrumentation gap, not a conceptual one. Separate events are on the roadmap.

---

### 5.6 Acquisition cohort engagement trajectory

**Why:** The headline mixes suppliers at different lifecycle stages. Cohort analysis shows whether newer suppliers onboard into engagement faster than older cohorts did at the same age.

- 2025 cohorts start between 6–17% at month 0 (only F4, F5, F7 instrumented), dip slightly in months 1–2, then grow gradually and stabilize around 24–27% by month 6.
- 2026 cohorts start significantly higher (25–45%) because F1, F2, F3 are now in the metric, then decline toward a similar 25–29% steady state. The month-0 spike reflects setup activity.
- 2026 cohorts score higher than 2025 cohorts at the same age. This is the instrumentation effect, not a behavioral improvement.

**Verdict: flag.** Like-for-like cohort comparison is only valid from Q1 2026 onward.

---

### 5.7 Month-on-month stability (June vs July 2026)

**Why:** A metric that flips randomly each month is driven by noise, not behavior.

54,540 suppliers were active in both June and July 2026.

| Month-on-month change | Suppliers | % of paired base |
|---|---|---|
| Down 2 or more features | 8,138 | 15.0% |
| Down 1 feature | 8,155 | 15.0% |
| No change | 23,933 | 44.1% |
| Up 1 feature | 7,422 | 13.7% |
| Up 2 or more features | 6,652 | 12.3% |

**Stable (within ±1 feature): 72.8%** (44.1% no change + 15.0% down 1 + 13.7% up 1)

**Verdict: pass.** Acceptable stability for a monthly behavioral metric. Acceptable range: 65%+ within ±1 feature.

---

### 5.8 Monthly trend stability

**Why:** A metric that jumps erratically is hard to trust and act on.

| Period | Score | MoM | Explanation |
|---|---|---|---|
| Mar 2026 | 19.08% | +4.2pp | First clean month. F3 partially live (2.0% reach). |
| Apr 2026 | 27.88% | +8.8pp | F3 ramps to 39.7%. F1 proxy events go live. |
| May 2026 | 29.29% | +1.4pp | Organic growth across all features. |
| Jun 2026 | 29.75% | +0.5pp | F5 jumps from 7.7% to 8.5%, driven by deal campaign. |
| Jul 2026 | 29.56% | -0.2pp | F5 partially reverses as campaign ends. All other features stable. |

**Verdict: pass.** All step-changes are fully explained. The metric is not sensitive to noise.

---

## Limitations

**1. Breadth, not depth — once counts the same as daily**

A supplier who clicks the Performance tab once scores the same as one who analyzes it every week. The metric tells you a supplier touched a feature, not whether it changed how they operate.

**2. This metric does not claim a direct link to GMV**

The score measures whether suppliers use the tools we build. It does not measure whether using those tools improves their GMV. Connecting portal engagement to supplier growth outcomes is the next validation layer we are building toward — it has to be earned through analysis, not assumed.

**3. Reactive features inflate the score with GMV growth, not portal improvement**

F7 (Reviews) requires receiving a review, which requires bookings. F3 (Performance) is most useful when there is enough booking data to analyze. If GYG demand grows, these features go up automatically with no change in portal product quality. A rising headline can be GMV growth in disguise.

**4. Composition shifts confound the headline number**

Managed suppliers score 42.1% vs 28.2% non-managed. XL suppliers score 68.9% vs 27.0% for S-tier. If the mix shifts toward more managed or larger suppliers, the headline rises mechanically. Any target set on the headline needs to control for mix.

**5. 37.5% zero-feature suppliers define a structural floor**

More than a third of active suppliers used zero scored features in July. Moving this group requires onboarding interventions, account management, or incentives — not just product improvements. Without a strategy for this group, the metric has a realistic ceiling well below 50%.

**6. Equal weighting is unvalidated against outcomes**

Every feature contributes 1/6. There is no evidence this reflects actual value delivered to GYG or the supplier. Until features are connected to outcomes — conversion, cancellations, repeat bookings — the weights are arbitrary.
