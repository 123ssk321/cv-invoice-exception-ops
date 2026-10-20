# Invoice Exception Operations — execution plan

Planning revision: 2026-10-20. Track: high. Requested architecture/review role: GPT-6 Astra, high effort. Implementation delegates: GPT-6 Luna medium or GPT-5.6 medium. This describes the requested delegation policy, not a runtime attestation about the authoring session.

Repository: https://github.com/123ssk321/cv-invoice-exception-ops. The parent reports it public and verified. **Not activated; all implementation below is future work.** Month 1 starts only when this project is selected and an activation date is recorded. Planning publication is day-one visibility, not a completed product. No remote action is authorized by this planning task.

Basis: *Research report 2: high-effort computer-vision projects for a solo builder* (2026-10-16), section 1. This document is self-contained and does not rely on an unpublished parent file.

## 1. Outcome, discovery, and exact boundary

Hypothesis, not validated demand: a small accounts-payable team wants a review queue that explains why a received supplier invoice cannot proceed. The proposed unit of value is a correctly resolved exception with original evidence, reproducible rules, and an accounting-ready export. IE-002 records an assumption ledger, a current-workflow map, a ten-case fictional task script, and questions about exception volume, cost, review authority, and existing software. Optional interviews may test those assumptions; neither recruitment success nor private invoices gate the technical finish. Do not send outreach messages without the user's explicit authorization.

### Included by month 9

- One organization, one operator at a time; local browser interface and local CLI/API. All monetary transactions use EUR, with two-decimal totals and decimal quantities/unit prices.
- Supplier invoices only: digital PDF or PNG/JPEG scans (1–3 A4-equivalent pages, 20 MiB total, 20 line items), plus a pinned UBL 2.1 Invoice subset. English is the acceptance language; Portuguese has a separately reported smoke suite, not equal-quality claims.
- Supported business case: domestic purchase of ordinary goods, positive quantities, standard VAT category S with one explicit positive rate per invoice, no allowances, charges, prepayments, foreign exchange, exemptions, or reverse charge. This is an engineering profile, not a Portugal or EU tax compliance claim.
- One invoice references at most one PO; reconcile seller, currency, SKU/PO line, quantity, unit price, and outstanding quantity from versioned CSV snapshots. Exact identifiers only. Unknown or ambiguous matches enter review. A reservation ledger prevents multiple exported invoices silently consuming the same PO quantity.
- Required-field, decimal, arithmetic, duplicate, reconciliation, and profile-validation exceptions; evidence boxes or XML pointers; explicit abstention; correction and revalidation; immutable revision history; export of a passing subset of UBL plus JSON/CSV exception reports.
- Baseline compared with plain OCR/field extraction and with deterministic rules on exact structured input. A reproducible demo using fictional invoices, including a deliberately invalid one and a PO mismatch.

### Added by month 12

Bounded batch processing (50 invoices), one versioned CSV accounting adapter with a simulated import acknowledgment, restore-tested storage, instrumentation, a release/rollback procedure, user documentation, and a use-case/pilot evidence report. The adapter is not advertised as a certified ERP integration. Corrections are logged for workflow audit, not automatically reused as training labels.

### Excluded through month 12

Payments, bank-account change approval, automatic accounting posting, fraud detection, tax advice, legal or Peppol certification, network access-point transmission, multi-tenant hosting, live ERP credentials, handwritten invoices, delivery-note OCR, credit notes, mixed VAT rates, full arbitrary UBL support, document translation, foundation-model training, GPU procurement, and unrestricted public uploads. No user/contractor data labeling or dataset curation, including a disguised requirement to “fix public labels.” Review of generated software artifacts is QA; it is not invoice ground-truth creation.

This high-effort project differs from a quick extraction tool (such as FormTrace) through its rules engine, PO reservations/reconciliation, correction revision semantics, and standards validation/export gate. It has no dependency on any quick project or shared code arriving later. Similarly, the separate industrial-metrology proposal concerns calibrated dimensions/assembly beyond quick anomaly triage; neither industrial project is in this project's implementation scope.

## 2. Capacity, milestones, and stop/go gates

Only 16 h/week exists across the entire portfolio. This schedule is one alternative that consumes that allocation when selected. Concurrent projects reduce the available rate and require rebaselining; they do not multiply capacity. Gross capacity here is 50 weeks × 16 h = 800 h; 640 h planned + 160 h reserve = 800 h, with two further calendar weeks left unallocated within a 52-week/832-hour maximum. Those 32 hours are not another hidden budget. Normal planning rate is 12.8 h/week plus 3.2 h/week contingency.

