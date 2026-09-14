# Sanitization policy

This repository is based on a real paid commercial QA engagement for an AI SaaS web platform. It is intentionally maintained as a sanitized public-facing snapshot rather than as an export of the client's internal QA workspace.

## Applied rules

- client, company, and product names are removed;
- production domains and internal routes are omitted or generalized;
- internal IDs are replaced with synthetic identifiers;
- screenshots, videos, HAR files, logs, and raw production evidence are not stored here;
- personal, customer, and business information is removed;
- credentials, cookies, authorization material, reset links, and secrets are excluded;
- provider-specific account details are generalized;
- selected implementation details are generalized where they could identify the product;
- metrics are rounded/generalized where exact values could create a project fingerprint;
- production-safe scope boundaries are retained without exposing client-specific data.

No proprietary production data is intentionally included.

## Public-release review checklist

The current `main` tree was reviewed for:

- client/company/product identifiers;
- production domains and client-specific URLs;
- Drive/Sheets links and internal document identifiers;
- email addresses, phone numbers, physical addresses, and business registration data;
- user, agent, campaign, integration, chat, request, and correlation identifiers;
- cookies, authorization material, credentials, secrets, reset links, and autofill values;
- production screenshots, videos, HAR files, logs, blob URLs, and client-specific filenames;
- raw payloads, headers, provider-account details, or values that could identify the customer.

Only synthetic or generalized values should remain. Examples include `{integration_id}`, `qa.user@example.test`, and generalized HTTP/OpenAPI-style routes.

## Repository-history note

The active `main` branch was created as a sanitized documentation repository rather than by importing the client's working repository. No raw production evidence is present in the current tree. Publication should still be treated as a confidentiality decision: technical sanitization does not replace any contractual or client-approval requirement that may apply to the engagement.

## Publication status

The current sanitized tree is prepared for public release. Before changing repository visibility, the owner should confirm that publication is permitted by the commercial agreement or client expectations.

Any future addition of evidence must use a redacted or synthetic artifact and must repeat the confidentiality review before commit.
