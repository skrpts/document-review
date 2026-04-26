---
type: skill
id: summary-synthesis
title: Summary Synthesis
description: "Produces a reader-ready summary with key points, decisions, and action items"
tags: [Production, Quality]
connections:
  - target: llm-service
    type: runs_on
context_params:
  voice_profile:
    label: "Voice Profile"
    description: "Your writing style — the summary will match your voice"
    required: false
  summary_depth:
    label: "Summary Depth"
    description: "How detailed the summary should be — Brief, Standard, or Comprehensive"
    default: "Standard"
    required: false
  audience:
    label: "Audience"
    description: "Who will read this summary — Technical, Non-technical, or Executive"
    default: "Non-technical"
    required: false
---

## Capability

Takes the structured analysis and produces a readable summary tailored to the target audience. Adapts vocabulary, detail level, and emphasis based on who will read it.

## When to Use

- After document analysis has extracted the structured data
- When you need to share a document's contents with someone who won't read the original

## What It Does

1. **Executive summary** — 2–3 sentence overview of what the document is and why it matters
2. **Key points** — the main arguments or findings, adapted for the audience
3. **Decisions** — what was decided or proposed, with context
4. **Action items** — tasks with owners and deadlines, formatted as a checklist
5. **Open questions** — what remains unresolved

## Summary Depth Levels

- **Brief** — executive summary + action items only. 150–300 words.
- **Standard** — everything above plus key points and decisions. 300–600 words.
- **Comprehensive** — full summary with terminology glossary and open questions. 600–1,000 words.

## Audience Levels

- **Technical** — assumes domain knowledge. Uses precise terminology. Focuses on specifics.
- **Non-technical** — explains jargon. Uses analogies. Focuses on impact and outcomes.
- **Executive** — focuses on decisions, risks, and resource implications. Omits implementation detail.

## Outputs

Formatted summary in markdown, ready to share.
