---
name: ai-fabric-pattern
description: "Design textile and fabric patterns using each::sense AI. Create seamless repeating patterns for fashion, upholstery, wallpaper, and packaging. Supports florals, geometrics, abstract, ethnic, animal print, and custom motifs. Use for: textile design, fabric printing, surface pattern, wallpaper design, packaging patterns, fashion prints. Triggers: fabric pattern, textile design, pattern generator, seamless pattern, surface pattern, print design, textile print, repeat pattern, fabric design, wallpaper pattern"
allowed-tools: Bash(curl *), WebFetch
---

# AI Fabric Pattern

Design original textile and fabric patterns using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design a seamless repeating floral pattern with small wildflowers in soft pink, lavender, and sage green on a cream background. Watercolor illustration style, suitable for cotton fabric printing"
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
        "content": "Design a seamless repeating floral pattern with small wildflowers in soft pink, lavender, and sage green on a cream background. Watercolor illustration style, suitable for cotton fabric printing"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a mood board or existing pattern as inspiration:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a new seamless pattern inspired by the style and color palette of this reference. Keep the same mood but use different motifs — replace the florals with tropical leaves and exotic birds. Suitable for silk fabric."},
              {"type": "image_url", "image_url": {"url": "https://example.com/reference-pattern.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Pattern Categories

| Category | Motifs | Common Uses |
|----------|--------|-------------|
| **Floral** | roses, wildflowers, tropical flowers, botanicals | dresses, curtains, bedding |
| **Geometric** | chevrons, hexagons, triangles, tessellations | shirts, ties, upholstery |
| **Abstract** | brushstrokes, marble, watercolor washes | scarves, blouses, wallpaper |
| **Ethnic** | ikat, batik, paisley, tribal, aztec | bohemian fashion, home textiles |
| **Animal** | leopard, zebra, snakeskin, feathers | statement fashion, accessories |
| **Novelty** | food, animals, objects, characters | children's clothing, accessories |
| **Stripes & Checks** | pinstripe, plaid, gingham, tartan | suiting, casual wear |

## Prompt Engineering Tips

### Prompt Structure

```
[seamless/repeating] + [motif description] + [color palette] + [style] + [background] + [intended use]
```

### Key Phrases for Seamless Patterns

```
seamless repeating pattern, tileable design, continuous repeat,
all-over print, four-way repeat, half-drop repeat,
pattern tile, textile-ready design
```

### Scale Descriptors

```
ditsy (very small repeat), small-scale, medium-scale,
large-scale, oversized motif, micro print, macro print
```

## Examples

### Art Deco Geometric

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a seamless Art Deco geometric pattern with fan shapes and stepped arches. Gold metallic and deep navy color palette on a black background. Luxurious, symmetrical, repeating tile, suitable for evening wear fabric"
      }
    ],
    "stream": false
  }'
```

### Tropical Botanical

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a lush tropical seamless pattern with monstera leaves, palm fronds, and birds of paradise flowers. Rich greens, coral, and teal on a dark jungle green background. Hand-painted botanical illustration style, large-scale repeat for resort wear"
      }
    ],
    "stream": false
  }'
```

### Minimalist Abstract

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a minimalist abstract seamless pattern with irregular organic dots and thin curved lines. Muted terracotta and charcoal on an off-white linen-textured background. Scandinavian design aesthetic, medium-scale repeat, suitable for home textile printing"
      }
    ],
    "stream": false
  }'
```

### Japanese-Inspired Waves

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a seamless pattern inspired by traditional Japanese seigaiha waves. Indigo blue concentric wave arcs on a white background, clean line work, medium-scale repeat. Woodblock print aesthetic, suitable for cotton yukata fabric"
      }
    ],
    "stream": false
  }'
```

## Batch Workflow: Colorway Variations

```bash
COLORWAYS=(
  "coral pink, dusty rose, and cream on a white background"
  "navy blue, teal, and gold on a dark charcoal background"
  "sage green, olive, and tan on a natural linen background"
  "black and white monochrome with grey accents"
)

MOTIF="seamless ditsy floral pattern with small scattered wildflowers and leaves"

for COLORS in "${COLORWAYS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Design a $MOTIF in $COLORS. Hand-drawn illustration style, textile-ready repeat.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Seamless edges** are hard for AI to guarantee. Always specify "seamless repeating" in the prompt; you may still need post-processing to perfect tile edges.
- **Too many colors** (more than 5-6) make patterns look chaotic and are expensive to print.
- **Scale ambiguity** — always state "small-scale", "medium-scale", or "large-scale" to control repeat density.
- **Fabric suitability** — mention the intended fabric (silk, cotton, polyester) to influence weight and detail level.

## Related Skills

- [AI Fashion Model](../ai-fashion-model/SKILL.md) — Show patterns on model garments
- [AI Outfit Generator](../ai-outfit-generator/SKILL.md) — Create outfits with patterned pieces
- [AI Product Mockup](../../ecommerce/ai-product-mockup/SKILL.md) — Apply patterns to product mockups
- [AI Texture Generator](../../3d-ar/ai-texture-generator/SKILL.md) — PBR textures for 3D fabrics

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