| Milestone | Relative time | Issues | Planned h | Reserve allocation h | Gross h | Exit |
|---|---|---|---:|---:|---:|---|
| M1 Scope, rights, contracts | weeks 1–5; months 1–2 | IE-001–007 | 64 | 16 | 80 | Rights and schema gates, 50 generated examples |
| M2 Baseline and honest evaluation | weeks 6–12; months 2–3 | IE-008–012 | 88 | 22 | 110 | Extraction baseline and frozen evaluation protocol |
| M3 Exception and reconciliation engine | weeks 13–20; months 3–5 | IE-013–015 | 104 | 26 | 130 | Rules, PO matching, revisions reproducible |
| M4 Review and standards boundary | weeks 21–28; months 5–7 | IE-016–018 | 104 | 26 | 130 | Review loop and gated UBL export |
| M5 First functional public result | weeks 29–37; months 7–9 | IE-019–022 | 104 | 26 | 130 | v0.1 public reproducible functional demo, target month 9 |
| M6 Product and operating evidence | weeks 38–44; months 9–11 | IE-023–026 | 96 | 24 | 120 | Batch adapter, recovery, use-case report |
| M7 Product-candidate decision | weeks 45–50; months 11–12 | IE-027–030 | 80 | 20 | 100 | v0.2, final evidence and explicit commercial decision |
| Total | 50 funded weeks | 30 packages | **640** | **160** | **800** | |

Week ranges are capacity envelopes; gates can move inside them. Cumulative gross to M5 is 580 h, about 36.25 weeks at 16 h/week, consistent with month 9. First functional public result must be at least three months and no more than twelve months after activation; preferred delivery window is months 6–9. Before month 3 publish plans or work-in-progress honestly. By month 9 release v0.1 or invoke the bounded fallback below; by month 12 either demonstrate the functional result or explicitly record that the objective failed. Do not call the plan, screenshots, or a failing command a functional result.

The 640 h already includes learning, setup, review, tests, product work, documentation, packaging, and normal bug fixing. A mutually exclusive cost allocation for auditing estimates is: implementation/integration 344 h; learning/reproduction 48 h; tests/evaluation/security 112 h; discovery/use-case validation 56 h; documentation/handoff 48 h; release/operations drills 32 h. Total 640 h. Issue estimates, not this allocation, are the scheduling authority; tag actual time to one category only. Child slices in epic bodies sum to their parent estimate and are not additional issues or hours.

Reserve use: log cause, hours, remaining reserve, and impact in planning/reserve-log.md. Typical causes are dependency changes, parser failure, calibration rework, and restore defects. No reserve is precommitted to extra features. At each milestone compare actual + estimate-to-complete with 800 h. Stop expansion when reserve remaining is below 40 h or forecast exceeds budget. Astra may simplify scope, but may not invent more portfolio hours or silently change the timeline. Additional spending or remote deployment authorization remains a separate user decision.

Gate decisions:

1. M1: proceed if the CPU runtime can be installed under acceptable rights and exact synthetic labels reproduce; otherwise use the structured-only fallback. No downloads of uncleared assets.
2. M2: identify the largest measured error class; continue deterministic baseline or spend only IE-019's bounded alternative budget. A weak OCR score does not justify unbounded training.
3. M3: no silent acceptance of known invalid or conflicting records in the deterministic oracle suite. Fix correctness before interface work passes.
4. M4: corrections invalidate approval and exports; a standards-tool failure blocks UBL output. A local JSON exception workflow may remain usable.
5. M5: release only with the evidence and workflow gates in section 6. If extraction is weak, release a clearly named structured-invoice exception prototype with scan inputs forced to review. No reduced-scope release is described as the full OCR product.
6. M6/M7: without external evidence, finish the reproducible technical candidate and mark market fit and customer performance unvalidated. With evidence, make a bounded pilot decision; payment/posting automation remains excluded.

This project has no clinical or specialist hardware dependency. Assumed baseline hardware is 4 CPU cores, 16 GiB RAM, and 10 GiB free disk; measure it, do not claim it available. If that envelope or OCR licensing is unavailable, fallback is UBL/JSON input plus rules, CSV PO reconciliation, review, and reports on a 2-core/8-GiB target. Retain the same months/budget ceiling, replace affected OCR work with structured workflow checks inside its existing allocation, and require Astra to record the scope change. JSON export is the fallback if standards artifacts cannot be cleared; never call it validated UBL.

## 3. Data, rights, and generation

Existing public human-annotated data is allowed. The constraint is **no new manual dataset collection, labeling, or curation by the user or paid annotators**. Dataset selection must be scripted from declared metadata, hashes, and published splits; no cherry-picking good pages or correcting bad annotations. Report invalid existing labels and exclude them only through a versioned automated validity rule with counts.

