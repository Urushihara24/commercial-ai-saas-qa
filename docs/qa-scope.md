# QA Scope

## In scope

| Area | Coverage |
| --- | --- |
| Public/auth | guest access, registration/login, protected areas, logout |
| AI dialog | message submission, terminal response, history, reopen, runtime states |
| Custom agents | creation, editing, persistence, integration binding, disabled-state lifecycle |
| Generator | campaign steps, edit/reload persistence, preview, safe export |
| Integrations | specification handling, connection flow, auth semantics, state persistence |
| Admin read-only | list loading, opening existing objects, log visibility, export |
| Responsive | 390, 768, 1440, and 1920 px; overflow, clipping, controls, dialogs |
| Browsers/devices | Chrome, Firefox, Chrome Device Mode, real iPhone Safari |
| Defect flow | Expected/Actual, severity, priority, evidence, retest, affected regression |

## Environments

- Desktop Chrome: 1920×1080 and 1440 px responsive width.
- Desktop Firefox: cross-browser smoke and risk-based user flows.
- Chrome Device Mode: 390 px and 768 px.
- Real iPhone Safari: native portrait mobile smoke and critical workflow checks.

Exact OS/browser versions and client-specific test data are intentionally omitted.

## Out of scope

- security audit;
- load/performance testing;
- independent testing of third-party services;
- real payment execution or payment-gateway operations;
- destructive third-party OAuth/export/bid/campaign actions;
- state-changing admin CRUD, role mutation, and global billing/pricing changes;
- dedicated desktop Safari testing;
- test automation not evidenced by the source QA engagement.

An external service outage was not automatically classified as a product defect. The QA scope covered the SaaS product's handling of that state and the clarity of the user-facing message.

## Status model

- **PASS** — Expected was directly confirmed.
- **FAIL** — Expected was violated; current evidence and a linked defect exist.
- **BLOCKED** — the scenario cannot be completed because of a confirmed blocker or missing mandatory dependency.
- **SKIPPED** — deliberately excluded from scope with an explicit reason.
- **NOT RUN** — not yet executed and not blocked by a confirmed dependency.

## Production safety

Testing used QA-owned data and reversible actions. Paid/consumptive AI checks were performed only within the allowed safe QA scope. Real payments, third-party production data, and irreversible external actions were not executed.
