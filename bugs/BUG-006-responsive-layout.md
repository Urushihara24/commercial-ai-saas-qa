# BUG-006 — Narrow viewport crowded status and close controls in an integration form

- **Severity:** Minor
- **Priority:** P2
- **Environment:** Production-safe QA run; responsive checks at 390 px, 768 px and 1440 px; desktop and mobile emulation.
- **Preconditions:** The custom integration form is open with a visible draft/status badge and close control.

## Steps to Reproduce

1. Open the integration form.
2. Set the viewport to a narrow supported width.
3. Inspect the form header and the hit area of the status badge and close control.
4. Repeat at the wider responsive checkpoints.

## Expected Result

Status and close controls are visually separated, readable, and independently clickable. No clipping, overlap, or ambiguous hit area is present.

## Actual Result

At the affected layout state, the status and close affordance were crowded or visually insufficiently separated, reducing clarity and increasing the risk of an accidental close action.

## Evidence Strategy

Capture redacted screenshots at the affected viewport and record measured rectangles/overlap as supporting UI evidence. Do not include client branding, account details, or production screenshots in the public repository.

## Retest Result

**PASS — responsive fix verified.** The status badge and close control had separate hit areas with no measured overlap at the checked responsive widths.

## What this defect demonstrates

Responsive QA beyond page load, control-level layout checks, viewport-specific evidence, and verification of interaction safety in modal forms.

