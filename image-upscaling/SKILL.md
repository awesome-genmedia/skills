---
name: image-upscaling
description: "Upscale image resolution with AI using each::sense. Enhance low-resolution images to high resolution while preserving detail, sharpness, and texture. Recover detail from compressed or small images. Powered by topaz-upscale-image for studio-quality results. Use for: print preparation, restoring old photos, enhancing thumbnails, improving AI-generated images, social media quality, e-commerce. Triggers: upscale image, image upscaling, enhance resolution, increase resolution, super resolution, upscale photo, enlarge image, hd image, enhance image, sharpen image, improve quality, hi-res"
allowed-tools: Bash(curl *), WebFetch
---

# Image Upscaling

Upscale image resolution with AI-powered detail enhancement using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Upscale this image to the highest resolution possible. Preserve sharpness and fine detail. Enhance texture without adding artifacts."}],
    "image_urls": ["https://example.com/low-res-photo.jpg"],
    "stream": false
  }'
```

### Using Python (OpenAI SDK)

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{"role": "user", "content": "Upscale this image to the highest resolution possible. Preserve sharpness and fine detail. Enhance texture without adding artifacts."}],
    extra_body={
        "image_urls": ["https://example.com/low-res-photo.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Reference Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Upscale the first image. Use the second image as a quality reference for the level of detail and sharpness I expect in the output."}],
    "image_urls": ["https://example.com/low-res.jpg", "https://example.com/quality-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Available Models

| Model | Strengths | Best For |
|-------|-----------|----------|
| **topaz-upscale-image** | Industry-leading upscaling, detail recovery, artifact removal | All upscaling tasks, print prep, photo restoration |

> each::sense automatically selects topaz-upscale-image when upscaling requests are detected.

## What AI Upscaling Can Do

| Capability | Description |
|------------|-------------|
| **Resolution increase** | Scale images 2x, 4x, or more while adding realistic detail |
| **Detail recovery** | Reconstruct textures, edges, and fine features from low-res sources |
| **Noise reduction** | Remove compression artifacts, JPEG blocking, and noise |
| **Sharpening** | Enhance edge clarity without halos or over-sharpening |
| **Face enhancement** | Recover facial detail from small or blurry face regions |
| **Texture synthesis** | Generate plausible texture detail that was not in the original |

## Upscaling Scenarios

| Scenario | Input Quality | What to Expect |
|----------|--------------|----------------|
| **Thumbnail to full-size** | 100-300px | Good overall shape; fine detail is synthesized |
| **Web image to print** | 600-1200px | Excellent; most detail preserved and enhanced |
| **Social media to poster** | 1080-2000px | Outstanding; print-ready quality |
| **Old photo restoration** | Variable, often degraded | Good recovery; combine with denoising |
| **AI-generated image** | 512-1024px typical | Excellent; AI upscaling works very well on AI images |
| **Screenshot to high-res** | Variable | Good for photos in screenshots; text may blur |

## Prompt Tips

### Basic Upscaling

```
"Upscale this image. Maximize resolution while keeping it sharp and natural."
```

### With Quality Direction

```
"Upscale this image 4x. Prioritize sharpness over smoothness.
Recover fabric texture detail and skin pore detail.
Do not over-smooth or make it look plasticky."
```

### Specific Use Case

```
"Upscale this product photo for a 24x36 inch print at 300 DPI.
Ensure edges remain crisp and colors stay accurate.
Remove any compression artifacts from the original."
```

### Combining Upscale with Enhancement

```
"Upscale this old family photo. Remove noise and grain.
Sharpen facial features. Correct any color fading.
Output at the highest resolution possible."
```

## Examples

### General Photo Upscale

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Upscale this photo to the maximum resolution. Keep it photorealistic, sharp, and detailed. Preserve natural skin texture and fabric detail. Remove any JPEG compression artifacts."}],
    "image_urls": ["https://example.com/vacation-photo-small.jpg"],
    "stream": false
  }'
```

