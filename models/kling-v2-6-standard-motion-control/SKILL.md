---
name: kling-v2-6-standard-motion-control
description: "Kling | v2.6 | Standard | Motion Control. Transfer motion from reference video to a character image using Kling Standard. Triggers: motion control, motion transfer, kling standard, character animation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v2.6 | Standard | Motion Control

Transfer motion from a reference video to a character in an image using the Kling v2.6 Standard model. A cost-effective option for motion transfer that maintains character appearance from the image while following reference video motion.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-standard-motion-control",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/character-portrait.jpg",
      "video_url": "https://example.com/gesture-reference.mp4",
      "prompt": "A person gesturing and talking in a casual setting",
      "keep_original_sound": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| character_orientation | string | - | Controls whether the output character's orientation matches the reference image or video. Options: `image`, `video` |
| image_url | string | - | Reference image URL. The characters and elements in the generated video will match this image. |
| keep_original_sound | boolean | true | Whether to keep the original sound from the reference video. |
| prompt | string | - | Text prompt to guide the generation. |
| video_url | string | - | Reference video URL. The character actions in the generated video will follow this video. |

## Examples

**Basic motion transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-standard-motion-control",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/avatar.jpg",
      "video_url": "https://example.com/wave-hello.mp4"
    }
  }'
```

**With orientation control:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-standard-motion-control",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product-mascot.jpg",
      "video_url": "https://example.com/jumping-reference.mp4",
      "prompt": "A mascot character jumping and celebrating",
      "character_orientation": "video",
      "keep_original_sound": false
    }
  }'
```

## Related Models

- [Kling | v2.6 | Pro | Motion Control](../kling-v2-6-pro-motion-control/) - Pro tier motion control for higher quality
- [Kling | v2.6 | Standard | Motion Control](../kling-v2-6-standard-motion-control/) - Standard motion control
- [Motion Video | 14B](../motion-video-14b/) - Alternative motion video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
