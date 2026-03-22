---
name: kling-v3-pro-image-to-video
description: "Kling | v3 | Pro | Image to Video. Pro-quality image animation with CFG control, elements, and multi-shot support. Triggers: image to video, kling, v3, pro, animate, i2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v3 | Pro | Image to Video

Animate images into high-quality videos using Kling v3 Pro with CFG guidance, start/end frame support, element binding, voice IDs, and native audio generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic eagle takes flight from the cliff edge, soaring over the valley",
      "start_image_url": "https://example.com/eagle-on-cliff.jpg",
      "duration": "8",
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

**High-quality image animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The waterfall cascades down the rocks as mist rises into the air",
      "start_image_url": "https://example.com/waterfall.jpg",
      "duration": "12",
      "aspect_ratio": "9:16",
      "cfg_scale": 0.6,
      "generate_audio": true
    }
  }'
```

**Morph between two images:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A smooth transformation from day to night in the city",
      "start_image_url": "https://example.com/city-day.jpg",
      "end_image_url": "https://example.com/city-night.jpg",
      "duration": "8",
      "negative_prompt": "flickering, jumpy, blurry"
    }
  }'
```

**Short character animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-image-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The character turns to the camera and winks",
      "start_image_url": "https://example.com/character-portrait.png",
      "duration": "3",
      "aspect_ratio": "1:1",
      "generate_audio": false
    }
  }'
```

## Related Models

- [kling-v3-standard-image-to-video](../kling-v3-standard-image-to-video/) - Standard tier image to video
- [kling-v3-pro-text-to-video](../kling-v3-pro-text-to-video/) - Kling v3 Pro text to video
- [kling-o3-pro-image-to-video](../kling-o3-pro-image-to-video/) - Kling o3 Pro image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
