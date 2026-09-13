# Commercial AI SaaS — QA Portfolio Project

<div align="center">

[![Manual QA](https://img.shields.io/badge/Manual_QA-Regression_%26_E2E-4B5563?style=for-the-badge)](docs/qa-scope.md)
[![Chrome](https://img.shields.io/badge/Chrome-DevTools-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white)](docs/responsive-cross-browser.md)
[![Firefox](https://img.shields.io/badge/Firefox-Cross_Browser-FF7139?style=for-the-badge&logo=firefoxbrowser&logoColor=white)](docs/responsive-cross-browser.md)
[![iOS](https://img.shields.io/badge/iPhone-Safari-000000?style=for-the-badge&logo=apple&logoColor=white)](docs/responsive-cross-browser.md)
[![OpenAPI](https://img.shields.io/badge/OpenAPI-Integration_Fixtures-6BA539?style=for-the-badge&logo=openapiinitiative&logoColor=white)](docs/e2e-scenarios.md)

</div>

This repository presents sanitized artifacts from a real paid commercial QA engagement for an AI SaaS web platform.

## My role

QA Engineer

## What I tested

- authentication and protected-area navigation;
- AI dialogs, saved history, and runtime states;
- custom AI agent configuration and lifecycle;
- campaign generation and persistence after reload;
- custom HTTP-style integrations;
- permissions, disabled states, and read-only administration flows;
- error mapping and recovery states;
- responsive behavior, cross-browser coverage, and real-device mobile checks.

## Testing types

Manual functional, negative, smoke, regression, exploratory, end-to-end, responsive, cross-browser, real-device, persistence/reload, runtime, and safe integration validation.

Automation, load/performance, and security testing are not claimed here because they were not part of the source QA engagement.

## Environments

- Chrome desktop at 1920×1080 and 1440 px;
- Firefox desktop;
- Chrome Device Mode at 390 px and 768 px;
- real iPhone Safari in portrait orientation.

The source QA scope used production-safe test data and excluded destructive third-party actions, real payment execution, external-service testing, and state-changing administrative mutations.

## Defect lifecycle

Each defect was evaluated through Expected vs Actual, severity and priority, reproducible steps, evidence strategy, fix verification, and affected regression. A known external limitation was kept distinct from a defect in the SaaS product's own error handling.

## Selected defects

The public examples cover configuration persistence, integration authentication semantics, reload duplication, notification history, external-error mapping, and narrow-viewport layout. They are rewritten examples of real defect classes; identifiers, URLs, screenshots, and client-specific wording were removed.

## Results

- 150+ manual test cases executed;
- 20+ defects documented and taken through retest where applicable;
- P0/P1 regression coverage across core user journeys;
- desktop, tablet, mobile, Firefox, and real iPhone Safari coverage;
- direct UI/runtime and network-observation evidence collected during the engagement.

The source snapshot was an interim QA cycle, not a release sign-off: the final regression gate had not been run at the time of the snapshot. This repository preserves that limitation instead of presenting the work as a blanket production approval.

## Tools and techniques

Chrome DevTools, Network inspection, Console inspection when relevant, responsive/device emulation, Firefox, real iPhone Safari, Google Sheets QA documentation, HTTP/OpenAPI-style fixtures, and manual E2E/regression testing. Git/GitHub is used here only to publish a sanitized portfolio artifact.

## Repository structure

```text
docs/          project context, scope, regression, E2E, exploratory, responsive, retest
test-cases/    representative samples, not a full client test suite
bugs/          selected sanitized defect reports
templates/     reusable QA working templates
evidence/      evidence policy; no production screenshots
```

## Confidentiality and sanitization

This repository contains no client name, product URL, customer data, production screenshots, Drive/Sheets links, internal IDs, credentials, or raw request identifiers. See [SANITIZATION.md](SANITIZATION.md) for the review rules applied before publication.
