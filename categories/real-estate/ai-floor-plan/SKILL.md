---
name: ai-floor-plan
description: "Generate floor plan layouts using each::sense AI. Create architectural floor plans for homes, apartments, offices, and commercial spaces from text descriptions. Supports single and multi-story layouts with room labels, dimensions, and furniture placement. Use for: architectural planning, real estate marketing, interior layout, space planning, renovation design. Triggers: floor plan, floor plan generator, house plan, room layout, architectural plan, space planning, apartment layout, home layout, building plan, room arrangement"
allowed-tools: Bash(curl *), WebFetch
---

# AI Floor Plan

Generate architectural floor plan layouts from text descriptions using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a 2D architectural floor plan for a 1200 sq ft, 2-bedroom, 2-bathroom apartment. Open-concept living room and kitchen, master bedroom with en-suite bathroom and walk-in closet, second bedroom near a shared bathroom, laundry closet, and a small balcony off the living area. Top-down view, clean black lines on white background, room labels included."
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
        "content": "Generate a 2D architectural floor plan for a 1200 sq ft, 2-bedroom, 2-bathroom apartment. Open-concept living room and kitchen, master bedroom with en-suite bathroom and walk-in closet, second bedroom near a shared bathroom, laundry closet, and a small balcony off the living area. Top-down view, clean black lines on white background, room labels included."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a rough sketch or existing floor plan to refine:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Redraw this rough floor plan sketch as a clean professional architectural floor plan. Add room labels, door swings, and window indicators. Maintain the same room layout and proportions. Black lines on white background, top-down view."
      }
    ],
    "image_urls": ["https://example.com/rough-sketch.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Floor Plan Types

| Type | Description | Use Case |
|------|-------------|----------|
| **2D Line Plan** | clean lines, walls, doors, windows | architectural documentation |
| **Furnished Plan** | floor plan with furniture placement | staging and layout |
| **Color-Coded Plan** | rooms shaded by function | marketing materials |
| **3D Isometric** | 3D cutaway view of the layout | presentations and visualization |
| **Site Plan** | building footprint on lot | real estate development |

## Prompt Engineering Tips

### Prompt Structure

```
"Generate a [plan type] floor plan for a [size] [property type]:" + [room list with relationships] + [special features] + [visual style] + [view type]
```

### Room Relationship Language

Use spatial relationships to guide layout:
```
"master bedroom adjacent to the en-suite bathroom"
"kitchen opens directly into the dining area"
"laundry room accessible from the hallway near the bedrooms"
"garage connects to the kitchen through a mudroom"
```

### Visual Style Keywords

```
architectural line drawing, black and white, blueprint style,
clean vector, minimalist technical drawing, color-coded rooms,
isometric 3D cutaway, top-down plan view
```

## Examples

### Single-Family Home

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a floor plan for a single-story 1800 sq ft family home with 3 bedrooms and 2 bathrooms. Open-concept kitchen, dining, and living area with a large island. Master suite on one side with walk-in closet and en-suite bath. Two secondary bedrooms sharing a jack-and-jill bathroom on the other side. Attached two-car garage connecting through a mudroom. Covered back patio. Clean architectural line drawing, top-down view, room labels, door swings shown."
      }
    ],
    "stream": false
  }'
```

### Studio Apartment

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a furnished floor plan for a 500 sq ft studio apartment. Combined living and sleeping area with a queen bed and a sofa separated by a bookshelf. Galley kitchen along one wall, small dining nook for two, bathroom with shower stall, and a closet near the entry. Show furniture placement. Top-down view, clean lines, labeled rooms."
      }
    ],
    "stream": false
  }'
```

### Office Space Layout

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a floor plan for a 3000 sq ft open-plan office: reception area at the entrance, open workspace with 16 desks in clusters of 4, two glass-walled meeting rooms seating 8 each, one private office for the manager, a kitchenette and break area, server room, and restrooms. Clearly labeled, top-down architectural drawing, clean black lines."
      }
    ],
    "stream": false
  }'
```

## Important Notes on AI Floor Plans

AI-generated floor plans are conceptual starting points, not construction documents:

- **Proportions may be approximate** — use the output for ideation, then refine in CAD software.
- **Text labels** can be imperfect — AI text rendering has limitations. Consider adding labels manually.
- **Building codes and structural requirements** are not considered — always consult an architect for buildable plans.
- **Dimensions shown** may not be mathematically precise — treat them as rough guides.

## Batch Workflow: Layout Variations

```bash
LAYOUTS=(
  "open-concept with kitchen island, bedrooms on opposite sides of the house"
  "traditional layout with separate formal dining room and living room, bedrooms clustered together"
  "split-level with living areas on the entry level and bedrooms half a flight up"
)

for LAYOUT in "${LAYOUTS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"Generate a floor plan for a 1600 sq ft 3-bedroom 2-bath home with $LAYOUT. Clean architectural line drawing, top-down, room labels.\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Common Pitfalls

- **No size reference** — always state total square footage or approximate room dimensions.
- **Forgetting circulation** — hallways, doorways, and stairways are often overlooked. Mention them explicitly.
- **Unrealistic room counts** — five bedrooms in 800 sq ft will produce cramped, impractical layouts.
- **Skipping adjacencies** — if you want the kitchen near the dining room, say so. Do not assume logical placement.

## Related Skills

- [AI Virtual Staging](../ai-virtual-staging/SKILL.md) — Stage rooms with furniture
- [AI Interior Design](../ai-interior-design/SKILL.md) — Redesign room interiors
- [AI Exterior Remodel](../ai-exterior-remodel/SKILL.md) — Exterior renovation visualization
- [AI 3D Model Generator](../../3d-ar/ai-3d-model-generator/SKILL.md) — 3D architectural models

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
