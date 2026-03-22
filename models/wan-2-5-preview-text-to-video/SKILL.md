---
name: wan-2-5-preview-text-to-video
description: "Wan | 2.5 | Preview | Text to Video. Generate videos from text prompts with audio support using the Wan 2.5 Preview model. Triggers: wan, text to video, video generation, wan 2.5"
allowed-tools: Bash(curl *), WebFetch
---

# Wan | 2.5 | Preview | Text to Video

Generate videos from text descriptions with optional background audio using the Wan 2.5 Preview model. Supports Chinese and English prompts, LLM-based prompt expansion, and multiple aspect ratios and resolutions.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A surfer riding a massive wave at sunset, spray of water catching the golden light",
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
| aspect_ratio | string | 16:9 | The aspect ratio. enum: 16:9, 9:16, 1:1 |
| audio_url | string | | URL of background music audio (must be publicly accessible) |
| duration | string | 5 | Duration in seconds. enum: 5, 10 |
| enable_prompt_expansion | boolean | true | Whether to enable LLM-based prompt rewriting |
| negative_prompt | string | | Negative prompt to avoid (max 500 chars) |
| prompt | string | | Text prompt for video generation. Supports Chinese and English (max 800 chars) |
| resolution | string | 1080p | Video resolution. enum: 480p, 720p, 1080p |
| seed | integer | | Random seed for reproducibility |

## Examples

**Square format with audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A pianist performing a classical piece in a grand concert hall, dramatic lighting, close-up of hands on keys",
      "aspect_ratio": "1:1",
      "duration": "10",
      "resolution": "1080p",
      "audio_url": "https://example.com/piano-music.mp3"
    }
  }'
```

**Vertical social content:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-2-5-preview-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "Chocolate being poured over a dessert in slow motion, glossy texture, food photography",
      "aspect_ratio": "9:16",
      "duration": "5",
      "resolution": "720p",
      "negative_prompt": "blurry, low quality, shaky",
      "seed": 42
    }
  }'
```

## Related Models

- [wan-2-5-preview-image-to-video](../wan-2-5-preview-image-to-video/) - Image to video
- [wan-2-5-preview-text-to-image](../wan-2-5-preview-text-to-image/) - Text to image
- [wan-2-5-preview-image-to-image](../wan-2-5-preview-image-to-image/) - Image to image editing

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
