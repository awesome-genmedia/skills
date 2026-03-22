---
name: seedance-v1-5-pro-text-to-video
description: "Seedance V1.5 | Pro | Text to Video. Generate videos from text prompts with audio and camera control. Triggers: text to video, video generation, seedance, ai video"
allowed-tools: Bash(curl *), WebFetch
---

# Seedance V1.5 | Pro | Text to Video

Generate videos from text prompts using the Seedance V1.5 Pro model. Features automatic audio generation, camera position control, flexible aspect ratios, and resolutions up to 1080p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-5-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cinematic drone shot over a misty mountain range at sunrise, golden light breaking through the clouds",
      "aspect_ratio": "16:9",
      "resolution": "720p",
      "duration": 5,
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. Options: `21:9`, `16:9`, `4:3`, `1:1`, `3:4`, `9:16` |
| camera_fixed | boolean | false | Whether to fix the camera position. |
| duration | integer | 5 | Duration of the video in seconds. |
| generate_audio | boolean | true | Whether to generate audio for the video. |
| prompt | string | - | The text prompt used to generate the video. |
| resolution | string | 720p | Video resolution. Options: `480p`, `720p`, `1080p` |
| seed | integer | - | Random seed to control video generation. Use -1 for random. |

## Examples

**Simple text-to-video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-5-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A butterfly landing on a wildflower in a meadow"
    }
  }'
```

**Cinematic widescreen with fixed camera:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "seedance-v1-5-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Rain falling on a quiet cobblestone street in Paris, reflections in puddles, warm streetlights",
      "aspect_ratio": "21:9",
      "resolution": "1080p",
      "camera_fixed": true,
      "duration": 5,
      "generate_audio": true,
      "seed": 2024
    }
  }'
```

## Related Models

- [Seedance V1.5 | Pro | Image to Video](../seedance-v1-5-pro-image-to-video/) - Generate videos from images with Seedance V1.5
- [Wan | v2.6 | Text to Video](../wan-v2-6-text-to-video/) - Wan-based text to video
- [Kandinsky 5 | Pro | Text to Video](../kandinsky5-pro-text-to-video/) - Kandinsky-based text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
