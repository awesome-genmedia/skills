---
name: app-icon-design
description: "Design mobile app icons for App Store and Google Play Store using each::sense AI. Generate distinctive, recognizable app icons in various styles including flat, skeuomorphic, gradient, glyph, and illustrated. Supports iOS and Android guidelines with proper rounded corners and visual weight. Use for: app icons, mobile icons, app store graphics, play store icons, favicon design, app branding. Triggers: app icon, mobile app icon, ios icon, android icon, app store icon, play store icon, app icon design, mobile icon design, app logo, favicon"
allowed-tools: Bash(curl *), WebFetch
---

# App Icon Design

Design distinctive mobile app icons for App Store and Google Play using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Design a mobile app icon for a meditation app. A simple lotus flower symbol in white on a smooth gradient background from deep purple to soft lavender, flat modern style, centered composition, clean and calming, square format with rounded corners."
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
        "content": "Design a mobile app icon for a meditation app. A simple lotus flower symbol in white on a smooth gradient background from deep purple to soft lavender, flat modern style, centered composition, clean and calming, square format with rounded corners."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Use an existing logo or brand asset to create a matching app icon:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Convert this logo into a mobile app icon format. Simplify the design to work at small sizes, place it centered on a solid background color that matches the brand, square format with rounded corners, recognizable at 60x60 pixels."},
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

## Icon Styles

| Style | Description | Popular With |
|-------|-------------|-------------|
| **Flat** | Solid colors, no shadows | Utility apps, productivity |
| **Gradient** | Smooth color transitions | Social apps, modern tools |
| **Glyph** | Single symbol on solid background | System tools, settings |
| **Illustrated** | Detailed illustration | Games, kids apps |
| **Skeuomorphic** | 3D, realistic textures | Premium apps, simulators |
| **Duotone** | Two-color design | Minimalist brands |

## Prompt Engineering Tips

### Keywords That Work

```
app icon, centered symbol, simple recognizable shape, bold single glyph,
smooth gradient background, flat vector style, rounded square format,
clean at small sizes, high contrast, distinctive silhouette
```

### Keywords to Avoid

```
text or letters — unreadable at small sizes on most AI models
thin line art — disappears at icon sizes
multiple objects — icons need one focal element
photorealistic — too complex for small formats
```

### Prompt Structure

```
app icon for [app type], [symbol/glyph description], [background style], [color palette], [visual style], square format with rounded corners
```

## Examples

### Fitness Tracker App

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design an app icon for a fitness tracker. A bold running shoe silhouette with motion lines, vibrant gradient from electric orange to hot pink, flat modern design, centered on the icon, square with rounded corners."
      }
    ],
    "stream": false
  }'
```

### Finance App

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create an app icon for a personal finance app. An upward trending chart arrow forming a shield shape, deep green gradient background, white symbol, professional and trustworthy, clean flat design, square with rounded corners."
      }
    ],
    "stream": false
  }'
```

### Music Streaming App

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design an app icon for a music streaming app. Stylized sound wave forming a circular pattern, gradient from deep violet to electric cyan, glowing neon effect, dark background, modern and energetic, square with rounded corners."
      }
    ],
    "stream": false
  }'
```

## App Store Requirements

| Platform | Size | Shape |
|----------|------|-------|
| **iOS App Store** | 1024 x 1024 px | Square (system applies corner mask) |
| **Google Play Store** | 512 x 512 px | Square (system applies corner radius) |
| **iOS Home Screen** | 180 x 180 px (3x) | Superellipse corners |
| **Android Home Screen** | 192 x 192 px (xxxhdpi) | Adaptive icon |
| **Favicon** | 32 x 32 px / 16 x 16 px | Square |

## Icon Design Checklist

- Recognizable at 29x29px (smallest iOS display size)
- Works on both light and dark wallpapers
- Single focal element, not multiple objects
- No transparency (iOS requires opaque backgrounds)
- Distinct silhouette when viewed in monochrome
- Stands out among competitor icons in store search results

## Workflow

```bash
# Step 1: Generate the icon concept
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "App icon for a recipe sharing app. A chef hat with a heart cutout in the center, warm gradient from peach to coral, friendly and inviting, flat vector style, square with rounded corners."
      }
    ],
    "stream": false
  }'

# Step 2: Explore variations
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "App icon for a recipe sharing app. A chef hat with a heart cutout in the center, warm gradient from peach to coral, friendly and inviting, flat vector style, square with rounded corners."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Try a different concept: instead of the chef hat, use a steaming cooking pot with the steam forming a heart shape. Same coral gradient background, same flat style."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Logo Design](../logo-design/SKILL.md) — Brand logos to adapt for app icons
- [OG Image Design](../og-image-design/SKILL.md) — Link preview images for app landing pages
- [Social Media Post](../social-media-post/SKILL.md) — App launch promotional graphics
- [Banner Ad Design](../banner-ad-design/SKILL.md) — App install ad creatives

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
