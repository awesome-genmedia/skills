---
name: mureka-stem-song
description: "Mureka | Stem Song. Separate audio tracks into individual stems from a song. Triggers: stem, separate, audio, mureka, music, split"
allowed-tools: Bash(curl *), WebFetch
---

# Mureka | Stem Song

Separate a song into individual audio stems (vocals, instruments, etc.) from an audio URL.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-stem-song",
    "version": "0.0.1",
    "input": {
      "url": "https://example.com/song.mp3"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| url | string | false | URL of the song to separate into stems. |

## Examples

**Separate a pop song:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-stem-song",
    "version": "0.0.1",
    "input": {
      "url": "https://example.com/pop-track.mp3"
    }
  }'
```

**Separate a WAV file:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "mureka-stem-song",
    "version": "0.0.1",
    "input": {
      "url": "https://example.com/rock-song.wav"
    }
  }'
```

## Related Models

- [mureka-recognize-song](../mureka-recognize-song/) - Song recognition
- [mureka-extend-song](../mureka-extend-song/) - Song extension
- [mureka-generate-instrumental](../mureka-generate-instrumental/) - Instrumental generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
