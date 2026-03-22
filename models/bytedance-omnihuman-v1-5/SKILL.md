---
name: bytedance-omnihuman-v1-5
description: "Bytedance | Omnihuman v1.5. Generate human animation videos from an image and audio. Triggers: talking head, human animation, audio to video, omnihuman, avatar"
allowed-tools: Bash(curl *), WebFetch
---

# Bytedance | Omnihuman v1.5

Generate realistic human animation videos from a reference image and audio input. Creates natural-looking talking head videos with lip sync and body movement at up to 1080p resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-omnihuman-v1-5",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/person-portrait.jpg",
      "audio_url": "https://example.com/speech.mp3",
      "prompt": "A person speaking naturally with subtle head movements",
      "resolution": "1080p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | The URL of the audio file to generate the video. Audio must be under 30s long. |
| image_url | string | - | The URL of the image used to generate the video. |
| prompt | string | - | The text prompt used to guide the video generation. |
| resolution | string | 1080p | The resolution of the generated video. Options: `720p`, `1080p` |
| turbo_mode | boolean | false | Generate a video at a faster rate with a slight quality trade-off. |

## Examples

**Standard quality animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-omnihuman-v1-5",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/headshot.jpg",
      "audio_url": "https://example.com/greeting.mp3",
      "resolution": "1080p"
    }
  }'
```

**Fast generation with turbo mode:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-omnihuman-v1-5",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/presenter.jpg",
      "audio_url": "https://example.com/presentation-audio.mp3",
      "prompt": "Professional presenter speaking confidently with hand gestures",
      "resolution": "720p",
      "turbo_mode": true
    }
  }'
```

## Related Models

- [Infinitalk | Image to Video](../infinitalk-image-to-video/) - Image-based talking head animation
- [Infinitalk | Video to Video](../infinitalk-video-to-video/) - Video-based talking head animation
- [Sync | Lipsync | v2 | Pro](../sync-lipsync-v2-pro/) - Professional lip sync

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
