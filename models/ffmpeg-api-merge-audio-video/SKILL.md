---
name: ffmpeg-api-merge-audio-video
description: "Ffmpeg Api | Merge Audio Video. Merge an audio track with a video file. Triggers: merge audio video, combine audio video, ffmpeg merge, add audio to video"
allowed-tools: Bash(curl *), WebFetch
---

# Ffmpeg Api | Merge Audio Video

Merge an audio file with a video file into a single output video. Supports configurable start offset for audio synchronization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ffmpeg-api-merge-audio-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/silent-video.mp4",
      "audio_url": "https://example.com/background-music.mp3",
      "start_offset": 0
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | URL of the audio file to use as the audio track. |
| start_offset | number | 0 | Offset in seconds for when the audio should start relative to the video. |
| video_url | string | - | URL of the video file to use as the video track. |

## Examples

**Merge audio and video with no offset:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ffmpeg-api-merge-audio-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/timelapse.mp4",
      "audio_url": "https://example.com/ambient-music.mp3"
    }
  }'
```

**Merge with audio starting 5 seconds in:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ffmpeg-api-merge-audio-video",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/presentation.mp4",
      "audio_url": "https://example.com/narration.wav",
      "start_offset": 5
    }
  }'
```

## Related Models

- [Extract Frame](../extract-frame/) - Extract frames from a video
- [Merge Videos](../merge-videos/) - Merge multiple videos together

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