The report's suggestion of 50,000–250,000 synthetic pages is intentionally replaced by staged subsets: 50 smoke documents; 240 development documents; then a frozen 1,200-document suite (600 train/development, 200 calibration, 400 untouched test). Up to 3,000 total only if a recorded error analysis justifies it and resource measurements fit the existing budget. No large initial download or model training job. For DocLayNet, stream/select 40 documents first, then at most 200 pages using a deterministic hashed-document order within its published splits; cap transfer at 1 GiB. If selective access is unavailable, record the component evaluation as unavailable instead of downloading the full archive. Public evaluation is useful but not a prerequisite to a synthetic-only technical finish.

Synthetic implementation: a self-authored Python generator uses ReportLab plus a separately cleared redistributable font to render English/Portuguese fictional invoices. Generate the business transaction first with Python Decimal, then an independent label serializer and renderer. Output canonical invoice truth, PO snapshot, expected rule-code set, line/cell IDs, text tokens, boxes, and rendered assets. Use at least 12 self-authored template families, assigned 6/3/3 to train/calibration/test by family before any rendering; keep all derivatives of a base invoice in the same split. New layout families are code, not hand-labeled examples.

Generate both valid and invalid cases: missing required values, malformed dates, one-cent total errors, duplicate identifiers, PO quantity overrun, price mismatch, unknown SKU, mismatched supplier/currency, and unsupported profile values. Retain intended transaction truth separately from printed corrupt values and expected errors. A changed printed value must change the printed-text label. Rules on exact printed values are not OCR failures. Independent arithmetic tests use explicit oracle examples and property checks; the product rule engine must not generate its own expected labels.

Seeded affine rotations/skew, blur, JPEG artifacts, contrast changes, generated stamps, and occlusion create robustness strata. Save transform matrices and transform all box corners; store page-pixel polygons and their bounding boxes. Keep token identity even when occluded, record visibility ratio and an unobservable flag, and exclude deliberately hidden text from visible-token OCR accuracy while including the resulting review requirement in workflow evaluation. Reject cropped/invalid geometry automatically. PDFs have stable metadata/time fields so identical inputs in the pinned environment yield identical hashes. Do not use an LLM to invent supposedly exact boxes or real tax identities.

Every manifest row includes asset_id, sha256, source_kind, source_url, source_revision, license_ref, generator_commit, seed, template_family, base_document_id, split, language, perturbation, label_version, and expected_exception_codes. Keep raw assets and labels separate from inference inputs. Tests must prove inference cannot read truth files. Training is not planned; pretrained OCR weights are used after gating.

### Separate rights gates

Create docs/licenses/ledger.json and dependency notices before using a component. For each exact version/hash record owner, URL, license text snapshot/hash, use (research/evaluation/training/service/distribution), commercial evaluation permission, redistribution conditions, attribution, transitive components, and decision allowed/blocked/unknown. Unknown means blocked for that use. Separate entries are required for source code, model architecture/implementation, model weights, input data, synthetic fonts/templates, standards artifacts, native binaries, and container/runtime images. A permissive Python wrapper does not clear its native binary or weights.

Noncommercial terms are not a default permission for commercial evaluation or R&D. This is a product-oriented project: leave XFUND, DocVQA, and any NC/ambiguous asset out unless the intended use is explicitly cleared. A benchmark-only folder does not solve that rights problem. Existing rights-cleared annotated data is acceptable; no new paid labeling is assumed. Public screenshots and redistribution need their own clearance, even if local evaluation is allowed.

## 4. Concrete implementation defaults and module contracts

Defaults are design choices; exact package versions are selected once at activation after smoke/license checks and committed to lockfiles. Target Python 3.12, FastAPI/Pydantic 2, SQLAlchemy 2 with SQLite migrations, Jinja2 server-rendered HTML with small vanilla JavaScript, pytest, and Playwright browser tests. Use a single service plus one bounded local worker, no Redis/Celery, external LLM API, vector database, or React build chain. Windows local development and a Linux container are the two tested environments.

OCR baseline: Tesseract 5.x CLI with tessdata_fast eng.traineddata and por.traineddata, pinned by source revision and SHA-256; OEM 1, PSM 6 for the first baseline, TSV token boxes/confidence. PDF rendering: pypdfium2/PDFium at 150 DPI, bounded at 200 DPI; embedded-text comparison: pdfplumber/pdfminer.six with word coordinates. Synthetic rendering: ReportLab; transforms: Pillow. These latter choices have **not** had their exact installed distributions/transitive licenses cleared in this planning task. IE-003 and IE-005 must clear them, including bundled native/font assets. Avoid switching to PyMuPDF/Ghostscript implicitly.

