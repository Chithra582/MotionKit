# EXPLAINABILITY.md

This document explains the internal mechanisms, data lineage, operational boundaries, and governance framework of **MotionKit Agent** (`motionkit-agent`) in accordance with the **OpenGAP v0.1.0** specification for the **HiDevs GitAgent Passport** clearance pipeline.

> **Agent Name:** MotionKit Agent (`motionkit-agent`)  
> **Specification:** OpenGAP v0.1.0  
> **Category / Domain:** Education / UI/UX Design, Figma Component Architecture & Prototyping  
> **Compliance Standard:** OpenGAP Checkpoint 2 (Explainability & Decision Governance), FERPA, GDPR  

---

## How the Agent Decides

MotionKit Agent is an autonomous Figma UI/UX component engineering, interactive prototyping, design systems auditing, and micro-interaction verification agent designed for **MotionKit** (OpenCode '25). The agent coordinates Auto-Layout responsiveness checks, component variant state matrices, Minimum Design Criteria (MDC) scoring, and interactive prototype flow validation.

### 1. Decision Architecture

The UI design submission intake, component inspection, and prototype evaluation pipeline operates across a deterministic, five-stage architecture:

```
Contributor Action (Submit Pull Request with Figma Link / Video Preview / Task Assets)
    │
    ▼
[Stage 1: Submission Ingestion & Integrity Check]
    │  - Verifies submission resides inside designated task folder (e.g. `1-loader/`, `2-tab-navigation/`)
    │  - Validates accessibility of public Figma URL (checks view/inspect permissions)
    │  - Confirms inclusion of demo video/GIF and design rationale markdown
    ▼
[Stage 2: Auto-Layout & Spatial Grid Auditing]
    │  - Inspects component frame hierarchy: checks horizontal/vertical directionality
    │  - Evaluates dynamic responsiveness: enforces `Hug contents` vs `Fill container` constraints
    │  - Audits spacing consistency: validates padding and item spacing against 4pt/8pt spatial grid
    ▼
[Stage 3: Component Variant Matrix & Property Inspection]
    │  - Evaluates interactive state completeness:
    │      ├── Default / Inactive state
    │      ├── Hover / Focus state
    │      ├── Pressed / Active state
    │      └── Disabled / Loading state
    │  - Verifies boolean property toggles (e.g., `hasIcon`, `showBadge`) and component set naming
    ▼
[Stage 4: Interactive Micro-Prototyping & Motion Verification]
    │  - Audits prototype connection noodles between variants
    │  - Validates transition settings: Smart Animate easing curves and duration (200ms - 400ms)
    │  - Checks trigger types: `While hovering`, `On click`, `After delay`
    ▼
[Stage 5: MDC Scoring & Review Dossier Generation]
    │  - Computes composite Design Quality Score ($Q_{\text{design}} \in [0, 100]$)
    │  - Evaluates Minimum Design Criteria (MDC) pass/fail checklist
    │  - Prepares structured feedback dossier with actionable refactoring tips for mentor review
    ▼
Evaluated Design Review & OpenCode Leaderboard Score Published to PR
```

### 2. Design Scoring & MDC Rubric Formulations

MotionKit evaluates design submissions through a structured, multi-factor scoring formula:

1. **Composite Design Score ($Q_{\text{design}}$)**:
   $$Q_{\text{design}} = (w_a \cdot A_{\text{autolayout}}) + (w_v \cdot V_{\text{variants}}) + (w_m \cdot M_{\text{motion}}) + (w_c \cdot C_{\text{contrast}})$$
   where:
   - $A_{\text{autolayout}} \in [0, 100]$: Auto-Layout compliance (penalizing fixed pixel widths on responsive containers).
   - $V_{\text{variants}} \in [0, 100]$: Completeness of interactive variant states (Default, Hover, Pressed, Disabled).
   - $M_{\text{motion}} \in [0, 100]$: Prototype animation fidelity (Smart Animate easing curves, appropriate durations).
   - $C_{\text{contrast}} \in [0, 100]$: WCAG 2.1 AA accessibility contrast score ($\ge 4.5:1$ ratio).
   - Weights: $w_a = 0.35, w_v = 0.25, w_m = 0.25, w_c = 0.15$ ($\sum w_i = 1.0$).

2. **Minimum Design Criteria (MDC) Full Points Qualification**:
   Full competitive points are awarded if and only if the submission satisfies all three binary criteria:
   $$\text{MDC Qualified} \iff (Q_{\text{design}} \ge 75) \land (\text{Plagiarism Check} = \text{PASS}) \land (\text{Deadline Met} = \text{TRUE})$$

### 3. Thresholding & Refusal Decision Criteria

MotionKit Agent deterministically enforces strict boundaries to protect community learning:
- **Refusal on Plagiarism**: Submissions that copy existing community Figma files or peer PRs without original authorship fail immediately with code `ERR_PLAGIARISM_DISQUALIFICATION`.
- **Refusal on Static Non-Auto-Layout Frames**: Components constructed using free-floating, absolute-positioned shapes without Auto-Layout fail technical criteria with code `ERR_MISSING_AUTO_LAYOUT`.
- **Refusal on Private / Inaccessible Figma URLs**: Submissions with restricted Figma file permissions that prevent layer inspection are flagged with code `ERR_FIGMA_LINK_INACCESSIBLE`.
- **Refusal on Missing Variant States**: Component sets missing core interactive states (e.g., missing Hover or Pressed state) receive an actionable revision notice (`WARN_INCOMPLETE_VARIANT_MATRIX`).

### 4. Fallback Decision Mechanism

MotionKit Agent maintains reliable feedback through layered fallback strategies:
- **Local JSON Schema Fallback**: If the Figma REST API is unreachable or rate-limited, the agent evaluates exported SVG/frame JSON exports or local video demo assets.
- **Static Design Pattern Library**: If generative design advice is offline, the agent provides standardized guidance cards from the curated MotionKit component reference library.
- **Model Fallback Cascade**: High-level design critique and constructive feedback default to `gemini-2.0-flash` with automatic failover to `gpt-4o` and `claude-3-5-sonnet`.

### 5. Human-in-the-Loop Governance

MotionKit maintains mentor oversight and student advocacy:
- **Mentor Final Adjudication**: While automated checks verify Auto-Layout syntax and contrast mathematically, subjective points (Design Thinking, Aesthetic Innovation) rest with human mentors (Soham Donode & GeekHaven Organizers).
- **Constructive Revision Opportunities**: Contributors receiving revision notices have an allotted window to update their Figma file and push corrections before final scoring.
- **Inclusive Beginner Support**: Beginners are provided with step-by-step visual Auto-Layout diagrams on Discord to help them overcome initial learning curves.

---

## The Data It Uses

MotionKit Agent operates under strict privacy and open-source educational standards.

### 1. Ingested Input Data

The agent processes only UI/UX design deliverables submitted by contributors:
- **Figma File Metadata**: Public file URLs, node hierarchies, frame constraints, variant properties, and prototype connection noodles.
- **Task Deliverables**: Video recordings (MP4/GIF), design rationale notes, and contributor information.
- **Issue Requirements**: Markdown specifications and Minimum Design Criteria from task folders (`1-loader/`, `2-tab-navigation/`, etc.).

### 2. Configuration & Reference Data

- **Design System Token Schemas**: 4pt/8pt spatial grid scales, standard typography hierarchies, and elevation drop-shadow levels.
- **WCAG 2.1 Contrast Baselines**: Authoritative color luminance tables for text and graphical interface components.
- **OpenCode '25 Event Schedule**: Task release timetables, submission deadlines, and leaderboard rules.

### 3. Base Model & Inference Lineage

- **Deterministic Geometry & Color Linters**: Frame dimension calculation, contrast ratio evaluation, and variant completeness checks are executed via deterministic algorithms.
- **AI Design Review Copilot**: Frontier foundation models (`gemini-2.0-flash`, `gpt-4o`, `claude-3-5-sonnet`) utilized exclusively for natural-language constructive critique and design thinking suggestions.
- **Zero Training on Contributor Designs**: Submitted Figma frames, vector artwork, and creative prototypes are never used for commercial generative AI training.

### 4. Data Privacy, Storage, and Retention

- **FERPA & GDPR Compliance**: Student contributor identities, email addresses, and student roll numbers are treated as private educational records.
- **Zero Credential Retention**: Personal Figma API access tokens or private account credentials are never requested, stored, or retained.
- **Open-Source Attribution**: All merged contributions are permanently credited to their respective student designers under open-source project licenses.

---

## Limitations

Understanding the technical boundaries and tool constraints of MotionKit Agent is essential for realistic design evaluation.

### 1. Figma Cloud API Access Token & Permission Boundaries
- **Limitation**: The Figma REST API requires public file permissions or authenticated tokens to query deep layer trees, and rate limits heavy inspection during high-traffic submission bursts.
- **Mitigation**: The agent encourages contributors to provide short screen-recording previews (GIF/MP4) alongside public file links, allowing multimodal visual inspection even during API throttles.

### 2. Subjective Visual Attractiveness vs Algorithmic Scoring
- **Limitation**: While contrast ratios and Auto-Layout rules are mathematically quantifiable, aesthetic taste, visual balance, and modern design elegance are inherently subjective.
- **Mitigation**: Algorithmic scoring focuses strictly on technical MDC adherence, reserving qualitative aesthetic scoring for human design mentors.

### 3. Complex Smart-Animate Physics & Easing Nuances
- **Limitation**: Figma's browser rendering engine computes proprietary spring physics and layer interpolation that static node graphs cannot fully simulate offline.
- **Mitigation**: The review pipeline relies on video recording evidence of the running prototype to verify animation smoothness and damping.

### 4. Cross-Platform Viewport Scaling Variance
- **Limitation**: Components designed for desktop viewports may render differently on high-DPI mobile screens or diverse web browsers.
- **Mitigation**: The agent stresses Auto-Layout constraint testing across multiple predefined frame sizes (e.g., Mobile: 375px, Tablet: 768px, Desktop: 1440px).

### 5. Automated Critique vs Live Mentor Interaction
- **Limitation**: An automated agent cannot replace the interactive dialogue, career mentorship, and design critique provided in live studio sessions.
- **Mitigation**: The agent directs students to the GeekHaven OpenCode Discord server for synchronous discussions with mentors.

---

## Summary & Compliance Checklist

| Checkpoint 2 Requirement | Corresponding Section | Status |
| :--- | :--- | :---: |
| **How the agent decides** | [How the Agent Decides](#how-the-agent-decides) | **Covered** |
| - Decision architecture & 5-stage pipeline | Section 1 | Verified |
| - Design scoring & MDC rubric formulations | Section 2 | Verified |
| - Thresholding, plagiarism refusal & criteria | Section 3 | Verified |
| - Fallback decision mechanism & local schemas | Section 4 | Verified |
| - Human-in-the-loop & mentor governance | Section 5 | Verified |
| **The data it uses** | [The Data It Uses](#the-data-it-uses) | **Covered** |
| - Ingested Figma URLs, node hierarchies & videos | Section 1 | Verified |
| - Configuration, design tokens & WCAG baselines | Section 2 | Verified |
| - Base model lineage & deterministic linters | Section 3 | Verified |
| - Data privacy, zero credential storage & FERPA/GDPR | Section 4 | Verified |
| **Its limitations** | [Limitations](#limitations) | **Covered** |
| - Figma Cloud API token & rate limit boundaries | Section 1 | Verified |
| - Subjective visual attractiveness vs algorithmic scores | Section 2 | Verified |
| - Smart-animate physics & easing curve nuances | Section 3 | Verified |
| - Cross-platform viewport scaling variance | Section 4 | Verified |
| - Automated critique vs live mentor interaction | Section 5 | Verified |
