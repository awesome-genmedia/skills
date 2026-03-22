---
name: fooocus-api
description: "Fooocus | Advanced AI Image Generation. Generate images with extensive controls including styles, LoRAs, inpainting, outpainting, and upscaling. Triggers: fooocus, image generation, styled image, inpaint, outpaint, upscale"
allowed-tools: Bash(curl *), WebFetch
---

# Fooocus

Generate images with Fooocus, featuring extensive controls including style presets, image prompting, inpainting, outpainting, upscaling, and custom LoRA support.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "fooocus-api",
    "version": "0.0.1",
    "input": {
      "prompt": "a majestic dragon flying over a medieval castle at sunset, epic fantasy art",
      "aspect_ratios_selection": "1152*896",
      "performance_selection": "Quality",
      "style_selections": "Fooocus V2,Fooocus Enhance,Fooocus Sharp",
      "guidance_scale": 7
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| aspect_ratios_selection | string | 1152*896 | Output resolution. enum: 704*1408, 768*1344, 832*1216, 896*1152, 960*1088, 1024*1024, 1088*960, 1152*896, 1216*832, 1280*768, 1344*768, 1408*704, and more |
| cn_img1 | string | - | Input image for image prompt slot 1 |
| cn_img2 | string | - | Input image for image prompt slot 2 |
| cn_img3 | string | - | Input image for image prompt slot 3 |
| cn_img4 | string | - | Input image for image prompt slot 4 |
| cn_stop1 | number | 0.5 | Stop at for image prompt 1 |
| cn_type1 | string | ImagePrompt | Control type for slot 1. enum: ImagePrompt, FaceSwap, PyraCanny, CPDS |
| cn_weight1 | number | - | Weight for image prompt 1 |
| guidance_scale | number | 7 | Guidance scale |
| image_number | integer | 1 | How many images to generate |
| image_seed | integer | -1 | Seed, -1 for random |
| inpaint_additional_prompt | string | - | Prompt for inpainting |
| inpaint_input_image | string | - | Input image for inpaint or outpaint |
| inpaint_input_mask | string | - | Input mask for inpaint |
| loras_custom_urls | string | - | Custom LoRA URLs in format 'url,weight' separated by ; |
| negative_prompt | string | - | Negative prompt |
| outpaint_distance_bottom | number | 0 | Outpaint expansion from bottom |
| outpaint_distance_left | number | 0 | Outpaint expansion from left |
| outpaint_distance_right | number | 0 | Outpaint expansion from right |
| outpaint_distance_top | number | 0 | Outpaint expansion from top |
| outpaint_selections | string | - | Outpaint directions: Left, Right, Top, Bottom (comma separated) |
| performance_selection | string | Speed | Performance mode. enum: Speed, Quality, Extreme Speed |
| prompt | string | - | Prompt for image generation |
| refiner_switch | number | 0.5 | Refiner switch point |
| sharpness | number | 2 | Sharpness |
| style_selections | string | Fooocus V2,Fooocus Enhance,Fooocus Sharp | Fooocus styles, separated by comma |
| uov_input_image | string | - | Input image for upscale or variation |
| uov_method | string | Disabled | Upscale/variation method. enum: Disabled, Vary (Subtle), Vary (Strong), Upscale (1.5x), Upscale (2x), Upscale (Fast 2x), Upscale (Custom) |
| uov_upscale_value | number | 0 | Custom upscale value |
| use_default_loras | boolean | true | Use default LoRAs |

## Examples

**Quality generation with face swap:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "fooocus-api",
    "version": "0.0.1",
    "input": {
      "prompt": "a professional headshot portrait, studio lighting, clean background",
      "cn_img1": "https://example.com/face-reference.jpg",
      "cn_type1": "FaceSwap",
      "cn_stop1": 0.8,
      "performance_selection": "Quality",
      "aspect_ratios_selection": "1024*1024"
    }
  }'
```

**Image outpainting:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "fooocus-api",
    "version": "0.0.1",
    "input": {
      "prompt": "a beautiful landscape with mountains and a lake, golden hour",
      "inpaint_input_image": "https://example.com/cropped-landscape.jpg",
      "outpaint_selections": "Left,Right",
      "outpaint_distance_left": 200,
      "outpaint_distance_right": 200,
      "performance_selection": "Quality"
    }
  }'
```

## Related Models

- [flux-dev](../flux-dev/) - Flux Dev text-to-image
- [stable-diffusion-3-5-large](../stable-diffusion-3-5-large/) - SD 3.5 image generation
- [recraft-v3](../recraft-v3/) - Styled image generation

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
