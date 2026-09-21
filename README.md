# Supplier Portal Analytics

Analysis code behind the Supplier Portal engagement work: the Portal Optimization
Engagement metric and the per-feature audits that preceded it.

Owner: Shazeb Asad (Supply Analytics).

## Canonical documentation

**[Portal Optimization Engagement: Definition, Results and Validation (v1)](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4763779185)**
is the source of truth for the metric definition, the six scored features, the
results series and the validation tests. Everything in this repo maps to a page
under that one in the Confluence
[Supplier Portal Engagement](https://getyourguide.atlassian.net/wiki/spaces/DA/folder/4545643051)
folder.

## Layout

```
engagement_framework/   the holistic 6-feature metric (v1, Aug 2026)
feature_audits/         per-feature deep dives (Apr 2026)
docs/history/           how the framework was arrived at (Apr to Jun 2026)
```

## Notebooks and their documentation

| Notebook | Confluence page | Date |
|---|---|---|
| [engagement_framework/supplier_portal_engagement_v1.ipynb](engagement_framework/supplier_portal_engagement_v1.ipynb) | [Portal Optimization Engagement (v1)](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4763779185) | Aug 2026 |
| [feature_audits/performance_hub.ipynb](feature_audits/performance_hub.ipynb) | [Feature Audit: Performance Hub](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4205936693) | Apr 2026 |
| [feature_audits/recommended_actions.ipynb](feature_audits/recommended_actions.ipynb) | [Feature Audit: Recommended Actions](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4197253805) | Apr 2026 |
| [feature_audits/product_creation.ipynb](feature_audits/product_creation.ipynb) | [Catalog Feature Audit: Product Creation](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4206461002) | Apr 2026 |
| [feature_audits/portal_login_engagement.ipynb](feature_audits/portal_login_engagement.ipynb) | [Who Logs In, How Often, and What Patterns Emerge](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4186865707) | Apr 2026 |

`engagement_framework/supplier_portal_engagement_methodology.md` is the local copy
of the canonical Confluence page.

## Analyses documented on Confluence only

These have no notebook in this repo. They were run directly in the Databricks
workspace.

| Analysis | Confluence page | Date |
|---|---|---|
| Supplier Portal Engagement Analysis by Container (49 containers) | [DA 4486660370](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4486660370) | Jun 2026 |
| Causal Impact: Moving Messaging Outside the Supplier Portal (DiD) | [DA 4498260224](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4498260224) | Jun 2026 |
| Performance Hub Engagement Analysis, Q2 2026 KR Tracking | [BOI 4504256916](https://getyourguide.atlassian.net/wiki/spaces/BOI/pages/4504256916) | Jun 2026 |
| Request: Supplier Portal Event Prioritization Framework | [DA 4499898374](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4499898374) | Jun 2026 |
| Performance Hub Dashboard, Technical Documentation | [DA 4548984855](https://getyourguide.atlassian.net/wiki/spaces/DA/pages/4548984855) | Jul 2026 |

## Data sources

| Table | Purpose |
|---|---|
| `production.supply_analytics.supplier_portal_events` | All supplier portal events, web and mobile |
| `production.core_supply.agg_supplier_portal_events_session_daily` | Session-daily aggregate, source for the engagement metric |
| `production.supply_analytics.dim_recommended_actions` | Recommended Actions surfaced, resolved, dismissed |
| `production.events.events` | Raw event source used by the April feature audits |

Standard exclusions applied throughout: GYG staff accounts, internal office IPs,
and GYG-owned supplier accounts.

## Running the notebooks

The notebooks in `feature_audits/` were authored as Databricks source-format
notebooks and converted to `.ipynb`. They carry no stored outputs. Import them into
the Databricks workspace to run them.
