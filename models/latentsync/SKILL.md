---
name: "LatentSync"
description: "Generate lip-synced videos by combining audio with existing video. Trigger: Use when the user wants to add lip sync to a video, or requests 'latentsync', 'lip sync', 'sync lips to audio', or 'dub video with audio'."
allowed-tools: ["Bash"]
---

# LatentSync

Synchronize lip movements in a video to match provided audio. Supports loop modes for cases where the audio is longer than the video.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "latentsync",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/talking-head.mp4",
      "audio_url": "https://example.com/new-dialogue.mp3",
      "guidance_scale": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `audio_url` | string | (empty) | The URL of the audio to generate the lip sync for |
| `guidance_scale` | number | `1` | Guidance scale for the model inference |
| `loop_mode` | string | (empty) | Video loop mode when audio is longer than video. Options: `pingpong`, `loop` |
| `seed` | integer | (empty) | Random seed for generation. If None, a random seed will be used |
| `video_url` | string | (empty) | The URL of the video to generate the lip sync for |

## Output

- **Type:** video

## Examples

### Basic Lip Sync
```json
{
  "model": "latentsync",
  "version": "0.0.1",
  "input": {
    "video_url": "https://example.com/speaker.mp4",
    "audio_url": "https://example.com/new-speech.mp3",
    "guidance_scale": 1,
    "seed": 123
  }
}
```

### Looped Lip Sync for Longer Audio
```json
{
  "model": "latentsync",
  "version": "0.0.1",
  "input": {
    "video_url": "https://example.com/short-clip.mp4",
    "audio_url": "https://example.com/long-narration.mp3",
    "guidance_scale": 1.5,
    "loop_mode": "pingpong"
  }
}
```

## Related Models

- [EchoMimic V3](../echomimic-v3/SKILL.md) - Generate talking head videos from images
- [Kling V1 Pro AI Avatar](../kling-v1-pro-ai-avatar/SKILL.md) - AI avatar video generation
- [Character 3](../character-3/SKILL.md) - Audio-driven character video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
