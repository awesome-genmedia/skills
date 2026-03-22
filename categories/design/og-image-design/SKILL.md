---
name: og-image-design
description: "Design Open Graph images for link previews using each::sense AI. Generate compelling OG images that drive clicks when shared on Twitter, Facebook, LinkedIn, Slack, Discord, and iMessage. Optimized for 1200x630 dimensions with bold visuals and clear text areas for titles. Use for: OG images, link previews, social share images, meta images, Twitter cards, Facebook share images. Triggers: og image, open graph image, link preview, social share image, meta image, twitter card image, facebook share, og design, preview image, share graphic, link card"
allowed-tools: Bash(curl *), WebFetch
---

# OG Image Design

Design compelling Open Graph images for link previews using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create an OG image for a blog post about machine learning. Dark gradient background from deep navy to dark teal, a stylized neural network visualization glowing in the center, clean and techy, 1200x630 proportions with a large dark area on the left side for article title text overlay."
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
        "content": "Create an OG image for a blog post about machine learning. Dark gradient background from deep navy to dark teal, a stylized neural network visualization glowing in the center, clean and techy, 1200x630 proportions with a large dark area on the left side for article title text overlay."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Use brand assets to create consistent OG images:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create an OG image background that matches this brand style. Same color palette and visual language, 1200x630 proportions, leave generous space for a large title on the left and a small logo area in the bottom right corner."},
              {"type": "image_url", "image_url": {"url": "https://example.com/brand-style.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Where OG Images Appear

| Platform | Display | Notes |
|----------|---------|-------|
| **Twitter/X** | Summary large image card | Crops to 2:1 on feed |
| **Facebook** | Link preview | Full 1200x630 display |
| **LinkedIn** | Article/link share | Prominent in feed |
| **Slack** | URL unfurl | Inline preview |
| **Discord** | Embed card | Sidebar preview |
| **iMessage** | Link preview bubble | Compact view |

## Prompt Engineering Tips

### Keywords That Work

```
OG image, link preview graphic, 1200x630 proportions, bold visual,
high contrast, clear focal point, dark background with text area,
branded and professional, eye-catching at small sizes, social share image
```

### Keywords to Avoid

```
detailed small elements — OG images are often viewed at 300px wide
centered text — different platforms crop differently
important content at edges — safe zone is the inner 80%
light gray backgrounds — low contrast on white platform UIs
```

### Prompt Structure

```
OG image for [content type], [visual elements], [background], [color palette], 1200x630 proportions, [text area placement]
```

## Examples

### Developer Blog Post

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design an OG image for a developer blog about API design. Dark charcoal background, stylized code brackets and curly braces floating in teal and green, subtle grid pattern, developer tool aesthetic, 1200x630, left half reserved for title text."
      }
    ],
    "stream": false
  }'
```

### Product Launch Page

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create an OG image for a SaaS product launch. Gradient from deep indigo to violet, abstract dashboard mockup fading in from the right edge, glowing accent highlights, premium tech feel, 1200x630, center-left area clear for product name."
      }
    ],
    "stream": false
  }'
```

### Podcast Episode Share

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design an OG image for a podcast episode share. Warm dark background with a vintage microphone illustration on the right side, abstract sound waves radiating outward in gold and amber tones, cozy and professional podcast aesthetic, 1200x630, left side for episode title."
      }
    ],
    "stream": false
  }'
```

## OG Image Best Practices

- **1200 x 630 pixels** is the universal recommended size
- **Keep critical content in the center 80%** — platforms crop edges differently
- **Dark backgrounds** with light text areas perform best on most platforms
- **Bold and simple** — the image is often displayed at thumbnail size
- **Consistent template** — use the same layout across all pages for brand recognition
- **Test across platforms** — check how your image looks on Twitter, Facebook, and Slack

## Automated OG Image Pipeline

For blogs and content sites, batch-generate OG images:

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

topics = [
    "API authentication best practices",
    "Database scaling strategies",
    "CI/CD pipeline optimization"
]

for topic in topics:
    response = client.chat.completions.create(
        model="eachsense/beta",
        messages=[{
            "role": "user",
            "content": f"Create an OG image background for a technical blog post about {topic}. Dark navy gradient, subtle tech-themed visual element on the right, clean left side for title overlay, professional developer aesthetic, 1200x630 proportions."
        }]
    )
    print(f"OG image for '{topic}': {response.choices[0].message.content}")
```

## Workflow

```bash
# Step 1: Create the base OG template
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "OG image template background for a design blog. Soft gradient from slate gray to warm charcoal, abstract paint brush strokes in muted teal and coral on the right side, editorial and artistic, 1200x630."
      }
    ],
    "stream": false
  }'

# Step 2: Create a variation for a specific post
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "OG image template background for a design blog. Soft gradient from slate gray to warm charcoal, abstract paint brush strokes in muted teal and coral on the right side, editorial and artistic, 1200x630."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Create a variation where the brush strokes form the shape of a color palette. Same background and style but with this specific subject matter for an article about color theory."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Social Media Post](../social-media-post/SKILL.md) — Full social media graphics
- [YouTube Thumbnail](../youtube-thumbnail/SKILL.md) — Video preview images
- [Banner Ad Design](../banner-ad-design/SKILL.md) — Display ad visuals
- [Email Header Design](../email-header-design/SKILL.md) — Email campaign headers

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
