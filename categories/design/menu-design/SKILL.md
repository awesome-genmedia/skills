---
name: menu-design
description: "Design restaurant and cafe menu layouts using each::sense AI. Generate beautiful menu backgrounds, food illustrations, decorative borders, and themed visual elements for restaurants, cafes, bars, bakeries, and food trucks. Supports various cuisines and dining styles from fine dining to casual eateries. Use for: restaurant menus, cafe menus, bar menus, bakery menus, food truck menus, wine lists, cocktail menus, catering menus. Triggers: menu design, restaurant menu, cafe menu, food menu, bar menu, cocktail menu, bakery menu, wine list, menu layout, menu template, dining menu, catering menu"
allowed-tools: Bash(curl *), WebFetch
---

# Menu Design

Design beautiful restaurant and cafe menu visuals using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design a restaurant menu background for an Italian trattoria. Warm aged parchment texture, rustic olive branch illustrations framing the top and bottom borders, hand-drawn style, Tuscan warm earth tones with olive green accents, portrait orientation with generous center space for menu text."
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
        "content": "Design a restaurant menu background for an Italian trattoria. Warm aged parchment texture, rustic olive branch illustrations framing the top and bottom borders, hand-drawn style, Tuscan warm earth tones with olive green accents, portrait orientation with generous center space for menu text."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide your restaurant's branding or interior photos to match the vibe:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a menu background that matches the aesthetic of this restaurant interior. Capture the same mood and color palette, design decorative borders and background texture that complement the dining atmosphere, portrait format."
      }
    ],
    "image_urls": ["https://example.com/restaurant-interior.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Menu Styles by Cuisine

| Cuisine | Visual Style | Colors | Elements |
|---------|-------------|--------|----------|
| **Italian** | Rustic, hand-drawn | Earth tones, olive green | Olive branches, grape vines |
| **Japanese** | Minimal, elegant | Black, red, cream | Ink brush strokes, cherry blossoms |
| **Mexican** | Vibrant, folk art | Bold reds, yellows, teals | Papel picado, cacti, peppers |
| **French** | Classic, sophisticated | Navy, gold, cream | Art nouveau borders, fleur-de-lis |
| **American Diner** | Retro, nostalgic | Red, white, chrome | Checkered patterns, neon accents |
| **Indian** | Ornate, colorful | Saffron, burgundy, gold | Mandala patterns, paisley |
| **Cocktail Bar** | Moody, premium | Dark tones, copper | Art deco, geometric patterns |

## Prompt Engineering Tips

### Keywords That Work

```
menu background, decorative border, food illustration, hand-drawn elements,
textured paper, themed visual elements, ornamental frame, generous text area,
cuisine-appropriate, portrait orientation, print-ready quality
```

### Keywords to Avoid

```
menu text and prices — add actual content in design software
photorealistic food photos — illustrations work better for menus
cluttered backgrounds — menu text must be easily readable
digital/tech aesthetic — menus need a warm, inviting feel
```

### Prompt Structure

```
menu design for [cuisine/restaurant type], [background texture], [decorative elements], [color palette], [style], portrait orientation with [text area description]
```

## Examples

### Japanese Izakaya Menu

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a menu background for a Japanese izakaya. Deep charcoal textured paper, minimalist ink brush stroke border at the top, small watercolor illustrations of sake cups and chopsticks in the corners, wabi-sabi aesthetic, muted ink black and warm gray with a single red accent element, portrait orientation."
      }
    ],
    "stream": false
  }'
```

### Craft Cocktail Bar Menu

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a cocktail bar menu design. Dark navy matte background, elegant art deco gold line borders, small decorative illustrations of cocktail glasses and botanicals in gold line art at the top and bottom, Gatsby-era sophistication, portrait orientation with wide margins for drink descriptions."
      }
    ],
    "stream": false
  }'
```

### Bakery Menu

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a bakery menu background. Soft cream-white background with subtle flour dust texture, delicate hand-drawn illustrations of wheat sheaves and a rolling pin framing the top, gentle watercolor pastry sketches along the bottom border, warm and artisanal, pastel pink and gold accents, portrait orientation."
      }
    ],
    "stream": false
  }'
```

## Menu Design Principles

- **Readability first** — the background must never compete with menu text
- **Genre-appropriate** — the visual style should match the dining experience
- **Warm and inviting** — menus are held in hand, the design should feel welcoming
- **Consistent margins** — leave at least 15% border for text safe zones
- **Two sides** — consider generating both a front cover and an interior background
- **Print quality** — design at 300 DPI for physical menus

## Standard Menu Sizes

| Format | Size | Use |
|--------|------|-----|
| **Single Page** | 8.5 x 11 in / A4 | Simple menus |
| **Bi-fold** | 11 x 17 in folded | Standard restaurant |
| **Tri-fold** | 8.5 x 14 in folded | Takeout menus |
| **Table Tent** | 4 x 6 in | Specials, drinks |
| **Large Format** | 11 x 17 in | Chalkboard-style |

## Workflow

```bash
# Step 1: Generate the menu cover
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Menu cover design for a farm-to-table restaurant. Kraft paper background, beautiful watercolor illustration of a rustic farmhouse surrounded by vegetable garden rows, warm earthy palette with pops of fresh green, hand-crafted and organic feel, portrait orientation."
      }
    ],
    "stream": false
  }'

# Step 2: Generate matching interior page background
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Menu cover design for a farm-to-table restaurant. Kraft paper background, beautiful watercolor illustration of a rustic farmhouse surrounded by vegetable garden rows, warm earthy palette with pops of fresh green, hand-crafted and organic feel, portrait orientation."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now create the interior menu page background. Same kraft paper texture but much simpler: just thin watercolor vegetable illustrations running along the left margin and a subtle vine border at the top. 90% of the page should be clean for text."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Logo Design](../logo-design/SKILL.md) — Restaurant logo for menu integration
- [Business Card Design](../business-card-design/SKILL.md) — Matching restaurant cards
- [Social Media Post](../social-media-post/SKILL.md) — Share menu specials online
- [Packaging Design](../packaging-design/SKILL.md) — Takeout packaging design

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
