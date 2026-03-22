---
name: minimax-hailuo-v2-pro-text-to-video
description: "Minimax Hailuo V2 | Pro | Text to Video. Generate high-quality videos from text prompts using Minimax Hailuo V2 Pro. Premium AI text-to-video generation. Triggers: hailuo pro text to video, minimax pro t2v, hailuo v2 pro video, minimax pro video, premium text to video"
allowed-tools: Bash(curl *), WebFetch
---

# Minimax Hailuo V2 | Pro | Text to Video

Generate high-quality videos from text descriptions using Minimax Hailuo V2 Pro. The premium tier for text-to-video generation with the highest quality output and built-in prompt optimization.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A samurai standing on a hilltop at sunset, cherry blossom petals drifting in the wind, cinematic wide shot"
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| prompt | string | - | Text prompt for video generation |
| prompt_optimizer | boolean | true | Whether to use the model's prompt optimizer |

## Examples

**Epic cinematic scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A massive whale breaching the ocean surface in slow motion, water droplets catching sunlight, dramatic underwater to above-water transition",
      "prompt_optimizer": true
    }
  }'
```

**Product commercial:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "minimax-hailuo-v2-pro-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A sleek smartphone floating and rotating in a dark studio with blue accent lighting, reflective surface below, premium product showcase",
      "prompt_optimizer": true
    }
  }'
```

## Related Models

- [Minimax Hailuo V2 | Standard | Text to Video](../minimax-hailuo-v2-standard-text-to-video/) - Standard tier (faster)
- [Minimax Hailuo V2 | Pro | Image to Video](../minimax-hailuo-v2-pro-image-to-video/) - Pro image-to-video
- [Google Veo 3](../veo-3/) - Google's premium text-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
