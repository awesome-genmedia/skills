---
name: mureka-generate-instrumental
description: "Mureka | Generate Instrumental. Generate instrumental music tracks from a text prompt. Triggers: instrumental, music, mureka, generate, background music"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Generate Instrumental

Generate instrumental music tracks from a text prompt. Supports generating up to 3 instrumental variations per request with model selection.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-instrumental",
    "version": "0.0.1",
    "input": {
      "prompt": "An uplifting cinematic orchestral piece with strings and piano",
      "model": "auto",
      "n": 2
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| instrumental_id | boolean | false | Instrumental ID reference. |
| model | string | false | Model to use. enum: auto, mureka-7.5 |
| n | integer | 2 | Number of instrumentals to generate (max 3). |
| prompt | string | false | Text prompt describing the instrumental. |
| stream | boolean | false | Enable streaming output. |

## Examples

**Cinematic orchestral piece:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-instrumental",
    "version": "0.0.1",
    "input": {
      "prompt": "Epic cinematic trailer music with drums, brass, and choir",
      "model": "auto",
      "n": 3
    }
  }'
```

**Lo-fi background music:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-instrumental",
    "version": "0.0.1",
    "input": {
      "prompt": "Chill lo-fi hip hop beats with warm piano chords and vinyl crackle",
      "model": "mureka-7.5",
      "n": 2
    }
  }'
```

**Ambient music:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-generate-instrumental",
    "version": "0.0.1",
    "input": {
      "prompt": "Peaceful ambient soundscape with soft synth pads and nature sounds",
      "n": 1
    }
  }'
```

## Related Models

- [mureka-generate-lyrics](../mureka-generate-lyrics/) - Generate song lyrics
- [mureka-extend-song](../mureka-extend-song/) - Extend a song
- [minimax-music-2-5](../minimax-music-2-5/) - MiniMax music generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
