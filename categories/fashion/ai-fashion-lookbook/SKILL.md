---
name: ai-fashion-lookbook
description: "Generate complete fashion lookbook layouts using each::sense AI. Create cohesive multi-look editorial spreads with consistent styling, themed collections, and professional compositions for seasonal campaigns, brand launches, and fashion portfolios. Use for: fashion collections, seasonal lookbooks, brand campaigns, editorial spreads, portfolio presentation, fashion marketing. Triggers: fashion lookbook, lookbook generator, fashion collection, editorial spread, seasonal collection, lookbook layout, fashion campaign, brand lookbook, collection showcase, style book"
allowed-tools: Bash(curl *), WebFetch
---

# AI Fashion Lookbook

Generate complete fashion lookbook imagery and layouts using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A fashion lookbook photo: a model wearing a flowing maxi dress in terracotta, walking through a sunlit olive grove in Tuscany. Wind catching the fabric, golden hour, editorial photography, full body shot, warm color grading, Vogue style"
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
        "content": "A fashion lookbook photo: a model wearing a flowing maxi dress in terracotta, walking through a sunlit olive grove in Tuscany. Wind catching the fabric, golden hour, editorial photography, full body shot, warm color grading, Vogue style"
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a mood board or sample look for the collection aesthetic:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a lookbook photo matching this mood and color palette. A model in a structured wool coat and turtleneck, same visual tone and lighting style as the reference. Urban winter setting, overcast sky, editorial fashion photography."
      }
    ],
    "image_urls": ["https://example.com/mood-board.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Lookbook Themes

| Theme | Setting | Color Palette | Season |
|-------|---------|---------------|--------|
| **Mediterranean Summer** | olive groves, white walls, coast | terracotta, white, sky blue | SS |
| **Nordic Winter** | snow, concrete, birch forests | ivory, charcoal, pale blue | AW |
| **Urban Night** | city lights, neon, rain-wet streets | black, silver, electric blue | AW |
| **Desert Modernist** | desert, mid-century architecture | sand, rust, sage | Resort |
| **Parisian Spring** | cafes, gardens, architecture | blush, cream, dusty blue | SS |
| **Industrial Raw** | warehouses, steel, exposed brick | grey, khaki, raw denim | Pre-Fall |

## Prompt Engineering Tips

### Prompt Structure

```
"A fashion lookbook photo:" + [model description] + [outfit details] + [setting/location] + [mood/atmosphere] + [photography style] + [camera details]
```

### Consistency Across Looks

For a cohesive lookbook, keep these elements constant across all prompts:
- **Location type** (same setting or setting category)
- **Lighting** (golden hour, overcast, studio)
- **Color grading** (warm, cool, desaturated)
- **Photography style** (editorial, commercial, street)
- **Model description** (same height, hair, build)

## Examples

### Look 1 — Hero Shot

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A fashion lookbook hero shot: a tall female model with slicked-back dark hair wearing a sculptural white blazer with exaggerated shoulders over a matching wide-leg trouser. Standing on a rooftop overlooking a city at dusk. Dramatic side lighting, strong shadow, high fashion editorial, shot from low angle, desaturated teal and warm amber color grade"
      }
    ],
    "stream": false
  }'
```

### Look 2 — Detail Close-Up

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A fashion lookbook detail shot: close-up on hands adjusting the cuff of a cream silk blouse, delicate pearl button visible, soft natural light from a window, shallow depth of field, minimal warm-toned editorial photography, macro lens feel"
      }
    ],
    "stream": false
  }'
```

### Look 3 — Lifestyle Context

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A fashion lookbook lifestyle shot: a model in a camel cashmere overcoat and cream scarf, walking through a misty Parisian street with bare autumn trees. Candid mid-stride movement, film photography aesthetic with slight grain, warm desaturated tones, full body shot"
      }
    ],
    "stream": false
  }'
```

## Collection Workflow: Seasonal Lookbook

```bash
COLLECTION_THEME="Autumn/Winter collection, Nordic minimalism, muted earth tones, overcast natural light, editorial fashion photography"

LOOKS=(
  "Look 1: oversized charcoal wool coat over cream cable-knit sweater and dark brown leather trousers, standing in a birch forest"
  "Look 2: camel turtleneck dress belted at the waist with cognac leather boots, seated on a concrete bench in an urban park"
  "Look 3: layered outfit — grey knit vest over white poplin shirt with wide olive trousers, walking along a misty lakefront"
  "Look 4: black tailored suit with an open-neck silk shirt in ivory, leaning against a steel railing at a modernist building"
  "Look 5: chunky cream fisherman sweater with a long pleated skirt in heather grey, standing on weathered wooden pier"
)

for LOOK in "${LOOKS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"A fashion lookbook photo: female model with short auburn hair, $LOOK. $COLLECTION_THEME, full body shot, Vogue Scandinavia style\"}],
      \"stream\": false
    }"
  echo "=== $LOOK ==="
done
```

## Shot List for a Complete Lookbook

1. **Hero / Cover** — full body, dramatic composition, establishes the collection mood
2. **Full Length Front** — clean front-facing shot showing complete outfit
3. **Three-Quarter Turn** — shows garment from an angled perspective
4. **Detail Close-Up** — fabric texture, buttons, stitching, jewelry
5. **Back View** — reveals back design elements
6. **Lifestyle / Movement** — model walking, turning, interacting with environment
7. **Group / Pairing** — two looks styled together for contrast

## Common Pitfalls

- **Inconsistent model** across shots — repeat the exact same model description in every prompt.
- **Mixed photography styles** — keep the same camera, lighting, and grading keywords throughout.
- **Overly complex backgrounds** that distract from the garments. The setting should complement, not compete.
- **Ignoring negative space** — lookbooks need breathing room for text overlays in final layout.

## Related Skills

- [AI Fashion Model](../ai-fashion-model/SKILL.md) — Individual model shots
- [AI Outfit Generator](../ai-outfit-generator/SKILL.md) — Outfit creation and styling
- [AI Fabric Pattern](../ai-fabric-pattern/SKILL.md) — Custom textile designs
- [AI Clothing Try-On](../ai-clothing-try-on/SKILL.md) — Virtual try-on for real people

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
