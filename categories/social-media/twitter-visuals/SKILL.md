---
name: twitter-visuals
description: "Create Twitter/X header images and post visuals using each::sense AI. Generate optimized graphics for Twitter/X including profile headers (1500x500), post images (1600x900), thread visuals, quote tweet graphics, and promotional banners. Supports personal brands, companies, and creator accounts. Use for: Twitter headers, X post images, tweet graphics, thread visuals, Twitter banner, profile header, Twitter card images. Triggers: twitter visual, twitter header, x header, tweet image, twitter graphic, twitter banner, x post image, twitter card, tweet graphic, x visual, twitter profile, thread visual"
allowed-tools: Bash(curl *), WebFetch
---

# Twitter/X Visuals

Create optimized Twitter/X header images and post visuals using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a Twitter/X post image for a product announcement. Clean dark background with a soft radial gradient from deep navy to black, a glowing product silhouette in the center with light rays emanating outward, premium tech reveal aesthetic, 16:9 aspect ratio."
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
        "content": "Create a Twitter/X post image for a product announcement. Clean dark background with a soft radial gradient from deep navy to black, a glowing product silhouette in the center with light rays emanating outward, premium tech reveal aesthetic, 16:9 aspect ratio."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Match your existing brand or personal visual identity:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a Twitter header image that matches this brand style. Same color palette and visual language, wide panoramic composition at 3:1 ratio, subtle and professional, abstract elements on the right side leaving the left clear for the profile picture overlap area."},
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

## Twitter/X Image Formats

| Format | Dimensions | Aspect Ratio | Notes |
|--------|-----------|-------------|-------|
| **Profile Header** | 1500 x 500 px | 3:1 | Profile photo overlaps bottom-left |
| **Post Image** | 1600 x 900 px | 16:9 | Single image tweet |
| **Two Images** | 700 x 800 px each | 7:8 | Side-by-side layout |
| **Card Image** | 1200 x 628 px | ~1.9:1 | Link preview card |
| **Thread Visual** | 1200 x 675 px | 16:9 | Consistent across thread |

## Prompt Engineering Tips

### Keywords That Work

```
Twitter post image, clean and impactful, bold visual, dark background,
high contrast, tech aesthetic, 16:9 wide format, professional and modern,
sharp focus, single focal point, minimal composition, statement visual
```

### Keywords to Avoid

```
vertical or portrait — Twitter crops to landscape
busy backgrounds — timeline is already content-dense
subtle pastel — needs to pop against white/dark mode feeds
lots of small text — unreadable in timeline preview
```

### Prompt Structure

```
Twitter/X [format] for [purpose], [subject/scene], [visual style], [color palette], [aspect ratio]
```

## Examples

### Developer Personal Brand Header

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a Twitter profile header for a software developer. Dark gradient background with subtle matrix-style code rain in muted green, a clean terminal window outline on the right side, hacker aesthetic but professional, 3:1 aspect ratio (1500x500), left third clear for profile picture area."
      }
    ],
    "stream": false
  }'
```

### Startup Launch Tweet Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a Twitter post image for a startup launch announcement. Bold gradient from coral to deep purple, a rocket made of abstract geometric shapes ascending from the bottom, particle trail behind it, energetic and celebratory, modern flat design, 16:9 wide format."
      }
    ],
    "stream": false
  }'
```

### Thread Visual Series

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a Twitter thread header image for a thread about AI trends. Abstract brain made of interconnected light nodes on a deep indigo background, clean and futuristic, subtle grid pattern in the background, thought-provoking and authoritative, 16:9 format with space on the left for text overlay."
      }
    ],
    "stream": false
  }'
```

## Twitter/X Design Considerations

- **Dark mode dominant** — most power users use dark mode, test your images against dark backgrounds
- **Profile header safe zones** — the profile photo overlaps the bottom-left, keep that area uncluttered
- **Mobile crops** — headers crop differently on mobile vs desktop, keep important elements centered
- **Timeline competition** — your image competes with dozens of tweets, bold and simple wins
- **Consistent branding** — use the same visual style across all tweet images for recognition
- **Alt text** — always include descriptive alt text for accessibility

## Workflow

```bash
# Step 1: Create the profile header
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Twitter profile header for a design agency. Smooth gradient from slate blue to warm charcoal, abstract paint splatter elements in teal and coral on the right side, editorial and creative, 3:1 aspect ratio, left third intentionally sparse."
      }
    ],
    "stream": false
  }'

# Step 2: Create a matching post template
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Twitter profile header for a design agency. Smooth gradient from slate blue to warm charcoal, abstract paint splatter elements in teal and coral on the right side, editorial and creative, 3:1 aspect ratio, left third intentionally sparse."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now create a matching post image template for regular tweets. Same color palette and paint splatter elements, but in 16:9 format, with the splatters concentrated in the corners leaving the center open for content overlay."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [LinkedIn Content](../linkedin-content/SKILL.md) — Professional social media content
- [Social Media Post](../../design/social-media-post/SKILL.md) — General social graphics
- [OG Image Design](../../design/og-image-design/SKILL.md) — Link preview images for tweets
- [Instagram Content](../instagram-content/SKILL.md) — Instagram visuals

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
