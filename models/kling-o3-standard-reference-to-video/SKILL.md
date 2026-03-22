---
name: kling-o3-standard-reference-to-video
description: "Kling | o3 | Standard | Reference to Video. Generate videos from reference images and elements with start/end frame control. Triggers: reference to video, kling, o3, standard, reference, video"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | o3 | Standard | Reference to Video

Generate videos using reference images for style and appearance with start/end frame control. Supports elements for character consistency and multi-shot generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A person walking through a garden in the style of @Image1",
      "image_urls": ["https://example.com/art-style.jpg"],
      "start_image_url": "https://example.com/start-frame.jpg",
      "duration": "5",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | false | Aspect ratio of the generated video. enum: 16:9, 9:16, 1:1 |
| duration | string | 5 | Video duration in seconds (3-15s). enum: 3-15 |
| elements | array | false | Optional reference subjects. Use in prompt as @Element1, @Element2. |
| end_image_url | string | false | Image for the last frame. Not used with multi-prompt. |
| generate_audio | boolean | false | Whether to generate native audio for the video. |
| image_urls | array | false | Reference images for style/appearance. Reference as @Image1, @Image2. |
| multi_prompt | array | false | List of prompts for multi-shot generation. |
| prompt | string | false | Text prompt. Either prompt or multi_prompt required. |
| shot_type | string | customize | Multi-shot generation type. enum: customize |
| start_image_url | string | false | Image for the first frame. |

## Examples

**Style-guided video from reference:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A dancer performing ballet in the artistic style of @Image1",
      "image_urls": ["https://example.com/watercolor-style.jpg"],
      "duration": "8",
      "aspect_ratio": "16:9",
      "generate_audio": true
    }
  }'
```

**Start and end frame with reference:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Transition from sunrise to sunset over the ocean",
      "start_image_url": "https://example.com/sunrise.jpg",
      "end_image_url": "https://example.com/sunset.jpg",
      "duration": "10",
      "aspect_ratio": "16:9"
    }
  }'
```

## Related Models

- [kling-o3-pro-reference-to-video](../kling-o3-pro-reference-to-video/) - Kling o3 Pro reference to video
- [kling-o3-standard-text-to-video](../kling-o3-standard-text-to-video/) - Kling o3 Standard text to video
- [kling-o3-standard-image-to-video](../kling-o3-standard-image-to-video/) - Kling o3 Standard image to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
