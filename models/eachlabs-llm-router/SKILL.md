---
name: eachlabs-llm-router
description: "eachlabs-llm-router. Route requests to the optimal LLM model automatically. Triggers: llm, router, language model, chat, text generation"
allowed-tools: Bash(curl *), WebFetch
---

# eachlabs-llm-router

Automatically route requests to the optimal LLM model based on the input. Intelligent model selection for text generation tasks.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-llm-router",
    "version": "0.0.1",
    "input": {
      "input": {}
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| input | object | false | Input object for the LLM router. Required. |

## Examples

**Basic LLM request:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "eachlabs-llm-router",
    "version": "0.0.1",
    "input": {
      "input": {}
    }
  }'
```

## Related Models

Refer to the each::labs documentation for the full list of available LLM models.

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
