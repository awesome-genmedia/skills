---
name: veo3-1-reference-to-video
description: "Veo 3.1 | Reference to Video. Generate videos with consistent subject appearance from reference images using Veo 3.1. Triggers: veo, reference to video, veo 3.1, subject consistency, video generation"
allowed-tools: Bash(curl *), WebFetch
---

# Veo 3.1 | Reference to Video

Generate videos with consistent subject appearance using reference images with Veo 3.1. Provide reference images for the subject and a text prompt to create videos maintaining visual consistency.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The person walks through a bustling market, picking up a piece of fruit and examining it",
      "image_urls": ["https://example.com/reference-face.jpg"],
      "duration": 8,
      "resolution": "720p",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of the generated video. enum: 16:9 |
| auto_fix | boolean | false | Whether to automatically attempt to fix prompts that fail content policy |
| duration | integer | 8 | The duration of the generated video in seconds |
| generate_audio | boolean | true | Whether to generate audio for the video. If false, 33% less credits used |
| image_urls | array | | URLs of the reference images for consistent subject appearance |
| prompt | string | | The text prompt describing the video |
| resolution | string | 720p | Resolution of the generated video. enum: 720p, 1080p |

## Examples

**Character-consistent narrative video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The character gives a passionate speech at a podium in front of a large audience",
      "image_urls": ["https://example.com/character-front.jpg", "https://example.com/character-side.jpg"],
      "duration": 8,
      "resolution": "1080p",
      "generate_audio": true,
      "auto_fix": true
    }
  }'
```

**Silent reference video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The subject sits at a desk writing in a journal, warm lamp light, cozy room",
      "image_urls": ["https://example.com/person-reference.jpg"],
      "duration": 8,
      "resolution": "720p",
      "generate_audio": false
    }
  }'
```

## Related Models

- [veo3-1-text-to-video](../veo3-1-text-to-video/) - Text to video with Veo 3.1
- [veo3-1-image-to-video](../veo3-1-image-to-video/) - Image to video with Veo 3.1
- [veo3-1-first-last-frame-to-video](../veo3-1-first-last-frame-to-video/) - First/last frame to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
