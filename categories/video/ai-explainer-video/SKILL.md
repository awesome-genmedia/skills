---
name: ai-explainer-video
description: "Create educational and product explainer videos using each::sense AI. Generate animated explanations, tutorial sequences, concept visualizations, and step-by-step demonstrations for products, services, and educational topics. Supports motion graphics, animated infographics, and visual storytelling. Use for: product demos, tutorial videos, educational content, onboarding videos, how-to guides, concept explanations, training materials. Triggers: explainer video, educational video, tutorial video, product demo, how-to video, animated explanation, concept video, training video, onboarding video, demo video, instruction video"
allowed-tools: Bash(curl *), WebFetch
---

# AI Explainer Video

Create educational and product explainer video clips using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": "Generate a video: an animated infographic showing the water cycle. A sun heats an ocean, water evaporates upward as visible steam, forms into clouds, rain falls onto mountains, water flows down rivers back to the ocean. Clean motion graphics style, soft blue and white palette, educational and clear."
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
        "content": "Generate a video: an animated infographic showing the water cycle. A sun heats an ocean, water evaporates upward as visible steam, forms into clouds, rain falls onto mountains, water flows down rivers back to the ocean. Clean motion graphics style, soft blue and white palette, educational and clear."
    }]
)

print(response.choices[0].message.content)
```

### With Visual Reference

Use product screenshots, diagrams, or slides as a starting point:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Animate this product screenshot into an explainer clip. Show the interface coming to life — buttons being clicked, menus opening, data flowing across the dashboard. Smooth motion graphics, professional SaaS product demo style."},
              {"type": "image_url", "image_url": {"url": "https://example.com/dashboard-screenshot.png"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time Server-Sent Events (SSE) responses, or `"stream": false` to receive the complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Explainer Video Types

| Type | Description | Best For |
|------|-------------|----------|
| **Process Visualization** | Step-by-step animated flow | How things work, workflows |
| **Product Demo** | UI walkthrough, feature showcase | SaaS, apps, platforms |
| **Concept Animation** | Abstract ideas made visual | Science, business concepts |
| **Comparison** | Side-by-side visual comparison | Before/after, product vs. competitor |
| **Data Visualization** | Animated charts and graphs | Reports, presentations |
| **Character Animation** | Animated characters explaining | Marketing, onboarding |

## Examples

### SaaS Product Feature

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: a clean motion graphics animation showing a smartphone screen. A finger taps to open an app, scrolls through a feed of AI-generated images, taps one to edit it, and the image transforms with a sparkle effect. Modern flat design, teal and white brand colors, smooth 60fps animation."
      }
    ],
    "stream": false
  }'
```

### Scientific Concept

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: an animated visualization of how a neural network learns. Show dots (neurons) in layers connected by lines (weights), data flowing from left to right, connections lighting up and strengthening, error signals flowing backward in red, clean dark background with glowing elements, educational motion graphics."
      }
    ],
    "stream": false
  }'
```

### Before/After Comparison

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Generate a video: split-screen comparison animation. Left side shows a cluttered, slow-loading old website (gray, boring). Right side shows a modern, fast, beautiful redesign (colorful, clean). A slider wipe transitions between them. Clean motion graphics, professional, side labels visible."
      }
    ],
    "stream": false
  }'
```

## Storyboard Workflow

Build an explainer video shot by shot:

```bash
# Scene 1: The Problem
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a video: a frustrated office worker surrounded by stacks of paper, cluttered desk, slow spinning loading icon on their computer screen, dim lighting, overwhelmed atmosphere, animated illustration style"}],
    "stream": false
  }'

# Scene 2: The Solution
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a video: the same office worker now smiling, clean desk with a single laptop showing a clean dashboard, papers flying away, bright lighting fills the room, energetic upward motion, animated illustration style matching the previous"}],
    "stream": false
  }'

# Scene 3: The Result
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": "Generate a video: animated graph showing productivity rising upward, green arrows, checkmarks appearing, happy team celebrating in the background, confetti, bright and positive, motion graphics, same illustration style"}],
    "stream": false
  }'
```

## Prompt Tips

- **Describe the sequence of events**: Explainers are about flow, not just a static scene
- **Use clear visual language**: "arrows pointing from A to B," "data flowing left to right"
- **Specify the style consistently**: Use the same style description across all clips for a cohesive video
- **Keep it simple**: One concept per clip — combine multiple clips in post-production
- **Mention pacing**: "smooth and slow" for educational, "snappy and energetic" for marketing

## Related Skills

- [Text to Video](../text-to-video/SKILL.md) — General video generation
- [AI Product Video](../ai-product-video/SKILL.md) — Product showcase videos
- [Image to Video](../image-to-video/SKILL.md) — Animate diagrams and slides

## Related Models

- [wan-2-1-14b](../../../models/wan-2-1-14b/SKILL.md) — High quality video generation
- [hailuo-minimax-video-01](../../../models/hailuo-minimax-video-01/SKILL.md) — Fast video generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
