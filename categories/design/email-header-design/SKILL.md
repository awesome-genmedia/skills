---
name: email-header-design
description: "Design email marketing headers and banners using each::sense AI. Generate professional email header graphics for newsletters, promotional campaigns, welcome sequences, product announcements, and seasonal marketing emails. Optimized for email client rendering at 600px width. Use for: email headers, newsletter banners, email campaign graphics, promotional email images, welcome email art, email marketing visuals. Triggers: email header, email banner, newsletter header, email graphic, email marketing image, newsletter banner, promotional email, campaign header, email design, newsletter design, email hero image"
allowed-tools: Bash(curl *), WebFetch
---

# Email Header Design

Design professional email marketing headers and banners using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design an email header for a weekly tech newsletter. Clean gradient from midnight blue to dark teal, abstract circuit board lines fading in from the edges, modern and professional, 600x200 proportions, centered area for newsletter title."
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
        "content": "Design an email header for a weekly tech newsletter. Clean gradient from midnight blue to dark teal, abstract circuit board lines fading in from the edges, modern and professional, 600x200 proportions, centered area for newsletter title."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Match your brand guidelines or existing email templates:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create an email header that matches this brand style. Same color palette and aesthetic, 600x200 proportions, suitable for a product update newsletter, clean with logo placement area on the left."},
              {"type": "image_url", "image_url": {"url": "https://example.com/brand-reference.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Email Header Types

| Type | Dimensions | Purpose |
|------|-----------|---------|
| **Standard Header** | 600 x 200 px | Newsletter masthead |
| **Hero Banner** | 600 x 300 px | Promotional campaigns |
| **Full Width Hero** | 600 x 400 px | Product launches |
| **Minimal Strip** | 600 x 100 px | Transactional emails |
| **Section Divider** | 600 x 50 px | Content separation |

## Prompt Engineering Tips

### Keywords That Work

```
email header, newsletter banner, clean and professional, brand-consistent,
horizontal banner format, email-safe colors, bold yet simple,
centered composition, 600px width proportions, text overlay area
```

### Keywords to Avoid

```
animation or motion — static images only in most email clients
transparent background — not all clients support PNG transparency
ultra-fine details — images are often compressed for email delivery
neon glow effects — can look different across email clients
```

### Prompt Structure

```
email header for [email type], [visual elements], [background], [color palette], [dimensions] proportions, [text area placement]
```

## Examples

### Product Launch Email

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a hero banner for a product launch email. Smooth gradient from charcoal to warm copper, a sleek product silhouette spotlight area in the center, light rays emanating upward, premium and exciting, 600x300 proportions."
      }
    ],
    "stream": false
  }'
```

### Seasonal Holiday Email

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a holiday season email header. Rich dark green background with scattered golden snowflakes and bokeh light effects, festive and elegant without being kitschy, sophisticated brand aesthetic, 600x200 proportions."
      }
    ],
    "stream": false
  }'
```

### Welcome Series Email

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a welcome email header for a SaaS onboarding sequence. Bright and optimistic gradient from sky blue to white, abstract confetti-like geometric shapes floating upward, friendly and inviting, 600x250 proportions with centered greeting area."
      }
    ],
    "stream": false
  }'
```

## Email Design Constraints

- **600px max width** is the safe standard for email clients
- **Total email size under 100KB** of images for fast loading
- **JPEG for photos**, PNG for graphics with solid colors
- **Always include alt text** — many clients block images by default
- **Dark mode support** — test how your header looks inverted
- **Retina displays** — generate at 2x (1200px wide) and display at 600px

## Workflow

```bash
# Step 1: Generate the main header design
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Email header for a fitness brand newsletter. Energetic gradient from deep orange to magenta, abstract silhouette of a runner in motion on the right, dynamic and motivating, 600x200 proportions."
      }
    ],
    "stream": false
  }'

# Step 2: Create a matching promotional banner
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Email header for a fitness brand newsletter. Energetic gradient from deep orange to magenta, abstract silhouette of a runner in motion on the right, dynamic and motivating, 600x200 proportions."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now create a matching promotional banner for a mid-email section. Same color palette but as a 600x150 strip, with the gradient reversed and a more subtle version of the motion elements. This will be used as a sale announcement divider."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Banner Ad Design](../banner-ad-design/SKILL.md) — Display advertising banners
- [Social Media Post](../social-media-post/SKILL.md) — Matching social media graphics
- [OG Image Design](../og-image-design/SKILL.md) — Link preview for email landing pages
- [Logo Design](../logo-design/SKILL.md) — Brand logos for email headers

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
