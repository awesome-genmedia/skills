---
name: creatify-aurora
description: "Creatify | Aurora. Generate videos from images, audio, and text prompts using Creatify Aurora. Triggers: video generation, creatify, aurora, image to video, audio to video"
allowed-tools: Bash(curl *), WebFetch
---

# Creatify | Aurora

Generate videos using the Creatify Aurora model. Combine images, audio, and text prompts with configurable guidance scales for precise control over text and audio adherence.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "creatify-aurora",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/product-photo.jpg",
      "prompt": "The product rotates slowly on a display stand with soft studio lighting",
      "resolution": "720p",
      "guidance_scale": 1
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_guidance_scale | number | 2 | Guidance scale for audio adherence. |
| audio_url | string | - | The URL of the audio file to be used for video generation. |
| guidance_scale | number | 1 | Guidance scale for text prompt adherence. |
| image_url | string | - | The URL of the image file to be used for video generation. |
| prompt | string | - | A text prompt to guide the video generation process. |
| resolution | string | 720p | The resolution of the generated video. Options: `480p`, `720p` |

## Examples

**Image-based video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "creatify-aurora",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "Clouds drifting across the sky, trees swaying gently"
    }
  }'
```

**Audio-driven video with custom guidance:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "creatify-aurora",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/concert-stage.jpg",
      "audio_url": "https://example.com/rock-music.mp3",
      "prompt": "Energetic concert scene with stage lights flashing to the beat",
      "audio_guidance_scale": 3,
      "guidance_scale": 1.5,
      "resolution": "720p"
    }
  }'
```

## Related Models

- [Wan | v2.6 | Image to Video](../wan-v2-6-image-to-video/) - Wan-based image to video
- [Seedance V1.5 | Pro | Image to Video](../seedance-v1-5-pro-image-to-video/) - Seedance image to video
- [Motion | Fast](../motion-fast/) - Fast motion video generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
