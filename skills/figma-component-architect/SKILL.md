---
name: figma-component-architect
description: Auto-Layout verification, component variant property inspection, and responsive container constraint validation.
---

# Figma Component Architect Skill

## Overview
The `figma-component-architect` skill inspects Figma UI component hierarchies, verifying that components utilize Auto-Layout with responsive sizing rules (`Hug contents` vs `Fill container`), structured variant properties, and scalable layer naming.

## Core Capabilities
- **Auto-Layout Direction & Padding Audit**: Checks horizontal/vertical stack direction, uniform padding, and gap spacing.
- **Responsive Constraint Validation**: Verifies that components adapt cleanly across viewport resizes rather than relying on fixed pixel widths.
- **Variant Property Inspection**: Audits component set definitions for comprehensive state matrices (`Default`, `Hover`, `Pressed`, `Disabled`).
- **Boolean & Text Property Checks**: Recommends modern Figma component properties (`Boolean`, `Instance swap`, `Text`) for clean developer handoff.

## Inputs
- `figma_component_data`: Serialized JSON representation of Figma frame/component node tree.
- `component_type`: Category of UI component (button, tab bar, dropdown, modal).

## Outputs
- `auto_layout_compliance`: Boolean indicating correct Auto-Layout usage.
- `missing_variants`: List of expected states not discovered in the component set.
- `refactoring_suggestions`: Concrete recommendations for layer restructuring.
