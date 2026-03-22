---
name: ovi-text-to-video
description: "Ovi | Text to Video. Generate videos with audio from text prompts using the Ovi model. Triggers: ovi, text to video, video generation, ovi video"
allowed-tools: Bash(curl *), WebFetch
---

# Ovi | Text to Video

Generate videos with audio from text descriptions using the Ovi model. Supports multiple resolutions, configurable inference steps, and separate negative prompts for video and audio quality control.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ovi-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A jazz musician playing saxophone in a dimly lit club, smooth camera movement",
      "resolution": "992x512",
      "num_inference_steps": 30
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| audio_negative_prompt | string | robotic, muffled, echo, distorted | Negative prompt for audio generation |
| negative_prompt | string | jitter, bad hands, blur, distortion | Negative prompt for video generation |
| num_inference_steps | integer | 30 | The number of inference steps |
| prompt | string | | The text prompt to guide video generation |
| resolution | string | 992x512 | Resolution in WxH format. enum: 512x992, 992x512, 960x512, 512x960, 720x720, 448x1120, 1120x448 |
| seed | string | | Random seed for reproducibility |

## Examples

**Widescreen cinematic scene:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ovi-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "An epic battle scene in a fantasy kingdom with dragons flying overhead and armies clashing",
      "resolution": "1120x448",
      "num_inference_steps": 40,
      "negative_prompt": "jitter, bad hands, blur, distortion, low resolution"
    }
  }'
```

**Vertical video with seed:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "ovi-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A dancer performing contemporary dance in a studio with dramatic side lighting",
      "resolution": "512x992",
      "num_inference_steps": 30,
      "seed": "12345"
    }
  }'
```

## Related Models

- [ovi-image-to-video](../ovi-image-to-video/) - Image to video with Ovi

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
