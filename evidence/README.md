# Evidence policy

Production evidence is intentionally not stored in this repository.

## Evidence model used in the QA engagement

Select the smallest artifact that proves the claim:

- **Direct UI:** screenshot or continuous video showing the causal interaction and resulting state;
- **Before/after:** two states with the same synthetic data and clearly recorded viewport;
- **Network:** safe HTTP status/error code and generalized route, with headers, payloads, IDs, and secrets removed;
- **Console/runtime:** relevant error or state transition, with user data and identifiers redacted;
- **Download validation:** file type, openability, and structural checks without uploading client data.

## Naming pattern

Synthetic names such as `BUG-XXX_01_UI.png`, `BUG-XXX_02_NETWORK.txt`, or `E2E-XXX_01_FINAL.png` are examples only. No production artifact is included here.

## Redaction rules

Never store credentials, authorization material, cookies, reset links, raw request identifiers, personal data, client URLs, or production screenshots. Replace values with placeholders such as `{user_id}`, `{integration_id}`, `{request_id}`, and `qa.user@example.test` before any artifact is considered for publication.

The `.gitignore` also prevents common local screenshots, videos, HAR files, logs, and secret files from being committed accidentally.

