---
name: social-media-post
description: "Create branded social media graphics using each::sense AI. Generate scroll-stopping visuals for Instagram, Facebook, Twitter, LinkedIn, and TikTok with proper dimensions and platform-optimized layouts. Supports quotes, announcements, promotions, event graphics, and branded content templates. Use for: social media graphics, branded posts, promotional images, announcement cards, quote graphics, carousel slides. Triggers: social media post, social graphic, instagram post, facebook post, branded content, social media design, post design, promotional graphic, quote card, announcement image, social template"
allowed-tools: Bash(curl *), WebFetch
---

# Social Media Post Design

Create branded social media graphics for any platform using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a square social media post graphic for a summer sale promotion. Vibrant gradient background in coral and gold, bold geometric shapes, clean modern layout with space for overlay text, fashion brand aesthetic."
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
        "content": "Create a square social media post graphic for a summer sale promotion. Vibrant gradient background in coral and gold, bold geometric shapes, clean modern layout with space for overlay text, fashion brand aesthetic."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Use a brand reference or mood board to maintain visual consistency:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a social media post in the same visual style as this brand reference. Announce a new product launch, keep the color palette and layout consistent, modern and clean."
      }
    ],
    "image_urls": ["https://example.com/brand-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Platform Dimensions Guide

| Platform | Format | Recommended Size |
|----------|--------|-----------------|
| **Instagram** | Feed Post | 1080 x 1080 px |
| **Instagram** | Story | 1080 x 1920 px |
| **Facebook** | Post | 1200 x 630 px |
| **Twitter/X** | Post | 1600 x 900 px |
| **LinkedIn** | Post | 1200 x 627 px |
| **Pinterest** | Pin | 1000 x 1500 px |

## Prompt Engineering Tips

### Keywords That Work

```
social media post, branded graphic, clean layout, bold typography space,
modern minimalist, vibrant colors, scroll-stopping, eye-catching design,
negative space for text overlay, square format, professional layout
```

### Keywords to Avoid

```
blurry background — reduces visual impact
too many elements — cluttered feeds perform poorly
small text — unreadable on mobile devices
generic stock photo look — low engagement
```

### Prompt Structure

```
[platform] social media post for [purpose/event], [visual style], [color palette], [layout notes], [brand aesthetic]
```

## Examples

### Product Launch Announcement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a sleek product launch social media graphic. Dark navy background with gold accent lines, centered product spotlight area, minimalist luxury aesthetic, square format for Instagram feed."
      }
    ],
    "stream": false
  }'
```

### Motivational Quote Card

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a motivational quote background graphic. Soft watercolor wash in blush pink and lavender, dreamy abstract texture, large open center area for text overlay, calming and inspirational mood."
      }
    ],
    "stream": false
  }'
```

### Event Promotion

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a music festival social media post. Electric neon colors on black background, abstract sound wave patterns, energetic and dynamic composition, futuristic vibe, square format."
      }
    ],
    "stream": false
  }'
```

### Seasonal Campaign

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a cozy autumn social media graphic for a coffee shop promotion. Warm amber and burnt orange tones, falling leaves, rustic texture, inviting atmosphere, space for promotional text overlay."
      }
    ],
    "stream": false
  }'
```

## Content Strategy Tips

- **Consistency beats perfection** — use the same color palette and style across posts
- **Leave text space** — always reserve 30-40% of the image for text overlay
- **Mobile first** — design for small screens, keep elements large and clear
- **Brand colors** — mention specific hex codes or color names in your prompts for consistency
- **Batch creation** — generate multiple variations in one session for A/B testing

## Workflow

```bash
# Step 1: Generate the base graphic
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a bold social media post background. Deep purple gradient to electric blue, abstract geometric shapes, modern tech aesthetic, square format."
      }
    ],
    "stream": false
  }'

# Step 2: Iterate on the concept
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a bold social media post background. Deep purple gradient to electric blue, abstract geometric shapes, modern tech aesthetic, square format."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Make the geometric shapes more angular and add a subtle grid pattern. Keep the same color scheme but increase contrast."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Instagram Content](../../social-media/instagram-content/SKILL.md) — Instagram-specific content creation
- [LinkedIn Content](../../social-media/linkedin-content/SKILL.md) — Professional LinkedIn graphics
- [Twitter Visuals](../../social-media/twitter-visuals/SKILL.md) — Twitter/X optimized graphics
- [OG Image Design](../og-image-design/SKILL.md) — Link preview images
- [Banner Ad Design](../banner-ad-design/SKILL.md) — Display ad creatives

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
