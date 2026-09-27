---
name: interactive-prototype-validator
description: Prototyping flow verification, trigger action auditing, Smart Animate transition checking, and interaction dead-end detection.
---

# Interactive Prototype Validator Skill

## Overview
The `interactive-prototype-validator` skill reviews Figma interaction connections, validating that triggers (`On click`, `While hovering`, `On drag`) transition smoothly between variants using appropriate Smart Animate easing curves and realistic durations.

## Core Capabilities
- **Prototype Flow Traversal**: Audits navigation flows and micro-interactions across component states.
- **Smart Animate Fidelity**: Verifies consistent layer naming across variants to enable seamless Smart Animate vector morphing.
- **Duration & Easing Curve Auditing**: Ensures transition times adhere to natural UI physics ($200\text{ms} - 400\text{ms}$, Gentle Spring or Ease Out).
- **Dead-End Detection**: Identifies state transitions that leave the prototype in an un-resettable or locked condition.

## Inputs
- `prototype_connections`: List of interaction trigger and destination mappings.
- `component_variant_pairs`: Source and destination component states.

## Outputs
- `flow_status`: Traversal outcome (`VALID_PROTOTYPE`, `DEADLOCK_DETECTED`, `UNNAMED_LAYER_WARNING`).
- `timing_analysis`: Evaluation of transition durations and easing types.
- `animation_polish_score`: Normalized score ($0-100$) reflecting motion realism.
