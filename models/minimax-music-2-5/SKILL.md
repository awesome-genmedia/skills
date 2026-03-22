---
name: minimax-music-2-5
description: "minimax music 2.5. Generate music using MiniMax's music generation model. Triggers: music, generate music, minimax, audio, song"
allowed-tools: Bash(curl *), WebFetch
---

# minimax music 2.5

Generate music using MiniMax's music 2.5 model.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-music-2-5",
    "version": "0.0.1",
    "input": {}
  }'
```

## Parameters

This model has no documented parameters. Refer to the API documentation for usage details.

## Examples

**Basic music generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-music-2-5",
    "version": "0.0.1",
    "input": {}
  }'
```

## Related Models

- [mureka-generate-instrumental](../mureka-generate-instrumental/) - Mureka instrumental generation
- [mureka-generate-lyrics](../mureka-generate-lyrics/) - Mureka lyrics generation
- [mureka-extend-song](../mureka-extend-song/) - Mureka song extension

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
