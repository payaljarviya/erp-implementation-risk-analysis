# ERP Implementation Risk Analysis — Revlon SAP Failure

In 2019, Revlon's SAP S/4HANA go-live caused a supply chain collapse so severe the company cited it in SEC filings as a direct contributor to a $64M revenue shortfall in a single quarter. Total implementation cost overruns and losses exceeded $130M. The project had passed every internal milestone. It went live on schedule. And then it broke.

This case study is a root cause analysis of what went wrong — written from four years inside live PeopleSoft FSCM environments, where I saw the same failure patterns in smaller form on a regular basis.

## The core argument

ERP failures aren't usually caused by bad software. They're caused by the gap between how a system is configured and how a business actually operates — a gap that grows invisibly during implementation and becomes visible only at go-live.

In Revlon's case, three things compounded:

**Data migration was treated as a technical task, not a business one.** Legacy data was migrated without adequate cleansing or business validation. The people who understood what the data meant — the operations and planning teams — were largely excluded from the migration workstream. When SAP went live, it was operating on data that didn't reflect how Revlon actually made and shipped products.

**Testing covered the system, not the business process.** UAT focused on whether transactions could be completed, not whether the outputs matched what operations needed. A system that processes a transaction without errors but produces incorrect inventory positions has passed UAT and failed the business simultaneously.

**The cutover window was too aggressive.** Revlon's manufacturing and distribution operations ran 24/7. The go-live plan didn't account for the operational support load during stabilisation — the period immediately after go-live when every exception surfaces and the team is already exhausted from cutover. That's when the order processing backlog developed.

## Framework

The analysis uses the SCQA (Situation, Complication, Question, Answer) structure — the same framework McKinsey and BCG use to structure consulting problem statements.

| Component | Summary |
|-----------|---------|
| **Situation** | Revlon undertook SAP S/4HANA implementation to modernise supply chain operations across its manufacturing and distribution network |
| **Complication** | The go-live caused an order management system failure that blocked order processing for weeks, resulting in $64M Q3 2019 revenue shortfall and $130M+ total impact |
| **Question** | What were the root causes, and what implementation controls would have prevented or contained the failure? |
| **Answer** | Data migration governance failures + inadequate integration testing + insufficient hypercare resourcing. All three were preventable with standard implementation risk controls. |

## Key findings

**Root cause 1 — Data migration governance.** No business sign-off gate on migrated data quality before go-live. Operations teams were not required to validate that migrated inventory, BOM, and customer data was fit for purpose.

**Root cause 2 — Integration testing gaps.** The system was tested end-to-end in a sandbox environment that didn't replicate the volume, complexity, or exception patterns of production operations. High-volume order processing stress tests were not run.

**Root cause 3 — Hypercare resourcing.** The post-go-live support plan assumed a steady-state stabilisation. It didn't account for the elevated exception volume that's normal in the first weeks after go-live. The SI team was already demobilising when the backlog started accumulating.

## What a different outcome would have required

Three implementation controls that are standard practice but inconsistently applied:

1. **Data readiness gate** — Mandatory business sign-off on migrated data quality 30 days before go-live. Operations and planning leads validate that the data their teams will work with on day one is accurate.

2. **Volume integration testing** — Load testing against production-representative transaction volumes, not just functional scenario coverage. This surfaces performance issues and exception handling failures before go-live.

3. **Extended hypercare commitment** — SI team retention at full strength for 60–90 days post go-live, not 30. The cost of hypercare extension is a fraction of the cost of a failed go-live.

## Files

```
Revlon_ERP_Case_Study_Payal_Jarviya.docx    # Full consulting brief with SCQA analysis
README.md
```

---

*Payal Jarviya | MBA Candidate, SKK GSB Seoul | Former IT Analyst, NTT DATA North America*

*Four years of PeopleSoft FSCM consulting across Fortune 500 environments.*
