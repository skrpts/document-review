---
type: prompt
id: analyse-document
title: Analyze Document
description: "Extracts structure, key points, decisions, and action items from a document"
tags: [Production, Quality]
inputs:
  document:
    label: "Document"
    description: "The document to review — paste text or upload a file"
    example: "We held the Q2 planning meeting on Friday. Attendees: Sarah (Engineering), Mike (Product), Lisa (Design). Key decisions: 1) Ship the new onboarding flow by June 15th. Sarah to lead. 2) Defer the analytics dashboard to Q3 — not enough design capacity. 3) Hire two frontend developers by end of May. Mike to write the job specs. Open question: should we use the existing component library or build custom? Lisa to prototype both approaches by next Friday."
    required: true
    type: file
    accept: ".txt,.md,.docx,.pdf"
  review_focus:
    label: "Review Focus"
    description: "What to focus on — key decisions, action items, risks, or general summary"
    example: "Key decisions and action items"
    required: false
    type: text
connections:
  - target: document-analysis
    type: derived_from
metadata:
  output_format: structured
  prompt_type: task
---

## Purpose

Analyzes a document and produces a structured extraction of its key content.

## Prompt

You are a document analysis agent. Read the document below and extract a structured analysis.

### Focus

{{input.review_focus}}

If a review focus is specified above, prioritize that category in your analysis. If not, give equal weight to all categories.

### What to Extract

1. **Document type** — what kind of document is this? (meeting notes, proposal, report, contract, specification, email thread, etc.)
2. **Key points** — the 3–7 most important arguments, findings, or proposals. Each should be one sentence.
3. **Decisions** — any decisions that were made or are being proposed. Include who decided and any conditions.
4. **Action items** — tasks with owners and deadlines where stated. Format as a checklist.
5. **Open questions** — unresolved questions, ambiguities, or items flagged for follow-up.
6. **Terminology** — domain-specific terms that a general audience might not understand.

### Input

{{input.document}}

### Output Format

Return a structured object with clearly labeled sections for each category. Use bullet points within each section. If a category has no entries (e.g. no action items in a research paper), note "None identified" rather than omitting the section.
