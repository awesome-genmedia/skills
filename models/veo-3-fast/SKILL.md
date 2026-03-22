---
name: veo-3-fast
description: "Google Veo 3 | Fast. Generate videos with audio from text prompts using Google Veo 3 Fast. Fast AI video generation with built-in audio. Triggers: veo 3 fast, google video fast, fast text to video, veo fast, google veo 3, video generation fast, veo text to video"
allowed-tools: Bash(curl *), WebFetch
---

# Google Veo 3 | Fast

Generate videos with optional audio from text prompts using Google Veo 3 Fast. A speed-optimized variant of Veo 3 that produces high-quality videos with built-in audio generation, prompt enhancement, and multiple duration options.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A chef preparing sushi in a traditional Japanese restaurant, close-up of hands slicing fish, ambient restaurant sounds",
      "aspect_ratio": "16:9",
      "duration": "8s",
      "generate_audio": true
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. Options: `16:9`, `9:16` |
| auto_fix | boolean | false | Automatically attempt to fix prompts that fail content policy |
| duration | string | 8s | Video duration. Options: `4s`, `6s`, `8s` |
| enhance_prompt | boolean | true | Whether to enhance the prompt for better results |
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
    "model": "veo-3-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A thunderstorm rolling over a countryside farm, lightning flashing, rain pouring down on the barn roof",
      "duration": "8s",
      "aspect_ratio": "16:9",
      "resolution": "1080p",
      "generate_audio": true
    }
  }'
```

**Short vertical clip for social media:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "veo-3-fast",
    "version": "0.0.1",
    "input": {
      "prompt": "A barista pouring latte art into a coffee cup, smooth milk swirl, cafe ambiance",
      "duration": "4s",
      "aspect_ratio": "9:16",
      "negative_prompt": "blurry, low quality, distorted",
      "seed": 5678
    }
  }'
```

## Related Models

- [Google Veo 3](../veo-3/) - Higher quality Veo 3 (slower)
- [Google Veo 3 Fast | Image to Video](../veo-3-fast-image-to-video/) - Image-to-video with Veo 3 Fast
- [Google Veo 2 | Image to Video](../veo-2-image-to-video/) - Previous generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
