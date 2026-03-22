---
name: kling-v1-standard-text-to-video
description: "Kling v1 | Standard | Text to Video. Generate videos from text using Kling v1 Standard with camera control. Affordable AI text-to-video with camera movements. Triggers: kling v1 text to video, kling standard video, kling v1 t2v, kling standard text to video, kling camera control"
allowed-tools: Bash(curl *), WebFetch
---

# Kling v1 | Standard | Text to Video

Generate videos from text prompts using Kling v1 Standard. Features camera control options including predefined movements and advanced camera parameters for creative video generation at an affordable price point.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A majestic waterfall in a tropical jungle, mist rising, birds flying through the canopy",
      "aspect_ratio": "16:9",
      "duration": 5
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratio | string | 16:9 | Aspect ratio. Options: `16:9`, `9:16`, `1:1` |
| camera_control | string | - | Predefined camera movement. Options: `down_back`, `forward_up`, `right_turn_forward`, `left_turn_forward` |
| camera_control_config_type | string | - | Advanced camera control type. Options: `horizontal`, `vertical`, `pan`, `tilt`, `roll`, `zoom` |
| camera_control_config_value | number | - | Value for the advanced camera control |
| cfg_scale | number | 0.5 | Classifier-free guidance scale |
| duration | integer | 5 | Video duration in seconds |
| negative_prompt | string | blur, distort, and low quality | Things to avoid in generation |
| prompt | string | - | Text prompt for video generation |

## Examples

**Video with camera movement:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A medieval castle on a hilltop at sunset, dramatic clouds",
      "aspect_ratio": "16:9",
      "duration": 5,
      "camera_control": "forward_up",
      "negative_prompt": "blur, distort, and low quality"
    }
  }'
```

**Advanced camera zoom:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "kling-v1-standard-text-to-video",
    "version": "0.0.1",
    "input": {
      "prompt": "A single red rose in a garden, dewdrops on the petals, morning light",
      "aspect_ratio": "1:1",
      "camera_control_config_type": "zoom",
      "camera_control_config_value": 2,
      "cfg_scale": 0.5
    }
  }'
```

## Related Models

- [Kling v1 | Pro | Text to Video](../kling-v1-pro-text-to-video/) - Higher quality Pro tier
- [Kling v2.1 | Master | Text to Video](../kling-v2-1-master-text-to-video/) - Latest generation
- [Kling v1 | Standard | Image to Video](../kling-v1-standard-image-to-video/) - Standard image-to-video

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
