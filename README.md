# AI SaaS Platform — Commercial QA Project

> Sanitized documentation from a real paid production QA engagement covering AI dialogs, custom agents, campaign generation, integrations, persistence, responsive behavior, and real-device validation.

<div align="center">

[![Commercial QA](https://img.shields.io/badge/Commercial_QA-Paid_Engagement-8B5CF6?style=for-the-badge)](docs/project-overview.md)
[![Manual QA](https://img.shields.io/badge/Manual_QA-Regression_%26_E2E-4B5563?style=for-the-badge)](docs/qa-scope.md)
[![Chrome](https://img.shields.io/badge/Chrome-DevTools-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white)](docs/responsive-cross-browser.md)
[![iOS](https://img.shields.io/badge/iPhone-Safari-000000?style=for-the-badge&logo=apple&logoColor=white)](docs/responsive-cross-browser.md)
[![OpenAPI](https://img.shields.io/badge/OpenAPI-Integrations-6BA539?style=for-the-badge&logo=openapiinitiative&logoColor=white)](docs/e2e-scenarios.md)

</div>

| Engagement | Role | Coverage | Evidence |
|---|---|---|---|
| Paid commercial QA · production-safe execution | **QA Engineer** | Functional · E2E · regression · exploratory · responsive · integrations | UI/runtime · Network · Console where relevant · retest records |

**Start here:** [project overview](docs/project-overview.md) · [QA scope](docs/qa-scope.md) · [E2E scenarios](docs/e2e-scenarios.md) · [selected defects](bugs/) · [sanitization rules](SANITIZATION.md)

## Product surface tested

The product was an AI SaaS web platform with multiple connected user flows. The public repository intentionally omits the client and product identity while preserving the technical QA work.

- authentication and protected-area navigation;
- ready-made AI specialists, dialogs, history, and runtime states;
- custom AI agent configuration and lifecycle;
- campaign generator steps, edit/reload persistence, preview, and safe export;
- custom HTTP/OpenAPI-style integrations and authentication semantics;
- permissions, disabled states, and read-only administration flows;
- external-error mapping and recovery states;
- responsive behavior, cross-browser coverage, and real-device mobile checks.

## QA approach

Testing combined manual functional, negative, smoke, regression, exploratory, end-to-end, responsive, cross-browser, real-device, persistence/reload, runtime, and safe integration validation.

Every FAIL required current-run evidence appropriate to the problem: UI state, before/after sequence, Network status, Console/runtime observation, or another direct artifact. Retest and affected regression were recorded separately so a targeted fix verification was not presented as full release approval.

Automation, load/performance, and security testing are not claimed because they were not part of this commercial QA engagement.

## Selected defect classes

| Defect | Area | What was validated |
|---|---|---|
| [BUG-001](bugs/BUG-001-agent-config-persistence.md) | Custom AI agent | saved configuration persisted and affected a new dialog |
| [BUG-002](bugs/BUG-002-integration-auth-none.md) | Integration contract | `auth:none` did not request nonexistent credentials |
| [BUG-003](bugs/BUG-003-generator-reload-duplication.md) | Generator persistence | reload no longer duplicated the active prompt |
| [BUG-004](bugs/BUG-004-notification-history.md) | Event history | a new event did not replace an earlier archive item |
| [BUG-005](bugs/BUG-005-api-error-mapping.md) | Error handling | permanent external failure was mapped to the correct SaaS-side message |
| [BUG-006](bugs/BUG-006-responsive-layout.md) | Responsive UI | status and close controls remained independently usable at narrow widths |

The reports are rewritten public examples of real defect classes. Client-specific wording, identifiers, URLs, screenshots, provider account details, and production evidence were removed.

## Execution snapshot

- **150+** manual test cases executed;
- **20+** defects documented, with retest where verification was possible;
- P0/P1 risk coverage across authentication, AI runtime, custom agents, integrations, generator, and responsive/mobile flows;
- Chrome, Firefox, mobile emulation, and real iPhone Safari coverage;
- targeted affected regression after fix batches.

The source snapshot represents an interim QA cycle. The final regression gate had not yet been run, so this repository does not claim blanket production approval.

## Environments

- Chrome desktop at 1920×1080 and 1440 px;
- Firefox desktop;
- Chrome Device Mode at 390 px and 768 px;
- real iPhone Safari in portrait orientation.

Production-safe QA data and reversible actions were used. Real payments, independent testing of external services, destructive third-party OAuth/export/bid/campaign actions, and state-changing global administration operations were outside scope.

## Tools and techniques

Chrome DevTools · Network · Console · Firefox · real iPhone Safari · responsive/device emulation · Google Sheets QA documentation · HTTP/OpenAPI-style fixtures · manual E2E/regression testing.

## Repository structure

```text
docs/          project context, scope, regression, E2E, exploratory, responsive, retest
test-cases/    representative sanitized checks, not a full client test suite
bugs/          selected sanitized defect reports
templates/     reusable QA working templates
evidence/      evidence policy; no production screenshots or raw artifacts
```

## Confidentiality and publication

This repository contains no client or product name, production domain, customer data, production screenshots, Drive/Sheets links, internal IDs, credentials, cookies, authorization material, or raw request identifiers.

The repository is a sanitized public-facing snapshot of the QA work, not an export of the client's internal tracker. See [SANITIZATION.md](SANITIZATION.md) for publication rules and the confidentiality review checklist.

No open-source license is granted for reuse of the commercial QA documentation in this repository.