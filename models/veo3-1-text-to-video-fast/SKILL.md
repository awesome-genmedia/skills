---
name: veo3-1-text-to-video-fast
description: "Veo 3.1 | Text to Video | Fast. Quickly generate videos from text prompts with audio using Veo 3.1 Fast. Triggers: veo, text to video, fast video, veo fast, google veo"
allowed-tools: Bash(curl *), WebFetch
---

# Veo 3.1 | Text to Video | Fast

Quickly generate videos from text descriptions with optional audio using the Veo 3.1 Fast model. Supports prompt enhancement, negative prompts, and seed-based reproducibility.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-text-to-video-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A drone shot flying over a coral reef with tropical fish swimming below crystal-clear water",
      "duration": 8,
      "resolution": "720p",
      "generate_audio": true,
      "enhance_prompt": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. enum: 9:16, 16:9 |
| auto_fix | boolean | true | Whether to automatically fix prompts that fail content policy |
| duration | integer | 8 | The duration of the generated video in seconds |
| enhance_prompt | boolean | true | Whether to enhance the video generation prompt |
| generate_audio | boolean | true | Whether to generate audio. If false, 33% less credits used |
| negative_prompt | string | | A negative prompt to guide the video generation |
| prompt | string | | The text prompt describing the video |
| resolution | string | 720p | The resolution of the generated video. enum: 720p, 1080p |
| seed | integer | | A seed for reproducible video generation |

## Examples

**Cinematic scene with negative prompt:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-text-to-video-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A samurai standing in a cherry blossom garden, petals falling, cinematic lighting",
      "negative_prompt": "blurry, low quality, distorted faces",
      "duration": 8,
      "resolution": "1080p",
      "generate_audio": true,
      "enhance_prompt": true
    }
  }'
```

**Reproducible vertical video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo3-1-text-to-video-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A barista making latte art in a cozy coffee shop, close-up of the milk pour",
      "aspect_ratio": "9:16",
      "duration": 8,
      "resolution": "720p",
      "generate_audio": true,
      "seed": 54321
    }
  }'
```

## Related Models

- [veo3-1-text-to-video](../veo3-1-text-to-video/) - Standard quality text to video
- [veo3-1-image-to-video-fast](../veo3-1-image-to-video-fast/) - Fast image to video
- [veo3-1-first-last-frame-to-video-fast](../veo3-1-first-last-frame-to-video-fast/) - Fast first/last frame to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
