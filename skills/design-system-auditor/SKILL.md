---
name: design-system-auditor
description: Design system token compliance, 4pt/8pt spatial grid adherence, typography scale auditing, and WCAG accessibility contrast checks.
---

# Design System Auditor Skill

## Overview
The `design-system-auditor` skill audits UI components against design system foundations, enforcing 4pt/8pt spacing intervals, standardized typography scales, elevation token consistency, and WCAG accessibility contrast ratios.

## Core Capabilities
- **Spatial Grid Alignment**: Validates that paddings, margins, and component dimensions adhere to standard 4pt/8pt increments.
- **Typography Scale Hierarchy**: Confirms appropriate typographic scale usage (Display, Heading, Body, Caption) and consistent line-height ratios.
- **WCAG 2.1 AA Contrast Verification**: Calculates color contrast between foreground text/icons and background fills, enforcing $\ge 4.5:1$ ratios.
- **Token Consistency Check**: Identifies detached colors or arbitrary hex values that should reference global design system color tokens.

## Inputs
- `element_styles`: Color fills, typography settings, and spatial metrics of inspected frames.
- `design_tokens`: Defined color palettes and typography token tables.

## Outputs
- `compliance_rating`: Overall design system adherence score ($0-100$).
- `contrast_results`: Matrix of evaluated color pairs with pass/fail WCAG statuses.
- `token_deviations`: List of arbitrary hardcoded values that break system guidelines.
