---
name: kling-v3-standard-text-to-video
description: "Kling | v3 | Standard | Text to Video. Generate videos from text with CFG control, audio, and multi-shot support. Triggers: text to video, kling, v3, standard, video generation, t2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v3 | Standard | Text to Video

Generate videos from text prompts using Kling v3 Standard with CFG guidance control, native audio generation, multi-shot prompts, and voice ID support.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A drone shot flying over a coral reef with tropical fish swimming below",
      "duration": "8",
      "aspect_ratio": "16:9",
      "generate_audio": true,
      "cfg_scale": 0.5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of the generated video. enum: 16:9, 9:16, 1:1 |
| cfg_scale | number | 0.5 | Classifier Free Guidance scale. Controls how closely output follows the prompt. |
| duration | string | 5 | Video duration in seconds. enum: 3-15 |
| generate_audio | boolean | true | Generate native audio. Supports Chinese and English voices. |
| multi_prompt | array | | List of prompts for multi-shot video generation. Overrides single prompt. |
| negative_prompt | string | blur, distort, and low quality | Negative prompt to exclude unwanted content. |
| prompt | string | | Text prompt for video generation. |
| shot_type | string | customize | Multi-shot generation type. enum: customize, intelligent |
| voice_ids | array | | Optional Voice IDs. Reference voices in prompt with << >>. |

## Examples

**Cinematic text to video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "An epic wide shot of a medieval castle under siege with catapults firing",
      "duration": "12",
      "aspect_ratio": "16:9",
      "cfg_scale": 0.7,
      "negative_prompt": "blurry, distorted, low quality, text"
    }
  }'
```

**Vertical video for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A barista making latte art in a cozy coffee shop, close-up",
      "duration": "5",
      "aspect_ratio": "9:16",
      "generate_audio": true
    }
  }'
```

**Short silent clip:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cat slowly stretching and yawning on a sunny windowsill",
      "duration": "3",
      "aspect_ratio": "1:1",
      "generate_audio": false
    }
  }'
```

## Related Models

- [kling-v3-pro-text-to-video](../kling-v3-pro-text-to-video/) - Kling v3 Pro text to video
- [kling-v3-standard-image-to-video](../kling-v3-standard-image-to-video/) - Kling v3 Standard image to video
- [kling-o3-standard-text-to-video](../kling-o3-standard-text-to-video/) - Kling o3 Standard text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
