---
name: kling-v3-standard-motion-control
description: "Kling | v3 | Standard | Motion Control. Generate videos with motion from reference video and character from reference image. Triggers: motion control, kling, v3, video, animation, character"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v3 | Standard | Motion Control

Generate videos by combining a reference image (for appearance) with a reference video (for motion). Transfer character actions from a video onto a new character from an image.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-motion-control",
    "version": "0.0.1",
    "input": {
      "prompt": "A person dancing gracefully",
      "image_url": "https://example.com/character.jpg",
      "video_url": "https://example.com/dance-reference.mp4",
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

**Dance motion transfer:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-motion-control",
    "version": "0.0.1",
    "input": {
      "prompt": "A character performing an energetic hip-hop dance",
      "image_url": "https://example.com/cartoon-character.png",
      "video_url": "https://example.com/hiphop-dance.mp4",
      "character_orientation": "video"
    }
  }'
```

**Motion transfer with image orientation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-motion-control",
    "version": "0.0.1",
    "input": {
      "prompt": "A person waving and smiling at the camera",
      "image_url": "https://example.com/portrait.jpg",
      "video_url": "https://example.com/waving-motion.mp4",
      "character_orientation": "image",
      "keep_original_sound": false
    }
  }'
```

## Related Models

- [kling-v3-pro-motion-control](../kling-v3-pro-motion-control/) - Kling v3 Pro motion control (higher quality)
- [kling-v3-standard-image-to-video](../kling-v3-standard-image-to-video/) - Kling v3 Standard image to video
- [kling-v3-standard-text-to-video](../kling-v3-standard-text-to-video/) - Kling v3 Standard text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
