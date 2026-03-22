---
name: become-image
description: "Image to Become | Style Transfer with Identity Preservation. Transform a person's photo into any style while preserving their identity. Triggers: become image, style transfer, identity transfer, person transform, image become"
allowed-tools: Bash(curl *), WebFetch
---

# Image to Become

Transform a person's photo into any target style while preserving their facial identity. Upload a person's photo and a target style image to generate a blend using InstantID technology.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "become-image",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/person-photo.jpg",
      "image_to_become": "https://example.com/superhero-poster.jpg",
      "prompt": "a superhero in an action pose",
      "instant_id_strength": 1,
      "image_to_become_strength": 0.75
    }
  }'
```

## Parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| control_depth_strength | number | 0.8 | Strength of depth controlnet |
| denoising_strength | number | 1 | How much of the original image to keep. 1 is complete destruction |
| disable_safety_checker | boolean | true | Disable safety checker |
| image | string | - | An image of a person to be converted |
| image_to_become | string | - | Any image to convert the person to |
| image_to_become_noise | number | 0.3 | Noise added to style image before processing |
| image_to_become_strength | number | 0.75 | How strong the style will be applied |
| instant_id_strength | number | 1 | How strong the InstantID will be |
| negative_prompt | string | - | Things you do not want in the image |
| number_of_images | integer | 2 | Number of images to generate |
| prompt | string | a person | Prompt to guide generation |
| prompt_strength | number | 2 | CFG scale, higher numbers lead to stronger prompt influence |
| seed | integer | - | Fix random seed for reproducibility |

## Examples

**Transform into painting style:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "become-image",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/selfie.jpg",
      "image_to_become": "https://example.com/renaissance-painting.jpg",
      "prompt": "a Renaissance nobleman in oil painting style",
      "instant_id_strength": 0.9,
      "image_to_become_strength": 0.8,
      "number_of_images": 3,
      "seed": 42
    }
  }'
```

**Cosplay transformation:**
```bash
curl -X POST https://api.eachlabs.ai/v1/prediction \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "model": "become-image",
    "version": "0.0.1",
    "input": {
      "image": "https://example.com/face-photo.jpg",
      "image_to_become": "https://example.com/anime-character.jpg",
      "prompt": "an anime character with dramatic lighting",
      "instant_id_strength": 1,
      "image_to_become_strength": 0.7,
      "control_depth_strength": 0.6,
      "denoising_strength": 0.9
    }
  }'
```

## Related Models

- [instant-id](../instant-id/) - Instant ID avatar generation
- [instant-id-ip-adapter](../instant-id-ip-adapter/) - Anime and styled avatar generation
- [face-swap-new](../face-swap-new/) - Face swapping between images

## Documentation

- [each::labs Docs](https://docs.eachlabs.ai)
- [API Reference](https://docs.eachlabs.ai/api/overview)
