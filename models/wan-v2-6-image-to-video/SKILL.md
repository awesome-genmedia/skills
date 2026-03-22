---
name: wan-v2-6-image-to-video
description: "Wan | v2.6 | Image to Video. Generate videos from images with the Wan v2.6 model featuring multi-shot and audio support. Triggers: image to video, video generation, wan video, animate image"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | v2.6 | Image to Video

Generate videos from images using the Wan v2.6 model. Features LLM prompt expansion, multi-shot segmentation for narrative coherence, background audio support, and resolutions up to 1080p with durations of 5-15 seconds.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/cityscape.jpg",
      "prompt": "Traffic flowing through the city streets, lights blinking, people walking on sidewalks",
      "duration": "5",
      "resolution": "1080p",
      "enable_prompt_expansion": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_url | string | - | URL of the audio to use as background music. Must be publicly accessible. |
| duration | string | 5 | Duration of the generated video in seconds. Options: `5`, `10`, `15` |
| enable_prompt_expansion | boolean | true | Whether to enable prompt rewriting using LLM. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| image_url | string | - | URL of the image to use as the first frame. Must be publicly accessible. |
| multi_shots | boolean | false | When true, enables intelligent multi-shot segmentation. |
| negative_prompt | string | - | Negative prompt to describe content to avoid. Max 500 characters. |
| prompt | string | - | The text prompt describing the desired video motion. Max 800 characters. |
| resolution | string | 1080p | Video resolution. Options: `720p`, `1080p` |
| seed | integer | - | Random seed for reproducibility. |

## Examples

**Basic image to video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/sunset-ocean.jpg",
      "prompt": "Waves rolling in slowly, sun sinking below the horizon"
    }
  }'
```

**Long video with audio and multi-shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/mountain-trail.jpg",
      "prompt": "Camera follows the trail through the forest, birds flying overhead, sunlight filtering through the canopy",
      "audio_url": "https://example.com/nature-ambient.mp3",
      "duration": "15",
      "multi_shots": true,
      "negative_prompt": "blurry, shaky, low quality",
      "resolution": "1080p",
      "seed": 42
    }
  }'
```

## Related Models

- [Wan | v2.6 | Text to Video](../wan-v2-6-text-to-video/) - Generate video from text with Wan v2.6
- [Wan | v2.6 | Reference to Video](../wan-v2-6-reference-to-video/) - Generate video with reference subjects
- [Wan | v2.6 | Image to Image](../wan-v2-6-image-to-image/) - Edit images with Wan v2.6

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
