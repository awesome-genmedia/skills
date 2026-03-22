---
name: ai-3d-model-generator
description: "Generate 3D models from text or images using each::sense AI. Create 3D objects, characters, environments, and product models from descriptions or reference photos. Supports mesh generation for games, product visualization, architectural models, and 3D printing. Use for: 3D asset creation, product 3D models, game 3D assets, prototyping, 3D printing models, architectural visualization. Triggers: 3d model generator, text to 3d, ai 3d model, 3d object, 3d asset, generate 3d, create 3d model, 3d mesh, 3d generation, ai 3d"
allowed-tools: Bash(curl *), WebFetch
---

# AI 3D Model Generator

Generate 3D models from text descriptions or reference images using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a 3D model of a medieval treasure chest: wooden planks with iron bands, a heavy padlock on the front latch, slightly worn and aged appearance, ornate iron corner reinforcements. Isometric 3D render on a neutral grey background, game-ready asset quality."
      }
    ],
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
        "content": "Generate a 3D model of a medieval treasure chest: wooden planks with iron bands, a heavy padlock on the front latch, slightly worn and aged appearance, ornate iron corner reinforcements. Isometric 3D render on a neutral grey background, game-ready asset quality."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a photo or sketch to generate the 3D model from:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Generate a 3D model based on this reference image. Recreate the object as a clean 3D render from a three-quarter view angle, maintaining the proportions, colors, and details. Neutral studio background, soft lighting."},
              {"type": "image_url", "image_url": {"url": "https://example.com/reference-object.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Use Cases

| Domain | Examples |
|--------|----------|
| **Gaming** | props, weapons, vehicles, characters, environment pieces |
| **E-commerce** | product 3D previews, configurators, AR try-on |
| **Architecture** | building models, furniture, fixtures |
| **3D Printing** | figurines, prototypes, replacement parts |
| **Education** | anatomical models, molecular structures, historical artifacts |
| **Film/VFX** | pre-visualization, CG assets, matte painting elements |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate a 3D model of [object]:" + [shape and proportions] + [materials and colors] + [surface details] + [render style] + [camera angle] + [background]
```

### Material Description

```
brushed steel, polished wood, matte plastic, rough stone,
translucent glass, worn leather, oxidized copper, frosted ice,
glossy ceramic, weathered concrete, carbon fiber
```

### Render Style Keywords

```
3D render, isometric view, three-quarter angle,
Blender render, octane render, clay render (no texture),
wireframe overlay, turntable view, studio lighting
```

## Examples

### Stylized Game Weapon

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 3D model of a fantasy war hammer: a massive stone head with glowing blue rune carvings, a thick leather-wrapped oak handle, and a spiked pommel. Stylized low-poly game art style, three-quarter view, dramatic rim lighting, dark background, game-ready 3D asset."
      }
    ],
    "stream": false
  }'
```

### Product Visualization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 3D model of a modern desk lamp: a thin adjustable arm in matte black metal, a cone-shaped shade, a weighted circular base, and a visible fabric-covered power cord. Photorealistic 3D render, studio product photography lighting, clean white background, commercial quality."
      }
    ],
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
        "content": "Generate a 3D model of a modern minimalist house: flat roof, floor-to-ceiling glass walls on the front facade, white concrete exterior, a cantilevered upper floor, a small reflecting pool at the entrance, and surrounding landscaped garden. Architectural 3D rendering, isometric aerial view, daytime with soft shadows, clean neutral background."
      }
    ],
    "stream": false
  }'
```

### 3D Printable Figurine

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a 3D model of a tabletop miniature: a dwarven warrior holding an axe and shield, beard braided, heavy plate armor, standing on a small round base. Grey clay render style showing surface detail without color, three-quarter view, suitable for 3D printing, clean background."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Multi-Angle Views

```bash
OBJECT="a sci-fi hover bike with sleek chrome body, blue thruster glow, and a leather seat"

ANGLES=(
  "front view, straight-on"
  "three-quarter view from the left side"
  "side profile, left-facing"
  "rear three-quarter view"
  "top-down orthographic view"
)

for ANGLE in "${ANGLES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a 3D render of $OBJECT. Camera angle: $ANGLE. Photorealistic render, studio lighting, neutral grey background.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **AI generates images of 3D models**, not actual mesh files (OBJ, FBX, GLB). Use the output as reference for manual modeling or as a visual asset.
- **Overly complex geometry descriptions** may not translate well. Focus on overall shape and key features.
- **Inconsistent scale** — include a size reference or context object if scale matters.
- **Multiple objects** in one prompt reduce quality. Generate one object at a time.
- **Thin or intricate details** (chains, fine wire, filigree) are harder to render accurately.

## Related Skills

- [Image to 3D](../image-to-3d/SKILL.md) — Convert photos to 3D objects
- [AI Texture Generator](../ai-texture-generator/SKILL.md) — PBR textures for 3D models
- [AI AR Filter](../ai-ar-filter/SKILL.md) — AR face filters and effects
- [AI Game Asset](../../gaming/ai-game-asset/SKILL.md) — Game-ready assets

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
