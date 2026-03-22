---
name: "PixVerse v5 Image to Video"
description: "Generate videos from images using PixVerse v5. Trigger: Use when the user wants to animate an image with PixVerse, or requests 'pixverse image to video', 'animate image pixverse', or 'pixverse v5 image animation'."
allowed-tools: ["Bash"]
---

# PixVerse v5 | Image to Video

Animate a still image into a video using PixVerse v5. Supports lip-sync TTS, sound effects, multiple styles, and quality levels.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "pixverse-v5-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "Waves gently crash on the shore as seagulls fly overhead",
      "duration": 5,
      "quality": "720p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `duration` | integer | `5` | Duration of the video in seconds |
| `image_url` | string | `false` | URL of the input image |
| `lip_sync_switch` | boolean | `false` | Enable lip sync feature |
| `lip_sync_tts_content` | string | `false` | TTS content for lip sync, up to ~140 UTF-8 characters |
| `lip_sync_tts_speaker_id` | string | `false` | Speaker ID. Options: `1` (Emily), `2` (James), `3` (Isabella), `4` (Liam), `5` (Chloe), `6` (Adrian), `7` (Harper), `8` (Ava), `9` (Sophia), `10` (Julia), `11` (Mason), `12` (Jack), `13` (Oliver), `14` (Ethan), `Auto` |
| `motion_mode` | string | `normal` | Motion mode. Options: `normal` |
| `negative_prompt` | string | `false` | Things to avoid in the video |
| `prompt` | string | `false` | Text prompt guiding the animation |
| `quality` | string | `540p` | Resolution quality. Options: `360p`, `540p`, `720p`, `1080p` |
| `seed` | integer | `false` | Random seed for reproducibility |
| `sound_effect_content` | string | `false` | Sound effect description |
| `sound_effect_switch` | boolean | `true` | Enable sound effects |
| `style` | string | `false` | Visual style. Options: `anime`, `3d_animation`, `clay`, `comic`, `cyberpunk` |

## Output

- **Type:** video

## Examples

### Nature Animation
```json
{
  "model": "pixverse-v5-image-to-video",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/forest.jpg",
    "prompt": "Wind blows through the trees, leaves rustling gently",
    "duration": 5,
    "quality": "1080p",
    "sound_effect_switch": true,
    "sound_effect_content": "Wind and rustling leaves"
  }
}
```

### Talking Character with TTS
```json
{
  "model": "pixverse-v5-image-to-video",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/character-portrait.jpg",
    "prompt": "A character speaking warmly to the viewer",
    "duration": 5,
    "quality": "720p",
    "lip_sync_switch": true,
    "lip_sync_tts_content": "Hello! Welcome to our channel. Today we have something special for you.",
    "lip_sync_tts_speaker_id": "1",
    "style": "anime"
  }
}
```

## Related Models

- [PixVerse v5 Text to Video](../pixverse-v5-text-to-video/SKILL.md) - Generate videos from text
- [PixVerse v5 Extend](../pixverse-v5-extend/SKILL.md) - Extend existing videos
- [Wan v2.2 A14B Image to Video](../wan-v2-2-a14b-image-to-video/SKILL.md) - Alternative image-to-video

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
