---
name: kling-v3-pro-motion-control
description: "Kling | v3 | Pro | Motion Control. Pro-quality video generation with motion from reference video and character from reference image. Triggers: motion control, kling, v3, pro, video, animation, character"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v3 | Pro | Motion Control

Generate high-quality videos by combining a reference image (for appearance) with a reference video (for motion). Pro tier delivers superior quality for character motion transfer.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-motion-control",
    "version": "0.0.1",
    "input": {
      "prompt": "A character performing a ballet routine",
      "image_url": "https://example.com/ballerina.jpg",
      "video_url": "https://example.com/ballet-reference.mp4",
      "character_orientation": "video",
      "keep_original_sound": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| character_orientation | string | video | Controls whether output character orientation matches the reference image or video. enum: image, video |
| elements | array | false | Optional element for facial consistency binding. |
| image_url | string | false | Reference image URL. Characters and elements in the generated video match this image. |
| keep_original_sound | boolean | true | Whether to keep the original sound from the reference video. |
| prompt | string | false | Text prompt describing the desired output. |
| video_url | string | false | Reference video URL. Character actions in the generated video follow this video. |

## Examples

**High-quality dance motion transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-motion-control",
    "version": "0.0.1",
    "input": {
      "prompt": "An anime character performing a dramatic sword fight sequence",
      "image_url": "https://example.com/anime-warrior.png",
      "video_url": "https://example.com/sword-fight.mp4",
      "character_orientation": "video"
    }
  }'
```

**Character animation with image orientation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-motion-control",
    "version": "0.0.1",
    "input": {
      "prompt": "A person giving a presentation and gesturing with hands",
      "image_url": "https://example.com/business-person.jpg",
      "video_url": "https://example.com/presentation-gestures.mp4",
      "character_orientation": "image",
      "keep_original_sound": false
    }
  }'
```

## Related Models

- [kling-v3-standard-motion-control](../kling-v3-standard-motion-control/) - Standard tier motion control
- [kling-v3-pro-image-to-video](../kling-v3-pro-image-to-video/) - Kling v3 Pro image to video
- [kling-v3-pro-text-to-video](../kling-v3-pro-text-to-video/) - Kling v3 Pro text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