One bounded OCR alternative only: Tesseract PSM 3 versus 6, optionally tessdata_best eng/por after a separate weight-rights gate, on the same calibration subset. IE-019 caps alternative implementation/measurement at 12 h. No detector or OCR-free model is required. Table proposals begin as token/line grouping and ruling-line geometry. Baseline learning time includes OCR limitations and standards semantics. A larger model or new runtime requires Astra design review and a budget-neutral change.

Standards default: UBL 2.1 XSD plus pinned OpenPeppol May 2026 Billing 3.0 TC434 and Peppol rules, with a Saxon-HE command-line Java runner for XSLT2-compatible validation. IE-017 must verify the exact Saxon distribution, Java runtime, schema/rule artifacts, compilation path, transitive includes, and all redistribution rights. Prefer publisher-provided compiled artifacts if available and verified; otherwise compile the pinned Schematron with a compatible, separately cleared compiler. Do not assume Python lxml executes XPath/XSLT2 rules. Cache exact local artifacts and forbid network resolution during validation. If this cannot be made reproducible in IE-017, disable UBL export and escalate the documented JSON-only fallback.

All paths below are relative to this standalone repository root. They describe future files, not current implementations.

| Module/path | Interface | Contract and failure behavior |
|---|---|---|
| src/invoice_ops/domain/models.py | Pydantic Asset, Token, FieldValue, InvoiceRevision, Finding, POSnapshot, Decision, ExportReceipt | Strict schema v1; reject unknown business fields; explicit missing values; immutable revisions |
| src/invoice_ops/ingest/service.py | ingest(stream, media_type, idempotency_key) -> Asset | Sniff bytes, size/page caps, content hash; reject malformed/encrypted PDF, archive, path traversal, oversized raster; XML DTD/entities disabled |
| src/invoice_ops/vision/ocr.py | extract(asset, engine_config) -> TokenPage[] | Resource-limited subprocess; timeout returns a typed failure, never an empty successful invoice; no truth-label access |
| src/invoice_ops/extract/invoice.py | parse(tokens_or_xml, profile) -> InvoiceRevision | Header anchors + line grouping; direct namespace-aware UBL adapter; ambiguous candidates remain missing/review, no guessed IDs |
| src/invoice_ops/rules/engine.py | validate(revision, ruleset) -> Finding[] | Pure deterministic functions; fixed codes/severity/field paths; all arithmetic Decimal |
| src/invoice_ops/reconcile/service.py | reconcile(revision, po_snapshot, reservations) -> Finding[] | Exact matching, quantities/prices; stale/missing snapshot is review; no fuzzy auto-match |
| src/invoice_ops/workflow/service.py | assess(id, revision); correct(id, expected_revision, patch, actor, reason); approve(id, expected_revision, actor) | Revalidate every mutation; optimistic concurrency; transactionally audit and reserve quantities |
| src/invoice_ops/export/ubl.py | export(id, expected_revision, format) -> ExportReceipt | Current approved revision only; rerun local standards checks; idempotent, cached bytes and hashes; failures export no UBL |
| src/invoice_ops/storage/repository.py | UnitOfWork, AssetStore, RevisionStore, POStore, AuditStore | SQLite transactions and WAL, foreign keys; files outside web root, migrations; recoverable atomic writes |
| src/invoice_ops/api/app.py; templates/ | HTTP contracts below | UI uses workflow services, no duplicate rules in JavaScript; renders escaped values and evidence |
| src/invoice_ops/synthetic/; eval/ | generate(config); evaluate(manifest, run_config) | Separate truth access; seeded generation, frozen splits, evidence reports and comparison |
| src/invoice_ops/cli.py | invoice-ops subcommands below | Same services as API; stable exit codes and machine-readable results |

### Schema v1

Invoice business fields (25 scalar leaf paths plus repeatable rows): invoice_number, issue_date, due_date, currency, po_number; seller.{id,name,vat_id,street,city,postal_code,country}; buyer.{id,name,vat_id,street,city,postal_code,country}; totals.{net,tax,gross,payable}; tax.{category,rate}. All are required for the supported business profile except due_date and po_number; missing due_date blocks UBL export unless a supported payment-terms alternative is supplied (alternative is excluded in v1, so collect due_date). Missing PO references require an explicitly reviewed no-PO decision, never silently reconciled status. Address/identity facts may come from a versioned organization profile, marked as such rather than falsely attributed to OCR.

