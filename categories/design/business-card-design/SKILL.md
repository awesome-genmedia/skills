---
name: business-card-design
description: "Design professional business cards using each::sense AI. Generate modern, creative, and industry-appropriate business card layouts with custom backgrounds, patterns, and visual elements for professionals, startups, freelancers, and corporate teams. Use for: business card design, professional cards, corporate identity, contact cards, visiting cards, name cards. Triggers: business card, visiting card, name card, professional card, corporate card, card design, contact card, business card layout, freelancer card, executive card"
allowed-tools: Bash(curl *), WebFetch
---

# Business Card Design

Design professional and creative business cards using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design a modern business card layout for a tech startup. Clean white background, subtle circuit board pattern in light gray on the left edge, accent stripe of electric blue along the bottom, minimal and professional, landscape orientation 3.5x2 inches."
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
        "content": "Design a modern business card layout for a tech startup. Clean white background, subtle circuit board pattern in light gray on the left edge, accent stripe of electric blue along the bottom, minimal and professional, landscape orientation 3.5x2 inches."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide your logo or brand assets to integrate into the card design:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Design a business card background that complements this logo. Use the same color palette, create a subtle pattern for the card back, keep the front clean with the logo placement area in the upper left, landscape format."},
              {"type": "image_url", "image_url": {"url": "https://example.com/company-logo.png"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Card Styles

| Style | Description | Best For |
|-------|-------------|----------|
| **Minimalist** | Clean, lots of white space | Corporate, tech, consulting |
| **Bold Color** | Strong background color, white text area | Creative agencies, startups |
| **Textured** | Subtle patterns or material textures | Architecture, design, craft |
| **Luxury** | Dark background, gold/silver accents | Finance, law, executive |
| **Creative** | Unique layouts, artistic elements | Photographers, artists, designers |
| **Vintage** | Letterpress feel, classic typography | Artisanal brands, boutiques |

## Prompt Engineering Tips

### Keywords That Work

```
business card design, clean professional layout, minimal and elegant,
subtle pattern, accent color stripe, generous white space, landscape format,
logo placement area, contact info area, print-ready, premium finish
```

### Keywords to Avoid

```
text and phone numbers — add contact details in design software
too many colors — 2-3 max for professional appearance
busy backgrounds — legibility is critical on small cards
portrait orientation — landscape is standard unless deliberately vertical
```

### Prompt Structure

```
business card [style] for [industry/profession], [background], [design elements], [color palette], [finish/texture], landscape 3.5x2 inches
```

## Examples

### Luxury Financial Advisor Card

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a luxury business card for a financial advisor. Matte black background with a thin gold foil line running diagonally across the card, subtle embossed geometric pattern, premium and authoritative feel, landscape format."
      }
    ],
    "stream": false
  }'
```

### Creative Photographer Card

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a photographer business card design. Full bleed dramatic landscape photo on the back side, front side is clean white with a thin black border and a small camera aperture icon, modern editorial style, landscape format."
      }
    ],
    "stream": false
  }'
```

### Eco-Friendly Brand Card

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a business card for an organic skincare brand. Kraft paper texture background, delicate botanical line illustrations of lavender and eucalyptus along the edges, sage green accents, natural and clean aesthetic, landscape format."
      }
    ],
    "stream": false
  }'
```

## Print Specifications

| Spec | Standard | Notes |
|------|----------|-------|
| **Size** | 3.5 x 2 inches (US) / 85 x 55mm (EU) | Include 3mm bleed |
| **Resolution** | 300 DPI minimum | For sharp printing |
| **Color Mode** | CMYK | Convert from RGB for print |
| **Safe Zone** | 3mm from each edge | Keep important elements inside |
| **File Format** | PDF or high-res PNG | Vector preferred for final |

## Workflow

```bash
# Step 1: Generate the front design concept
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Business card front design for an architecture firm. Clean white background, thin charcoal gray lines forming an abstract building wireframe in the bottom right corner, minimalist and sophisticated, landscape format."
      }
    ],
    "stream": false
  }'

# Step 2: Generate the matching back design
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Business card front design for an architecture firm. Clean white background, thin charcoal gray lines forming an abstract building wireframe in the bottom right corner, minimalist and sophisticated, landscape format."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now create the back of this card. Full coverage of the same wireframe pattern in charcoal gray, filling the entire card, creating a striking contrast to the clean front. Same style and line weight."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Logo Design](../logo-design/SKILL.md) — Create a logo for your card
- [Social Media Post](../social-media-post/SKILL.md) — Matching branded social graphics
- [Email Header Design](../email-header-design/SKILL.md) — Consistent email branding
- [Packaging Design](../packaging-design/SKILL.md) — Extended brand identity

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
