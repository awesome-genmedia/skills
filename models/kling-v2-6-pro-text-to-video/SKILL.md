---
name: kling-v2-6-pro-text-to-video
description: "Kling | v2.6 | Pro | Text to Video. Generate videos from text prompts with configurable aspect ratio and duration. Triggers: text to video, kling, video generation, t2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v2.6 | Pro | Text to Video

Generate high-quality videos from text prompts with configurable aspect ratio, duration, and CFG guidance. Supports native audio generation in Chinese and English.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "a drone flying over a tropical rainforest, cinematic",
      "aspect_ratio": "16:9",
      "duration": "10",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video frame. enum: 16:9, 9:16, 1:1 |
| cfg_scale | number | 0.5 | The CFG (Classifier Free Guidance) scale controls how closely the output follows the prompt. |
| duration | string | 10 | The duration of the generated video in seconds. enum: 5, 10 |
| generate_audio | boolean | true | Whether to generate native audio for the video. Supports Chinese and English voices. |
| negative_prompt | string | blur, distort, and low quality | Negative prompt to avoid unwanted elements. |
| prompt | string | | Text prompt describing the desired video. |

## Examples

**Cinematic landscape video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "aurora borealis dancing over a frozen lake, time-lapse, cinematic 4K",
      "aspect_ratio": "16:9",
      "duration": "10",
      "cfg_scale": 0.7,
      "generate_audio": true
    }
  }'
```

**Vertical social media clip:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v2-6-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "a barista pouring latte art, close-up shot, warm cafe lighting",
      "aspect_ratio": "9:16",
      "duration": "5",
      "negative_prompt": "blur, distort, low quality, shaky camera"
    }
  }'
```

## Related Models

- [Kling | v2.6 | Pro | Image to Video](../kling-v2-6-pro-image-to-video/) - Generate video from an image
- [Kling O1](../kling-o1/) - O1-tier image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
