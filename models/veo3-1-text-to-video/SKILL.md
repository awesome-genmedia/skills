---
name: veo3-1-text-to-video
description: "Veo 3.1 | Text to Video. Generate high-quality videos from text prompts with audio using Google Veo 3.1. Triggers: veo, text to video, veo 3.1, video generation, google veo"
allowed-tools: Bash(curl *), WebFetch
---

# Veo 3.1 | Text to Video

Generate high-quality videos from text descriptions with optional audio using Google Veo 3.1. Supports prompt enhancement, negative prompts, and seed-based reproducibility for maximum control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A group of friends laughing around a campfire under a starry sky, warm orange glow on their faces",
      "duration": 8,
      "resolution": "1080p",
      "generate_audio": true,
      "enhance_prompt": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 9:16, 16:9 |
| auto_fix | boolean | true | Whether to automatically fix prompts that fail content policy |
| duration | integer | 8 | The duration of the generated video in seconds |
| enhance_prompt | boolean | true | Whether to enhance the video generation prompt |
| generate_audio | boolean | true | Whether to generate audio. If false, 33% less credits used |
| negative_prompt | string | | A negative prompt to guide the video generation |
| prompt | string | | The text prompt describing the video |
| resolution | string | 720p | The resolution of the generated video. enum: 720p, 1080p |
| seed | integer | | A seed for reproducible video generation |

## Examples

**Epic cinematic scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "An astronaut floating in space above Earth, the sun rising behind the planet, dramatic orchestral music atmosphere",
      "negative_prompt": "low quality, blurry, shaky camera",
      "duration": 8,
      "resolution": "1080p",
      "generate_audio": true,
      "enhance_prompt": true,
      "auto_fix": true
    }
  }'
```

**Vertical content without audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Slow-motion pouring of honey onto a stack of pancakes with berries, food photography style",
      "aspect_ratio": "9:16",
      "duration": 8,
      "resolution": "720p",
      "generate_audio": false,
      "seed": 98765
    }
  }'
```

## Related Models

- [veo3-1-text-to-video-fast](../veo3-1-text-to-video-fast/) - Fast text to video
- [veo3-1-image-to-video](../veo3-1-image-to-video/) - Image to video
- [veo3-1-reference-to-video](../veo3-1-reference-to-video/) - Reference to video with subject consistency
- [veo3-1-first-last-frame-to-video](../veo3-1-first-last-frame-to-video/) - First/last frame to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
