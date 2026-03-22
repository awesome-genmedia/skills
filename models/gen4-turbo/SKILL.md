---
name: gen4-turbo
description: "Runway | Gen4 | Turbo. Generate videos from text and images using Runway Gen4 Turbo. Fast AI video generation with prompt and optional first frame control. Triggers: runway gen4, gen4 turbo, runway video, text to video, image to video, ai video generation, runway turbo"
allowed-tools: Bash(curl *), WebFetch
---

# Runway | Gen4 | Turbo

Generate videos from text prompts and optional reference images using Runway Gen4 Turbo. This fast video generation model supports multiple aspect ratios and durations, with the ability to use an initial image as the first frame.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gen4-turbo",
    "version": "0.0.1",
    "input": {
      "prompt": "A golden retriever running through a field of wildflowers in slow motion, cinematic lighting",
      "aspect_ratio": "16:9",
      "duration": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of the output video. Options: `16:9`, `9:16`, `4:3`, `3:4`, `1:1`, `21:9` |
| duration | integer | 5 | Duration of the generated video in seconds |
| image | string | - | Initial image for video generation (used as first frame) |
| prompt | string | - | Text prompt for video generation |
| seed | integer | - | Random seed for reproducible generation |

## Examples

**Text-to-video cinematic scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gen4-turbo",
    "version": "0.0.1",
    "input": {
      "prompt": "A drone flying over a futuristic city at night, neon lights reflecting on wet streets, cyberpunk atmosphere",
      "aspect_ratio": "21:9",
      "duration": 5
    }
  }'
```

**Image-to-video with first frame:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gen4-turbo",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/beach-sunset.jpg",
      "prompt": "Waves gently lapping at the shore, sun slowly setting, warm golden light",
      "aspect_ratio": "16:9",
      "duration": 5
    }
  }'
```

**Vertical video for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "gen4-turbo",
    "version": "0.0.1",
    "input": {
      "prompt": "A person walking down a neon-lit alley in Tokyo at night, rain falling, reflections on the ground",
      "aspect_ratio": "9:16",
      "seed": 7890
    }
  }'
```

## Related Models

- [Runway | Gen4 | Image](../runway-gen4-image/) - Generate images with Runway Gen4
- [Google Veo 3](../veo-3/) - Google's text-to-video model
- [Kling v2.1 | Master | Text to Video](../kling-v2-1-master-text-to-video/) - Kling's premium text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
