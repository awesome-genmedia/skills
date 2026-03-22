---
name: wan-v2-6-reference-to-video
description: "Wan | v2.6 | Reference to Video. Generate videos with subject consistency using reference videos. Triggers: reference to video, subject video, wan reference, consistent character video"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | v2.6 | Reference to Video

Generate videos with subject consistency using reference videos. Use @Video1, @Video2, @Video3 in prompts to reference subjects from your uploaded videos. Supports multi-shot segmentation and resolutions up to 1080p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "The character from @Video1 walks through a snowy forest, breath visible in the cold air",
      "video_urls": ["https://example.com/character-ref.mp4"],
      "aspect_ratio": "16:9",
      "duration": "5",
      "resolution": "1080p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. Options: `16:9`, `9:16`, `1:1`, `4:3`, `3:4` |
| duration | string | 5 | Duration of the generated video in seconds. Options: `5`, `10` |
| enable_prompt_expansion | boolean | true | Whether to enable prompt rewriting using LLM. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| multi_shots | boolean | true | When true, enables intelligent multi-shot segmentation for coherent narratives. |
| negative_prompt | string | - | Negative prompt to describe content to avoid. Max 500 characters. |
| prompt | string | - | Use @Video1, @Video2, @Video3 to reference subjects from your videos. Works for 1-3 videos. |
| resolution | string | 1080p | Video resolution. Options: `720p`, `1080p` |
| seed | integer | - | Random seed for reproducibility. |
| video_urls | array | - | Reference videos for subject consistency (1-3 videos). Reference in prompt as @Video1, etc. |

## Examples

**Single reference video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "@Video1 dances in a brightly lit ballroom with chandeliers",
      "video_urls": ["https://example.com/dancer-ref.mp4"]
    }
  }'
```

**Multiple references with custom settings:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-reference-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "@Video1 and @Video2 meet at a cafe and shake hands, cinematic lighting",
      "video_urls": ["https://example.com/person-a.mp4", "https://example.com/person-b.mp4"],
      "aspect_ratio": "16:9",
      "duration": "10",
      "multi_shots": true,
      "negative_prompt": "blurry, distorted faces",
      "resolution": "1080p",
      "seed": 42
    }
  }'
```

## Related Models

- [Wan | v2.6 | Text to Video](../wan-v2-6-text-to-video/) - Generate video from text with Wan v2.6
- [Wan | v2.6 | Image to Video](../wan-v2-6-image-to-video/) - Generate video from images with Wan v2.6
- [Wan | v2.6 | Text to Image](../wan-v2-6-text-to-image/) - Generate images with Wan v2.6

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
