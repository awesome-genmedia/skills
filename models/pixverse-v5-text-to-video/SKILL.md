---
name: "PixVerse v5 Text to Video"
description: "Generate videos from text using PixVerse v5. Trigger: Use when the user wants to create a video from text with PixVerse, or requests 'pixverse text to video', 'pixverse v5 video', or 'generate video from text pixverse'."
allowed-tools: ["Bash"]
---

# Pixverse v5 | Text to Video

Generate videos from text descriptions using PixVerse v5. Supports multiple aspect ratios, styles, lip-sync TTS, and sound effects.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cat walking through a field of sunflowers on a sunny day",
      "aspect_ratio": "16:9",
      "duration": 5,
      "quality": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `aspect_ratio` | string | `16:9` | Aspect ratio. Options: `16:9`, `4:3`, `1:1`, `3:4`, `9:16` |
| `duration` | integer | `5` | Length of the video in seconds |
| `lip_sync_switch` | boolean | `false` | Enable lip sync feature |
| `lip_sync_tts_content` | string | `false` | TTS content for lip sync, up to ~140 UTF-8 characters |
| `lip_sync_tts_speaker_id` | string | `false` | Speaker ID. Options: `1` (Emily), `2` (James), `3` (Isabella), `4` (Liam), `5` (Chloe), `6` (Adrian), `7` (Harper), `8` (Ava), `9` (Sophia), `10` (Julia), `11` (Mason), `12` (Jack), `13` (Oliver), `14` (Ethan), `Auto` |
| `motion_mode` | string | `normal` | Motion mode. Options: `normal` |
| `negative_prompt` | string | `false` | Things to avoid in the video. Max 2048 characters |
| `prompt` | string | `false` | Text description of the video. Max 2048 characters |
| `quality` | string | `540p` | Resolution quality. Options: `360p`, `540p`, `720p`, `1080p` |
| `seed` | integer | `false` | Random seed for reproducibility |
| `sound_effect_content` | string | `false` | Sound effect description |
| `sound_effect_switch` | boolean | `true` | Enable sound effects |
| `style` | string | `false` | Visual style. Options: `anime`, `3d_animation`, `clay`, `comic`, `cyberpunk` |

## Output

- **Type:** video

## Examples

### Cinematic Scene
```json
{
  "model": "pixverse-v5-text-to-video",
  "version": "0.0.1",
  "input": {
    "prompt": "A majestic eagle soaring over snow-capped mountains at sunrise, cinematic wide shot",
    "aspect_ratio": "16:9",
    "duration": 5,
    "quality": "1080p",
    "negative_prompt": "blurry, low quality, distorted"
  }
}
```

### Anime Style Video
```json
{
  "model": "pixverse-v5-text-to-video",
  "version": "0.0.1",
  "input": {
    "prompt": "A samurai walking through cherry blossom trees with petals falling",
    "aspect_ratio": "16:9",
    "duration": 5,
    "quality": "720p",
    "style": "anime",
    "sound_effect_switch": true,
    "sound_effect_content": "Wind blowing through trees, birds chirping"
  }
}
```

## Related Models

- [PixVerse v5 Image to Video](../pixverse-v5-image-to-video/SKILL.md) - Animate images into videos
- [PixVerse v5 Extend](../pixverse-v5-extend/SKILL.md) - Extend existing videos
- [Runway Gen4 Aleph](../runway-gen4-aleph/SKILL.md) - Alternative text-to-video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