Each line has line_id, po_line_id (nullable), sku, description, quantity, unit_code, unit_price, net. At least one and at most 20 lines. Row-level tax inherits the single invoice rate. Dates use ISO-8601; monetary values and quantities are decimal strings, never JSON floats. Money quantizes to 0.01 using ROUND_HALF_UP; unit prices allow four decimals, quantities three; line net rounds quantity × price, invoice net sums rounded lines, VAT rounds invoice net × rate / 100, gross = net + tax, payable = gross. This supported arithmetic is checked against pinned standards cases, not assumed sufficient for other tax profiles. Default PO price tolerance is zero after declared precision normalization; quantity cannot exceed ordered minus committed reservations. No blanket one-cent tolerance hides discrepancies.

FieldValue = {value: string|null, raw_text: string|null, source: ocr|pdf_text|ubl|profile|review, evidence: EvidenceRef[], confidence_raw: number|null, confidence_calibrated: number|null, status: present|missing|ambiguous}. EvidenceRef = {asset_id, page: integer>=1|null, polygon_px: number[][]|null, xpath: string|null, profile_revision: string|null}. Pixels are in the rendered page's top-left coordinate system; page width/height and transforms live on Asset. XML uses XPath evidence; review adds evidence without deleting the original.

InvoiceRevision = {schema_version:'1', invoice_id, revision, asset_id, fields, lines, profile_revision, po_snapshot_id|null, extractor_version, created_at}. Finding = {code, severity: blocking|review|info, field_paths: string[], message, observed, expected, evidence_refs, ruleset_version}. Codes include MISSING_REQUIRED, UNSUPPORTED_PROFILE, ARITHMETIC_MISMATCH, DUPLICATE_CANDIDATE, PO_NOT_FOUND, PO_LINE_AMBIGUOUS, PO_OVER_QTY, PO_PRICE_MISMATCH, SUPPLIER_MISMATCH, CURRENCY_MISMATCH, LOW_CONFIDENCE, STANDARD_FAILURE, VALIDATOR_UNAVAILABLE. Stable code and path, not prose text, identify a finding.

Organization export profile supplies customization_id, profile_id, seller/buyer endpoint IDs and scheme IDs, and payment means code; schema stores source revision and effective date. These values must be explicitly configured and validated; do not fabricate them from invoice appearance. Party identifiers in fixtures are fictional. Invoice type code is 380; country codes and unit codes must be in pinned supported lists. Schema rejects out-of-profile UBL rather than discarding unrecognized financial constructs.

POSnapshot = {snapshot_id, sha256, created_at, currency, supplier_id, po_number, lines:[{po_line_id,sku,ordered_qty,already_invoiced_qty,unit_price}]}. CSV uses those column names plus schema_version; validate every row before committing a snapshot. Duplicate keys and negative outstanding quantities reject the entire import. Each import supersedes a prior snapshot explicitly; reconcile local reservations against the new snapshot without counting acknowledged exports twice.

Persistence tables: assets(id,sha256 UNIQUE,media_type,path,page_count); jobs(id,asset_id,status,attempts,error_code); invoices(id,active_revision,status); revisions(invoice_id,revision,payload_json,sha256, UNIQUE(invoice_id,revision)); findings(invoice_id,revision,code,path,payload_json); po_snapshots(id,sha256,payload_json); reservations(invoice_id,revision,po_snapshot_id,po_line_id,quantity,status); audit_events(sequence,actor,action,invoice_id,revision,reason,at,payload_hash); exports(id,invoice_id,revision,format,sha256,path, UNIQUE(invoice_id,revision,format)); idempotency_keys(key,request_hash,response_json). SQLite audit is append-only by application contract, not tamper-proof against a database administrator. Foreign keys and transactional tests enforce revision consistency.

Workflow: received -> processing -> needs_review or ready_for_review; reviewer approval -> approved; successful export -> exported. Parse/resource errors -> failed; invalid/unsupported inputs -> rejected. Human approval is mandatory for every export in v1, including high-confidence cases. Internal eligibility metrics do not authorize payment or remove this gate. Corrections produce a new revision, release stale reservations where appropriate, invalidate approval and previous export eligibility, and return to review. Existing exported bytes remain historical; replacement exports are explicitly superseding, never silently overwritten. Approve/reserve/export concurrency is covered by one transaction boundary and unique keys; no duplicate PO consumption on retry.

### API and commands to implement

