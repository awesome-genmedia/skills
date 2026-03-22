---
name: "Wan v2.2 A14B Image to Video"
description: "Generate videos from images using Wan v2.2 A14B. Trigger: Use when the user wants to animate an image into a video, or requests 'wan image to video', 'animate image', or 'image to video with wan'."
allowed-tools: ["Bash"]
---

# Wan | v2.2 A14B | Image to Video

Animate a still image into a video guided by a text prompt. Features advanced controls including frame interpolation, dual guidance scales, and multiple resolution options.

## Quick Start

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "wan-v2-2-a14b-image-to-video",
    "version": "0.0.1",
    "input": {
      "image_url": "https://example.com/landscape.jpg",
      "prompt": "Camera slowly pans across the landscape as clouds drift by",
      "resolution": "720p",
      "aspect_ratio": "16:9",
      "num_frames": 81
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `acceleration` | string | `regular` | Acceleration level. Options: `none`, `regular` |
| `adjust_fps_for_interpolation` | boolean | `true` | If true, FPS will be multiplied by the number of interpolated frames |
| `aspect_ratio` | string | `auto` | Aspect ratio. `auto` derives from input image. Options: `auto`, `16:9`, `9:16`, `1:1` |
| `enable_prompt_expansion` | boolean | `false` | Whether to expand the prompt using an LLM |
| `enable_safety_checker` | boolean | `false` | If true, input data will be checked for safety |
| `end_image_url` | string | (empty) | URL of the end image |
| `frames_per_second` | integer | `16` | Frames per second |
| `guidance_scale` | number | `3.5` | Classifier-free guidance scale for prompt adherence |
| `guidance_scale_2` | number | `3.5` | Guidance scale for the second stage of the model |
| `image_url` | string | (empty) | URL of the input image |
| `interpolator_model` | string | `film` | Frame interpolation model. Options: `none`, `film`, `rife` |
| `negative_prompt` | string | (empty) | Negative prompt for video generation |
| `num_frames` | integer | `81` | Number of frames to generate |
| `num_inference_steps` | integer | `27` | Number of inference steps |
| `num_interpolated_frames` | integer | `1` | Number of frames to interpolate between each generated frame |
| `prompt` | string | (empty) | The text prompt to guide video generation |
| `resolution` | string | `720p` | Resolution of the generated video. Options: `480p`, `580p`, `720p` |
| `seed` | integer | (empty) | Random seed for reproducibility |
| `shift` | number | `5` | Shift value for the video. Must be between 1.0 and 10.0 |

## Output

- **Type:** video

## Examples

### Cinematic Image Animation
```json
{
  "model": "wan-v2-2-a14b-image-to-video",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/sunset-beach.jpg",
    "prompt": "Waves gently crashing on the shore as the sun sets, warm golden light",
    "resolution": "720p",
    "aspect_ratio": "16:9",
    "num_frames": 81,
    "guidance_scale": 4.0,
    "num_inference_steps": 30,
    "interpolator_model": "rife"
  }
}
```

### Start-to-End Animation
```json
{
  "model": "wan-v2-2-a14b-image-to-video",
  "version": "0.0.1",
  "input": {
    "image_url": "https://example.com/morning-city.jpg",
    "end_image_url": "https://example.com/night-city.jpg",
    "prompt": "Time-lapse of a city transitioning from day to night",
    "resolution": "720p",
    "aspect_ratio": "auto",
    "num_frames": 81,
    "seed": 42
  }
}
```

## Related Models

- [Wan v2.2 A14B Image to Video Turbo](../wan-v2-2-a14b-image-to-video-turbo/SKILL.md) - Faster image-to-video generation
- [Wan v2.2 A14B Text to Video Turbo](../wan-v2-2-a14b-text-to-video-turbo/SKILL.md) - Text-to-video generation
- [PixVerse v5 Image to Video](../pixverse-v5-image-to-video/SKILL.md) - Alternative image-to-video model

## Documentation

- [EachLabs API Docs](https://docs.eachlabs.ai)
