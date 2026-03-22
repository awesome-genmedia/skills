---
name: veo-3
description: "Google Veo 3. Generate premium videos with audio from text prompts using Google Veo 3. The highest quality text-to-video model from Google. Triggers: veo 3, google veo, google video, text to video veo, veo 3 video, premium video generation, google text to video"
allowed-tools: Bash(curl *), WebFetch
---

# Google Veo 3

Generate premium-quality videos with optional audio from text prompts using Google Veo 3. The flagship text-to-video model from Google, producing the highest quality video output with built-in audio generation and multiple duration options.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3",
    "version": "0.0.1",
    "input": {
      "prompt": "A professional chef plating an elaborate dessert in a Michelin-star restaurant kitchen, close-up hands carefully placing garnish, ambient kitchen sounds",
      "aspect_ratio": "16:9",
      "duration": "8s",
      "generate_audio": true,
      "resolution": "1080p"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. Options: `16:9`, `9:16` |
| duration | string | 8s | Video duration. Options: `4s`, `6s`, `8s` |
| enhance_prompt | boolean | false | Whether to enhance the prompt for better results |
| generate_audio | boolean | true | Whether to generate audio with the video |
| negative_prompt | string | - | Text describing what to avoid |
| prompt | string | - | Text prompt for video generation |
| resolution | string | 720p | Video resolution. Options: `720p`, `1080p` |
| seed | integer | - | Random seed for reproducible results |

## Examples

**Cinematic scene with audio:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3",
    "version": "0.0.1",
    "input": {
      "prompt": "A jazz musician playing saxophone on a dimly lit New Orleans street corner at night, rain gently falling, neon signs reflecting on the wet pavement",
      "duration": "8s",
      "aspect_ratio": "16:9",
      "resolution": "1080p",
      "generate_audio": true,
      "negative_prompt": "blurry, low quality, distorted"
    }
  }'
```

**Short vertical clip:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3",
    "version": "0.0.1",
    "input": {
      "prompt": "A hummingbird hovering near a tropical flower, wings beating rapidly, macro shot, vivid colors",
      "duration": "4s",
      "aspect_ratio": "9:16",
      "resolution": "720p",
      "seed": 42
    }
  }'
```

## Related Models

- [Google Veo 3 | Fast](../veo-3-fast/) - Faster variant for quicker results
- [Google Veo 3 | Image to Video](../veo-3-image-to-video/) - Image-to-video with Veo 3
- [Google Veo 2 | Image to Video](../veo-2-image-to-video/) - Previous generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
