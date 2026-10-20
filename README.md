# Invoice Exception Operations

Status: **public planning only; implementation is not activated.** No application, trained model, evaluation result, deployment, or customer validation is claimed here. The parent reports the [public repository](https://github.com/123ssk321/cv-invoice-exception-ops) created and verified. Publication of this plan is not a functional release.

This proposed tool would turn a narrow family of English/Portuguese supplier invoices into an evidence-backed exception queue: extract fields, check arithmetic and required information, reconcile against purchase-order records, review corrections, and export a validated subset of UBL. The value is rules, reconciliation, and review traceability beyond quick document extraction.

The planned scope is single-organization, local-first processing of EUR invoices: digital PDFs, bounded scans, and a UBL Invoice subset; one to three pages and at most 20 lines; deterministic rules; a browser review workflow; audit history; and one versioned CSV accounting adapter. It excludes payments, autonomous accounting postings, Peppol transmission, jurisdictional tax certification, arbitrary document understanding, handwriting, credit notes, and multi-tenant SaaS.

When selected, this is an **alternative allocation of the portfolio's total 16 hours/week**, not a concurrent 16-hour project. First functional public release targets **month 9** (preferred window months 6–9; absolute window months 3–12). Product-candidate finish targets month 12. The budget is **800 gross hours: 640 planned + 160 contingency (20%)**, below the 832-hour ceiling. Nothing starts merely because the repository is public.

The default technical route is CPU Tesseract with separately licensed English/Portuguese weights, deterministic extraction/rules, a Python service, SQLite, and server-rendered review pages. Dependency versions and licenses must pass activation gates. Small synthetic sets with exact generated labels come first. Existing public human-annotated datasets are permitted after rights checks; no manual collection, relabeling, curation, private invoice contribution, or paid annotator is needed to complete the technical plan.

Synthetic robustness, public-data component evaluation, and actual customer validation are separate evidence categories. Without external workflow evidence, the month-12 outcome can be a reproducible technical product candidate, but not a demonstrated commercially effective accounts-payable product.

- [Execution plan](docs/EXECUTION_PLAN.md): exact scope, contracts, commands, licenses, evaluation, schedule, gates, and implementer handoff.
- [Machine-actionable backlog](planning/backlog.json): 30 budgeted packages across seven milestones, including later operations and validation.

Source context: *Research report 2: high-effort computer-vision projects for a solo builder*, dated 2026-10-16, section 1, “Document-to-structured-data and e-invoice exception handling.” This standalone plan narrows and corrects that recommendation. Its primary-source links and explicit assumptions are included in the execution plan. Shared agent instructions are supplied by the parent; this project does not add an AGENTS.md.
