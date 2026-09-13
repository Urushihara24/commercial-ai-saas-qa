# BUG-005 — Permanent external access error was mapped to a temporary retry message

- **Severity:** Minor
- **Priority:** P2
- **Environment:** Production-safe QA run; Firefox desktop; generator semantic-analysis step.
- **Preconditions:** The external provider returns a known permanent access/tariff error; the SaaS flow receives the provider status safely.

## Steps to Reproduce

1. Start the generator step that depends on the external provider.
2. Allow the provider to return the permanent access/tariff error.
3. Record the safe external status/error code.
4. Compare the UI message with the actual error class.

## Expected Result

The SaaS explains that the provider is unavailable for the current access level or configuration and gives an actionable next step. A retry-later message is not used for a permanent condition.

## Actual Result

The UI presented a temporary-unavailability message suggesting that the user should try again shortly, although the provider response represented a permanent access/tariff limitation.

## Evidence Strategy

Capture the UI message together with the safe HTTP status and error code only. Do not test or publish the external service itself, raw response bodies, request IDs, credentials, or provider account details.

## Retest Result

**PASS — error mapping verified.** The SaaS now distinguishes the permanent external limitation and presents a corresponding message. The external limitation itself remains outside the product QA scope.

## What this defect demonstrates

Error taxonomy, product-side integration boundaries, safe network evidence, and the distinction between an external known limitation and a product defect in error handling.

