---
name: ai-interior-design
description: "Redesign interiors from photos using each::sense AI. Transform existing rooms into new design concepts while preserving room structure. Supports all design styles from modern minimalist to bohemian, with realistic furniture, materials, and lighting. Use for: interior design concepts, renovation planning, client presentations, room makeovers, design mood boards. Triggers: interior design, room redesign, room makeover, ai interior, interior decorator, room transformation, design concept, home design, interior renovation, room design"
allowed-tools: Bash(curl *), WebFetch
---

# AI Interior Design

Redesign existing interiors from photos using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Redesign this living room in a japandi style: replace the furniture with low-profile pieces in natural wood and muted earth tones. Add a shoji-inspired room divider, floor cushions, a low coffee table, and indoor bonsai plants. Keep the room dimensions and window positions. Warm natural lighting, photorealistic interior design rendering."
      }
    ],
    "image_urls": ["https://example.com/current-living-room.jpg"],
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
        "content": "Redesign this living room in a japandi style: replace the furniture with low-profile pieces in natural wood and muted earth tones. Add a shoji-inspired room divider, floor cushions, a low coffee table, and indoor bonsai plants. Keep the room dimensions and window positions. Warm natural lighting, photorealistic interior design rendering."
    }],
    extra_body={
        "image_urls": ["https://example.com/current-living-room.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide the current room plus a style reference or mood board:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Redesign the room in the first image to match the style of the second image. Apply the same color palette, material choices, and furniture style. Preserve the room layout and window placement from the first image. Photorealistic interior design visualization."
      }
    ],
    "image_urls": [
      "https://example.com/current-room.jpg",
      "https://example.com/inspiration-room.jpg"
    ],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Design Styles Reference

| Style | Key Materials | Color Palette | Defining Features |
|-------|--------------|---------------|-------------------|
| **Modern Minimalist** | glass, steel, concrete | white, grey, black | clean lines, open space, few objects |
| **Japandi** | light wood, linen, ceramic | beige, sage, charcoal | wabi-sabi meets Scandi simplicity |
| **Art Deco** | marble, brass, velvet | emerald, gold, black | geometric patterns, luxury details |
| **Bohemian** | rattan, macrame, textiles | warm earthy + jewel tones | layered textures, global eclectic |
| **Industrial** | exposed brick, metal, concrete | grey, brown, black | raw materials, open-plan |
| **Coastal Modern** | white wood, rattan, sisal | white, navy, sand | airy, organic textures, natural light |
| **Traditional** | dark wood, silk, wool | burgundy, navy, gold | ornate details, symmetry |

## Prompt Engineering Tips

### Prompt Structure

```
"Redesign this [room type] in [style]:" + [specific changes] + [materials and colors] + "Keep [preserved elements]. [Lighting description], photorealistic interior design rendering."
```

### What to Change vs. Preserve

Explicitly separate what should change from what should stay:
```
Change: all furniture, wall color, lighting fixtures, decor
Keep: room dimensions, window positions, ceiling height, floor layout
```

### Material and Finish Vocabulary

```
matte, glossy, satin, brushed, polished, textured, distressed,
whitewashed, lacquered, oiled, patinated, raw, honed, fluted
```

## Examples

### Modern Kitchen Renovation

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Redesign this dated kitchen into a contemporary open kitchen: flat-panel white cabinets, quartz waterfall island in calacatta marble pattern, matte black fixtures and hardware, integrated appliances, pendant lights over the island. Keep the window placement and room footprint. Bright natural light, photorealistic architectural visualization."
      }
    ],
    "image_urls": ["https://example.com/old-kitchen.jpg"],
    "stream": false
  }'
```

### Cozy Bedroom Makeover

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this bedroom into a cozy bohemian retreat: change wall color to warm terracotta, add a low platform bed with a rattan headboard and layered textile bedding in rust and cream, macrame wall hanging, vintage kilim rug, trailing pothos plants on a shelf. Warm evening lamp glow, photorealistic interior design photo."
      }
    ],
    "image_urls": ["https://example.com/plain-bedroom.jpg"],
    "stream": false
  }'
```

### Bathroom Upgrade

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Redesign this bathroom into a spa-inspired space: replace tiles with large-format zellige tiles in sage green, freestanding oval soaking tub, floating vanity in natural oak with a vessel stone basin, matte brass fixtures, frameless glass shower partition, eucalyptus branch in a ceramic vase. Soft diffused lighting, photorealistic interior visualization."
      }
    ],
    "image_urls": ["https://example.com/old-bathroom.jpg"],
    "stream": false
  }'
```

## Workflow: Before/After Comparison

```bash
# Generate redesigns in multiple styles for client comparison
ROOM="https://example.com/current-room.jpg"

DESIGNS=(
  "modern minimalist: white walls, clean-line furniture in light oak, minimal decor, lots of negative space"
  "bohemian eclectic: warm terracotta walls, layered textiles, vintage furniture, plants everywhere"
  "art deco luxury: dark teal walls, velvet furniture, brass accents, geometric patterns, dramatic lighting"
)

for DESIGN in "${DESIGNS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Redesign this room in $DESIGN style. Keep the room dimensions and windows. Photorealistic interior design rendering.\"}],
      \"image_urls\": [\"$ROOM\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Not anchoring to the photo** — without `image_urls`, you get a generic room, not a redesign of your specific space.
- **Changing the architecture** unintentionally — always state "keep room dimensions, window positions, and ceiling height."
- **Mixing too many styles** — "industrial bohemian art deco" produces incoherent results. Pick one primary style.
- **Ignoring scale** — specifying oversized furniture in a small room creates unrealistic output.
- **Forgetting lighting** — mention lighting fixtures and ambient light quality to set the right mood.

## Related Skills

- [AI Virtual Staging](../ai-virtual-staging/SKILL.md) — Furnish empty rooms
- [AI Exterior Remodel](../ai-exterior-remodel/SKILL.md) — Exterior renovation ideas
- [AI Floor Plan](../ai-floor-plan/SKILL.md) — Floor plan generation
- [AI Property Video](../ai-property-video/SKILL.md) — Property walkthrough videos

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided edits
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
