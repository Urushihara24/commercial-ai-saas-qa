# Responsive and Cross-Browser Coverage

## Environment matrix

| Environment | Coverage | Observation |
| --- | --- | --- |
| Chrome desktop, 1920×1080 | functional baseline, dialog, generator, admin read-only | primary desktop baseline |
| Chrome desktop, 1440 px | responsive desktop, modal/header, integrations | layout and hit-area validation |
| Chrome Device Mode, 768 px | tablet layout, dialog, generator, forms | wrapping and control accessibility |
| Chrome Device Mode, 390 px | mobile menu, dialog, generator, FAQ, overlays | clipping/overflow and workflow usability |
| Firefox desktop | smoke and risk-based flows | no Firefox-specific defect reproduced in the verified run |
| Real iPhone Safari | native mobile menu, dialog, generator, FAQ | an initial runtime failure was registered; a blanket PASS for the complete post-fix real-device E2E is not claimed without a dedicated full rerun |

## Responsive checklist

- no horizontal scroll;
- header/status/close controls do not overlap;
- text wraps and remains readable;
- inputs, buttons, and hit areas remain accessible;
- menus, overlays, and modals open and close correctly;
- generator steps remain completable;
- long AI responses do not break the layout;
- loading, error, and empty states remain understandable;
- reload does not create duplicates or lose user state.

## Evidence

For viewport-dependent issues, the exact width, before/after state, and rect/overlap measurements were recorded when they helped prove the defect. Production screenshots are intentionally not copied into this public repository.
