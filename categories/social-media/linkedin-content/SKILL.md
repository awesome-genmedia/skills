---
name: linkedin-content
description: "Create LinkedIn professional content graphics using each::sense AI. Generate polished visuals for LinkedIn posts (1200x627), article cover images, carousel documents, company page banners, and thought leadership content. Optimized for the professional network with corporate-appropriate aesthetics. Use for: LinkedIn posts, article covers, LinkedIn banners, company page graphics, professional content, thought leadership visuals, LinkedIn carousel. Triggers: linkedin content, linkedin post, linkedin banner, linkedin graphic, linkedin visual, linkedin article, linkedin carousel, professional content, linkedin image, linkedin header, company page graphic"
allowed-tools: Bash(curl *), WebFetch
---

# LinkedIn Content

Create professional LinkedIn content graphics using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Create a LinkedIn post image for a thought leadership article about the future of remote work. Clean white to light gray gradient background, abstract illustration of connected nodes representing a distributed team, teal and navy blue professional palette, polished corporate style, 1200x627 proportions."
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
        "content": "Create a LinkedIn post image for a thought leadership article about the future of remote work. Clean white to light gray gradient background, abstract illustration of connected nodes representing a distributed team, teal and navy blue professional palette, polished corporate style, 1200x627 proportions."
    }]
)

print(response.choices[0].message.content)
```

### With Reference Image

Match company brand guidelines or existing LinkedIn content:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a LinkedIn post image that matches this company brand style. Same professional color palette and visual elements, but for a hiring announcement. Include abstract people silhouettes and upward growth elements, 1200x627 proportions."
      }
    ],
    "image_urls": ["https://example.com/company-brand.jpg"],
    "stream": false
  }'
```

> `image_urls` is a top-level request parameter (not inside messages). Maximum 4 images.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## LinkedIn Image Formats

| Format | Dimensions | Use Case |
|--------|-----------|----------|
| **Post Image** | 1200 x 627 px | Standard feed post |
| **Square Post** | 1080 x 1080 px | Carousel-style single |
| **Article Cover** | 1200 x 644 px | LinkedIn article header |
| **Company Banner** | 1128 x 191 px | Company page header |
| **Personal Banner** | 1584 x 396 px | Personal profile header |
| **Carousel Slide** | 1080 x 1080 px | Document carousel pages |
| **Event Cover** | 1776 x 444 px | LinkedIn event image |

## Prompt Engineering Tips

### Keywords That Work

```
LinkedIn post image, professional and polished, corporate aesthetic,
clean layout, business-appropriate, thought leadership visual,
subtle abstract elements, professional color palette, trustworthy,
modern corporate, executive-level design, refined and authoritative
```

### Keywords to Avoid

```
casual or playful — LinkedIn is a professional network
loud neon colors — feels unprofessional
meme-style graphics — undermines credibility
cluttered or busy — professionals scroll quickly
```

### Prompt Structure

```
LinkedIn [format] for [topic/purpose], [visual elements], [color palette], [professional style], [dimensions]
```

## Examples

### Company Milestone Announcement

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a LinkedIn post graphic for a company milestone celebration. Abstract upward trajectory of golden light particles forming an ascending curve on a deep navy background, premium and celebratory without being flashy, gold and navy corporate palette, 1200x627 proportions."
      }
    ],
    "stream": false
  }'
```

### Industry Insights Post

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a LinkedIn post image for an AI industry analysis. Clean light background with subtle hexagonal grid pattern, a stylized magnifying glass over a data chart illustration, teal and charcoal professional tones, analytical and insightful mood, 1200x627."
      }
    ],
    "stream": false
  }'
```

### Job Posting Graphic

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Design a LinkedIn hiring post graphic. Welcoming office environment illustration with abstract silhouettes of a diverse team collaborating, warm daylight tones, modern open office aesthetic, inviting and inclusive, teal and warm gray palette, 1200x627 with space for job title text overlay."
      }
    ],
    "stream": false
  }'
```

### Personal Brand Banner

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Create a LinkedIn personal profile banner for a product management leader. Clean gradient from white to soft steel blue, subtle abstract product roadmap illustration on the right side with milestone dots and connecting lines, professional and forward-thinking, 1584x396 proportions with the left side clean."
      }
    ],
    "stream": false
  }'
```

## LinkedIn Content Best Practices

- **Professional tone** — LinkedIn users expect polished, business-appropriate visuals
- **Blue dominates** — blues convey trust and professionalism; it is the most successful color family on LinkedIn
- **Light backgrounds** perform better in LinkedIn's white feed than dark backgrounds
- **Single image posts** get 2x more engagement than text-only posts
- **Carousel documents** (uploaded as PDFs) get the highest engagement rate of all formats
- **Consistency builds authority** — post with the same visual template regularly

## LinkedIn Carousel Strategy

Generate a cohesive set of carousel slides:

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

slides = [
    "Title slide: bold topic statement area, abstract ascending arrows, navy background",
    "Content slide: clean layout with icon placeholder on left, text area on right, white background with navy accent",
    "Statistics slide: large number display area with subtle chart illustration, light gray background",
    "Summary slide: key takeaways layout with checkmark icons, gradient navy to teal",
    "CTA slide: follow/connect prompt area, matching navy background with subtle pattern"
]

for i, slide_desc in enumerate(slides, 1):
    response = client.chat.completions.create(
        model="eachsense/beta",
        messages=[{
            "role": "user",
            "content": f"LinkedIn carousel slide {i}/5 about leadership principles. {slide_desc}. Professional corporate style, 1080x1080 square format."
        }]
    )
    print(f"Slide {i}: {response.choices[0].message.content}")
```

## Workflow

```bash
# Step 1: Generate the post image
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "LinkedIn post image for a quarterly business review summary. Clean professional layout, abstract ascending bar chart visualization in navy and teal on white background, corporate and data-driven, 1200x627."
      }
    ],
    "stream": false
  }'

# Step 2: Create a variation for an article cover
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "LinkedIn post image for a quarterly business review summary. Clean professional layout, abstract ascending bar chart visualization in navy and teal on white background, corporate and data-driven, 1200x627."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": "Adapt this to a LinkedIn article cover image. Same visual concept but slightly taller at 1200x644, add more context with subtle data dashboard elements in the background, keep the clean corporate style."
      }
    ],
    "stream": false
  }'
```

## Related Skills

- [Twitter Visuals](../twitter-visuals/SKILL.md) — Twitter/X post graphics
- [Social Media Post](../../design/social-media-post/SKILL.md) — General social graphics
- [Presentation Slides](../../design/presentation-slides/SKILL.md) — Slide deck visuals
- [OG Image Design](../../design/og-image-design/SKILL.md) — Link preview images

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — Highest quality image generation
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Best for text rendering in images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative and artistic styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
