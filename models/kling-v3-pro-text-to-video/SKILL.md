---
name: kling-v3-pro-text-to-video
description: "Kling | v3 | Pro | Text to Video. Pro-quality text to video with CFG control, audio, and intelligent shot types. Triggers: text to video, kling, v3, pro, video generation, t2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | v3 | Pro | Text to Video

Generate high-quality videos from text using Kling v3 Pro with CFG guidance, multi-shot prompts, intelligent shot types, voice IDs, and native audio generation.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A time-lapse of the Northern Lights dancing over a frozen lake in Norway",
      "duration": "10",
      "aspect_ratio": "16:9",
      "cfg_scale": 0.5,
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. enum: 16:9, 9:16, 1:1 |
| cfg_scale | number | 0.5 | Classifier Free Guidance scale. Controls prompt adherence. |
| duration | string | 5 | Video duration in seconds. enum: 3-15 |
| generate_audio | boolean | true | Generate native audio. Supports Chinese and English voices. |
| multi_prompt | array | | List of prompts for multi-shot generation. Overrides single prompt. |
| negative_prompt | string | blur, distort, and low quality | Negative prompt to exclude unwanted content. |
| prompt | string | | Text prompt for video generation. |
| shot_type | string | customize | Multi-shot generation type. enum: customize, intelligent |
| voice_ids | array | | Optional Voice IDs. Reference voices in prompt with << >>. |

## Examples

**High-quality cinematic video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A dramatic close-up of a samurai drawing his sword in slow motion, cherry blossoms falling",
      "duration": "12",
      "aspect_ratio": "16:9",
      "cfg_scale": 0.7,
      "negative_prompt": "blurry, distorted, low resolution",
      "generate_audio": true
    }
  }'
```

**Vertical video with intelligent shots:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A fashion model walking down a runway in an elegant evening gown",
      "duration": "8",
      "aspect_ratio": "9:16",
      "shot_type": "intelligent"
    }
  }'
```

**Silent art piece:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Abstract fluid art in motion, swirling colors of gold, blue, and crimson",
      "duration": "5",
      "aspect_ratio": "1:1",
      "cfg_scale": 0.3,
      "generate_audio": false
    }
  }'
```

## Related Models

- [kling-v3-standard-text-to-video](../kling-v3-standard-text-to-video/) - Standard tier text to video
- [kling-v3-pro-image-to-video](../kling-v3-pro-image-to-video/) - Pro image to video
- [kling-o3-pro-text-to-video](../kling-o3-pro-text-to-video/) - Kling o3 Pro text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
