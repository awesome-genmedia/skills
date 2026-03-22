---
name: ai-face-swap
description: "Swap faces between photos realistically using each::sense AI. Transfer a face from one image onto another while preserving lighting, skin tone, and expression. Supports single and multi-face swaps with natural blending. Use for: entertainment, memes, movie poster parodies, cosplay previews, creative projects, social media content. Triggers: face swap, swap face, face replacement, face transfer, put my face on, face change, switch faces, face paste, face morph, swap heads"
allowed-tools: Bash(curl *), WebFetch
---

# AI Face Swap

Swap faces between photos with realistic blending and natural results using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

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
        "content": [
              {"type": "text", "text": "Swap the face from the first image onto the person in the second image. Keep the lighting, skin tone, and expression natural."},
              {"type": "image_url", "image_url": {"url": "https://example.com/source-face.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/target-photo.jpg"}}
            ]
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
        "content": "Swap the face from the first image onto the person in the second image. Keep the lighting, skin tone, and expression natural."
    }],
    # Images are included in the message content array above
)

print(response.choices[0].message.content)
```

### With Reference Image

Face swap requires reference images. Provide the source face and target photo via `image_urls`:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [{"role": "user", "content": [
              {"type": "text", "text": "Swap the face from image one onto the person in image two, matching the lighting and angle perfectly"},
              {"type": "image_url", "image_url": {"url": "https://example.com/my-face.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/target-body.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

> Images are sent inside messages using the OpenAI multimodal content format. Maximum 4 images per request.

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## How It Works

1. **Source image** — The photo containing the face you want to use
2. **Target image** — The photo where the face will be placed
3. **AI processing** — The model detects both faces, maps landmarks, and blends the source face onto the target while adjusting lighting, color, and perspective

## Best Practices for Input Photos

### Source Face (Image 1)
- Clear, well-lit, front-facing photo
- High resolution (at least 512x512)
- Minimal obstructions (no sunglasses, hands over face)
- Neutral or clear expression works best

### Target Photo (Image 2)
- Face clearly visible and not heavily occluded
- Similar angle to source face yields best results
- Good lighting and resolution

## Prompt Engineering Tips

### Specify the Direction

Always clarify which image is the source face and which is the target:

```
Swap the face from [image 1 description] onto [image 2 description]
```

### Quality Hints

Include quality instructions for better results:

```
Match the skin tone and lighting. Blend naturally around the jawline and hairline.
Preserve the original expression and head angle of the target.
```

## Examples

### Portrait Face Swap

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Take the face from the first photo and place it on the person in the second photo. The result should look like a natural portrait with proper skin tone matching and seamless blending around the edges."},
              {"type": "image_url", "image_url": {"url": "https://example.com/person-a-headshot.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/person-b-portrait.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Creative Costume Swap

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Swap my face from the first image onto the person wearing the medieval knight armor in the second image. Keep the armor and background unchanged, only replace the face."},
              {"type": "image_url", "image_url": {"url": "https://example.com/my-selfie.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/knight-portrait.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

### Group Photo Swap

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "In the group photo (second image), swap the face of the person on the far left with the face from the first image. Keep everyone else unchanged."},
              {"type": "image_url", "image_url": {"url": "https://example.com/new-face.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/group-photo.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Workflow

```bash
# Step 1: Basic face swap
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Swap the face from image one onto the person in image two. Natural blending, match skin tone."},
              {"type": "image_url", "image_url": {"url": "https://example.com/source.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/target.jpg"}}
            ]
          }
    ],
    "stream": false
  }'

# Step 2: Refine if needed
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "Swap the face from image one onto the person in image two. Natural blending, match skin tone."
      },
      {
        "role": "assistant",
        "content": "..."
      },
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Good result but the skin tone looks slightly off. Please adjust the skin tone to better match the target photo lighting and make the blend around the jawline smoother."},
              {"type": "image_url", "image_url": {"url": "https://example.com/source.jpg"}},
              {"type": "image_url", "image_url": {"url": "https://example.com/target.jpg"}}
            ]
          }
    ],
    "stream": false
  }'
```

## Related Skills

- [AI Beauty Filter](../ai-beauty-filter/SKILL.md) — Enhance the swapped result
- [AI Face Restoration](../ai-face-restoration/SKILL.md) — Fix quality issues after swap
- [AI Expression Editor](../ai-expression-editor/SKILL.md) — Adjust expression post-swap
- [AI Caricature](../ai-caricature/SKILL.md) — Turn the result into a caricature
- [AI Aging Filter](../ai-aging-filter/SKILL.md) — Age the swapped face

## Related Models

- [face-swap](../../../models/face-swap/SKILL.md) — Dedicated face swap model
- [flux-kontext-pro](../../../models/flux-kontext-pro/SKILL.md) — Image editing with context
- [pulid-flux](../../../models/pulid-flux/SKILL.md) — Identity-preserving generation

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