### E-commerce Product Enhancement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Upscale this product image for a high-resolution e-commerce listing. The output should be sharp enough for zoom-in product inspection. Enhance material textures — leather grain, stitching detail, metal hardware shine. Remove any noise or compression artifacts."}],
    "image_urls": ["https://example.com/handbag-thumbnail.jpg"],
    "stream": false
  }'
```

### Old Photo Restoration

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Upscale and restore this old scanned photograph. Remove film grain and scanning artifacts. Sharpen facial features while keeping the image natural. Correct any color shifts from aging. Output at the highest possible resolution while maintaining a realistic look."}],
    "image_urls": ["https://example.com/1970s-family-photo.jpg"],
    "stream": false
  }'
```

### AI-Generated Art Enhancement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Upscale this AI-generated artwork for large-format printing. Enhance the painterly textures and fine brush stroke details. Keep the artistic style intact while increasing resolution. Target print quality at 300 DPI for a 20x30 inch poster."}],
    "image_urls": ["https://example.com/ai-artwork-1024px.png"],
    "stream": false
  }'
```

### Print Preparation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Upscale this landscape photograph for large-format printing on canvas. Maximum resolution. Enhance foliage detail, water reflections, and sky gradients. Ensure smooth tonal transitions with no banding. The output will be printed at 40x60 inches, so quality must be exceptional."}],
    "image_urls": ["https://example.com/landscape-web-size.jpg"],
    "stream": false
  }'
```

## Batch Upscaling

```bash
# Upscale a batch of product images
IMAGES=(
  "https://example.com/product-a.jpg"
  "https://example.com/product-b.jpg"
  "https://example.com/product-c.jpg"
)

for IMG in "${IMAGES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Upscale to maximum resolution. Preserve sharpness and detail. Remove compression artifacts.\"}],
      \"image_urls\": [\"$IMG\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Resolution and Print Size Guide

| Input Resolution | Upscale Factor | Output Resolution | Max Print Size (300 DPI) |
|-----------------|---------------|-------------------|-------------------------|
| 512 x 512 | 4x | 2048 x 2048 | ~7 x 7 inches |
| 1024 x 1024 | 4x | 4096 x 4096 | ~14 x 14 inches |
| 1920 x 1080 | 4x | 7680 x 4320 | ~26 x 14 inches |
| 2048 x 1536 | 2x | 4096 x 3072 | ~14 x 10 inches |
| 3000 x 2000 | 2x | 6000 x 4000 | ~20 x 13 inches |

## Common Pitfalls

- **Extremely low resolution** (under 100px) has very little data to work with. Results will be soft regardless.
- **Over-upscaling** (e.g., 16x) produces diminishing returns. 2x-4x is the sweet spot for quality.
- **Expecting new information**: Upscaling enhances and synthesizes detail, but cannot recover information that was never captured.
- **Text in images** may become blurry or distorted during upscaling. Text is harder to reconstruct than natural imagery.
- **Heavy JPEG compression** in the source adds artifacts that upscaling may amplify. Ask for artifact removal explicitly.
- **Over-smoothing** can make images look artificial. Specify "preserve texture, avoid plastic look" if faces appear too smooth.

## Recommended Workflow

1. **Start with the best source** you have (highest resolution, least compressed)
2. **Upscale first**, then apply other edits
3. **Specify the end use** (web, print, social) so the model optimizes accordingly
4. **Combine with editing** for complete enhancement: upscale, then color correct, then final adjustments

## Related Skills

- [Image Editing](../image-editing/SKILL.md) — Edit images after upscaling
- [Background Removal](../background-removal/SKILL.md) — Remove backgrounds from upscaled images
- [Image Generation](../image-generation/SKILL.md) — Generate high-quality images from scratch
- [Face Swap](../face-swap/SKILL.md) — Swap faces on upscaled high-res photos

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
