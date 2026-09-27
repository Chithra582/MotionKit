---
name: motion-interaction-evaluator
description: Minimum Design Criteria (MDC) compliance verification, video prototype inspection, and OpenCode scoring dossier generation.
---

# Motion Interaction Evaluator Skill

## Overview
The `motion-interaction-evaluator` skill evaluates student design deliverables against task-specific Minimum Design Criteria (MDC), analyzes video prototype demonstrations, checks for plagiarism, and compiles structured mentor review dossiers.

## Core Capabilities
- **MDC Checkpoint Verification**: Audits whether a submission fulfills all required criteria in the task folder's `MDC.md`.
- **Anti-Plagiarism Screening**: Evaluates design structures against known public templates and fellow submissions to verify original creation.
- **Multimodal Video Demo Inspection**: Reviews screen recording previews (GIF/MP4) to verify fluid animation behavior in real-time.
- **Review Dossier Assembly**: Produces structured feedback summaries with score breakdowns across Design Thinking, Auto-Layout, and Visual Polish.

## Inputs
- `task_id`: Identifier of the challenge task (e.g., `1-loader`, `2-tab-navigation`).
- `submission_data`: Figma URL, video demo link, and contributor metadata.
- `mdc_criteria`: Task-specific pass/fail requirements.

## Outputs
- `mdc_status`: `QUALIFIED` or `NEEDS_REVISION`.
- `total_points`: Evaluated points recommendation for OpenCode leaderboard.
- `mentor_review_summary`: Formatted Markdown review comment for GitHub PR.
