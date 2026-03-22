---
name: mureka-generate-lyrics
description: "Mureka | Generate Lyrics. Generate song lyrics from a text prompt. Triggers: lyrics, generate, mureka, songwriting, write lyrics"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Generate Lyrics

Generate complete song lyrics from a text prompt describing the desired theme, mood, or style.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-lyrics",
    "version": "0.0.1",
    "input": {
      "prompt": "An upbeat pop song about chasing your dreams and never giving up"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| prompt | string | false | The prompt to generate lyrics for. |

## Examples

**Pop song lyrics:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-lyrics",
    "version": "0.0.1",
    "input": {
      "prompt": "A heartfelt ballad about long-distance love, piano-driven, emotional chorus"
    }
  }'
```

**Rock song lyrics:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-lyrics",
    "version": "0.0.1",
    "input": {
      "prompt": "An energetic rock anthem about freedom and rebellion, with powerful guitar riffs"
    }
  }'
```

**Country song lyrics:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-lyrics",
    "version": "0.0.1",
    "input": {
      "prompt": "A country song about small-town life, Friday night bonfires, and old friends"
    }
  }'
```

## Related Models

- [mureka-extend-lyrics](../mureka-extend-lyrics/) - Extend existing lyrics
- [mureka-extend-song](../mureka-extend-song/) - Extend a song with new audio
- [mureka-generate-instrumental](../mureka-generate-instrumental/) - Generate instrumental music

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
