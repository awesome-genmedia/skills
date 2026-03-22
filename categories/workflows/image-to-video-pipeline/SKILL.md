---
name: image-to-video-pipeline
description: "Multi-step pipeline: generate an image then animate it to video using each::sense AI. First create a high-quality still image from a text prompt, then animate the result into a short video with motion and camera effects. Use for: image animation, still to video, photo animation, motion from image, animated stills. Triggers: image to video, animate image, still to video, photo to video, image animation, picture to video, animate photo, image to video pipeline, motion from image, bring image to life"
allowed-tools: Bash(curl *), WebFetch
---

# Image to Video Pipeline

Generate an image and then animate it into a video in a multi-step pipeline using [each::sense](https://docs.eachlabs.ai/sense/overview) — the intelligent AI agent that automatically selects the best model for your request.

## Quick Start

> Requires an each::labs API key. Get one at [eachlabs.ai](https://eachlabs.ai).

### Step 1: Generate the Image

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A majestic eagle perched on a snow-covered pine branch in a winter mountain landscape, dramatic morning light breaking through storm clouds, photorealistic wildlife photography, sharp detail on the feathers"
      }
    ],
    "stream": false
  }'
```

### Step 2: Animate to Video

Once you have the generated image URL from Step 1, use it as the reference image for animation:

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Animate this image: the eagle slowly spreads its wings preparing to take flight, snow particles drift gently in the wind, clouds move slowly in the background, subtle camera zoom in, cinematic wildlife documentary style"}
            ]
          }
    ],
    "stream": false
  }'
```

### Full Pipeline in Python

```python
from openai import OpenAI
import json

client = OpenAI(
    api_key="YOUR_EACHLABS_API_KEY",
    base_url="https://eachsense-agent.core.eachlabs.run/v1"
)

# Step 1: Generate the image
image_response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{
        "role": "user",
        "content": "A majestic eagle perched on a snow-covered pine branch in a winter mountain landscape, dramatic morning light breaking through storm clouds, photorealistic wildlife photography, sharp detail on the feathers"
    }]
)

image_result = image_response.choices[0].message.content
print("Step 1 - Image generated:", image_result)

# Extract image URL from the response
# (parse the URL from the response content)
image_url = "EXTRACTED_IMAGE_URL"

# Step 2: Animate the image into video
video_response = client.chat.completions.create(
    model="eachsense/beta",
    messages=[{
        "role": "user",
        "content": "Animate this image: the eagle slowly spreads its wings preparing to take flight, snow particles drift gently in the wind, clouds move slowly in the background, subtle camera zoom in, cinematic wildlife documentary style"
    }],
    # Images are included in the message content array above
)

video_result = video_response.choices[0].message.content
print("Step 2 - Video generated:", video_result)
```

### Streaming

Set `"stream": true` for real-time SSE responses, or `"stream": false` for complete result in a single response. Streaming is useful for showing progress in UIs; non-streaming is simpler for scripts and automation.

## Tips for Image-to-Video Pipeline

- **Generate a composition-ready still first** — the image quality directly affects the video quality.
- **Describe motion intentionally** — "slow pan," "gentle zoom," "subtle movement" works better than complex actions.
- **Keep motion descriptions simple** — one or two movements per clip for best results.
- **Match the motion to the subject** — landscape = slow pan, portrait = subtle expression change, action = dynamic movement.
- **Use cinematic language** — "dolly in," "crane shot up," "tracking shot left" for professional camera motion.

## Examples

### Landscape Animation

**Step 1: Generate the still**

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A serene Japanese garden with a red torii gate reflected in a still koi pond, cherry blossoms in full bloom, soft morning mist, photorealistic landscape photography"
      }
    ],
    "stream": false
  }'
```

**Step 2: Animate**

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Animate this scene: cherry blossom petals gently falling and landing on the pond surface creating small ripples, koi fish slowly swimming beneath the surface, a very gentle breeze moving the branches, slow cinematic pan from left to right"}
            ]
          }
    ],
    "stream": false
  }'
```

### Product Reveal

**Step 1: Generate the product shot**

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": "A premium perfume bottle on a reflective black surface, golden liquid inside a faceted crystal bottle, dramatic studio lighting with a single spotlight from above, luxury product photography, dark background"
      }
    ],
    "stream": false
  }'
```

**Step 2: Animate into a reveal**

```bash
curl -X POST https://eachsense-agent.core.eachlabs.run/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "X-API-Key: $EACHLABS_API_KEY" \
  -d '{
    "messages": [
      {
        "role": "user",
        "content": [
              {"type": "text", "text": "Animate this product shot: slow 360-degree rotation of the perfume bottle, light catching different facets as it turns, subtle sparkle effects on the crystal, smooth cinematic rotation, luxury brand commercial style"}
            ]
          }
    ],
    "stream": false
  }'
```

## Workflow: Complete Image-to-Video Pipeline

1. **Craft the image prompt** — Design the still image with animation potential in mind.
2. **Generate the base image** — Create a high-quality still with each::sense.
3. **Extract the image URL** — Parse the response to get the generated image URL.
4. **Design the motion** — Plan what elements should move and how.
5. **Animate the image** — Pass the image URL and motion description to each::sense.
6. **Post-process** — Add audio, captions, or additional effects as needed.

## Related Skills

- [Text to Multimedia](../text-to-multimedia/SKILL.md) — Image + video + audio from one prompt
- [Product Media Suite](../product-media-suite/SKILL.md) — Complete product media pipeline
- [Text to Image](../../image/text-to-image/SKILL.md) — Image generation
- [AI Educational Video](../../education/ai-educational-video/SKILL.md) — Educational video content

## Related Models

- [flux-2-max](../../../models/flux-2-max/SKILL.md) — High-quality source images
- [seedream-v4-5](../../../models/seedream-v4-5/SKILL.md) — Creative visual styles
- [nano-banana-pro](../../../models/nano-banana-pro/SKILL.md) — Fast pipeline iterations

## Documentation

- [each::sense Overview](https://docs.eachlabs.ai/sense/overview)
- [each::labs API](https://docs.eachlabs.ai)
