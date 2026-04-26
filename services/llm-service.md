---
type: service
id: llm-service
title: LLM Service
description: "Language model service for document analysis, summarisation, and action item extraction"
tags: [Production, Tested]
connections: []
metadata:
  serviceType: llm
  auth_type: api_key
---

## LLM Service

This skrpt uses a language model for analytical and generative tasks. The LLM handles document structure analysis, key point extraction, and summary synthesis.

### Configuration

- **Temperature:** 0.2 for document analysis, 0.5 for summary synthesis
- **Max tokens:** 4,000 for analysis, 6,000 for synthesis
- **Context window:** The analysis step receives the full document. The synthesis step receives the analysis output.

### Requirements

- A configured LLM provider in skrptiq settings
- Sufficient token quota for the full pipeline
- No external network access required beyond your AI provider's endpoint
