---
name: kling-v3-standard-image-to-video
description: "Kling | v3 | Standard | Image to Video. Animate images into videos with CFG control, elements, and multi-shot support. Triggers: image to video, kling, v3, standard, animate, i2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v3 | Standard | Image to Video

Animate images into videos using Kling v3 Standard with CFG guidance, start/end frame support, element binding, and native audio generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The scene comes alive as wind blows through the trees and birds fly across the sky",
      "start_image_url": "https://example.com/forest-scene.jpg",
      "duration": "5",
      "aspect_ratio": "16:9",
      "generate_audio": true,
      "cfg_scale": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of the generated video. enum: 16:9, 9:16, 1:1 |
| cfg_scale | number | 0.5 | Classifier Free Guidance scale. Controls prompt adherence. |
| duration | string | 5 | Video duration in seconds. enum: 3-15 |
| elements | array | false | Elements (characters/objects) to include in the video. |
| end_image_url | string | false | URL of the end frame image. |
| generate_audio | boolean | true | Generate native audio. Supports Chinese and English voices. |
| multi_prompt | array | false | List of prompts for multi-shot generation. |
| negative_prompt | string | false | Negative prompt. Default: blur, distort, and low quality. |
| prompt | string | false | Text prompt for video generation. |
| shot_type | string | customize | Multi-shot generation type. enum: customize |
| start_image_url | string | false | URL of the start frame image. |
| voice_ids | array | false | Optional Voice IDs. Reference voices in prompt with << >>. |

## Examples

**Animate a landscape:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Waves gently lap the shore as the sun sinks below the horizon",
      "start_image_url": "https://example.com/sunset-beach.jpg",
      "duration": "10",
      "aspect_ratio": "16:9",
      "cfg_scale": 0.5
    }
  }'
```

**Start-to-end frame transition:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A timelapse showing the seasons changing from summer to winter",
      "start_image_url": "https://example.com/summer-park.jpg",
      "end_image_url": "https://example.com/winter-park.jpg",
      "duration": "8",
      "generate_audio": false,
      "negative_prompt": "blurry, flickering, low quality"
    }
  }'
```

## Related Models

- [kling-v3-pro-image-to-video](../kling-v3-pro-image-to-video/) - Kling v3 Pro image to video
- [kling-v3-standard-text-to-video](../kling-v3-standard-text-to-video/) - Kling v3 Standard text to video
- [kling-o3-standard-image-to-video](../kling-o3-standard-image-to-video/) - Kling o3 Standard image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
