---
name: wan-v2-6-text-to-video
description: "Wan | v2.6 | Text to Video. Generate videos from text prompts with multi-shot and audio support. Triggers: text to video, video generation, wan video, ai video"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | v2.6 | Text to Video

Generate videos from text prompts using the Wan v2.6 model. Features multi-shot segmentation for narrative coherence, LLM prompt expansion, background audio support, and durations of 5-15 seconds at up to 1080p.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A cinematic aerial shot of a medieval castle at dawn, mist rising from the valley below",
      "aspect_ratio": "16:9",
      "duration": "5",
      "resolution": "1080p",
      "enable_prompt_expansion": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | The aspect ratio of the generated video. Options: `16:9`, `9:16`, `1:1`, `4:3`, `3:4` |
| audio_url | string | - | URL of the audio to use as background music. Must be publicly accessible. |
| duration | string | 5 | Duration of the generated video in seconds. Options: `5`, `10`, `15` |
| enable_prompt_expansion | boolean | true | Whether to enable prompt rewriting using LLM. Improves results for short prompts. |
| enable_safety_checker | boolean | true | If set to true, the safety checker will be enabled. |
| multi_shots | boolean | true | When true, enables intelligent multi-shot segmentation for coherent narratives. |
| negative_prompt | string | - | Negative prompt to describe content to avoid. Max 500 characters. |
| prompt | string | - | The text prompt for video generation. Supports Chinese and English, max 800 characters. |
| resolution | string | 1080p | Video resolution. Options: `720p`, `1080p` |
| seed | integer | - | Random seed for reproducibility. |

## Examples

**Quick text-to-video:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A kitten playing with a ball of yarn on a wooden floor"
    }
  }'
```

**Long video with audio and multi-shot:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A chef prepares a gourmet dish in a professional kitchen: chopping vegetables, searing the steak, plating the final dish",
      "audio_url": "https://example.com/kitchen-ambience.mp3",
      "aspect_ratio": "16:9",
      "duration": "15",
      "multi_shots": true,
      "negative_prompt": "blurry, low resolution, text overlay",
      "resolution": "1080p",
      "seed": 42
    }
  }'
```

**Vertical social media format:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-6-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A person doing a trendy dance move in a colorful studio",
      "aspect_ratio": "9:16",
      "duration": "10",
      "resolution": "1080p"
    }
  }'
```

## Related Models

- [Wan | v2.6 | Image to Video](../wan-v2-6-image-to-video/) - Generate video from images with Wan v2.6
- [Wan | v2.6 | Reference to Video](../wan-v2-6-reference-to-video/) - Generate video with subject consistency
- [Wan | v2.6 | Text to Image](../wan-v2-6-text-to-image/) - Generate images with Wan v2.6

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
