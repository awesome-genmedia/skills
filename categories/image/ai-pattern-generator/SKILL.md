---
name: ai-pattern-generator
description: "Generate seamless tileable patterns using each::sense AI. Create repeating designs for textiles, wallpapers, packaging, web backgrounds, and surface design in any style from floral to geometric, abstract to vintage. Supports fabric-ready, print-ready, and digital-ready patterns. Use for: textile design, fabric patterns, wrapping paper, web backgrounds, packaging design, surface design, brand patterns. Triggers: ai pattern, pattern generator, seamless pattern, tileable pattern, textile design, fabric pattern, surface pattern, repeating pattern, wallpaper pattern, wrapping paper, background pattern"
allowed-tools: Bash(curl *), WebFetch
---

# AI Pattern Generator

Generate seamless tileable patterns for textiles, surfaces, and digital backgrounds using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a seamless tileable pattern of tropical monstera leaves and palm fronds on a deep navy background. Botanical illustration style, green and emerald tones, repeating pattern suitable for fabric printing."
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
        "content": "Generate a seamless tileable pattern of tropical monstera leaves and palm fronds on a deep navy background. Botanical illustration style, green and emerald tones, repeating pattern suitable for fabric printing."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Use a reference pattern or style image:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a seamless tileable pattern inspired by this design style but with a different motif: use small wildflowers and herbs instead. Keep the same color palette and density. Repeating tile format."
      }
    ],
    "image_urls": ["https://example.com/reference-pattern.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Pattern Categories

| Category | Subjects | Applications |
|----------|---------|--------------|
| **Floral** | Roses, wildflowers, tropical flowers | Fabric, wallpaper, stationery |
| **Botanical** | Leaves, ferns, eucalyptus, herbs | Home decor, wrapping paper |
| **Geometric** | Hexagons, triangles, chevrons, diamonds | Modern textiles, tiles, tech |
| **Abstract** | Organic blobs, brush strokes, splatters | Fashion, backgrounds |
| **Animal** | Leopard print, zebra, scales, feathers | Fashion, accessories |
| **Art Deco** | Fan shapes, zigzags, gold accents | Luxury packaging, invitations |
| **Terrazzo** | Stone chips, speckles, confetti | Stationery, surfaces |
| **Toile** | Scenic illustrations, pastoral | Traditional home decor |

## Examples

### Geometric Mid-Century

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Seamless tileable pattern in mid-century modern style. Atomic age starbursts, boomerang shapes, and organic ovals. Mustard yellow, teal, burnt orange, and cream on a warm white background. Clean vector style, repeating tile."
      }
    ],
    "stream": false
  }'
```

### Luxury Wrapping Paper

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Seamless tileable pattern for luxury gift wrapping paper. Art Deco style with golden fan shapes, geometric lines, and small diamond accents. Gold on a deep midnight blue background. Elegant, sophisticated, repeating tile format."
      }
    ],
    "stream": false
  }'
```

### Children's Fabric Pattern

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Seamless tileable pattern for children's fabric. Cute hand-drawn dinosaurs in pastel colors — mint green, soft pink, lavender, and peach. Small stars and leaves scattered between the dinosaurs. White background, playful illustration style, repeating tile."
      }
    ],
    "stream": false
  }'
```

## Prompt Tips for Seamless Patterns

- **Always say "seamless tileable"** — this signals the model to create edges that match when repeated
- **Specify the background color** to control the overall feel
- **Describe density**: "densely packed" vs. "scattered with space between elements"
- **Mention the end use**: "for fabric printing," "for web background," "for packaging" — this helps optimize the scale
- **Keep motif count low**: 3-5 distinct elements tile better than complex scenes
- **Add "repeating tile format"** for the clearest intent

## Scale Guide

| Application | Pattern Density | Motif Size |
|-------------|----------------|------------|
| **Dress Fabric** | Medium density | Small to medium motifs |
| **Upholstery** | Large scale | Big motifs, bold |
| **Stationery** | Fine, delicate | Tiny repeated elements |
| **Web Background** | Subtle, low contrast | Small, non-distracting |
| **Wrapping Paper** | Medium density | Medium motifs |
| **Tile/Flooring** | Structured grid | Geometric, precise |

## Related Skills

- [Text to Image](../text-to-image/SKILL.md) — General image generation
- [AI Wallpaper Generator](../ai-wallpaper-generator/SKILL.md) — Full wallpaper designs
- [AI Coloring Page](../ai-coloring-page/SKILL.md) — Line art pattern pages
- [AI Tattoo Generator](../ai-tattoo-generator/SKILL.md) — Mandala and pattern-based designs

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
