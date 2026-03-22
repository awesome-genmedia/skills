---
name: kling-o1-video-to-video-reference
description: "Kling O1 | Video to Video Reference. Transform videos using reference images and elements. Triggers: video to video, kling, o1, style transfer, video editing"
allowed-tools: Bash(curl *), WebFetch
---

# Kling O1 | Video to Video Reference

Transform existing videos using reference images and elements for style and appearance control. Reference elements with @Element1 and images with @Image1 in prompts.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-video-to-video-reference",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/original-video.mp4",
      "prompt": "transform into anime style with @Image1 color palette",
      "image_urls": ["https://example.com/style-ref.jpg"],
      "duration": "5",
      "aspect_ratio": "16:9"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | auto | The aspect ratio of the generated video frame. enum: auto, 16:9, 9:16, 1:1 |
| duration | string | 5 | Video duration in seconds. enum: 5, 10 |
| elements | array | | Elements (characters/objects) to include. Reference in prompt as @Element1, @Element2. |
| image_urls | array | | Reference images for style/appearance. Reference in prompt as @Image1, @Image2. |
| keep_audio | boolean | false | Whether to keep the original audio from the video. |
| prompt | string | | Use @Element1, @Element2 to reference elements and @Image1, @Image2 to reference images. |
| video_url | string | | Reference video URL. Only .mp4/.mov formats, 3-10 seconds duration, 720p+. |

## Examples

**Style transfer with audio preservation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-video-to-video-reference",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/interview.mp4",
      "prompt": "apply watercolor painting style from @Image1",
      "image_urls": ["https://example.com/watercolor-style.jpg"],
      "keep_audio": true,
      "duration": "10"
    }
  }'
```

**Character replacement with elements:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o1-video-to-video-reference",
    "version": "0.0.1",
    "input": {
      "video_url": "https://example.com/scene.mp4",
      "prompt": "replace the main character with @Element1 walking through the scene",
      "elements": [{"image_url": "https://example.com/character.jpg"}],
      "aspect_ratio": "16:9",
      "duration": "5"
    }
  }'
```

## Related Models

- [Kling O1 | Video to Video | Edit](../kling-o1-video-to-video-edit/) - Direct video editing
- [Kling O1 | Image to Video](../kling-o1-image-to-video/) - Image-to-video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
