---
name: mureka-describe-song
description: "Mureka | Describe Song. Analyze and describe a song from its URL. Triggers: song analysis, music description, describe audio, mureka analyze"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Describe Song

Analyze and describe a song by providing its URL. Returns detailed information about the song's characteristics, mood, genre, and musical elements.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-describe-song",
    "version": "0.0.1",
    "input": {
      "url": "https://example.com/song.mp3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| url | string | - | URL of the song to describe and analyze. |

## Examples

**Analyze a hosted audio file:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-describe-song",
    "version": "0.0.1",
    "input": {
      "url": "https://storage.example.com/music/track.mp3"
    }
  }'
```

**Analyze a WAV file:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-describe-song",
    "version": "0.0.1",
    "input": {
      "url": "https://cdn.example.com/audio/demo-track.wav"
    }
  }'
```

## Related Models

- [Mureka | Generate Song](../mureka-generate-song/) - Generate songs with AI
- [Mureka | Recognize Song](../mureka-recognize-song/) - Recognize and identify songs
- [Mureka | Stem Song](../mureka-stem-song/) - Separate a song into stems

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
