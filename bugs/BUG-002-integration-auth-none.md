# BUG-002 — `auth:none` integration incorrectly required credentials

- **Severity:** Major
- **Priority:** P1
- **Environment:** Production-safe QA run; Chrome desktop; current supported viewport.
- **Preconditions:** A safe HTTP-style integration specification declares that no authentication is required.

## Steps to Reproduce

1. Open the custom integration form.
2. Select the no-authentication mode.
3. Provide the safe specification using a synthetic endpoint such as `POST /api/integrations/{integration_id}/connect`.
4. Start the connection flow.

## Expected Result

The platform submits the no-authentication integration without requesting a credential that the specification does not define.

## Actual Result

The connection flow requested credential input and stopped even though the selected authentication mode was `auth:none`.

## Evidence Strategy

Record the selected auth mode, the visible validation message, and safe HTTP status/error metadata. Redact all payloads, headers, secrets, cookies, and identifiers. The external endpoint itself is not tested as an independent service.

## Retest Result

**PASS — fix verified.** A clean no-authentication flow completed without credential input. The previously blocked agent-binding path was then checked separately.

## What this defect demonstrates

Contract-oriented integration testing, safe API observation, negative-path validation, and separation of auth semantics from binding persistence.

