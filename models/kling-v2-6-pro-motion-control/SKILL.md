---
name: kling-v2-6-pro-motion-control
description: "Kling | v2.6 | Pro | Motion Control. Transfer motion from reference video to a character image using Kling Pro. Triggers: motion control, motion transfer, kling pro, character animation"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v2.6 | Pro | Motion Control

Transfer motion from a reference video to a character in an image using the Kling v2.6 Pro model. The generated video maintains the character appearance from the image while following the motion patterns from the reference video.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-pro-motion-control",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/character.jpg",
      "video_url": "https://example.com/dance-reference.mp4",
      "prompt": "A person dancing energetically in a studio",
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
    "model": "kling-v2-6-pro-motion-control",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/model-photo.jpg",
      "video_url": "https://example.com/walking-reference.mp4"
    }
  }'
```

**With character orientation and custom prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-pro-motion-control",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/anime-character.jpg",
      "video_url": "https://example.com/martial-arts.mp4",
      "prompt": "An anime character performing martial arts moves in a dojo",
      "character_orientation": "image",
      "keep_original_sound": false
    }
  }'
```

## Related Models

- [Kling | v2.6 | Standard | Motion Control](../kling-v2-6-standard-motion-control/) - Standard tier motion control
- [Kling | v2.6 | Pro | Image to Video](../kling-v2-6-pro-image-to-video/) - Pro image to video generation
- [Kling | v2.6 | Pro | Text to Video](../kling-v2-6-pro-text-to-video/) - Pro text to video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
