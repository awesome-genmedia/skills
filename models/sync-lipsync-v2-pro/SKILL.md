---
name: sync-lipsync-v2-pro
description: "Sync | Lipsync | v2 | Pro. Professional lip sync for video with audio replacement. Triggers: lip sync, lipsync, audio sync, video dubbing, sync"
allowed-tools: Bash(curl *), WebFetch
---

# Sync | Lipsync | v2 | Pro

Professional lip sync solution that synchronizes video with a new audio track. Supports multiple sync modes for handling duration mismatches between audio and video, including cut_off, loop, bounce, silence, and remap.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sync-lipsync-v2-pro",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/talking-person.mp4",
      "audio_url": "https://example.com/new-voiceover.mp3",
      "sync_mode": "cut_off"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | URL of the input audio. |
| sync_mode | string | cut_off | Lipsync mode when audio and video durations are out of sync. Options: `cut_off`, `loop`, `bounce`, `silence`, `remap` |
| video_url | string | - | URL of the input video. |

## Examples

**Basic lip sync:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sync-lipsync-v2-pro",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/presenter.mp4",
      "audio_url": "https://example.com/script-reading.mp3"
    }
  }'
```

**Lip sync with loop mode for shorter video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sync-lipsync-v2-pro",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/short-clip.mp4",
      "audio_url": "https://example.com/long-narration.mp3",
      "sync_mode": "loop"
    }
  }'
```

**Lip sync with remap for timing adjustment:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "sync-lipsync-v2-pro",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/interview.mp4",
      "audio_url": "https://example.com/translated-audio.mp3",
      "sync_mode": "remap"
    }
  }'
```

## Related Models

- [Infinitalk | Video to Video](../infinitalk-video-to-video/) - Video-based talking head animation
- [Infinitalk | Image to Video](../infinitalk-image-to-video/) - Image-based talking head animation
- [Bytedance | Omnihuman v1.5](../bytedance-omnihuman-v1-5/) - Human animation from audio and image

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
