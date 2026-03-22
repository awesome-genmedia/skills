---
name: pdf-to-text
description: "PDF to Text Generator. Extract text content from PDF documents using PDF to Text Generator. Triggers: pdf to text"
allowed-tools: Bash(curl *), WebFetch
---

# PDF to Text Generator

Extract text content from PDF documents using PDF to Text Generator.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pdf-to-text",
    "version": "0.0.1",
    "input": {
      "url": "https://example.com/document.pdf"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `url` | string |  | Pdf Url |

## Examples

**Extract text from PDF:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pdf-to-text",
    "version": "0.0.1",
    "input": {
      "url": "https://example.com/document.pdf"
    }
  }'
```

**Extract from research paper:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pdf-to-text",
    "version": "0.0.1",
    "input": {
      "url": "https://example.com/research-paper.pdf"
    }
  }'
```

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
