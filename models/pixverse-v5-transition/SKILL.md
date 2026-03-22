---
name: "PixVerse v5 Transition"
description: "Create video transitions between two images using PixVerse v5. Trigger: Use when the user wants to create a video transition, or requests 'pixverse transition', 'image transition video', 'morph between images', or 'transition effect'."
allowed-tools: ["Bash"]
---

# PixVerse v5 | Transition

Create smooth video transitions between two images. Optionally add lip-sync TTS and sound effects for richer output.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-transition",
    "version": "0.0.1",
    "input": {
      "first_frame_url": "https://example.com/scene-a.jpg",
      "last_frame_url": "https://example.com/scene-b.jpg",
      "prompt": "A smooth cinematic transition from day to night",
      "duration": 5,
      "quality": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `duration` | integer | `5` | Duration of the transition video |
| `first_frame_url` | string | `false` | URL of the first frame image |
| `last_frame_url` | string | `false` | URL of the last frame image |
| `lip_sync_switch` | boolean | `false` | Enable lip sync feature |
| `lip_sync_tts_content` | string | `false` | TTS content for lip sync, up to ~140 UTF-8 characters |
| `lip_sync_tts_speaker_id` | string | `false` | Speaker ID for TTS. Options: `1` (Emily), `2` (James), `3` (Isabella), `4` (Liam), `5` (Chloe), `6` (Adrian), `7` (Harper), `8` (Ava), `9` (Sophia), `10` (Julia), `11` (Mason), `12` (Jack), `13` (Oliver), `14` (Ethan), `Auto` |
| `motion_mode` | string | `normal` | Motion mode. Options: `normal` |
| `prompt` | string | `false` | Text prompt guiding the transition |
| `quality` | string | `540p` | Resolution quality. Options: `360p`, `540p`, `720p`, `1080p` |
| `seed` | integer | `false` | Random seed for reproducibility |
| `sound_effect_content` | string | `false` | Sound effect description |
| `sound_effect_switch` | boolean | `true` | Enable sound effects |

## Output

- **Type:** video

## Examples

### Day to Night Transition
```json
{
  "model": "pixverse-v5-transition",
  "version": "0.0.1",
  "input": {
    "first_frame_url": "https://example.com/daytime-city.jpg",
    "last_frame_url": "https://example.com/nighttime-city.jpg",
    "prompt": "Time-lapse transition from bright day to glowing neon night",
    "duration": 5,
    "quality": "1080p"
  }
}
```

### Transition with TTS
```json
{
  "model": "pixverse-v5-transition",
  "version": "0.0.1",
  "input": {
    "first_frame_url": "https://example.com/speaker-a.jpg",
    "last_frame_url": "https://example.com/speaker-b.jpg",
    "prompt": "A smooth transformation between two speakers",
    "duration": 5,
    "quality": "720p",
    "lip_sync_switch": true,
    "lip_sync_tts_content": "Watch as one scene transforms into the next",
    "lip_sync_tts_speaker_id": "1"
  }
}
```

## Related Models

- [PixVerse v5 Text to Video](../pixverse-v5-text-to-video/SKILL.md) - Generate videos from text
- [PixVerse v5 Image to Video](../pixverse-v5-image-to-video/SKILL.md) - Animate images into videos
- [PixVerse v5 Extend](../pixverse-v5-extend/SKILL.md) - Extend existing videos

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