HTTP: POST /api/assets (multipart, Idempotency-Key; 202 + job_id); GET /api/jobs/{id}; GET /api/invoices/{id}; POST /api/po-snapshots; PATCH /api/invoices/{id}/revisions (expected_revision, field patch, reason); POST /api/invoices/{id}/approve (expected_revision); POST /api/invoices/{id}/exports (expected_revision, format); GET /api/exports/{id}; GET /healthz; GET /readyz. Return 409 for stale revision/idempotency-body conflicts, 413 for input cap, 422 for invalid schema/profile, 503 for unavailable validation/runtime. Failed business checks are findings, not HTTP 500. Export requests with unresolved blocking/review findings return 409. A no-PO disposition requires a reason and remains visible in the report.

Local mode binds 127.0.0.1, uses a generated local session secret and CSRF protection, and limits file reads to the asset store. Public demo mode only accepts bundled fixture IDs and uses per-session disposable stores, limits sessions/processing, and never exposes general upload or profile-edit endpoints. Public deployment is a later authorized release action, not part of this planning task.

Planned commands (not runnable yet):

```text
python -m venv .venv
python -m pip install --require-hashes -r requirements.lock
python -m invoice_ops.cli doctor --licenses docs/licenses/ledger.json
python -m invoice_ops.cli synth --config configs/smoke.yaml --out data/generated/smoke
python -m invoice_ops.cli eval --manifest data/manifests/calibration.jsonl --config configs/baseline.yaml --out reports/baseline
python -m invoice_ops.cli import-po --csv examples/po.csv
python -m invoice_ops.cli ingest --input examples/invoice.pdf --json
python -m invoice_ops.cli assess --invoice-id DEMO_ID --revision 1 --json
python -m invoice_ops.cli approve --invoice-id DEMO_ID --revision 1 --actor local-reviewer
python -m invoice_ops.cli export --invoice-id DEMO_ID --revision 1 --format ubl --out artifacts/demo
python -m invoice_ops.cli serve --host 127.0.0.1 --port 8000
python -m invoice_ops.cli demo --fixtures examples/demo --offline
python -m invoice_ops.cli backup --out artifacts/backup
python -m invoice_ops.cli restore --input artifacts/backup --target artifacts/restore-test
python -m pytest -q
python -m pytest -m acceptance -q
docker compose -f deploy/compose.yaml up --build
```

README at implementation time must include shell-specific environment activation, OCR/Java installation, hash verification and pinned version commands. No network installs at inference time. CLI exit codes: 0 completed without blockers, 2 schema/unsupported input, 3 review/blocking findings, 4 infrastructure/validator unavailable. Evaluation exits nonzero when the requested gate fails; it always writes the measured report with reasons.

## 5. Independent evidence streams and metrics

Freeze configs/evaluation.yaml before tuning and preserve denominator counts, missing cases, raw predictions, hardware, elapsed time, dependency hashes, and run IDs. Report confidence intervals, not just point scores. Bootstrap by base document/template, not by correlated tokens; use Wilson 95% intervals for proportions. If strata have too few independent templates, say so. A frozen test set is opened at M5 and again only for a documented final regression, never used as a tuning set; changed models require a new automatically generated family holdout and explicit comparison.

| Stream | Data and objective | What it does not establish |
|---|---|---|
| Synthetic robustness | Exact generated truth; controlled layout/scan shift; business-rule precision/recall and workflow correctness | Frequency of real supplier failures or customer accuracy |
| Public-data component evaluation | Rights-cleared DocLayNet published boxes; table-region proposal precision/recall at IoU 0.5, grouping by document; preserve official split | Invoice field accuracy, tax correctness, PO matching, customer benefit |
| Actual customer/use-case validation | Optional AP practitioners completing fictional tasks and describing workflow; later separately permitted real-world pilot if available | Synthetic/public benchmark results cannot substitute for this stream |

Baseline B0: OCR + fixed anchors/regular expressions and line grouping, no learned extractor. Baseline B1: exact structured invoice/PO input through independent arithmetic/reconciliation rules; this isolates business logic from OCR. Product comparison holds OCR/parser constant and compares B0 extraction-only review against the full exception workflow on the same ten fictional tasks. Report field exact-match, critical-field precision, table row accuracy, exception precision/recall per code, missed critical exceptions, unnecessary review rate, evidence-box overlap, eligible-document coverage, review time, actions per task, p50/p95 latency, peak RSS, and measured cost/page (local power cost unknown unless measured; no invented dollar figure).

Predeclared engineering targets, not measured facts:

