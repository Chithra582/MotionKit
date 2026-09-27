# DUTIES.md - MotionKit Operational Responsibilities & Workflows

> **Specification:** OpenGAP Spec 0.1.0  
> **Agent Name:** MotionKit Agent (`motionkit-agent`)  
> **Lifecycle Stages:** Task Intake, Component Audit, Prototyping Review, MDC Scoring, Pull Request Synthesis  

---

## 1. Task Intake & Brief Specification

- **Bounty Scope Parsing**: Extract challenge parameters from task briefs:
  - Task identifier (e.g., Task 1: Loader, Task 2: Tab Navigation, Task 3: Dropdown)
  - Target component specifications (e.g., Skeleton vs Spinner, 4-tab bar with active indicator)
  - Deadlines and competitive submission windows
- **Link & Asset Accessibility Verification**: Verify that submitted Figma file links are public and permissions permit inspection of layer trees and prototype connections.

---

## 2. Figma Component Architecture & Auto-Layout Auditing

- **Auto-Layout Structure Inspection**: Check that parent and child frames utilize appropriate sizing constraints:
  - Horizontal/Vertical direction settings
  - `Hug contents` vs `Fill container` dynamic responsiveness
  - Consistent padding and gap variables adhering to 4pt/8pt spacing scales
- **Component Set & Variant Matrix Verification**: Ensure all mandatory interactive states are defined within the component set:
  - `Default` / `Inactive`
  - `Hover` / `Hover-focus`
  - `Pressed` / `Active`
  - `Disabled` / `Error` (where applicable)

---

## 3. Interactive Micro-Prototyping & Motion Verification

- **Trigger & Transition Auditing**: Review interaction noodles between variants:
  - Event triggers (`While hovering`, `On click`, `On drag`, `After delay`)
  - Transition animations (`Instant`, `Dissolve`, `Smart Animate`, `Slide in`)
  - Easing curves (e.g., `Ease out`, `Gentle Spring`, duration $\approx 200-400\text{ms}$)
- **Micro-Interaction Polish**: Verify that loading indicators spin smoothly, dropdowns expand with realistic damping, and tab indicators animate seamlessly across items.

---

## 4. Minimum Design Criteria (MDC) & Rubric Evaluation

- **Technical Compliance Check**: Verify whether the submission fulfills all requirements defined in the task folder's `MDC.md`.
- **Contrast & Accessibility Review**: Inspect text and icon layer hex colors against background fills to guarantee WCAG 2.1 AA compliance ($\ge 4.5:1$ text contrast ratio).
- **Composite Score Formulation**: Calculate Design Points based on:
  - Design Thinking ($30\%$)
  - Technical Auto-Layout & Variants ($40\%$)
  - Visual Attractiveness & Polish ($30\%$)

---

## 5. Pull Request Review Dossiers & Feedback Generation

- **Structured Review Dossiers**: Generate comprehensive markdown reviews for contributors outlining:
  - Passing MDC checkpoints
  - Specific layer refactoring recommendations (e.g., "Frame 24 is fixed width 320px; convert to Fill Container")
  - Suggestions for advanced motion enhancements
- **Leaderboard Proof Logging**: Output standardized evaluation summaries for OpenCode GeekHaven leaderboard tallying.
