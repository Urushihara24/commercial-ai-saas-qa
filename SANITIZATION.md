# Sanitization policy

This repository is based on a real paid commercial QA engagement for an AI SaaS web platform.

## Applied rules

- product and company names were removed;
- URLs were generalized or omitted;
- internal IDs were replaced with synthetic identifiers;
- screenshots and videos were omitted or described without copying client evidence;
- personal and business information was removed;
- credentials and secrets were never included;
- selected technical implementation details were generalized;
- metrics were rounded/generalized where exact values could create a project fingerprint;
- external provider names were replaced with generic descriptions;
- production-safe scope boundaries were retained without exposing client-specific data.

No proprietary production data is intentionally included.

## Review checklist

Before publication, the working tree and every commit were checked for:

- client/company/product identifiers;
- real domains and Drive/Sheets URLs;
- email addresses, phone numbers, physical addresses, and business registration data;
- user, agent, campaign, integration, chat, request, and correlation identifiers;
- cookies, authorization material, credentials, secrets, reset links, and autofill values;
- production screenshots, client evidence, blob URLs, and client-specific filenames;
- raw payloads or values that could identify the customer.

Only synthetic placeholders remain, for example `{integration_id}`, `qa.user@example.test`, and `POST /api/integrations/{integration_id}/connect`.

## Publication rule

This repository must remain **private** until the owner completes a manual confidentiality review. Any future addition of evidence must use a redacted, synthetic artifact and must be reviewed before commit.

