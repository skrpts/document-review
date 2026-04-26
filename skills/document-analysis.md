---
type: skill
id: document-analysis
title: Document Analysis
description: "Extracts structure, key points, decisions, terminology, and action items from a document"
tags: [Production, Quality]
connections:
  - target: llm-service
    type: runs_on
---

## Capability

Reads a document and produces a structured analysis: document type, key points, decisions made, action items, open questions, and important terminology. This structured output feeds the synthesis step.

## When to Use

- As the first step in a document review pipeline
- When you need to quickly understand what a document says and what it asks of you

## What It Does

1. **Document type** — identifies what kind of document this is (proposal, report, meeting notes, contract, specification, etc.)
2. **Key points** — extracts the main arguments, findings, or proposals
3. **Decisions** — identifies any decisions that were made or are being proposed
4. **Action items** — extracts tasks, deadlines, and responsible parties
5. **Open questions** — flags unresolved questions or ambiguities
6. **Terminology** — notes domain-specific terms that may need explanation for a broader audience

## Inputs

One document: text, markdown, or file upload.

## Outputs

Structured analysis object with sections for each category above.
