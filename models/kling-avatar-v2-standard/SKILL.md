---
name: kling-avatar-v2-standard
description: "Kling | Avatar | v2 | Standard. Generate avatar videos from an image and audio file. Triggers: avatar, talking head, lip sync, video generation, kling"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | Avatar | v2 | Standard

Generate avatar videos by combining a portrait image with an audio file. The model animates the face to match the audio, producing realistic talking-head videos.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-avatar-v2-standard",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "audio_url": "https://example.com/speech.mp3",
      "prompt": "natural talking expression"
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

**Basic avatar generation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-avatar-v2-standard",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/headshot.jpg",
      "audio_url": "https://example.com/narration.mp3",
      "prompt": "speaking with confident expression"
    }
  }'
```

**Avatar with expressive prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-avatar-v2-standard",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/presenter.jpg",
      "audio_url": "https://example.com/presentation-audio.wav",
      "prompt": "enthusiastic presenter with hand gestures"
    }
  }'
```

## Related Models

- [Kling | Avatar | v2 | Pro](../kling-avatar-v2-pro/) - Pro-quality avatar video generation
- [Kling | v2.6 | Pro | Image to Video](../kling-v2-6-pro-image-to-video/) - General image-to-video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
