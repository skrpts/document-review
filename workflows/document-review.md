---
type: workflow
id: document-review
title: Document Review
description: "Analyzes a document, extracts key points and action items, and produces a summary tailored to your audience"
tags: [Production, Quality]
connections:
  - target: document-analysis
    type: uses
  - target: synthesise-document-summary
    type: uses
  - target: language-polish
    type: uses
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "15-30 seconds"
  avg_tokens: 8000
  trigger: manual
output_step: "language-polish"
composite_steps:
  - "document-analysis"
  - "synthesise-document-summary"
  - "language-polish"
execution:
  - skill: "document-analysis"
    step_type: "generation"
    prompt: "analyse-document"
    output: { name: "analysis", type: "text" }
  - skill: "synthesise-document-summary"
    step_type: "synthesis"
    prompt: "synthesise-summary"
    output: { name: "summary", type: "text" }
    context:
      voice_profile: "Neutral professional tone"
      summary_depth: "Standard"
      audience: "General professional audience"
  - skill: "language-polish"
    step_type: "content"
    prompt: "polish-summary"
    output: { name: "polished_summary", type: "text" }
    context:
      voice_profile: "Neutral professional tone"
      grammar_strictness: "Professional"
---

## Overview

This workflow takes any document — meeting notes, proposals, reports, contracts, specifications — and produces a reader-ready summary with key points, decisions, and action items. The summary is tailored to your target audience and written in your voice.

## Pipeline Stages

### Stage 1: Document Analysis

**Input:** Document text or file upload

Reads the document and extracts a structured analysis: document type, key points, decisions, action items, open questions, and terminology.

### Stage 2: Summary Synthesis

Takes the structured analysis and produces a formatted summary. Adapts depth (Brief, Standard, Comprehensive) and vocabulary (Technical, Non-technical, Executive) based on your settings.

### Stage 3: Language Polish

Final cleanup: spelling, grammar, clarity, and Voice Profile alignment. Uses British English throughout.

**Output:** Publication-ready document summary.

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.document}}` | Yes | The document to review | Paste text or upload a file |
| `{{input.review_focus}}` | No | What to focus on. Default: general summary. | `Key decisions and action items` |

## Outputs

| Name | Description |
|------|-------------|
| Document summary | Formatted summary with key points, decisions, action items, and optional glossary |

## Setup

No external services required — this workflow runs entirely on your configured LLM provider.

## Provider Notes

- Document analysis benefits from a model with strong reading comprehension.
- Summary synthesis benefits from a model with good writing capabilities.
- Short documents (under 2,000 words) work well with any model. Longer documents benefit from a model with generous context limits.

## Example Input

To test this workflow immediately after import, use **Try with Examples** — the pre-populated example contains meeting notes with decisions and action items.
