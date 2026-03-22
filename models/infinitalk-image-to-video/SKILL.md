---
name: infinitalk-image-to-video
description: "Infinitalk | Image to Video. Animate a static image with audio-driven lip sync and motion. Triggers: talking head, lip sync, image animation, photo to video, infinitalk"
allowed-tools: Bash(curl *), WebFetch
---

# Infinitalk | Image to Video

Animate a static image by syncing it with audio input, creating a talking head video. Supports mask images for specifying which person to animate and configurable resolution.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "infinitalk-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/headshot.jpg",
      "audio_url": "https://example.com/speech.mp3",
      "prompt": "A person speaking naturally with expressive facial movements",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | The URL of the audio file. |
| image_url | string | - | URL of the input image. |
| mask_image | string | - | Optional mask image to specify the person in the image to animate. |
| prompt | string | - | The text prompt to guide video generation. |
| resolution | string | 720p | Resolution of the video to generate. Options: `480p`, `720p` |
| seed | integer | - | Random seed for reproducibility. If not provided, a random seed is chosen. |

## Examples

**Basic image animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "infinitalk-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "audio_url": "https://example.com/greeting.mp3"
    }
  }'
```

**With mask and reproducible seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "infinitalk-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/group-photo.jpg",
      "audio_url": "https://example.com/narration.wav",
      "mask_image": "https://example.com/speaker-mask.png",
      "prompt": "The highlighted person speaking with natural head movements",
      "resolution": "720p",
      "seed": 42
    }
  }'
```

## Related Models

- [Infinitalk | Video to Video](../infinitalk-video-to-video/) - Animate an existing video with audio
- [Bytedance | Omnihuman v1.5](../bytedance-omnihuman-v1-5/) - Full body human animation
- [Sync | Lipsync | v2 | Pro](../sync-lipsync-v2-pro/) - Professional lip sync

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
