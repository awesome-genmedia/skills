---
name: kling-o3-pro-text-to-video
description: "Kling | o3 | Pro | Text to Video. Pro-quality text to video with audio generation and multi-shot support. Triggers: text to video, kling, o3, pro, video generation, t2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | o3 | Pro | Text to Video

Generate high-quality videos from text prompts using Kling o3 Pro with multi-shot generation, voice IDs, and configurable duration up to 15 seconds.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cinematic aerial shot of a volcanic eruption with lava flowing into the ocean",
      "duration": "10",
      "aspect_ratio": "16:9",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. enum: 16:9, 9:16, 1:1 |
| duration | string | 5 | Video duration in seconds (3-15s). enum: 3-15 |
| generate_audio | boolean | false | Whether to generate native audio for the video. |
| multi_prompt | array | | List of prompts for multi-shot video generation. |
| prompt | string | | Text prompt. Required unless multi_prompt is provided. |
| shot_type | string | customize | Multi-shot generation type. enum: customize |
| voice_ids | array | | Optional Voice IDs. Reference voices in prompt with << >>. |

## Examples

**Epic cinematic video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A spaceship launching from a futuristic spaceport, camera follows it as it breaks through the clouds",
      "duration": "15",
      "aspect_ratio": "16:9",
      "generate_audio": true
    }
  }'
```

**Vertical social content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A professional chef flambeeing a dessert in a fine dining kitchen, dramatic flames",
      "duration": "8",
      "aspect_ratio": "9:16",
      "generate_audio": false
    }
  }'
```

## Related Models

- [kling-o3-standard-text-to-video](../kling-o3-standard-text-to-video/) - Standard tier text to video
- [kling-o3-pro-image-to-video](../kling-o3-pro-image-to-video/) - Pro image to video
- [kling-v3-pro-text-to-video](../kling-v3-pro-text-to-video/) - Kling v3 Pro text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
