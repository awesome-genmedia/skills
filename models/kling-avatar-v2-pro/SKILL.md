---
name: kling-avatar-v2-pro
description: "Kling | Avatar | v2 | Pro. Generate high-quality avatar videos from an image and audio file. Triggers: avatar, talking head, lip sync, video generation, kling, pro"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | Avatar | v2 | Pro

Generate professional-quality avatar videos by combining a portrait image with an audio file. Pro tier delivers higher fidelity face animation and lip synchronization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-avatar-v2-pro",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "audio_url": "https://example.com/speech.mp3",
      "prompt": "natural talking with subtle expressions"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | | The URL of the audio file. |
| image_url | string | | The URL of the image to use as your avatar. |
| prompt | string | . | The prompt to use for the video generation. |

## Examples

**Professional presenter avatar:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-avatar-v2-pro",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/professional-headshot.jpg",
      "audio_url": "https://example.com/sales-pitch.mp3",
      "prompt": "professional and engaging presentation style"
    }
  }'
```

**Expressive character avatar:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-avatar-v2-pro",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/character.jpg",
      "audio_url": "https://example.com/dialogue.wav",
      "prompt": "animated and expressive facial movements"
    }
  }'
```

## Related Models

- [Kling | Avatar | v2 | Standard](../kling-avatar-v2-standard/) - Standard-quality avatar video generation
- [Kling | v2.6 | Pro | Image to Video](../kling-v2-6-pro-image-to-video/) - General image-to-video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
