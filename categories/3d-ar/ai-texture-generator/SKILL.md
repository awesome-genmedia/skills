---
name: ai-texture-generator
description: "Generate PBR textures for 3D models using each::sense AI. Create seamless tileable textures including diffuse/albedo, normal, roughness, and displacement maps for materials like wood, metal, stone, fabric, and organic surfaces. Use for: 3D texturing, game asset materials, architectural visualization, product rendering, VFX surfaces, environment art. Triggers: texture generator, pbr texture, seamless texture, 3d texture, material texture, tileable texture, normal map, diffuse map, surface texture, material generator"
allowed-tools: Bash(curl *), WebFetch
---

# AI Texture Generator

Generate PBR textures and seamless materials for 3D models using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a seamless tileable PBR texture of aged red brick wall with crumbling mortar joints, moss growing in the cracks, and some bricks chipped and worn. Square format, photorealistic, high detail, suitable for architectural visualization"
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
        "content": "Generate a seamless tileable PBR texture of aged red brick wall with crumbling mortar joints, moss growing in the cracks, and some bricks chipped and worn. Square format, photorealistic, high detail, suitable for architectural visualization"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Recreate or extend a material from a photo:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Generate a seamless tileable texture that matches this reference material. Replicate the color, grain pattern, and surface detail. Square format, photorealistic, seamless edges for tiling."},
              {"type": "image_url", "image_url": {"url": "https://example.com/material-sample.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Texture Types

| Map Type | Description | Use |
|----------|-------------|-----|
| **Diffuse / Albedo** | base color without lighting | color information |
| **Normal Map** | surface detail via RGB vectors | bump detail without geometry |
| **Roughness** | smooth vs. rough surface | reflection sharpness |
| **Displacement / Height** | actual surface elevation | parallax and tessellation |
| **Ambient Occlusion** | shadow in crevices | depth and realism |
| **Metallic** | metal vs. non-metal | PBR metal workflow |

## Material Categories

| Category | Examples | Key Details |
|----------|----------|-------------|
| **Wood** | oak, walnut, pine, bamboo, plywood | grain direction, knots, finish |
| **Stone** | marble, granite, slate, sandstone, cobblestone | veining, weathering, cut pattern |
| **Metal** | brushed steel, rusted iron, copper patina, gold | scratches, oxidation, reflectivity |
| **Fabric** | cotton, denim, silk, wool, leather | weave pattern, nap, wear |
| **Organic** | bark, moss, mud, sand, coral | irregularity, moisture |
| **Architectural** | concrete, brick, tile, stucco, plaster | joints, weathering, scale |
| **Sci-Fi** | hull plating, circuit board, energy field | paneling, glow, geometry |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate a seamless tileable [map type] texture of [material]:" + [surface details] + [condition/age] + [color] + [format] + [quality keywords]
```

### Seamless Texture Keywords

```
seamless tileable, continuous repeat, no visible seams,
square format 1:1, texture-ready, high resolution,
photographed straight-on, even lighting, no shadows
```

### Condition / Wear Keywords

```
pristine new, lightly weathered, heavily worn, ancient,
rust-pitted, moss-covered, paint-peeling, sun-bleached,
scratched, polished, wet, dusty, frost-covered
```

## Examples

### Sci-Fi Metal Panel

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a seamless tileable texture of sci-fi spaceship hull plating: brushed titanium panels with hexagonal rivets, subtle wear scratches, small warning decal placeholders, and recessed panel seam lines. Cool grey-blue metallic tone, square format, photorealistic PBR albedo map, even flat lighting."
      }
    ],
    "stream": false
  }'
```

### Natural Wood Flooring

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a seamless tileable texture of herringbone oak wood flooring: warm honey-brown tones with natural grain variation between planks, satin finish, slight gaps between boards, photorealistic, square format, flat overhead view, no perspective distortion, suitable for interior 3D rendering."
      }
    ],
    "stream": false
  }'
```

### Fantasy Stone Wall

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a seamless tileable texture of a medieval dungeon stone wall: rough-hewn grey stones of varying sizes fitted together with dark mortar, some stones cracked, green moss in lower crevices, torch soot stains. Hand-painted stylized game texture, square format, suitable for a fantasy RPG environment."
      }
    ],
    "stream": false
  }'
```

### Worn Leather

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a seamless tileable texture of aged brown leather: natural grain pattern, subtle wrinkles and creases, slightly darker patina along wear lines, warm chestnut brown color. Photorealistic, square format, even lighting, no highlights or shadows, PBR-ready diffuse map."
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Material Variants

```bash
MATERIAL="seamless tileable stone texture, square format, photorealistic, even flat lighting"

VARIANTS=(
  "polished white marble with grey veining, smooth reflective surface"
  "rough sandstone with wind-worn surface, warm tan color, desert weathering"
  "dark slate tiles with sharp edges, wet surface sheen, blue-grey tone"
  "volcanic basalt with fine porous holes, dark grey-black, matte rough surface"
)

for VARIANT in "${VARIANTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a $MATERIAL: $VARIANT. PBR albedo map, no perspective distortion.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Perspective distortion** — always specify "flat overhead view" or "straight-on" to avoid angled shots that cannot tile.
- **Lighting baked into texture** — specify "even flat lighting, no shadows, no highlights" for PBR-ready textures. Baked shadows cause artifacts when used with real-time lighting.
- **Non-square output** may not tile correctly. Always request square format.
- **Seamless edges** are not guaranteed by AI. Post-processing with clone/stamp tools or tiling plugins may be needed.
- **Requesting all PBR maps at once** — generate the diffuse map first, then derive normal, roughness, and height maps using dedicated texture tools.

## Related Skills

- [AI 3D Model Generator](../ai-3d-model-generator/SKILL.md) — 3D models to apply textures to
- [Image to 3D](../image-to-3d/SKILL.md) — Convert photos to 3D objects
- [AI Fabric Pattern](../../fashion/ai-fabric-pattern/SKILL.md) — Textile-specific patterns
- [AI Game Environment](../../gaming/ai-game-environment/SKILL.md) — Environments using these textures

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
