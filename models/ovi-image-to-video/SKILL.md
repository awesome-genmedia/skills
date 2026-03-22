---
name: ovi-image-to-video
description: "Ovi | Image to Video. Animate images into videos with audio using the Ovi model. Triggers: ovi, image to video, animate image, video generation, ovi video"
allowed-tools: Bash(curl *), WebFetch
---

# Ovi | Image to Video

Animate images into videos with audio using the Ovi model. Supports configurable inference steps, negative prompts for both video and audio, and seed-based reproducibility.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ovi-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/nature-scene.jpg",
      "prompt": "Wind blows through the trees, leaves scatter across the ground",
      "num_inference_steps": 30
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_negative_prompt | string | robotic, muffled, echo, distorted | Negative prompt for audio generation |
| image_url | string | | The image URL to guide video generation |
| negative_prompt | string | jitter, bad hands, blur, distortion | Negative prompt for video generation |
| num_inference_steps | integer | 30 | The number of inference steps |
| prompt | string | | The text prompt to guide video generation |
| seed | string | | Random seed for reproducibility |

## Examples

**Detailed scene animation with custom quality:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ovi-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/cafe-interior.jpg",
      "prompt": "People chatting at tables, a waiter carries drinks, steam rises from cups",
      "num_inference_steps": 40,
      "negative_prompt": "jitter, bad hands, blur, distortion, low quality",
      "audio_negative_prompt": "robotic, muffled, echo, distorted, noise"
    }
  }'
```

**Reproducible animation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ovi-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/dog-in-park.jpg",
      "prompt": "The dog wags its tail and runs toward the camera playfully",
      "num_inference_steps": 30,
      "seed": "42"
    }
  }'
```

## Related Models

- [ovi-text-to-video](../ovi-text-to-video/) - Text to video with Ovi

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
