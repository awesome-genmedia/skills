---
name: kokoro-82m
description: "Kokoro 82M. Generate natural-sounding speech from text using Kokoro 82M. Triggers: audio generation, kokoro"
allowed-tools: Bash(curl *), WebFetch
---

# Kokoro 82M

Generate natural-sounding speech from text using Kokoro 82M.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kokoro-82m",
    "version": "0.0.1",
    "input": {
      "text": "Hello, welcome to our platform. We are excited to have you here.",
      "voice": "af_heart"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `speed` | number | 1 | Speech speed multiplier (0.5 = half speed, 2.0 = double speed) |
| `text` | string |  | Text input (long text is automatically split into smaller chunks) |
| `voice` | string | af | An enumeration.. Options: `af`, `af_bella`, `af_sarah`, `am_adam`, `am_michael`, `bf_emma`, `bf_isabella`, `bm_george`, `bm_lewis`, `af_nicole`, `a... |

## Examples

**Generate speech:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kokoro-82m",
    "version": "0.0.1",
    "input": {
      "text": "Hello, welcome to our platform. We are excited to have you here.",
      "voice": "af_heart"
    }
  }'
```

**Custom voice and speed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kokoro-82m",
    "version": "0.0.1",
    "input": {
      "text": "The quick brown fox jumps over the lazy dog. This is a test of natural speech synthesis.",
      "voice": "af_bella",
      "speed": 1.2
    }
  }'
```

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
