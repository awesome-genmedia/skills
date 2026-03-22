---
name: youtube-thumbnail
description: "Design click-worthy YouTube thumbnails using each::sense AI. Generate attention-grabbing thumbnail images with bold visuals, dramatic expressions, contrasting colors, and high-impact compositions optimized for YouTube's grid layout. Use for: YouTube thumbnails, video thumbnails, clickbait visuals, channel branding, video preview images. Triggers: youtube thumbnail, video thumbnail, thumbnail design, youtube cover, click-worthy thumbnail, thumbnail maker, video preview, youtube graphic, yt thumbnail"
allowed-tools: Bash(curl *), WebFetch
---

# YouTube Thumbnail Design

Design click-worthy YouTube thumbnails that drive views using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a YouTube thumbnail for a tech review video. Split composition with a glowing smartphone on the left and an explosion of colorful app icons on the right, dark background, dramatic lighting, bold and vibrant, 16:9 aspect ratio."
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
        "content": "Create a YouTube thumbnail for a tech review video. Split composition with a glowing smartphone on the left and an explosion of colorful app icons on the right, dark background, dramatic lighting, bold and vibrant, 16:9 aspect ratio."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Provide a frame from your video or a style reference for consistent channel branding:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a YouTube thumbnail using this video frame as a base. Add dramatic lighting, increase contrast, make the background darker and more cinematic, 16:9 aspect ratio."
      }
    ],
    "image_urls": ["https://example.com/video-frame.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Thumbnail Anatomy

| Element | Purpose | Tip |
|---------|---------|-----|
| **Subject** | Primary focal point | Place on the left or right third |
| **Background** | Sets mood and context | Dark backgrounds increase contrast |
| **Color contrast** | Draws the eye | Use complementary colors |
| **Negative space** | Area for text overlay | Reserve 30% for title text |
| **Emotion** | Creates connection | Dramatic expressions or reactions |

## Prompt Engineering Tips

### Keywords That Work

```
YouTube thumbnail, dramatic lighting, bold contrast, vibrant saturated colors,
cinematic composition, dark background, eye-catching, 16:9 aspect ratio,
high impact visual, attention-grabbing, split composition, spotlight effect
```

### Keywords to Avoid

```
subtle and muted — thumbnails need to pop at small sizes
lots of small details — lost in YouTube's grid view
text-heavy — add text in post-production for reliability
realistic documentary style — too bland for thumbnail grid
```

### Prompt Structure

```
YouTube thumbnail for [topic], [subject description], [background/lighting], [color scheme], [composition notes], 16:9 aspect ratio
```

## Examples

### Cooking Channel Thumbnail

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a YouTube thumbnail for a cooking video. A perfectly plated gourmet burger with melting cheese and steam rising, dramatic dark background with warm spotlight, ultra close-up food photography style, vibrant colors, 16:9."
      }
    ],
    "stream": false
  }'
```

### Science Explainer Thumbnail

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a YouTube thumbnail for a space science video. A massive black hole warping light around it, stars streaking into the event horizon, deep blue and purple cosmic colors, dramatic and awe-inspiring, cinematic 16:9 aspect ratio."
      }
    ],
    "stream": false
  }'
```

### Before/After Transformation Thumbnail

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a YouTube thumbnail showing a dramatic room makeover. Split down the middle: left side is a dull, cluttered room in desaturated tones, right side is the same room transformed into a stylish modern space with warm lighting and vibrant colors, 16:9."
      }
    ],
    "stream": false
  }'
```

## Click-Through Rate Tips

- **Face close-ups** with exaggerated expressions consistently outperform other thumbnail styles
- **3 or fewer elements** — thumbnails are viewed at ~120px wide on mobile
- **High contrast** between subject and background is critical
- **Bright yellow, red, and orange** accents draw attention in YouTube's white feed
- **Consistency** — use a recognizable style across your channel for brand recall

## Workflow

```bash
# Step 1: Generate the base thumbnail concept
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "YouTube thumbnail for a fitness transformation video. Athletic person mid-action with dynamic pose, bold red and black background, dramatic gym lighting, powerful and motivating, 16:9."
      }
    ],
    "stream": false
  }'

# Step 2: Refine with more specifics
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "YouTube thumbnail for a fitness transformation video. Athletic person mid-action with dynamic pose, bold red and black background, dramatic gym lighting, powerful and motivating, 16:9."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Add more dramatic backlighting creating a silhouette edge glow effect. Make the reds more saturated and add subtle smoke in the background."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [YouTube Content](../../social-media/youtube-content/SKILL.md) — Full YouTube channel art suite
- [Social Media Post](../social-media-post/SKILL.md) — General social media graphics
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
