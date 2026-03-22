---
name: image-to-3d
description: "Convert photos to 3D objects using each::sense AI. Transform product photos, character art, and real-world objects into 3D model renders and multi-view outputs. Useful for 3D reconstruction from single images, product 3D previews, and creating 3D references from concept art. Use for: photo to 3D, product 3D modeling, 3D reconstruction, concept art to 3D, single image 3D, e-commerce 3D. Triggers: image to 3d, photo to 3d, picture to 3d, convert to 3d, 3d from photo, 3d reconstruction, single image 3d, 2d to 3d, image 3d model, photo 3d model"
allowed-tools: Bash(curl *), WebFetch
---

# Image to 3D

Convert photos and images into 3D object renders using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Using curl

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert this image into a 3D model. Generate a three-quarter view 3D render showing the object from a slightly elevated angle, revealing depth and volume. Clean studio background, soft lighting, photorealistic 3D rendering."
      }
    ],
    "image_urls": ["https://example.com/product-photo.jpg"],
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
    messages=[{
        "role": "user",
        "content": "Convert this image into a 3D model. Generate a three-quarter view 3D render showing the object from a slightly elevated angle, revealing depth and volume. Clean studio background, soft lighting, photorealistic 3D rendering."
    }],
    extra_body={
        "image_urls": ["https://example.com/product-photo.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Multiple Reference Images

Provide multiple angles for more accurate reconstruction:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert this object into a 3D model using these reference angles. The first image shows the front, the second shows the side. Generate a clean 3D render from a new angle (three-quarter view from above) that combines both perspectives. Studio lighting, neutral background."
      }
    ],
    "image_urls": [
      "https://example.com/front-view.jpg",
      "https://example.com/side-view.jpg"
    ],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Use Cases

| Use Case | Input | Output |
|----------|-------|--------|
| **Product 3D Preview** | product photo | 3D render from new angles |
| **Concept Art to 3D** | 2D character/object art | 3D visualization |
| **Real Object Digitization** | phone photo | 3D model render |
| **Multi-View Generation** | single photo | multiple angle renders |
| **E-commerce 360** | product image | rotated 3D views |
| **Game Asset Reference** | sketch or photo | 3D model for reference |

## Prompt Engineering Tips

### Prompt Structure

```
"Convert this image into a 3D model." + [output angle] + [render style] + [background] + [lighting] + [quality]
```

### Output Angle Keywords

```
front view, side profile, three-quarter view,
rear view, top-down, bottom-up, isometric,
turntable view (multiple angles in one image)
```

### Render Quality Keywords

```
photorealistic 3D render, octane render quality,
Blender Cycles render, studio product lighting,
soft ambient occlusion, subsurface scattering,
clean geometry, smooth shading
```

## Examples

### Product Photo to 3D

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert this product photo into a 3D model render. Show the object from a three-quarter elevated angle that reveals the top and two sides. Maintain exact colors, materials, and proportions from the original photo. Clean white studio background, product photography lighting, photorealistic 3D render."
      }
    ],
    "image_urls": ["https://example.com/headphones.jpg"],
    "stream": false
  }'
```

### Character Art to 3D

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert this 2D character illustration into a 3D model render. Show a three-quarter view from the right side with slightly elevated camera. Maintain the character design, colors, and proportions from the original art. Stylized 3D render with soft cel-shading, neutral grey background."
      }
    ],
    "image_urls": ["https://example.com/character-concept.png"],
    "stream": false
  }'
```

### Multi-View Turntable

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert this object into a 3D model and generate a turntable view showing 4 angles in a single image: front, right side, back, and left side. Arranged in a 2x2 grid. Same scale in each view, neutral grey background, consistent studio lighting, clean 3D render."
      }
    ],
    "image_urls": ["https://example.com/sneaker-front.jpg"],
    "stream": false
  }'
```

### Architectural Element

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Convert this photo of a decorative column capital into a 3D model render. Show it from an isometric angle with soft directional lighting to emphasize the carved relief details. Clean background, architectural 3D visualization quality, accurate proportions."
      }
    ],
    "image_urls": ["https://example.com/column-capital.jpg"],
    "stream": false
  }'
```

## Batch Workflow: 360-Degree Views

```bash
OBJECT_IMAGE="https://example.com/product.jpg"

ANGLES=(
  "front view, straight-on"
  "right side profile"
  "three-quarter view from the right, slightly elevated"
  "rear view"
  "three-quarter view from the left, slightly elevated"
  "left side profile"
)

for ANGLE in "${ANGLES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Convert this object into a 3D model render. Show it from $ANGLE. Maintain original colors and materials. Clean white background, studio lighting, photorealistic 3D render.\"}],
      \"image_urls\": [\"$OBJECT_IMAGE\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Best Practices for Input Images

- **Clean background** — white or solid color backgrounds produce better results than cluttered scenes.
- **Good lighting** — evenly lit photos reveal more surface detail for reconstruction.
- **Single object** — isolate the subject. Multiple objects confuse the reconstruction.
- **Sharp focus** — blurry or low-resolution images lose detail in 3D conversion.
- **No heavy occlusion** — the more of the object visible, the better the 3D inference.

## Common Pitfalls

- **AI generates rendered images**, not actual 3D mesh files. The output is a new-angle 2D render of the interpreted 3D form.
- **Occluded parts are inferred** — the back of an object seen only from the front is guessed. It may not match reality.
- **Flat or thin objects** (cards, stickers, flat art) do not convert meaningfully to 3D.
- **Reflective and transparent objects** (glass, mirrors) are harder to interpret correctly.
- **Scale is relative** — without reference objects, the model cannot infer absolute size.

## Related Skills

- [AI 3D Model Generator](../ai-3d-model-generator/SKILL.md) — Text-to-3D generation
- [AI Texture Generator](../ai-texture-generator/SKILL.md) — Surface textures for 3D models
- [AI Product Photo](../../ecommerce/ai-product-photo/SKILL.md) — Product photography
- [AI Product Mockup](../../ecommerce/ai-product-mockup/SKILL.md) — Product mockups

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided generation
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
