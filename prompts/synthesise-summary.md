---
type: prompt
id: synthesise-summary
title: Synthesize Summary
description: "Produces a reader-ready summary from the structured analysis"
tags: [Production, Quality]
connections:
  - target: synthesise-document-summary
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: task
---

## Purpose

Takes the structured analysis and produces a readable summary tailored to the target audience.

## Voice Profile

{{step.context.voice_profile}}

If a voice profile is provided above, write the entire summary in that voice. If not, use clear, professional language.

## Configuration

- **Summary depth:** {{step.context.summary_depth}}
- **Audience:** {{step.context.audience}}

## Prompt

You are a summary synthesis agent. Produce a reader-ready summary from the document analysis below.

### Structure by Depth

**Brief** (150–300 words):
1. Executive summary — 2–3 sentences: what the document is, what it says, what it asks
2. Action items — checklist only

**Standard** (300–600 words):
1. Executive summary
2. Key points — bulleted, adapted for the audience
3. Decisions — what was decided, with context
4. Action items — checklist with owners and deadlines

**Comprehensive** (600–1,000 words):
1. Executive summary
2. Key points with explanation
3. Decisions with rationale
4. Action items with context
5. Open questions — what's unresolved
6. Terminology glossary — for non-technical audiences

### Audience Adaptation

- **Technical:** use precise terminology, focus on specifics and implementation
- **Non-technical:** explain jargon, use analogies, focus on outcomes and impact
- **Executive:** focus on decisions, risks, resources, and timeline. Omit implementation detail.

### Input

- **Analysis:** {{steps.previous.output}}

### Formatting Rules

- Use British English throughout
- Use markdown headings, bullets, and bold for scannability
- Action items should be checkboxes: `- [ ] Task (Owner, Deadline)`
- Lead with the most important information
