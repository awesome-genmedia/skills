---
name: tiktok-content
description: "Create TikTok video content and cover images using each::sense AI. Generate eye-catching TikTok cover thumbnails, video intro frames, text background templates, transition visuals, and branded TikTok content optimized for the For You Page algorithm. Vertical 9:16 format for maximum impact. Use for: TikTok covers, video thumbnails, TikTok graphics, video intro frames, branded TikTok content, short-form video visuals. Triggers: tiktok content, tiktok cover, tiktok thumbnail, tiktok graphic, tiktok video, tiktok design, tiktok visual, short form video, tiktok template, tiktok background, fyp content"
allowed-tools: Bash(curl *), WebFetch
---

# TikTok Content

Create eye-catching TikTok cover images and video content visuals using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a TikTok video cover image for a cooking tutorial. Close-up of a sizzling pan with colorful stir-fry vegetables mid-toss, steam and oil droplets frozen in the air, dramatic kitchen lighting, vibrant and appetizing, vertical 9:16 format."
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
        "content": "Create a TikTok video cover image for a cooking tutorial. Close-up of a sizzling pan with colorful stir-fry vegetables mid-toss, steam and oil droplets frozen in the air, dramatic kitchen lighting, vibrant and appetizing, vertical 9:16 format."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Match your existing TikTok brand aesthetic:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a TikTok cover image in the same style as this reference. Match the bold color treatment and composition, but change the subject to a DIY craft project — hands holding a freshly painted ceramic mug, same energetic vibe, 9:16 vertical."
      }
    ],
    "image_urls": ["https://example.com/tiktok-style-ref.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## TikTok Visual Formats

| Format | Dimensions | Purpose |
|--------|-----------|---------|
| **Video Cover** | 1080 x 1920 px | Profile grid thumbnail |
| **Video Frame** | 1080 x 1920 px | Intro/outro screens |
| **Text Background** | 1080 x 1920 px | Behind on-screen text |
| **Green Screen** | 1080 x 1920 px | Background for green screen effect |
| **Product Showcase** | 1080 x 1920 px | Product-focused content |

## Prompt Engineering Tips

### Keywords That Work

```
TikTok cover, vertical format 9:16, bold and eye-catching, saturated colors,
dynamic composition, trending aesthetic, Gen-Z visual style, high energy,
close-up dramatic angle, vibrant and punchy, scroll-stopping
```

### Keywords to Avoid

```
corporate professional — TikTok rewards casual and authentic
subtle and muted — content gets lost in fast-scrolling feeds
landscape orientation — TikTok is strictly vertical
overly polished — raw and real performs better
```

### Prompt Structure

```
TikTok [content type] for [niche], [subject/scene], [visual style], [color treatment], [energy/mood], vertical 9:16 format
```

## Examples

### Beauty Tutorial Cover

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a TikTok cover for a makeup tutorial. Close-up of colorful eyeshadow palette with a brush sweeping through shimmer pigment, glitter particles floating in the air, punchy pink and gold tones, ring light reflections, glamorous and fun, 9:16 vertical."
      }
    ],
    "stream": false
  }'
```

### Fitness Content Cover

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a TikTok cover image for a workout video. Dynamic shot of a kettlebell mid-swing with chalk dust exploding around it, dark gym background with dramatic side lighting, intense red and orange accent lighting, powerful and motivating, 9:16 vertical format."
      }
    ],
    "stream": false
  }'
```

### Life Hack Video Cover

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a TikTok cover for a home organization hack video. Satisfying top-down view of a perfectly organized drawer with color-coded compartments, everything aligned symmetrically, bright clean lighting, oddly satisfying aesthetic, pastel rainbow organization, 9:16 vertical."
      }
    ],
    "stream": false
  }'
```

## TikTok Content Strategy

- **First frame matters** — the cover image determines whether people tap on your profile videos
- **Bold colors outperform** — saturated, high-contrast visuals stop the scroll
- **Face-forward content** gets 2-3x more views than faceless content
- **Trending aesthetics rotate** — match current visual trends (currently: high saturation, dramatic lighting)
- **Consistent cover style** across your profile creates a polished grid appearance
- **Text space** — leave the bottom 20% clear for TikTok's username/description overlay

## Safe Zones

TikTok's UI overlays take up significant screen space:

- **Top 15%** — status bar and back button
- **Bottom 20%** — username, caption, and music info
- **Right edge 10%** — like, comment, share, and bookmark buttons
- **Safe zone** — the center 60% of the frame

## Workflow

```bash
# Step 1: Generate the video cover concept
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "TikTok cover for a travel vlog. Breathtaking aerial view of turquoise water meeting white sand beach, tiny umbrella and lounger visible, vivid saturated colors, wanderlust-inducing, 9:16 vertical."
      }
    ],
    "stream": false
  }'

# Step 2: Create a matching text background for a follow-up post
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "TikTok cover for a travel vlog. Breathtaking aerial view of turquoise water meeting white sand beach, tiny umbrella and lounger visible, vivid saturated colors, wanderlust-inducing, 9:16 vertical."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now create a TikTok text background for a travel tips list. Same turquoise and white color palette but blurred and softened to 30% opacity, so white text will be easily readable over it, 9:16 vertical."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Instagram Content](../instagram-content/SKILL.md) — Instagram posts and stories
- [YouTube Content](../youtube-content/SKILL.md) — YouTube Shorts and thumbnails
- [Pinterest Pins](../pinterest-pins/SKILL.md) — Vertical visual content
- [Social Media Post](../../design/social-media-post/SKILL.md) — General social graphics

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
