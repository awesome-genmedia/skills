---
name: youtube-content
description: "Create YouTube channel art, end screens, and thumbnails using each::sense AI. Generate comprehensive YouTube visual assets including channel banners (2560x1440), video thumbnails (1280x720), end screen templates, community post images, YouTube Shorts covers, and branded intro/outro frames. Use for: YouTube channel art, banners, thumbnails, end screens, community posts, Shorts covers, channel branding. Triggers: youtube content, youtube channel art, youtube banner, youtube end screen, youtube shorts, youtube community post, channel art, youtube branding, youtube graphic, yt banner, yt channel art, youtube intro"
allowed-tools: Bash(curl *), WebFetch
---

# YouTube Content

Create comprehensive YouTube channel visual assets using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a YouTube channel banner for a gaming channel. Epic fantasy landscape with floating islands and dragons silhouetted against a sunset sky, bold and colorful, dramatic lighting with volumetric god rays, the scene wraps across a wide panoramic format, 2560x1440 with the important elements concentrated in the center 1546x423 safe area."
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
        "content": "Create a YouTube channel banner for a gaming channel. Epic fantasy landscape with floating islands and dragons silhouetted against a sunset sky, bold and colorful, dramatic lighting with volumetric god rays, the scene wraps across a wide panoramic format, 2560x1440 with the important elements concentrated in the center 1546x423 safe area."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Use existing channel assets to create matching content:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Create a YouTube end screen template that matches this channel banner style. Same color palette and visual elements, two circular video placeholder areas on the right side, subscribe button area below, clean and branded, 16:9 format."},
              {"type": "image_url", "image_url": {"url": "https://example.com/channel-banner.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## YouTube Visual Assets

| Asset | Dimensions | Safe Zone | Purpose |
|-------|-----------|-----------|---------|
| **Channel Banner** | 2560 x 1440 px | Center 1546 x 423 px | Channel header (all devices) |
| **Video Thumbnail** | 1280 x 720 px | Full area | Video click-through |
| **End Screen** | 1920 x 1080 px | Right side elements | Video/subscribe prompts |
| **Community Post** | 1200 x 675 px | Full area | Community tab images |
| **Shorts Cover** | 1080 x 1920 px | Center 60% | Shorts thumbnail |
| **Video Watermark** | 150 x 150 px | Full area | Subscribe branding |

## Prompt Engineering Tips

### Keywords That Work

```
YouTube channel art, bold and vibrant, wide panoramic, branded visual,
dynamic composition, eye-catching, high energy, channel identity,
consistent branding, dramatic lighting, professional YouTuber aesthetic
```

### Keywords to Avoid

```
important elements at edges — banners crop heavily on mobile
small text or details — banner displays at various sizes
dark and subtle — YouTube's white UI needs contrast
single narrow focal point — banners are extremely wide
```

### Prompt Structure

```
YouTube [asset type] for [channel niche], [visual scene/elements], [style], [color palette], [dimensions/safe zone notes]
```

## Examples

### Tech Review Channel Banner

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a YouTube channel banner for a tech review channel. Sleek dark gradient from gunmetal to black, floating holographic tech devices (phone, laptop, headphones) arranged across the panoramic width, neon blue and cyan accent lighting, futuristic and premium, 2560x1440 with key elements in the center safe zone."
      }
    ],
    "stream": false
  }'
```

### End Screen Template

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a YouTube end screen background. Animated-looking gradient from deep purple to dark blue, two rounded rectangle placeholders on the right for recommended video cards, a circular subscribe button area below them, subtle particle effects in the background, branded and polished, 1920x1080."
      }
    ],
    "stream": false
  }'
```

### YouTube Shorts Cover

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a YouTube Shorts cover image for a quick cooking tip. Top-down view of a colorful smoothie bowl being assembled, fresh berries and granola being sprinkled from above, frozen motion, bright and appetizing colors, kitchen counter background, vertical 9:16 format."
      }
    ],
    "stream": false
  }'
```

### Community Post Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a YouTube community post image asking viewers to vote on the next video topic. Split design with two distinct halves: left side shows a mountain landscape in cool blue tones, right side shows an ocean sunset in warm orange tones, clean dividing line between them, 1200x675."
      }
    ],
    "stream": false
  }'
```

## Channel Banner Safe Zone Guide

The channel banner displays differently on each device:

```
Full image:     2560 x 1440 px (TV)
Desktop:        2560 x 423 px  (center horizontal strip)
Tablet:         1855 x 423 px  (narrower strip)
Mobile:         1546 x 423 px  (narrowest — THE safe zone)
```

Always design with the mobile safe zone (center 1546 x 423 px) containing all critical visual elements. The surrounding area provides additional context on larger screens.

## Channel Branding Consistency

- **Color palette** — pick 2-3 brand colors and use them across all assets
- **Visual theme** — maintain the same artistic style from banner to thumbnails
- **Recognition** — viewers should recognize your content instantly in their feed
- **Template system** — create a thumbnail template and vary only the subject per video
- **Seasonal updates** — refresh your banner quarterly while maintaining brand identity

## Workflow

```bash
# Step 1: Create the channel banner
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "YouTube channel banner for a science education channel. Deep space background with a nebula in blues and purples, molecular structures and atom symbols floating across the panoramic scene, curious and wonder-filled, 2560x1440 with main elements centered."
      }
    ],
    "stream": false
  }'

# Step 2: Create a matching thumbnail template
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "YouTube channel banner for a science education channel. Deep space background with a nebula in blues and purples, molecular structures and atom symbols floating across the panoramic scene, curious and wonder-filled, 2560x1440 with main elements centered."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Now create a matching video thumbnail background for a video about black holes. Same deep space color palette and style, but 16:9 format at 1280x720, with a dramatic black hole as the central subject and strong light distortion effects. Leave the left third clean for title text."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [YouTube Thumbnail](../../design/youtube-thumbnail/SKILL.md) — Dedicated thumbnail design
- [TikTok Content](../tiktok-content/SKILL.md) — Short-form video content
- [Instagram Content](../instagram-content/SKILL.md) — Cross-platform content
- [Social Media Post](../../design/social-media-post/SKILL.md) — General social graphics

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
