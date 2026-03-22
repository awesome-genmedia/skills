---
name: kling-o3-standard-text-to-video
description: "Kling | o3 | Standard | Text to Video. Generate videos from text prompts with audio generation and multi-shot support. Triggers: text to video, kling, o3, video generation, t2v"
allowed-tools: Bash(curl *), WebFetch
---

# Kling | o3 | Standard | Text to Video

Generate videos from text descriptions using Kling o3 Standard with native audio generation, multi-shot prompts, and configurable duration up to 15 seconds.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A golden retriever running through a field of wildflowers at sunset",
      "duration": "8",
      "aspect_ratio": "16:9",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio of the generated video. enum: 16:9, 9:16, 1:1 |
| duration | string | 8 | Video duration in seconds (3-15s). enum: 3-15 |
| generate_audio | boolean | true | Whether to generate native audio for the video. |
| multi_prompt | array | | List of prompts for multi-shot video generation. |
| prompt | string | | Text prompt for video generation. Required unless multi_prompt is provided. |
| shot_type | string | customize | The type of multi-shot video generation. |
| voice_ids | array | | Optional Voice IDs for video generation. Reference voices in prompt with << >>. |

## Examples

**Simple text to video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "An astronaut floating in space with Earth visible in the background",
      "duration": "10",
      "aspect_ratio": "16:9",
      "generate_audio": true
    }
  }'
```

**Vertical video for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A chef preparing sushi in a traditional Japanese restaurant, close-up shots of hands slicing fish",
      "duration": "15",
      "aspect_ratio": "9:16",
      "generate_audio": false
    }
  }'
```

**Short clip without audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-o3-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Ocean waves crashing on a rocky coastline during a storm",
      "duration": "5",
      "aspect_ratio": "1:1",
      "generate_audio": false
    }
  }'
```

## Related Models

- [kling-o3-pro-text-to-video](../kling-o3-pro-text-to-video/) - Kling o3 Pro text to video
- [kling-o3-standard-image-to-video](../kling-o3-standard-image-to-video/) - Kling o3 Standard image to video
- [kling-v3-standard-text-to-video](../kling-v3-standard-text-to-video/) - Kling v3 Standard text to video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