- Deterministic rule/PO golden suite: all expected codes and statuses correct; zero accepted critical-invalid fixtures. At least ten generated cases per core code and explicit one-cent/locale/duplicate/retry/concurrency boundaries.
- Synthetic test: 400 base documents, including at least 100 critical-invalid examples distributed over rule classes, and at least 100 valid clean and 100 valid degraded examples. Remaining cases exercise unsupported/missing/ambiguous inputs. Families and base IDs remain disjoint. Rejection quality reported by stratum; ≥95% precision and ≥95% recall for detectable core exceptions, with CIs and sample counts; uncertain/occluded cases must request review.
- High-confidence internal eligibility: ≥100 evaluated eligible documents and Wilson 95% lower bound ≥0.95 for jointly correct critical fields (invoice_number, seller.id, currency, net, tax, gross, payable) plus no blocking findings; coverage target ≥20%. If insufficient admissions or accuracy, disable high-confidence eligibility and route all to review. Human approval remains required regardless. A narrow held-out synthetic result is never labeled real invoice reliability.
- Clean synthetic critical-field exact-match target ≥95%; degraded ≥80%, separately reported. Missing/ambiguous values count as errors for extraction metrics and as safe abstentions for workflow metrics. No claim that abstention alone is accurate extraction.
- CPU p95 target ≤20 seconds/page on 150-DPI inputs, peak RSS ≤4 GiB for one job; hard per-document timeout 90 seconds and two automatic attempts maximum. Record actual hardware. Missed speed target triggers explicit limitation or structured-only fallback, not a falsely passing run.
- Public component scores are descriptive, with no invoice-product pass threshold. If rights/access fails, publish “not evaluated,” never “passed.”
- Workflow study target, conditional on optional participants: three practitioners each complete ten fictional tasks with counterbalanced baseline/product order; ≥20% median time reduction, no critical incorrect resolution, and understandable explanations. Participant sample is small and exploratory. Without participants, timed maintainer rehearsal tests usability mechanics only, labeled internal; no market-validated claim.

Functional v0.1 gate: clean checkout/container can ingest a bundled supported invoice, show evidence and at least one deliberate exception, import a PO, correct a field, re-run checks, approve, and export a passing UBL (or expressly named JSON-only fallback). Another bundled invalid invoice must refuse export. Audit/retry/restore smoke tests pass. Publish the exact commands, hashes, limits, failures, and evaluation report. Accuracy targets may force all-review mode, but correctness/security gates may not be waived. No exception findings may be hidden to meet a target.

## 6. Deployment, operations, and product validation

v0.1 public result: tagged source/reproducible container with synthetic fixtures, a scripted local browser demo, accessible walkthrough, and evaluation report. This is a functional public deliverable without paid hosting. If separately authorized, the same container can run a fixture-only hosted demo; no cloud account, monthly fee, or credentials are required to finish the plan. Pin runtime image digest and list tested resource limits. IE-021 budgets packaging and deployment rehearsal; optional hosted setup must fit that allocation.

Use SQLite plus a local artifact directory, transactional revision/export IDs, job restart recovery, max two retries with a recorded failure, and no automatic repeated processing of poisoned inputs. Scrub invoice contents from logs; log request_id, rule codes, stage durations, model/rule versions, counts, and asset hash only. Demo resets disposable state after each session; local retention defaults to explicit operator deletion after export, with a documented purge command and seven-day rolling backups. Audited retention decisions must explain that deleted data may remain in backups until expiry. Backup and restore run offline, including hash comparison and schema compatibility; backup access is as sensitive as source invoices.

Track queue depth, job failure rate, p95 latency, eligibility coverage, reviewer corrections, and ruleset version. Monitor a fixed generated canary corpus on each build. Real-world drift cannot be claimed without real-world traffic; canary failures are software/fixture regressions. Standards/dependency updates are staged against pinned fixtures, reviewed for rights, and released deliberately, not silently pulled from moving URLs. Rollback retains compatible data or restores a tested backup; destructive migrations require explicit review.

Product discovery continues at M6: test whether exception explanations, PO matches, and exports fit a plausible AP workflow. Use optional interviews and task observation without soliciting private documents. Record respondent roles, consent, task script, measurements, counterexamples, and unmet requirements. A later customer pilot with private data needs separate permission, data-processing terms, a retention plan, and domain validation; it is outside this technical critical path and cannot be a hidden month-12 dependency.

Month-12 decision categories: (a) technical candidate complete, commercial evidence absent; (b) technical candidate plus exploratory external workflow evidence, bounded pilot justified; (c) scoped prototype only, full product not demonstrated; (d) stop because correctness/rights/resource gates remain unmet. Revenue, legal compliance, willingness to pay, and production ROI remain conditional until supported. Publish a candid decision; do not turn lack of customer access into an indefinite engineering task.

## 7. Implementer protocol and definition of done

