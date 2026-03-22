---
name: ai-exterior-remodel
description: "Visualize exterior renovations using each::sense AI. Transform home and building exteriors with new siding, roofing, paint colors, landscaping, additions, and architectural modifications from a photo. Use for: renovation planning, curb appeal visualization, contractor proposals, real estate improvement, homeowner decision-making. Triggers: exterior remodel, home exterior, curb appeal, exterior renovation, house makeover, siding change, paint color visualizer, exterior design, home facelift, facade renovation"
allowed-tools: Bash(curl *), WebFetch
---

# AI Exterior Remodel

Visualize exterior renovations and home makeovers from photos using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Remodel this house exterior: replace the siding with dark charcoal James Hardie board-and-batten, add a natural cedar accent around the front entry, replace the roof with standing seam metal in matte black, and update the front door to a warm wood pivot door. Keep the house structure, driveway, and surrounding trees. Photorealistic exterior rendering, sunny day."
      }
    ],
    "image_urls": ["https://example.com/current-house.jpg"],
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
        "content": "Remodel this house exterior: replace the siding with dark charcoal James Hardie board-and-batten, add a natural cedar accent around the front entry, replace the roof with standing seam metal in matte black, and update the front door to a warm wood pivot door. Keep the house structure, driveway, and surrounding trees. Photorealistic exterior rendering, sunny day."
    }],
    extra_body={
        "image_urls": ["https://example.com/current-house.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide the current property photo plus an inspiration exterior:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Remodel the house in the first image to match the architectural style and materials of the second image. Apply the same color scheme, siding type, and landscaping approach. Keep the original house footprint and lot. Photorealistic result."
      }
    ],
    "image_urls": [
      "https://example.com/my-house.jpg",
      "https://example.com/dream-house-inspiration.jpg"
    ],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Remodel Categories

| Category | Elements | Keywords |
|----------|----------|----------|
| **Siding** | clapboard, board-and-batten, stucco, stone veneer, brick | replace siding, new cladding |
| **Roofing** | asphalt shingle, standing seam metal, clay tile, slate | new roof, reroof |
| **Paint** | body color, trim color, accent color, door color | repaint exterior, color change |
| **Entry** | front door, porch, columns, railings, steps | new front entry, porch addition |
| **Windows** | replacement windows, shutters, trim style | update windows, add shutters |
| **Landscaping** | lawn, garden beds, walkway, driveway, fencing | curb appeal, landscape design |
| **Additions** | garage, porch, deck, dormers, second story | home addition, expand |

## Prompt Engineering Tips

### Prompt Structure

```
"Remodel this [building type] exterior:" + [specific changes by category] + "Keep [preserved elements]. Photorealistic exterior rendering, [lighting/weather]."
```

### Preserving Structure

Always state what must remain:
```
Keep the original house structure, footprint, driveway,
mature trees, and neighboring properties unchanged.
```

### Material Vocabulary

```
fiber cement (Hardie board), natural cedar, engineered stone,
cultured stone, stucco, lime wash, brick, vinyl, aluminum,
standing seam, architectural shingle, membrane
```

## Examples

### Paint Color Visualization

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Repaint this house exterior: body color in Benjamin Moore Hale Navy (deep navy blue), trim and window frames in crisp white, front door in a bold yellow ochre. Keep everything else the same — roof, landscaping, driveway. Photorealistic, bright overcast day for accurate color."
      }
    ],
    "image_urls": ["https://example.com/white-house.jpg"],
    "stream": false
  }'
```

### Modern Farmhouse Conversion

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Transform this dated ranch house into a modern farmhouse: white board-and-batten siding, black-framed windows, a metal gable roof accent over the entryway, a covered porch with black steel columns, and updated landscaping with ornamental grasses and a flagstone path. Keep the house footprint. Photorealistic rendering, golden hour lighting."
      }
    ],
    "image_urls": ["https://example.com/dated-ranch.jpg"],
    "stream": false
  }'
```

### Landscape Curb Appeal

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Improve the curb appeal of this property: add a landscaped front yard with a curved stone-edged walkway, layered garden beds with boxwood hedges and seasonal flowers, two symmetrical Japanese maple trees flanking the entry, landscape lighting along the path, and a new mailbox. Keep the house itself unchanged. Photorealistic, late afternoon soft light."
      }
    ],
    "image_urls": ["https://example.com/plain-yard.jpg"],
    "stream": false
  }'
```

## Batch Workflow: Color Options for Client

```bash
HOUSE="https://example.com/client-house.jpg"

COLORS=(
  "warm grey body with white trim and black front door"
  "sage green body with cream trim and walnut-stained front door"
  "classic white body with black trim and red front door"
  "navy blue body with white trim and brass-accent front door"
)

for COLOR in "${COLORS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Repaint this house exterior with $COLOR. Keep the roof, landscaping, and all structural elements the same. Photorealistic, overcast day for accurate color representation.\"}],
      \"image_urls\": [\"$HOUSE\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Changing the house footprint** when you only want cosmetic changes — explicitly state "keep the house structure and footprint."
- **Unrealistic additions** — adding a second story to a slab foundation looks wrong. Stay within structural plausibility.
- **Weather/season mismatch** — if the photo shows snow, specify whether the render should also show winter or a different season.
- **Ignoring neighboring context** — extreme style changes that clash with the surrounding neighborhood look out of place.
- **Vague color descriptions** — use specific paint names or hex colors when possible for accurate results.

## Related Skills

- [AI Virtual Staging](../ai-virtual-staging/SKILL.md) — Stage interiors with furniture
- [AI Interior Design](../ai-interior-design/SKILL.md) — Redesign room interiors
- [AI Floor Plan](../ai-floor-plan/SKILL.md) — Generate floor plan layouts
- [AI Property Video](../ai-property-video/SKILL.md) — Property tour videos

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided edits
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
