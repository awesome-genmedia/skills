---
name: instagram-content
description: "Create Instagram posts, stories, reels covers, and carousel slides using each::sense AI. Generate platform-optimized visuals for Instagram feed posts (1080x1080), stories (1080x1920), reels cover images, highlight covers, and multi-slide carousel content with consistent branding. Use for: Instagram posts, stories, reels covers, carousel slides, highlight covers, Instagram ads, IG content. Triggers: instagram post, instagram story, instagram reel, ig content, instagram graphic, instagram carousel, instagram highlight, instagram design, ig post, ig story, reels cover, instagram feed"
allowed-tools: Bash(curl *), WebFetch
---

# Instagram Content

Create platform-optimized Instagram posts, stories, reels covers, and carousel slides using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create an Instagram feed post for a wellness brand. Soft morning light scene with a ceramic mug of matcha on a linen tablecloth, fresh eucalyptus sprig beside it, overhead flat lay perspective, warm neutral tones with sage green accents, calming and aspirational, square 1:1 format."
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
        "content": "Create an Instagram feed post for a wellness brand. Soft morning light scene with a ceramic mug of matcha on a linen tablecloth, fresh eucalyptus sprig beside it, overhead flat lay perspective, warm neutral tones with sage green accents, calming and aspirational, square 1:1 format."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Maintain visual consistency with your existing Instagram grid:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a new Instagram post in the same visual style as this reference. Match the color grading, lighting, and composition style but feature a different product — a scented candle instead. Keep the same flat lay perspective and neutral background."
      }
    ],
    "image_urls": ["https://example.com/instagram-reference.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Instagram Formats

| Format | Dimensions | Aspect Ratio | Use Case |
|--------|-----------|-------------|----------|
| **Feed Post** | 1080 x 1080 px | 1:1 | Standard grid post |
| **Portrait Post** | 1080 x 1350 px | 4:5 | Takes up more feed space |
| **Story** | 1080 x 1920 px | 9:16 | Stories, reels covers |
| **Carousel Slide** | 1080 x 1080 px | 1:1 | Multi-image swipe |
| **Highlight Cover** | 1080 x 1080 px | 1:1 (circle crop) | Story highlights |
| **Reels Cover** | 1080 x 1920 px | 9:16 | Reel thumbnail |

## Prompt Engineering Tips

### Keywords That Work

```
Instagram aesthetic, curated feed, warm tones, editorial photography style,
flat lay composition, lifestyle photography, branded content, cohesive grid,
natural lighting, aspirational mood, clean minimalist, square format
```

### Keywords to Avoid

```
cluttered composition — Instagram rewards clean visuals
cold corporate look — feels out of place on Instagram
stock photo feel — followers want authentic aesthetics
heavy text overlays — Instagram prioritizes visual content
```

### Prompt Structure

```
Instagram [format] for [brand/niche], [scene/subject], [photography style], [color palette], [mood], [aspect ratio]
```

## Examples

### Fashion Brand Feed Post

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create an Instagram feed post for a streetwear brand. Urban rooftop setting at golden hour, a pair of vintage sneakers placed on a concrete ledge with a city skyline blurred in the background, warm amber light, gritty editorial style, 1:1 square format."
      }
    ],
    "stream": false
  }'
```

### Story Background for Announcement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design an Instagram story background for a product drop announcement. Bold gradient from electric violet to deep magenta, abstract geometric shapes bursting from the center, dynamic and energetic, space in the middle for product image and text stickers, 9:16 vertical format."
      }
    ],
    "stream": false
  }'
```

### Carousel Educational Post

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a carousel slide background for an educational Instagram post about skincare routine steps. Soft blush pink background with a gentle watercolor wash effect, delicate floral elements in the bottom corners, clean and feminine, generous space for text overlay, 1:1 square format."
      }
    ],
    "stream": false
  }'
```

### Highlight Cover Icons

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design an Instagram highlight cover icon for a travel category. Simple line art airplane icon in white on a dusty rose circle background, minimal and elegant, works when cropped to a circle, 1:1 square format."
      }
    ],
    "stream": false
  }'
```

## Instagram Grid Strategy

- **Color cohesion** — maintain the same 3-4 colors across your grid for visual harmony
- **Alternating patterns** — rotate between close-ups, wide shots, and graphic posts
- **Portrait posts (4:5)** take up more feed real estate and get better engagement
- **Carousel posts** have the highest engagement rate — design 5-10 cohesive slides
- **Consistent editing style** — same warmth, contrast, and saturation across all posts

## Batch Content Generation

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

content_plan = [
    "Flat lay of artisan sourdough bread on a marble surface, morning light",
    "Close-up of hands kneading dough, flour dust in warm backlight",
    "Overhead shot of a rustic wooden table with fresh pastries and coffee"
]

for i, scene in enumerate(content_plan, 1):
    response = client.chat.completions.create(
        model="eachsense/beta",
        messages=[{
            "role": "user",
            "content": f"Instagram feed post for a bakery brand. {scene}, warm golden tones with cream and brown palette, artisanal editorial photography style, 1:1 square format."
        }]
    )
    print(f"Post {i}: {response.choices[0].message.content}")
```

## Workflow

```bash
# Step 1: Create the hero post
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Instagram feed post for a plant shop. A lush monstera plant in a terracotta pot on a wooden shelf, dappled sunlight through a window, warm earthy bohemian interior, lifestyle photography style, 1:1 square."
      }
    ],
    "stream": false
  }'

# Step 2: Create a matching story
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Instagram feed post for a plant shop. A lush monstera plant in a terracotta pot on a wooden shelf, dappled sunlight through a window, warm earthy bohemian interior, lifestyle photography style, 1:1 square."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now create a matching Instagram story version in 9:16 vertical format. Same plant and setting but framed vertically, more of the shelf and surrounding decor visible, same warm lighting and color palette."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Social Media Post](../../design/social-media-post/SKILL.md) — General social media graphics
- [TikTok Content](../tiktok-content/SKILL.md) — Short-form video content
- [Pinterest Pins](../pinterest-pins/SKILL.md) — Vertical pin images
- [YouTube Content](../youtube-content/SKILL.md) — YouTube channel visuals

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
