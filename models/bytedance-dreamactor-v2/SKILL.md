---
name: bytedance-dreamactor-v2
description: "ByteDance | DreamActor | v2. Animate reference images using driving videos for motion transfer. Triggers: animation, dreamactor, bytedance, motion transfer, animate, video"
allowed-tools: Bash(curl *), WebFetch
---

# ByteDance | DreamActor | v2

Animate reference images using driving template videos. Transfer motion, facial expressions, and gestures from a driving video to a reference image of people, animation characters, or pets.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-dreamactor-v2",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/portrait.jpg",
      "video_url": "https://example.com/dance-template.mp4",
      "cut_result_first_second_switch": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| cut_result_first_second_switch | boolean | true | Whether to crop the first second of the output video (has a 1-second warmup). |
| image_url | string | | URL of the reference image to animate. Supports real people, animation, pets. |
| video_url | string | | URL of the driving template video providing motion, expressions, and gestures. |

## Examples

**Animate a portrait with dance motion:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-dreamactor-v2",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/headshot.jpg",
      "video_url": "https://example.com/dance-video.mp4",
      "cut_result_first_second_switch": true
    }
  }'
```

**Animate an anime character:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "bytedance-dreamactor-v2",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/anime-character.png",
      "video_url": "https://example.com/talking-head.mp4",
      "cut_result_first_second_switch": false
    }
  }'
```

## Related Models

- [kling-v3-standard-motion-control](../kling-v3-standard-motion-control/) - Kling motion control
- [kling-v3-pro-motion-control](../kling-v3-pro-motion-control/) - Kling Pro motion control

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