The backlog is authoritative for package IDs, hours, dependencies, milestones, and evidence. Choose the lowest-numbered unblocked package whose dependencies are done; one active package at a time. Epics >12 h contain explicit 2–12 h child slices in their bodies. Complete and review one slice at a time; do not add those slices as separately budgeted work. Parent-provided AGENTS.md applies; do not create a project replacement.

Luna medium or GPT-5.6 medium may implement scoped interfaces, tests, fixtures, and documentation without repeated permission prompts. For each slice, read only relevant contracts and prerequisite evidence, state a brief plan, implement, run the named checks, inspect outputs, and record a compact handoff. Continue routine reversible work within scope. No architecture substitution, private-data dependency, new paid service, additional model, changed financial arithmetic, loosened security gate, or expanded schedule without Astra high review. If an action also needs new user authority (for example external messages or spending), prepare the concrete proposal first and ask only for that authority.

Definition of done: named outputs exist; precise acceptance assertions pass on the declared environment; rights gate passed for each used artifact; tests and run IDs are captured; no required gate is silently skipped; limitations/metrics are honest; docs/CLI agree; review evidence is stored in planning/evidence/IE-NNN.md. Use a short status record there (status, slice, changed paths, commands, results, artifact hashes, actual hours, remaining estimate, unresolved risks, next issue). A separate reviewer inspects the diff and failure-path evidence; the implementer cannot mark an unrun check as passed. No hidden time beyond the issue estimate: review/test/documentation time is included in slices.

Blocked policy: distinguish external rights/access, deterministic test failure, missing prerequisite, and design uncertainty. After one bounded reproduction and one safe alternative (at most 2 h charged to the current issue), write the minimal failing command, evidence, impact, and recommended fallback in its evidence file. Continue an independent ready slice if available. Do not bypass a license gate, fabricate a passing result, keep retrying a remote service, or require manual invoice annotation. Escalate architecture or budget changes to Astra; keep the affected package blocked until the decision is recorded in docs/decisions/. Optional absent participants/public data are recorded as unavailable evidence, not a blocker to synthetic technical completion.

Handoff packet: issue/slice IDs; current branch/commit or local diff reference; allowed paths; invariant summary; inputs with hashes and license decisions; exact reproducer; tests passed/failed/not run; remaining hours; decision requested (if any); next safe step. Astra returns a concrete decision and updated acceptance/budget if needed. Later remote publication is performed only under the activation/release workflow's authority, never inferred from this planning document.

## 8. Checked primary sources and remaining assumptions

Read-only source checks performed during this planning session, 2026-10-19/20. Moving URLs must be pinned and rechecked at activation. These are narrow checks, not a completed dependency/license audit.

| Source | Checked fact and design consequence |
|---|---|
| [DocLayNet repository](https://github.com/DS4SD/DocLayNet) and [license text](https://raw.githubusercontent.com/DS4SD/DocLayNet/main/LICENSE) | Human-annotated page-layout boxes and published splits; CDLA-Permissive 1.0. Preserve required notices/attribution and modified-data notices. It is layout evidence, not invoice-field truth. |
| [OpenPeppol Billing 3.0](https://docs.peppol.eu/poacc/billing/3.0/) | Page identifies May 2026 release and links UBL syntax, code lists, TC434 and Peppol Schematron. Availability does not settle redistribution rights or jurisdictional compliance; artifact/runtime clearance remains IE-003/017. |
| [Tesseract repository](https://github.com/tesseract-ocr/tesseract) and [engine license](https://raw.githubusercontent.com/tesseract-ocr/tesseract/main/LICENSE) | Engine source carries Apache-2.0. Exact installed binary and dependencies still require inventory. |
| [tessdata_fast](https://github.com/tesseract-ocr/tessdata_fast) and [weight repository license](https://raw.githubusercontent.com/tesseract-ocr/tessdata_fast/main/LICENSE) | Separate pretrained fast LSTM model repository with Apache-2.0 license text. Pin/check actual eng/por assets independently from engine code. |
| [Creative Commons BY-NC-SA 4.0 deed](https://creativecommons.org/licenses/by-nc-sa/4.0/) | Noncommercial restriction exists. This plan does not infer permission for product-directed evaluation/R&D from public availability. |

Unverified assumptions to resolve in budgeted work: hardware availability/performance (IE-005/019); exact runtime/transitive/font/standards licenses (IE-003/005/017); public subset selective download support (IE-011); quality of Portuguese OCR (IE-012/019); sufficient realism of synthetic layouts (IE-007/020, cannot prove customer performance); AP demand and workflow fit (IE-002/025); actual hosting authorization/cost (optional, IE-021); exact support of generated profile by the standards validator (IE-017/018). Neither a public benchmark nor the source report resolves these assumptions.
