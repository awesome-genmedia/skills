---
name: instant-id
description: "Instant ID Generate Avatar | AI Avatar Generation. Generate personalized avatars from face photos with extensive controlnet and model options. Triggers: instant id, avatar generator, face avatar, id avatar, personalized avatar"
allowed-tools: Bash(curl *), WebFetch
---

# Instant ID Generate Avatar

Generate personalized avatars from face photos with extensive ControlNet options (pose, canny, depth), multiple SDXL base models, and configurable identity preservation strength.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "instant-id",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/face-photo.jpg",
      "prompt": "a person as a fantasy warrior in golden armor, epic background",
      "num_inference_steps": 4,
      "guidance_scale": 7.5,
      "controlnet_conditioning_scale": 0.8,
      "ip_adapter_scale": 0.8
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| canny_strength | number | 0.3 | Canny ControlNet strength (only if enable_canny_controlnet is true) |
| controlnet_conditioning_scale | number | 0.8 | Scale for IdentityNet strength (for fidelity) |
| depth_strength | number | 0.5 | Depth ControlNet strength (only if enable_depth_controlnet is true) |
| disable_safety_checker | boolean | false | Disable safety checker |
| enable_canny_controlnet | boolean | false | Enable canny edge detection control |
| enable_depth_controlnet | boolean | false | Enable depth control |
| enable_lcm | boolean | false | Enable LCM for faster inference |
| enable_pose_controlnet | boolean | true | Enable Openpose ControlNet |
| enhance_nonface_region | boolean | true | Enhance non-face region |
| guidance_scale | number | 7.5 | Scale for classifier-free guidance |
| height | integer | 640 | Height of output image |
| image | string | - | Input face image |
| ip_adapter_scale | number | 0.8 | Scale for image adapter strength (for detail) |
| lcm_guidance_scale | number | 1.5 | Guidance scale when using LCM |
| lcm_num_inference_steps | integer | 5 | Steps when using LCM |
| negative_prompt | string | - | Negative prompt |
| num_inference_steps | integer | 4 | Number of denoising steps |
| pose_image | string | - | Optional reference pose image |
| pose_strength | number | 0.4 | Openpose ControlNet strength |
| prompt | string | a person | Input prompt |
| scheduler | string | EulerDiscreteScheduler | Scheduler. enum: DEISMultistepScheduler, HeunDiscreteScheduler, EulerDiscreteScheduler, DPMSolverMultistepScheduler, DPMSolverMultistepScheduler-Karras, DPMSolverMultistepScheduler-Karras-SDE |
| sdxl_weights | string | stable-diffusion-xl-base-1.0 | Base model. enum: stable-diffusion-xl-base-1.0, juggernaut-xl-v8, afrodite-xl-v2, albedobase-xl-20, albedobase-xl-v13, animagine-xl-30, anime-art-diffusion-xl, anime-illust-diffusion-xl, dreamshaper-xl, dynavision-xl-v0610, guofeng4-xl, nightvision-xl-0791, omnigen-xl, pony-diffusion-v6-xl, protovision-xl-high-fidel |
| seed | integer | - | Random seed |
| width | integer | 640 | Width of output image |

## Examples

**Anime avatar with custom base model:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "instant-id",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/selfie.jpg",
      "prompt": "a person as an anime character, colorful, detailed, vibrant background",
      "sdxl_weights": "animagine-xl-30",
      "controlnet_conditioning_scale": 0.7,
      "ip_adapter_scale": 0.9,
      "num_inference_steps": 6,
      "guidance_scale": 8,
      "width": 640,
      "height": 640
    }
  }'
```

**Pose-guided avatar with depth:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "instant-id",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/face.jpg",
      "pose_image": "https://example.com/pose-reference.jpg",
      "prompt": "a person as a cyberpunk hacker in neon-lit room, detailed, high quality",
      "enable_pose_controlnet": true,
      "enable_depth_controlnet": true,
      "pose_strength": 0.5,
      "depth_strength": 0.4,
      "guidance_scale": 7.5,
      "num_inference_steps": 5,
      "seed": 42
    }
  }'
```

## Related Models

- [instant-id-ip-adapter](../instant-id-ip-adapter/) - Styled avatar generation (3D, Emoji, Pixels)
- [photomaker](../photomaker/) - Identity-preserving photo generation
- [become-image](../become-image/) - Style transfer with identity preservation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
