---
name: banner-ad-design
description: "Design web banner ads for display networks using each::sense AI. Generate high-converting banner ad visuals for Google Display Network, programmatic advertising, retargeting campaigns, and website placements in standard IAB sizes including leaderboard, medium rectangle, skyscraper, and half page. Use for: banner ads, display ads, web banners, Google ads, retargeting ads, programmatic creatives, ad campaign visuals. Triggers: banner ad, display ad, web banner, google display ad, ad creative, banner design, leaderboard ad, skyscraper ad, retargeting banner, programmatic ad, ad design"
allowed-tools: Bash(curl *), WebFetch
---

# Banner Ad Design

Design high-converting web banner ads for display networks using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a leaderboard banner ad visual for a SaaS product launch. Clean gradient from dark navy to royal blue, abstract dashboard wireframe fading in from the right side, modern tech aesthetic, 728x90 pixel proportions, space on the left for headline text and CTA button."
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
        "content": "Create a leaderboard banner ad visual for a SaaS product launch. Clean gradient from dark navy to royal blue, abstract dashboard wireframe fading in from the right side, modern tech aesthetic, 728x90 pixel proportions, space on the left for headline text and CTA button."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Use brand assets or previous ad creatives as style reference:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a banner ad background matching this brand style. Same color palette and visual language, medium rectangle format 300x250 proportions, leave space for product image overlay and CTA button."},
              {"type": "image_url", "image_url": {"url": "https://example.com/brand-guidelines.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Standard IAB Ad Sizes

| Name | Size | Use Case |
|------|------|----------|
| **Leaderboard** | 728 x 90 | Top of page |
| **Medium Rectangle** | 300 x 250 | Sidebar, in-content |
| **Wide Skyscraper** | 160 x 600 | Sidebar |
| **Half Page** | 300 x 600 | High-impact sidebar |
| **Large Rectangle** | 336 x 280 | In-content |
| **Billboard** | 970 x 250 | Premium top placement |
| **Mobile Leaderboard** | 320 x 50 | Mobile apps |
| **Large Mobile** | 320 x 100 | Mobile web |

## Prompt Engineering Tips

### Keywords That Work

```
banner ad visual, clean layout, bold focal point, high contrast CTA area,
brand-consistent, product spotlight, clear visual hierarchy, professional,
space for text overlay, call-to-action area, conversion-focused
```

### Keywords to Avoid

```
cluttered with text — add copy in design software
too many products — one focal point per ad
subtle and understated — ads need to stand out
small intricate details — banners are viewed at actual size
```

### Prompt Structure

```
banner ad visual for [product/service], [background/style], [focal element], [color scheme], [size proportions], space for [text/CTA placement]
```

## Examples

### E-commerce Product Ad

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a medium rectangle banner ad background for a luxury watch sale. Rich black background with subtle gold sparkle particles, dramatic spotlight in the center for product placement, premium and elegant, 300x250 proportions."
      }
    ],
    "stream": false
  }'
```

### Travel Campaign Ad

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a half page banner ad for a tropical travel deal. Stunning turquoise ocean fading into white sand beach, palm tree framing the left edge, warm golden sunlight, aspirational and inviting, 300x600 proportions with a dark overlay at the bottom for deal text."
      }
    ],
    "stream": false
  }'
```

### App Download Ad

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a mobile leaderboard banner for a fitness app. Energetic gradient from orange to magenta, abstract motion lines suggesting speed and movement, clean modern tech style, 320x100 proportions with phone mockup area on the right."
      }
    ],
    "stream": false
  }'
```

## Banner Ad Best Practices

- **One message per banner** — do not try to communicate multiple ideas
- **Clear visual hierarchy** — image, headline, CTA in that order
- **High contrast CTA area** — the call-to-action must pop against the background
- **Brand consistency** — use the same visual language across all ad sizes
- **File size matters** — keep final files under 150KB for fast loading
- **Border recommended** — a 1px border helps the ad stand out on white pages

## Workflow

```bash
# Step 1: Generate the primary ad creative (medium rectangle)
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Banner ad background for a fintech app. Deep indigo to teal gradient, abstract floating coins and upward arrows made of light particles, futuristic and trustworthy, 300x250 proportions."
      }
    ],
    "stream": false
  }'

# Step 2: Adapt to leaderboard format
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Banner ad background for a fintech app. Deep indigo to teal gradient, abstract floating coins and upward arrows made of light particles, futuristic and trustworthy, 300x250 proportions."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now adapt this same visual concept to a leaderboard format, 728x90 proportions. Stretch the gradient horizontally, place the light particle elements on the right side, leave the left half clean for text."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Social Media Post](../social-media-post/SKILL.md) — Social ad creatives
- [OG Image Design](../og-image-design/SKILL.md) — Link preview images
- [Email Header Design](../email-header-design/SKILL.md) — Email campaign visuals
- [Logo Design](../logo-design/SKILL.md) — Brand logos for ad integration

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
