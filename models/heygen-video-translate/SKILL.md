---
name: heygen-video-translate
description: "Heygen | Video Translate. Translate video content into 100+ languages with lip-sync using Heygen. Triggers: heygen, video translate, lip sync, dub video, video localization, translate"
allowed-tools: Bash(curl *), WebFetch
---

# Heygen | Video Translate

Translate video content into 100+ languages with automatic lip-sync using Heygen. Supports a wide range of language and regional dialect options for global content localization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "heygen-video-translate",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/english-presentation.mp4",
      "output_language": "Spanish"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| output_language | string | English | Target language for translation. Supports 100+ languages and regional dialects including English, Spanish, French, Hindi, Italian, German, Polish, Portuguese, Chinese, Japanese, Dutch, Turkish, Korean, Danish, Arabic, Romanian, and many more |
| video | string | | Input video file URL (.mp4) |

## Examples

**Translate to Japanese:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "heygen-video-translate",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/product-demo.mp4",
      "output_language": "Japanese"
    }
  }'
```

**Translate to Brazilian Portuguese:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "heygen-video-translate",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/tutorial-video.mp4",
      "output_language": "Portuguese(Brazil)"
    }
  }'
```

**Translate to Mandarin Chinese:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "heygen-video-translate",
    "version": "0.0.1",
    "input": {
      "video": "https://example.com/marketing-video.mp4",
      "output_language": "Mandarin"
    }
  }'
```

## Related Models

- [wizper](../wizper/) - Audio transcription and translation
- [merge-videos](../merge-videos/) - Merge translated video segments

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
