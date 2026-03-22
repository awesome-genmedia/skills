---
name: ai-menu-visualization
description: "Generate menu item imagery for restaurants using each::sense AI. Create consistent, appetizing photographs of dishes for digital menus, printed menus, delivery apps, and restaurant websites. Produce cohesive visual sets that match a restaurant's brand aesthetic. Use for: menu photography, restaurant menus, food delivery images, digital menu visuals, dish photography. Triggers: menu visualization, menu photo, restaurant menu, food menu, dish image, menu item, digital menu, delivery app photo, restaurant imagery, menu design"
allowed-tools: Bash(curl *), WebFetch
---

# AI Menu Visualization

Generate consistent, appetizing menu item imagery for restaurants and food services using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "A menu item photograph of a classic margherita pizza: thin crispy crust, fresh mozzarella, San Marzano tomato sauce, and basil leaves, slightly charred edges from a wood-fired oven, served on a round wooden board, 45-degree angle, warm ambient restaurant lighting, appetizing and inviting, consistent clean background"
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
        "content": "A menu item photograph of a classic margherita pizza: thin crispy crust, fresh mozzarella, San Marzano tomato sauce, and basil leaves, slightly charred edges from a wood-fired oven, served on a round wooden board, 45-degree angle, warm ambient restaurant lighting, appetizing and inviting, consistent clean background"
    }]
)

print(response.choices[0].message.content)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Menu Visualization

- **Use consistent style keywords** across all menu items — same surface, lighting, angle, and background.
- **Specify the plating and dishware** — match the restaurant's actual service style.
- **Include portion context** — describe the plate size and garnish for realistic proportions.
- **Match the cuisine aesthetic** — rustic for Italian, clean for Japanese, vibrant for Mexican.
- **Optimize for digital** — mention "delivery app photo" or "digital menu" for clean, well-lit images.

## Examples

### Appetizer Section

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A menu item photograph of bruschetta: three pieces of toasted ciabatta topped with diced tomatoes, fresh basil, and a balsamic glaze drizzle, arranged on a small white rectangular plate, dark slate surface, soft overhead lighting, clean menu photography style, delivery app ready"
      }
    ],
    "stream": false
  }'
```

### Main Course

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A menu item photograph of a grilled ribeye steak: medium-rare with visible grill marks, served with a side of creamy mashed potatoes and grilled broccolini, a small ramekin of peppercorn sauce, on a large white plate, dark wooden table, warm side lighting, premium steakhouse menu photography"
      }
    ],
    "stream": false
  }'
```

### Batch Menu Generation

```bash
# Generate a consistent set of menu item photos
ITEMS=(
  "Menu photo: chicken caesar salad with grilled chicken strips, romaine lettuce, croutons, parmesan shavings, and caesar dressing, white bowl, dark slate surface, soft overhead lighting, clean menu style"
  "Menu photo: fish and chips with crispy beer-battered cod, thick-cut fries, mushy peas, and tartar sauce, served in a paper-lined wire basket, dark slate surface, soft overhead lighting, clean menu style"
  "Menu photo: a towering gourmet cheeseburger with double patty, cheddar, lettuce, tomato, pickles, and special sauce, brioche bun, side of fries, dark slate surface, soft overhead lighting, clean menu style"
)

for ITEM in "${ITEMS[@]}"; do
  curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
    -H "Content-Type: application/json" \
    -H "X-API-Key: $EACHLABS_API_KEY" \
    -d "{
      \"messages\": [{\"role\": \"user\", \"content\": \"$ITEM\"}],
      \"stream\": false
    }"
  echo "---"
done
```

## Workflow: Full Menu Photography

1. **Define the visual style** — Choose surface, lighting, angle, and plate style for consistency.
2. **Generate appetizers** — Create images for all starter items.
3. **Generate mains** — Produce hero images for main courses.
4. **Generate desserts and drinks** — Complete the menu coverage.
5. **Review for consistency** — Ensure all images share the same visual language.
6. **Export for platforms** — Prepare images for print menu, website, and delivery apps.

## Related Skills

- [AI Food Photography](../ai-food-photography/SKILL.md) — Professional food photography
- [AI Recipe Visualization](../ai-recipe-visualization/SKILL.md) — Recipe process visuals
- [Social Media Batch](../../workflows/social-media-batch/SKILL.md) — Social media food content
- [Text to Image](../../image/text-to-image/SKILL.md) — General image generation

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Photorealistic food imagery
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Appetizing visual quality
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Rapid menu item generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
