---
name: veed-fabric-1-0
description: "Veed | Fabric 1.0. Generate videos from image and audio inputs using Veed Fabric 1.0. Triggers: veed, fabric, image to video, audio video, veed fabric"
allowed-tools: Bash(curl *), WebFetch
---

# Veed | Fabric 1.0

Generate videos by combining image and audio inputs using Veed Fabric 1.0. Create talking head videos or animated scenes by providing a source image and optional audio track.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veed-fabric-1-0",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/headshot.jpg",
      "audio_url": "https://example.com/speech-clip.mp3",
      "resolution": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | | URL of the audio file to sync with the video |
| image_url | string | | URL of the source image |
| resolution | string | 720p | Resolution of the output video. enum: 480p, 720p |

## Examples

**Talking head video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veed-fabric-1-0",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/presenter.jpg",
      "audio_url": "https://example.com/narration.mp3",
      "resolution": "720p"
    }
  }'
```

**Quick preview at lower resolution:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veed-fabric-1-0",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/avatar.jpg",
      "audio_url": "https://example.com/greeting.wav",
      "resolution": "480p"
    }
  }'
```

## Related Models

- [heygen-video-translate](../heygen-video-translate/) - Video translation with lip-sync
- [elevenlabs-text-to-dialogue](../elevenlabs-text-to-dialogue/) - Generate audio for Fabric input

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
