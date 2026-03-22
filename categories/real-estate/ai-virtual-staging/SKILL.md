---
name: ai-virtual-staging
description: "Stage empty rooms with virtual furniture using each::sense AI. Transform vacant property photos into beautifully furnished spaces with realistic furniture, decor, and lighting. Supports living rooms, bedrooms, kitchens, offices, and commercial spaces in any style. Use for: real estate listings, property marketing, home staging, interior visualization, rental listings. Triggers: virtual staging, stage empty room, ai staging, furniture staging, room staging, property staging, virtual furnishing, empty room design, real estate staging, home staging"
allowed-tools: Bash(curl *), WebFetch
---

# AI Virtual Staging

Stage empty rooms with photorealistic virtual furniture and decor using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Stage this empty living room with modern Scandinavian furniture: a light grey sectional sofa, a round walnut coffee table, a cream wool rug, floor-standing brass lamp, and two small potted plants. Keep the original room architecture, flooring, and windows exactly as they are. Photorealistic staging."
      }
    ],
    "image_urls": ["https://example.com/empty-living-room.jpg"],
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
        "content": "Stage this empty living room with modern Scandinavian furniture: a light grey sectional sofa, a round walnut coffee table, a cream wool rug, floor-standing brass lamp, and two small potted plants. Keep the original room architecture, flooring, and windows exactly as they are. Photorealistic staging."
    }],
    extra_body={
        "image_urls": ["https://example.com/empty-living-room.jpg"]
    }
)

print(response.choices[0].message.content)
```

### With Reference Image

Always provide a photo of the empty room. Optionally add a style reference:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Stage the empty room in the first image using the furniture style shown in the second image. Match the aesthetic, color palette, and level of furnishing. Keep the original room layout and architecture intact. Photorealistic result."
      }
    ],
    "image_urls": [
      "https://example.com/empty-room.jpg",
      "https://example.com/style-reference.jpg"
    ],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Staging Styles

| Style | Characteristics | Best For |
|-------|----------------|----------|
| **Modern Scandinavian** | light wood, clean lines, neutral palette, minimal | apartments, condos |
| **Mid-Century Modern** | walnut, tapered legs, organic shapes, muted tones | vintage-character homes |
| **Contemporary Luxury** | marble, brass, velvet, statement lighting | high-end listings |
| **Farmhouse** | shiplap, distressed wood, linen, warm whites | suburban homes |
| **Industrial Loft** | metal, exposed materials, leather, Edison bulbs | lofts, converted spaces |
| **Coastal** | white, blue, natural textures, rattan, driftwood | beach properties |
| **Urban Minimalist** | monochrome, few pieces, high-impact, geometric | city apartments |

## Prompt Engineering Tips

### Prompt Structure

```
"Stage this empty [room type] with [style] furniture:" + [specific furniture items] + "Keep the original [preserved elements]. Photorealistic staging."
```

### What to Preserve

Always explicitly state what should remain unchanged:
```
Keep the original room architecture, walls, flooring, windows,
ceiling, and natural lighting exactly as they are.
```

### Furniture Specificity

Be concrete about furniture instead of vague:
- Instead of "add a sofa" say "charcoal linen three-seater sofa with oak legs"
- Instead of "add a table" say "round marble-top dining table for four with black metal base"

## Examples

### Bedroom Staging

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Stage this empty bedroom with a queen-size upholstered bed in soft grey with white linen bedding, two oak nightstands with ceramic table lamps, a woven jute rug, and sheer white curtains. Modern Scandinavian style. Keep the original hardwood floor, walls, and window. Photorealistic result, real estate photography quality."
      }
    ],
    "image_urls": ["https://example.com/empty-bedroom.jpg"],
    "stream": false
  }'
```

### Kitchen / Dining Area

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Stage this empty kitchen dining area with a rectangular oak dining table and six black Windsor chairs, a pendant light fixture over the table, a small vase with eucalyptus branches, and placemats. Farmhouse style. Preserve the existing kitchen cabinets, countertops, and appliances. Photorealistic, natural daylight."
      }
    ],
    "image_urls": ["https://example.com/empty-kitchen-dining.jpg"],
    "stream": false
  }'
```

### Home Office

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Stage this empty room as a home office: walnut standing desk with a monitor, ergonomic mesh chair, wall-mounted floating shelves with books and small plants, a floor lamp with warm light, and a geometric area rug. Contemporary minimalist style. Keep original walls, floor, and window. Photorealistic, professional real estate photo."
      }
    ],
    "image_urls": ["https://example.com/empty-room.jpg"],
    "stream": false
  }'
```

## Batch Workflow: Multiple Style Options

```bash
ROOM_PHOTO="https://example.com/empty-living-room.jpg"

STYLES=(
  "modern Scandinavian: light grey sofa, birch coffee table, white wool rug, minimalist decor"
  "mid-century modern: teal velvet sofa, walnut credenza, sunburst mirror, warm brass accents"
  "contemporary luxury: cream leather sectional, marble coffee table, gold floor lamp, abstract art"
)

for STYLE in "${STYLES[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Stage this empty living room with $STYLE. Keep all original architecture, flooring, and windows. Photorealistic real estate photography.\"}],
      \"image_urls\": [\"$ROOM_PHOTO\"],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **Ignoring room scale** — specifying a king bed in a small room creates unrealistic results. Match furniture scale to the room.
- **Overloading the room** — less is more for real estate. 5-7 key pieces per room is the sweet spot.
- **Forgetting lighting** — always mention at least one light source (lamp, pendant) for warmth.
- **Not preserving architecture** — without explicit instructions, the model may alter walls, flooring, or window positions.
- **Floating furniture** — poorly described placement can result in furniture that does not sit naturally on the floor.

## Related Skills

- [AI Interior Design](../ai-interior-design/SKILL.md) — Full room redesign concepts
- [AI Exterior Remodel](../ai-exterior-remodel/SKILL.md) — Exterior renovation visualization
- [AI Floor Plan](../ai-floor-plan/SKILL.md) — Generate floor plan layouts
- [AI Property Video](../ai-property-video/SKILL.md) — Property tour videos

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for image-guided edits
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
